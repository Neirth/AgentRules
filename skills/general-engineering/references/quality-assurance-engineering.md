## Quality Assurance

### Measure Twice, Cut Once

**Principle**: Verify before irreversible actions.

**Implementation:**
- **Calculations**: Independent check before fabrication
- **Dimensions**: Confirm measurements before cutting
- **Settings**: Verify parameters before starting process
- **Procedures**: Review steps before beginning
- **Critical operations**: Stop and check at hold points

**Cost-Benefit**: Verification is cheap; rework is expensive.

### Root Cause Analysis

**Five Whys Technique:**

Ask "why" repeatedly to get past symptoms to root cause.

**Example:**
1. Why did the machine stop? → Fuse blew
2. Why did the fuse blow? → Bearing seized
3. Why did the bearing seize? → Insufficient lubrication
4. Why insufficient lubrication? → Pump malfunction
5. Why did pump malfunction? → Debris clogged intake
6. Root cause: No filter on pump intake

**Fishbone (Ishikawa) Diagram:**

Systematic identification of potential causes:

```
    Methods          Materials          Machines
        │                 │                  │
        ├─────────────────┼──────────────────┤
        │                                    │
        │              Problem               │
        │                                    │
        ├─────────────────┼──────────────────┤
        │                 │                  │
   Measurement       Environment         People
```

**Corrective vs. Preventive:**
- **Corrective**: Fix the immediate problem
- **Preventive**: Change process to prevent recurrence

Always implement both.

### Statistical Process Control (SPC)

Monitor processes to detect abnormal variation:

**Control Charts:**

Plot measurements over time with control limits:

```
UCL ├─────────────────────────────────── (Upper Control Limit)
    │     ·   ·       ·     ·
 X̄  ├─────·─────·───·─────·───────────── (Mean)
    │   ·   ·       ·   ·       ·
LCL ├─────────────────────────────────── (Lower Control Limit)
```

**Control Limits (typically ±3σ):**
```
UCL = X̄ + 3σ
LCL = X̄ - 3σ
```

**Interpretation:**
- Points within limits: Common cause variation (normal)
- Points outside limits: Special cause variation (investigate)
- Trends or patterns: Potential process shift

**Out-of-Control Signals:**
1. Point beyond control limits
2. 8 consecutive points on one side of centerline
3. 6 points in a row steadily increasing or decreasing
4. 14 points alternating up and down

**Process Capability:**

Compare process variation to specification limits:

```
Cp = (USL - LSL) / (6σ)      (Capability)
Cpk = min((USL - μ)/(3σ), (μ - LSL)/(3σ))  (Capability with centering)
```

Interpretation:
- Cp < 1.0: Process incapable
- Cp = 1.33: Adequate
- Cp > 2.0: Excellent

### Design for Manufacturability (DFM)

Design products that are easy to make:

**Guidelines:**

1. **Minimize part count**: Fewer parts = simpler assembly
2. **Standardize**: Use common parts and materials
3. **Tolerances**: Specify only necessary precision
4. **Simplify assembly**: Self-aligning features, minimize fasteners
5. **Material selection**: Consider availability and processability
6. **Minimize operations**: Each step adds cost and variation

**DFM Checklist:**
- Can this part be eliminated or combined?
- Can we use a standard component?
- Are tolerances achievable with normal processes?
- Does design allow for easy fixturing?
- Are there accessibility issues for assembly/inspection?
- Can we reduce number of different fasteners?

### Life Cycle Thinking

Consider entire product life:

**Stages:**
1. **Raw material extraction**
2. **Manufacturing**
3. **Distribution**
4. **Use**
5. **Maintenance**
6. **End of life** (disposal, recycling, reuse)

**Design Considerations:**

**Durability:**
- Design for intended life
- Fatigue life under cyclic loading
- Wear resistance for moving parts
- Corrosion protection

**Maintainability:**
- Accessible inspection points
- Replaceable wear components
- Modular design for repair
- Diagnostic capabilities

**Serviceability:**
- Availability of spare parts
- Standard tools for maintenance
- Clear maintenance documentation
- Safety during maintenance

**End-of-Life:**
- Recyclable materials
- Easy disassembly
- Hazardous material identification
- Remanufacturing potential

---
