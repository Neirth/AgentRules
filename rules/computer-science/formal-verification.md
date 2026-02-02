# Formal Verification Rules

When applying formal verification to prove code correctness:

## Language Constraints

**CRITICAL:** Only apply to **C, C++, or Rust** code
- ✅ C: Deterministic, explicit memory, minimal runtime
- ✅ C++: Strong typing, explicit control, modern safety features
- ✅ Rust: Memory safety by design, ownership system
- ❌ Other languages: Side-effects, GC, runtime complexity make verification impractical

## Verification Approach

1. **Start Simple**
   - Level 1: Static analysis (Clang, Coverity)
   - Level 2: Runtime error checking (Frama-C/RTE, CBMC)
   - Level 3: Function contracts (pre/postconditions)
   - Level 4: Module verification
   - Level 5: Full system proof (seL4-style, only for critical systems)

2. **Choose Right Tool**
   - Quick bug finding: CBMC, KLEE (automatic)
   - Absence of runtime errors: Frama-C, abstract interpretation
   - Functional correctness: Frama-C/WP, Prusti (Rust)
   - Full verification: Isabelle/HOL, Coq (manual proof)

## Writing Verifiable Code

- Explicit bounds checks and error handling
- Simple control flow (minimize nesting, no complex loops)
- Minimal pointer arithmetic (use array indices)
- Fixed-size data structures over dynamic allocation
- Pure functions (separate computation from I/O)
- Clear loop invariants

## Specification Guidelines

- **Preconditions**: What must be true before function call
- **Postconditions**: What is guaranteed after
- **Loop invariants**: What's true at each iteration
- **Frame conditions**: What doesn't change
- Document all assumptions explicitly

## Common Pitfalls

- Loop invariants too weak to prove postcondition
- Undefined behavior in C/C++ (use `-fsanitize=undefined`)
- SMT solver timeouts (simplify code, add intermediate assertions)
- Forgetting to verify absence of runtime errors first

## When to Use

- **Always**: Safety-critical (medical, aerospace, automotive)
- **Always**: Security-critical (crypto, kernels, authentication)
- **Often**: Complex algorithms, data structures, parsers
- **Rarely**: UI code, I/O-heavy code, prototypes

**For detailed methodology:** Use `/formal-verification` skill
