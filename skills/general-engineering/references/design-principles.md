## Design Principles

### KISS: Keep It Simple, Stupid

> *"Simplicity is the ultimate sophistication."* — Leonardo da Vinci

**Why Simplicity Matters:**
- Fewer parts = fewer failure modes
- Easier to understand = easier to maintain
- Simpler systems = more reliable
- Lower cost to produce and support

**Applying KISS:**
1. Start with the simplest design that could work
2. Add complexity only when justified
3. Can you remove anything without losing function?
4. Would a simpler design meet 90% of needs?

**Historical Example**: The AK-47 rifle's reliability comes from simplicity—only 8 moving parts, loose tolerances, operates when dirty.

### Factor of Safety (FoS)

Never design exactly to the limit:

```
Factor of Safety = Failure Load / Working Load
```

**Typical Values:**
- Steel structures: 1.5-2.0
- Brittle materials: 3.0-5.0
- Unknown loads: 4.0-6.0
- Human-carrying systems: 5.0-10.0

**Why Use FoS:**
1. **Material variability**: Properties vary batch-to-batch
2. **Load uncertainty**: Actual loads may exceed estimates
3. **Degradation**: Corrosion, wear, fatigue over time
4. **Model uncertainty**: Calculations are approximations
5. **Human safety**: Lives depend on conservative design

**Engineering Judgment**: Higher FoS for:
- Brittle failure modes (sudden, catastrophic)
- Poorly understood loading
- Difficult-to-inspect locations
- Critical safety systems

### Fail-Safe Design

Engineer systems to fail safely:

**Approaches:**

1. **Fail Passive**: System becomes safe when component fails
   - Example: Deadman switch releases when operator incapacitated
   - Example: Fire doors close automatically when power lost

2. **Fail Active**: System takes protective action on failure
   - Example: Emergency brakes engage on hydraulic failure
   - Example: Backup generator starts on main power failure

3. **Fail Operational**: System continues operating at reduced capacity
   - Example: Multi-engine aircraft can fly with one engine out
   - Example: RAID storage continues with one disk failed

**Design Questions:**
- What happens if component X fails?
- Does failure lead to hazard or just loss of function?
- Can we make the safe state the default state?
- Are failure modes obvious to operators?

### Redundancy

Critical systems need backup:

**Types:**

1. **Active Redundancy** (Parallel):
   - All systems operate simultaneously
   - Example: Multi-engine aircraft
   - Advantage: Instant failover
   - Disadvantage: All systems age together

2. **Standby Redundancy** (Series):
   - Backup activates on primary failure
   - Example: Emergency generator
   - Advantage: Backup stays fresh
   - Disadvantage: Switching delay and mechanism

3. **Diversity**:
   - Different approaches to same function
   - Example: GPS + inertial navigation
   - Advantage: Protects against common-mode failures
   - Disadvantage: Complex integration

**Calculate System Reliability:**
```
Parallel (OR logic): R_system = 1 - (1-R₁)(1-R₂)...(1-Rₙ)
Series (AND logic): R_system = R₁ × R₂ × ... × Rₙ
```

Example: Two independent systems each with 90% reliability:
- Series: 0.9 × 0.9 = 81% (worse)
- Parallel: 1 - (0.1 × 0.1) = 99% (better)

### Modularity

Divide complex systems into independent modules:

**Benefits:**
- **Testing**: Test modules independently
- **Maintenance**: Replace modules without affecting others
- **Development**: Parallel work by different teams
- **Reuse**: Standard modules across products
- **Understanding**: Easier to comprehend modular systems

**Principles:**
- High cohesion within modules (related functions together)
- Low coupling between modules (minimal dependencies)
- Well-defined interfaces between modules
- Information hiding (implementation details private)

**Example**: Personal computer with modular components (CPU, RAM, GPU, storage) vs. smartphone with integrated design. PC is more flexible; smartphone is more compact.

---
