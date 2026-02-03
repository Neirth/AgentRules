---
name: reverse-engineering
description: Apply clean room reverse engineering methodology to analyze external binaries, protocols, or code and produce legally defensible independent implementations using specification-based development
user-invocable: true
---

# Clean Room Reverse Engineering Rules

> *"The methodology was bulletproof. IBM never sued Columbia Data Products. They couldn't."*
> — On the first successful IBM BIOS clean room implementation (1982)

## Purpose

These rules establish the methodology for legally and ethically analyzing external binaries, protocols, or code to produce clean, independent implementations. The approach follows the **Clean Room Design** (also known as the Chinese Wall technique), proven successful in landmark cases including the IBM PC BIOS clones, the WINE project, video game emulators, and ReactOS.

---

## Table of Contents

- [Purpose](#purpose)
- [Core Principles](#core-principles)
- [The Clean Room Process](#the-clean-room-process)
- [Function Specification Template](#function-specification-template)
- [Specification Levels](#specification-levels)
- [System: File Compression Utility](#system-file-compression-utility)
- [Component: Compression Engine](#component-compression-engine)
- [Interface: Compressed File Format](#interface-compressed-file-format)
- [Test-Driven Reverse Engineering](#test-driven-reverse-engineering)
- [Test-Driven Specification](#test-driven-specification)
- [Legal and Ethical Framework](#legal-and-ethical-framework)
- [Documentation Requirements](#documentation-requirements)
- [Clean Room Development Log](#clean-room-development-log)
- [Historical Case Studies](#historical-case-studies)
- [Implementation Checklist](#implementation-checklist)
- [Remember](#remember)

---

## Core Principles

### 1. The Chinese Wall: Separation of Concerns

The foundation of clean room reverse engineering is the strict separation between **analysis** and **implementation**:

```
┌─────────────────────┐     ┌──────────────────┐     ┌─────────────────────┐
│     DIRTY ROOM      │     │     MONITOR      │     │     CLEAN ROOM      │
│  (Analysis Team)    │────▶│  (Specification  │────▶│ (Implementation     │
│                     │     │    Review)       │     │      Team)          │
│ • Examines original │     │ • Reviews specs  │     │ • Writes new code   │
│ • Documents behavior│     │ • Removes IP     │     │ • Never sees source │
│ • Creates specs     │     │ • Validates docs │     │ • Uses only specs   │
└─────────────────────┘     └──────────────────┘     └─────────────────────┘
```

**Historical Precedent:** Phoenix Technologies used this exact methodology in 1984 to create the first commercially available IBM-compatible BIOS, licensing it to OEMs for $290,000 and obtaining a $2 million insurance policy against copyright lawsuits.

### 2. The Specification is the Product

The analysis phase produces **functional specifications**, not code. These specifications must:

- Describe **what** the system does, never **how** it does it internally
- Document observable behavior, inputs, outputs, and state transitions
- Avoid any reference to implementation details, variable names, or code structure
- Be written in natural language or formal notation, not in programming constructs

**Example from WINE Project:** Developers use publicly available Microsoft documentation together with observed behavior of Windows to implement each Windows API call. They document behavior, not code.

---

## The Clean Room Process

### Phase 1: Analysis (Dirty Room)

The analysis team examines the target system and produces detailed behavioral specifications.

#### What to Document:

```markdown
## Function Specification Template

### Function Name: [Descriptive name based on behavior]

**Purpose:** [What problem does this solve for the user?]

**Observable Behavior:**
- When [condition], the system [behavior]
- Given [input], produces [output]
- If [error condition], responds with [error behavior]

**State Requirements:**
- Requires [preconditions]
- Modifies [state changes]
- Returns system to [postconditions]

**Timing Characteristics:**
- Expected latency: [range]
- Timeout behavior: [description]

**Edge Cases:**
- [Boundary condition]: [observed behavior]
- [Invalid input]: [error response]
```

#### Prohibited in Specifications:

- Actual source code or pseudocode mimicking implementation
- Variable names, function names, or identifiers from the original
- Memory layouts, data structure definitions copied verbatim
- Comments or documentation strings from the original
- Algorithmic descriptions that mirror the original implementation

### Phase 2: Specification Review (Monitor)

A designated monitor reviews all specifications before transfer to the clean room:

**Review Checklist:**
- [ ] No code or pseudocode present
- [ ] No copied identifiers or naming conventions
- [ ] Behavior described, not implementation
- [ ] Testable requirements defined
- [ ] No proprietary documentation referenced inappropriately

**If issues are found:** Return to Dirty Room with markup showing problems to resolve.

### Phase 3: Implementation (Clean Room)

The implementation team writes code using only the approved specifications.

#### Clean Room Requirements:

1. **Personnel:** Must have no prior exposure to the original implementation
2. **Documentation:** Can only access approved functional specifications
3. **Design Freedom:** May choose any algorithm, data structure, or approach
4. **Testing:** Must verify against behavioral specifications, not original code

---

## Specification Levels

### Level 1: High-Level Functional Specification

Describes the overall purpose and user-facing behavior:

```markdown
## System: File Compression Utility

**Purpose:** Reduces file sizes for storage and transmission efficiency.

**Core Functions:**
1. Compress: Takes input file, produces smaller output file
2. Decompress: Reverses compression, produces original file
3. Archive: Combines multiple files into single compressed package

**User Expectations:**
- Compression should be lossless for data files
- Progress indication for large files
- Error recovery for corrupted archives
```

### Level 2: Component Behavioral Specification

Describes individual component behaviors:

```markdown
## Component: Compression Engine

**Behavior:** Accepts byte stream, produces compressed byte stream.

**Observable Properties:**
- Output size <= Input size (with rare exceptions for incompressible data)
- Deterministic: Same input always produces same output
- Streamable: Can process data in chunks

**Error Conditions:**
- Insufficient memory: Returns error code, partial output discarded
- Invalid input: Graceful rejection with diagnostic information
```

### Level 3: Interface Specification

Describes external interfaces and protocols:

```markdown
## Interface: Compressed File Format

**Structure (from observed behavior):**
- Header: Identifies file type, contains metadata
- Body: Compressed data stream
- Footer: Integrity verification data

**Identification:**
- Files begin with identifiable signature bytes
- Version information present in header

**Interoperability:**
- Must produce files readable by reference implementation
- Must read files produced by reference implementation
```

---

## Test-Driven Reverse Engineering

Modern approach where specifications are expressed as test suites:

```markdown
## Test-Driven Specification

Instead of written specifications, provide executable tests:

**Advantages:**
- Tests are intentionally opaque (black-box)
- Verify inputs and outputs only
- No dependency on internal structure
- Automatic refactoring protection

**Process:**
1. Analysis team creates comprehensive test suites
2. Tests verify observable behavior only
3. Implementation team writes code to pass tests
4. Tests serve as living specification
```

**Precedent:** This approach has been advocated for modern clean room implementations as it "effectively screens all copyrightable expression from the development team."

---

## Legal and Ethical Framework

### Permitted Activities

Based on established legal precedents:

1. **Observational Analysis:** Running software and documenting behavior
2. **Black-Box Testing:** Testing inputs and outputs without examining code
3. **Protocol Analysis:** Capturing and documenting network communications
4. **Documentation Review:** Using publicly available official documentation
5. **Intermediate Copying:** Temporary copying for analysis purposes (Sony v. Connectix)

### Prohibited Activities

1. **Direct Code Copying:** Incorporating any original source code
2. **Literal Element Copying:** Copying code structure, organization, or sequence
3. **Trade Secret Violation:** Using information obtained through NDA breach
4. **Circumvention:** Bypassing technical protection measures (DMCA considerations)
5. **Leaked Material:** Using code or documentation from unauthorized disclosures

**Critical Warning from Dolphin Emulator Team:**
> "We cannot use anything of any sort from a leak. In fact, we can't even look at it. Dolphin is only legal because we are clean room reverse engineering the GameCube and Wii."

---

## Documentation Requirements

### Audit Trail

Maintain comprehensive records:

```markdown
## Clean Room Development Log

**Project:** [Name]
**Date Started:** [Date]
**Teams:**
- Dirty Room: [Names, no prior exposure to implementation verified]
- Monitor: [Names, qualifications]
- Clean Room: [Names, confirmed no prior exposure]

**Document Registry:**
| Document | Source | Classification | Approved By | Date |
|----------|--------|----------------|-------------|------|
| Spec v1  | Analysis | Dirty Room | [Monitor] | [Date] |

**Communication Log:**
| Date | From | To | Method | Content Summary |
|------|------|-----|--------|-----------------|
| | Dirty | Monitor | Encrypted | Spec review request |
```

### Physical/Logical Separation

- Dirty and clean rooms should be physically or logically separated
- All communication must go through the designated monitor
- No direct contact between dirty and clean team members
- Separate version control repositories

---

## Historical Case Studies

### IBM BIOS Clone (Columbia Data Products, 1982)

**Challenge:** Create IBM PC compatible computer without infringing BIOS copyright.

**Method:**
1. Team One documented every BIOS function: display initialization, keyboard handling, disk operations
2. Team Two (isolated) implemented from specifications alone

**Result:** Complete compatibility. IBM never sued—the methodology was legally sound.

### Phoenix Technologies BIOS (1984)

**Challenge:** Commercial BIOS for clone manufacturers.

**Method:**
1. Engineers studied IBM BIOS (~8KB code)
2. Described everything without referencing code
3. Second team wrote new BIOS from specifications

**Result:** Licensed to HP, Tandy, AT&T. Enabled the entire PC clone industry.

### WINE Project (Ongoing)

**Challenge:** Run Windows applications on Unix-like systems.

**Method:**
- Black-box testing reverse engineering
- Public Microsoft documentation
- Observed behavior analysis
- Comprehensive compliance test suites

**Status:** Actively maintained, legally defensible open-source project.

### Video Game Emulators (Dolphin, bsnes)

**Challenge:** Emulate game consoles without using proprietary code.

**Method:**
- Clean room hardware documentation
- No leaked SDKs or documentation
- Observable behavior only
- Open source for transparency

**Legal Status:** Protected under Sony v. Connectix (2000) precedent.

---

## Implementation Checklist

Before beginning a clean room project:

- [ ] Define clear project goals and scope
- [ ] Assemble separate dirty and clean teams
- [ ] Verify no team member has prior exposure to target implementation
- [ ] Establish communication protocols through monitor
- [ ] Set up separate development environments
- [ ] Document all sources of information
- [ ] Create specification templates
- [ ] Prepare test suites for validation
- [ ] Obtain legal review of process
- [ ] Maintain comprehensive audit trail

---

## Remember

> *"Functionality cannot be monopolized through copyright. Columbia Data Products proved this in 1982. Compaq scaled it. Phoenix commercialized it. The legal precedents matter."*

The goal is not to copy—it is to understand and reimplement. The specification is the bridge between understanding and creation, and it must remain free of any protected expression.

**When in doubt:**
1. Document behavior, not implementation
2. Describe what happens, not how it happens
3. Test outputs, not internals
4. Maintain separation, always
