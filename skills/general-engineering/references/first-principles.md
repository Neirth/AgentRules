## First Principles Thinking

### Conservation Laws (Inviolable)

**Mass Conservation:**
```
ṁ_in - ṁ_out = dm/dt
```
Mass entering a control volume equals mass leaving plus accumulation. Applies to all physical systems.

**Energy Conservation:**
```
E_in - E_out = ΔE_stored
```
First Law of Thermodynamics. Energy changes form but is never created or destroyed.

**Momentum Conservation:**
```
ΣF = dp/dt
```
Newton's Second Law. Sum of forces equals rate of change of momentum.

**Applications:**
- Material balances in chemical processes
- Energy audits in thermal systems
- Force analysis in mechanical structures
- Current conservation in electrical circuits (Kirchhoff's Current Law)

### Equilibrium and Stability

Systems naturally seek equilibrium states:

**Static Equilibrium:**
```
ΣF = 0  (Force balance)
ΣM = 0  (Moment balance)
```

**Steady-State Equilibrium:**
- Input rate = Output rate
- No accumulation over time
- System properties constant

**Stability Types:**
1. **Stable**: System returns to equilibrium after disturbance (ball in valley)
2. **Unstable**: System diverges from equilibrium after disturbance (ball on peak)
3. **Neutral**: System remains in new position after disturbance (ball on flat surface)

**Engineering Implication**: Design for stable equilibria. Unstable systems require active control.

### Scaling Laws

Properties change non-linearly with size:

**Linear Scaling (L):**
- Length, height, width
- Perimeter

**Square Scaling (L²):**
- Area, surface area
- Heat transfer rates (proportional to area)
- Drag force at constant velocity

**Cubic Scaling (L³):**
- Volume
- Mass (if density constant)
- Structural loads (if proportional to weight)

**Engineering Consequence: Square-Cube Law**

When you double the size of an object:
- Surface area increases 4x (2²)
- Volume increases 8x (2³)

This explains why:
- Small insects can walk on water (surface tension dominates)
- Large animals need proportionally thicker bones (strength ∝ area, load ∝ volume)
- Heat dissipation becomes harder in large electronic systems
- Microprocessors need advanced cooling (volume generates heat, area dissipates it)

### Feedback and Control

Systems respond to their own outputs:

**Negative Feedback** (Stabilizing):
```
Output increases → Feedback decreases input → Output decreases
```
Examples: Thermostat, cruise control, homeostasis

**Positive Feedback** (Destabilizing):
```
Output increases → Feedback increases input → Output increases further
```
Examples: Runaway nuclear reaction, acoustic feedback (microphone near speaker)

**Engineering Practice:**
- Use negative feedback for stability and regulation
- Avoid or carefully manage positive feedback
- Consider lag time in feedback loops (can cause oscillation)
- Implement rate limiting to prevent instability

---
