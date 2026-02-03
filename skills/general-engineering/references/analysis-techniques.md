## Analysis Techniques

### Free Body Diagrams (FBD)

Fundamental tool for force analysis:

**Steps:**
1. **Isolate** the object or system of interest
2. **Draw** the object as a simple shape
3. **Identify** all external forces acting on the object
4. **Draw** force vectors with direction and magnitude
5. **Choose** coordinate system
6. **Apply** equilibrium equations

**Example Forces:**
- Weight (W = mg, acts at center of gravity)
- Normal forces (perpendicular to contact surface)
- Friction (parallel to contact surface, μN)
- Tension (along cable/rope, pulls only)
- Applied forces
- Pressure forces (distributed loads)

**Common Mistakes:**
- Including internal forces (only external forces on FBD)
- Forgetting weight force
- Wrong direction for friction or normal force
- Neglecting distributed loads

### Control Volume Analysis

For fluid systems and flow processes:

**Concept**: Define a fixed region in space, analyze what crosses boundaries.

**Generic Balance:**
```
[Rate IN] - [Rate OUT] + [Generation] - [Consumption] = [Accumulation]
```

**Applications:**

**Mass Balance:**
```
ṁ_in - ṁ_out = dm_cv/dt
```

**Energy Balance:**
```
Q̇_in + Ẇ_in + Σṁ_in*h_in = Q̇_out + Ẇ_out + Σṁ_out*h_out + dE_cv/dt
```

**Momentum Balance:**
```
ΣF_external = Σṁ_out*v_out - Σṁ_in*v_in + d(mv)_cv/dt
```

**Choosing Control Volume:**
- Include region where you want to know conditions
- Place boundaries where conditions are known or simpler
- Boundaries can be real surfaces or imaginary planes
- Make boundary perpendicular to flow for easier calculation

### Dimensional Analysis

Check equation validity and develop scaling relationships:

**Fundamental Dimensions:**
- M: Mass (kg)
- L: Length (m)
- T: Time (s)
- I: Electric current (A)
- Θ: Temperature (K)
- N: Amount of substance (mol)
- J: Luminous intensity (cd)

**Dimensional Homogeneity:**

Every term in an equation must have the same dimensions.

**Example:**
```
F = ma
[M·L·T⁻²] = [M]·[L·T⁻²] ✓ Valid
```

**Buckingham Pi Theorem:**

If you have n variables and m fundamental dimensions, you can form (n-m) dimensionless groups.

**Application: Drag Force on a Sphere**

Variables: Drag force (F), velocity (v), fluid density (ρ), fluid viscosity (μ), sphere diameter (d)

Dimensional analysis yields:
```
C_D = F / (½ρv²A)  (Drag coefficient)
Re = ρvd/μ          (Reynolds number)
```

Where C_D = f(Re), determined experimentally.

### Order of Magnitude Estimation

**Fermi Estimation** (named after Enrico Fermi):

Make reasonable assumptions to estimate quantities without detailed calculation.

**Process:**
1. Break problem into estimable components
2. Make reasonable assumptions (state them clearly)
3. Round to nearest power of 10
4. Combine estimates
5. Check if result makes sense

**Example: How many piano tuners in New York City?**

Assumptions:
- NYC population: ~10⁷ people
- People per household: ~3
- Households with pianos: ~1/30
- Pianos per household: ~1
- Tunings per year: ~1
- Tunings per tuner per day: ~4
- Working days per year: ~250

Calculation:
- Households: 10⁷/3 ≈ 3×10⁶
- Pianos: 3×10⁶/30 ≈ 10⁵
- Tunings per year: 10⁵
- Tunings per tuner per year: 4×250 = 1000
- Tuners needed: 10⁵/10³ = 100

**Engineering Use:**
- Sanity check detailed calculations
- Quick feasibility assessment
- Identify critical parameters
- Determine measurement precision needed

### Sensitivity Analysis

Understand how output varies with input changes:

**Approach:**
1. Identify input parameters
2. Define baseline case
3. Vary each parameter individually (typically ±10%, ±20%)
4. Calculate effect on output
5. Identify critical parameters (high sensitivity)

**Sensitivity Index:**
```
S = (ΔOutput/Output) / (ΔInput/Input)
```

**Engineering Decisions:**
- Focus quality control on high-sensitivity parameters
- Refine models for critical variables
- Design for robustness to low-sensitivity variations
- Specify tighter tolerances where needed

---
