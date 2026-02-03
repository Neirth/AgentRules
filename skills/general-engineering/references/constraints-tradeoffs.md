## Constraints and Trade-Offs

### The Engineering Triangle

Every project balances three primary constraints:

```
        Performance
           /\
          /  \
         /    \
        /      \
       /  Good  \
      /   Fast   \
     /    Cheap   \
    /              \
   /________________\
 Cost            Time
```

**Reality**: You can optimize two, but rarely all three.

- Good + Fast = Expensive
- Good + Cheap = Slow
- Fast + Cheap = Low quality

**Engineering Judgment**: Which constraint can yield?

### Physical Constraints

**Laws of Physics** (Cannot be violated):

- Cannot exceed speed of light
- Cannot violate thermodynamic laws (perpetual motion impossible)
- Cannot have efficiency > 100%
- Cannot exceed material strength limits
- Cannot violate conservation laws

**Material Limits:**

- Maximum stress before yield/fracture
- Maximum temperature before degradation
- Corrosion in certain environments
- Fatigue life under cyclic loading

**Thermodynamic Limits:**

Carnot efficiency (heat engine):
```
η_max = 1 - T_cold/T_hot
```

No real engine can exceed this.

### Economic Constraints

**Life Cycle Cost:**

```
LCC = Initial Cost + Operating Cost + Maintenance Cost - Salvage Value
```

Present worth of future costs:
```
PW = Σ (C_i / (1+r)^i)
```

Where r = discount rate, i = year

**Optimization**: Find design that minimizes LCC, not just initial cost.

**Value Engineering:**

Maximize function/cost ratio:
```
Value = Function / Cost
```

Increase value by:
- Improving function at same cost
- Maintaining function at lower cost
- Improving function more than cost increase

### Temporal Constraints

**Time-to-Market:**
- First mover advantage in competitive markets
- Window of opportunity may close
- Delays cost money (interest, opportunity cost)

**Project Schedule:**
- Critical path determines minimum time
- Crashing activities (adding resources) increases cost
- Parallel work where possible
- Risk of rushing: quality suffers

**Development vs. Production:**
- Rapid prototyping for development (3D printing, breadboards)
- Tooling time for production (molds, fixtures, test equipment)
- Transition planning essential

### Regulatory Constraints

**Codes and Standards:**
- Legally binding requirements
- Non-negotiable minimums
- Vary by jurisdiction
- May require certified professionals

**Permits and Approvals:**
- Building permits
- Environmental permits (air, water, waste)
- Safety certifications (UL, CE marking)
- Timeline for approval process

**Liability:**
- Product liability for defects
- Professional liability (errors and omissions)
- Environmental liability (cleanup costs)
- Contractual obligations

### Environmental Constraints

**Sustainability Considerations:**

**Energy Efficiency:**
- Operating energy over life cycle
- Embodied energy in materials
- Renewable energy integration

**Material Selection:**
- Renewable vs. finite resources
- Recycled content
- Recyclability at end of life
- Toxicity and environmental persistence

**Emissions:**
- Greenhouse gases
- Air pollutants
- Water pollutants
- Waste generation

**Impact Assessment:**

Life Cycle Assessment (LCA) quantifies environmental impact:
- Raw material extraction
- Manufacturing energy
- Transportation
- Use phase
- Disposal or recycling

### Human Factors

**Usability:**
- Intuitive interfaces
- Error prevention and recovery
- Accessibility for all users
- Cultural appropriateness

**Ergonomics:**
- Anthropometric data (human dimensions)
- Biomechanics (force limits, repetitive motion)
- Cognitive load (mental effort)
- Environmental factors (lighting, noise, temperature)

**Safety:**
- Obvious hazards identified
- Guards and interlocks
- Emergency stops accessible
- Clear warnings and labels

**Example: Control Design**

Principles:
- Controls located where operator expects
- Critical controls distinct (size, color, shape)
- Feedback confirming action (visual, audible, tactile)
- Inadvertent activation prevented (guards, two-hand control)

---
