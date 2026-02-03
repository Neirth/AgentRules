## Risk Management

### Failure Modes and Effects Analysis (FMEA)

Systematic identification and mitigation of failures:

**FMEA Table:**

| Component | Failure Mode | Effects | Severity (S) | Causes | Occurrence (O) | Detection (D) | RPN | Actions |
|-----------|-------------|---------|--------------|--------|----------------|---------------|-----|---------|
| Bearing   | Seizes      | Machine stops | 7 | Lack of lubrication | 4 | 3 | 84 | Add lube monitor |

**Ratings (1-10):**
- **Severity**: How bad is the effect? (1=negligible, 10=catastrophic)
- **Occurrence**: How likely is the cause? (1=rare, 10=very frequent)
- **Detection**: Can we detect before failure? (1=certain detection, 10=cannot detect)

**Risk Priority Number (RPN):**
```
RPN = S × O × D
```

**Priority:**
- RPN > 100: High priority, address immediately
- RPN 50-100: Medium priority
- RPN < 50: Monitor

**Mitigation Strategies:**
1. **Reduce Severity**: Design changes to limit consequences
2. **Reduce Occurrence**: Prevent root causes
3. **Improve Detection**: Add sensors, inspections, tests

### Hazard Analysis

Identify and control hazards:

**Hazard Types:**
- **Energy**: Electrical, thermal, mechanical, radiation
- **Chemical**: Toxic, flammable, reactive, corrosive
- **Biological**: Infectious, allergenic
- **Ergonomic**: Repetitive strain, awkward postures
- **Environmental**: Noise, vibration, temperature

**Hierarchy of Controls:**

1. **Elimination**: Remove the hazard (best)
2. **Substitution**: Replace with less hazardous alternative
3. **Engineering Controls**: Isolate people from hazard (guards, ventilation)
4. **Administrative Controls**: Change work procedures, training
5. **PPE**: Personal protective equipment (last resort)

**Example: Noise Hazard**
1. Eliminate: Use different process (quiet technology)
2. Substitute: Replace loud equipment with quieter version
3. Engineering: Enclose noisy equipment, add damping
4. Administrative: Limit exposure time, rotate workers
5. PPE: Hearing protection (earplugs, earmuffs)

### Worst-Case Analysis

Design for extreme conditions:

**Approach:**
1. Identify critical parameters
2. Determine worst-case values (tolerances, environmental extremes)
3. Analyze performance under worst-case
4. Verify adequate margin

**Example: Structural Design**

Worst-case loading:
- Maximum dead load (tolerance stack-up)
- Maximum live load (code-specified)
- Environmental loads combined (wind + snow)
- Material properties at minimum (low strength)
- Elevated temperature (reduced strength)

**Combined Extremes:**

Question: Are all worst cases simultaneous?

Often no. Example:
- Maximum wind load rarely coincides with maximum snow
- Building codes specify load combinations with factors

**Load Combinations (LRFD):**
```
1.4D
1.2D + 1.6L
1.2D + 1.0L + 1.0W
1.2D + 1.0L + 0.5S
```

Where D=dead, L=live, W=wind, S=snow

### Defense in Depth

Multiple independent protective layers:

**Nuclear Safety Example:**

1. **Fuel pellets**: Ceramic form contains fission products
2. **Fuel cladding**: Zircaloy tubes contain pellets
3. **Reactor vessel**: Thick steel pressure boundary
4. **Containment building**: Reinforced concrete structure
5. **Emergency systems**: Cooling, shutdown systems
6. **Operating procedures**: Trained operators, rules

**Principle**: No single failure causes accident.

**General Application:**

For critical systems:
- Physical barriers (multiple containment)
- Functional redundancy (backup systems)
- Diverse methods (different technologies)
- Administrative controls (procedures, training)
- Monitoring and alarms (early detection)

### Continuous Monitoring

Detect problems before failure:

**Monitoring Types:**

1. **Condition Monitoring**: Measure parameters that indicate health
   - Vibration analysis (bearings, rotating equipment)
   - Thermography (hot spots, electrical connections)
   - Oil analysis (wear metals, contamination)
   - Acoustic emission (crack growth)

2. **Performance Monitoring**: Track operating metrics
   - Efficiency trends
   - Throughput rates
   - Energy consumption
   - Quality metrics

3. **Predictive Maintenance**: Forecast when maintenance needed
   - Remaining useful life estimation
   - Failure probability models
   - Prescriptive analytics

**Benefits:**
- Prevent unexpected failures
- Optimize maintenance timing
- Reduce downtime
- Extend equipment life
- Data-driven decision making

---
