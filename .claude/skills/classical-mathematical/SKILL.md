---
name: classical-mathematical
description: Apply mathematical modeling, numerical analysis, and computational mathematics following curricula from MIT, Harvard, Oxford, Berkeley, Peking University, and UPV Valencia
user-invocable: true
---

# Classical Mathematical Modeling Rules

> *"Mathematics is the language with which God has written the universe."*
> — Galileo Galilei

## Purpose

These rules establish the methodology for mathematical modeling, numerical analysis, and computational mathematics. Drawing from the curricula of the world's leading institutions—**MIT**, **Harvard**, **Oxford**, **Berkeley**, **Peking University**, and **UPV Valencia**—this guide covers linear algebra, differential equations, optimization, graph theory, stochastic methods, and numerical simulation.

---

## The Academic Foundations

### World-Leading Mathematics Programs

```
┌─────────────────────────────────────────────────────────────────┐
│              ACADEMIC FOUNDATIONS                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  MIT (Massachusetts Institute of Technology) ───────────────    │
│  │ Course 18: Mathematics                                       │
│  │ • 18.06: Linear Algebra (Gilbert Strang)                     │
│  │ • 18.03: Differential Equations                              │
│  │ • 18.085: Computational Science and Engineering              │
│  │ • 18.330: Introduction to Numerical Analysis                 │
│  │                                                              │
│  │ "Basic subject on matrix theory emphasizing topics useful    │
│  │  in other disciplines: systems of equations, vector spaces,  │
│  │  eigenvalues, SVD, and positive definite matrices."          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  HARVARD (SEAS Applied Mathematics) ────────────────────────    │
│  │ • AM 21a: Multivariable Calculus                             │
│  │ • AM 105: Ordinary & Partial Differential Equations          │
│  │ • AM 120: Applied Linear Algebra & Big Data                  │
│  │ • AM 207: Stochastic Methods for Data Analysis               │
│  │ • AM 225: Advanced Scientific Computing                      │
│  │                                                              │
│  │ "Emphasis on numerical methods for ODEs and PDEs,            │
│  │  including finite element, finite volume, and spectral."     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  OXFORD (Mathematical Institute) ───────────────────────────    │
│  │ • Pure & Applied Mathematics core                            │
│  │ • Probability and Statistics specialization                  │
│  │ • Numerical Analysis                                         │
│  │ • Mathematical Modelling                                     │
│  │                                                              │
│  │ "Strong research in statistical machine learning and         │
│  │  scalable methods for Big Data."                             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  UC BERKELEY (EECS + Mathematics) ──────────────────────────    │
│  │ • EECS 127: Optimization Models and Applications             │
│  │ • EE 227B/C: Convex Optimization                             │
│  │ • Math 128A: Numerical Analysis                              │
│  │                                                              │
│  │ "Theory and algorithms for nonlinear optimization,           │
│  │  focusing on machine learning and data analysis."            │
│  │  — Textbooks: Boyd & Vandenberghe, Nesterov                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  PEKING UNIVERSITY ─────────────────────────────────────────    │
│  │ School of Mathematical Sciences                              │
│  │ • Computational Mathematics                                  │
│  │ • Numerical PDEs                                             │
│  │ • Scientific Computing                                       │
│  │                                                              │
│  │ Research: "Numerical solution of PDEs and computation        │
│  │  and simulation of particle fluid dynamics."                 │
│  │  — Prof. Pingwen Zhang (CSIAM President)                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  UPV VALENCIA ──────────────────────────────────────────────    │
│  │ MUCEIM: Computational Engineering & Industrial Mathematics   │
│  │ • Mathematical Modeling in Industry                          │
│  │ • Simulation in Logistics and Finance                        │
│  │ • Optimization and Heuristic Algorithms                      │
│  │ • Computational Fluid Dynamics                               │
│  │                                                              │
│  │ "Training in complex systems modeling, algorithm             │
│  │  development, optimization, and simulation."                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Linear Algebra Foundations

### The Language of Data (Gilbert Strang, MIT)

```
┌─────────────────────────────────────────────────────────────────┐
│              LINEAR ALGEBRA ESSENTIALS                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  VECTOR SPACES ─────────────────────────────────────────────    │
│  │                                                              │
│  │ A vector space V over ℝ satisfies:                           │
│  │ • Closure under addition and scalar multiplication           │
│  │ • Associativity, commutativity of addition                   │
│  │ • Existence of zero vector and additive inverses             │
│  │ • Distributivity of scalar multiplication                    │
│  │                                                              │
│  │ Key subspaces of matrix A (m×n):                             │
│  │ • Column space C(A): span of columns, dim = rank             │
│  │ • Row space C(Aᵀ): span of rows, dim = rank                  │
│  │ • Null space N(A): {x : Ax = 0}, dim = n - rank              │
│  │ • Left null space N(Aᵀ): {y : Aᵀy = 0}, dim = m - rank       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MATRIX DECOMPOSITIONS ─────────────────────────────────────    │
│  │                                                              │
│  │ LU Decomposition: A = LU                                     │
│  │ ├── L: Lower triangular                                      │
│  │ ├── U: Upper triangular                                      │
│  │ └── Use: Solving linear systems, O(n³) once, O(n²) per solve │
│  │                                                              │
│  │ QR Decomposition: A = QR                                     │
│  │ ├── Q: Orthogonal (QᵀQ = I)                                  │
│  │ ├── R: Upper triangular                                      │
│  │ └── Use: Least squares, numerical stability                  │
│  │                                                              │
│  │ Eigendecomposition: A = VΛV⁻¹                                │
│  │ ├── V: Matrix of eigenvectors                                │
│  │ ├── Λ: Diagonal matrix of eigenvalues                        │
│  │ └── Use: Powers of A, stability analysis, PCA                │
│  │                                                              │
│  │ SVD (Singular Value Decomposition): A = UΣVᵀ                 │
│  │ ├── U: Left singular vectors (m×m orthogonal)                │
│  │ ├── Σ: Singular values (m×n diagonal, σ₁ ≥ σ₂ ≥ ... ≥ 0)     │
│  │ ├── V: Right singular vectors (n×n orthogonal)               │
│  │ └── Use: Rank, pseudoinverse, low-rank approximation, PCA    │
│  │                                                              │
│  │ Cholesky: A = LLᵀ (for positive definite A)                  │
│  │ └── Use: Efficient for symmetric positive definite systems   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  THE FUNDAMENTAL THEOREM OF LINEAR ALGEBRA ─────────────────    │
│  │                                                              │
│  │ For any m×n matrix A:                                        │
│  │                                                              │
│  │   ℝⁿ = C(Aᵀ) ⊕ N(A)       (row space ⊥ null space)          │
│  │   ℝᵐ = C(A) ⊕ N(Aᵀ)       (column space ⊥ left null)        │
│  │                                                              │
│  │ dim C(A) + dim N(A) = n   (rank + nullity = n)               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Key Applications

```
┌─────────────────────────────────────────────────────────────────┐
│              LINEAR ALGEBRA APPLICATIONS                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  LEAST SQUARES ─────────────────────────────────────────────    │
│  │                                                              │
│  │ Problem: Minimize ||Ax - b||²                                │
│  │ Solution: x̂ = (AᵀA)⁻¹Aᵀb  (normal equations)                 │
│  │ Better: x̂ = R⁻¹Qᵀb        (via QR, more stable)              │
│  │                                                              │
│  │ Applications:                                                │
│  │ • Linear regression                                          │
│  │ • Curve fitting                                              │
│  │ • Signal processing                                          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  PRINCIPAL COMPONENT ANALYSIS (PCA) ────────────────────────    │
│  │                                                              │
│  │ 1. Center data: X̃ = X - mean(X)                              │
│  │ 2. Compute covariance: C = X̃ᵀX̃/(n-1)                         │
│  │ 3. Eigendecomposition: C = VΛVᵀ                              │
│  │ 4. Project: Z = X̃V_k (keep top k eigenvectors)               │
│  │                                                              │
│  │ Via SVD: X̃ = UΣVᵀ → principal components are columns of V    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MARKOV CHAINS ─────────────────────────────────────────────    │
│  │                                                              │
│  │ Transition matrix P: P[i,j] = P(state j | state i)           │
│  │ Stationary distribution π: πP = π                            │
│  │ π is the eigenvector of Pᵀ with eigenvalue 1                 │
│  │                                                              │
│  │ Applications: PageRank, random walks, queueing theory        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Differential Equations

### Ordinary Differential Equations (ODEs)

```
┌─────────────────────────────────────────────────────────────────┐
│              ODE CLASSIFICATION                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FIRST ORDER ───────────────────────────────────────────────    │
│  │                                                              │
│  │ Linear: dy/dt + p(t)y = q(t)                                 │
│  │ ├── Solution: y = e^(-∫p dt)[∫q·e^(∫p dt) dt + C]            │
│  │ └── Integrating factor method                                │
│  │                                                              │
│  │ Separable: dy/dt = f(t)g(y)                                  │
│  │ └── Solution: ∫dy/g(y) = ∫f(t)dt                             │
│  │                                                              │
│  │ Exact: M(t,y)dt + N(t,y)dy = 0, where ∂M/∂y = ∂N/∂t          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  SECOND ORDER LINEAR ───────────────────────────────────────    │
│  │                                                              │
│  │ ay'' + by' + cy = f(t)                                       │
│  │                                                              │
│  │ Homogeneous (f=0):                                           │
│  │ ├── Characteristic equation: ar² + br + c = 0                │
│  │ ├── Distinct real roots: y = c₁e^(r₁t) + c₂e^(r₂t)           │
│  │ ├── Repeated root: y = (c₁ + c₂t)e^(rt)                      │
│  │ └── Complex roots α±βi: y = e^(αt)(c₁cos(βt) + c₂sin(βt))    │
│  │                                                              │
│  │ Non-homogeneous: y = y_h + y_p                               │
│  │ ├── Undetermined coefficients                                │
│  │ └── Variation of parameters                                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  SYSTEMS OF ODEs ───────────────────────────────────────────    │
│  │                                                              │
│  │ dx/dt = Ax                                                   │
│  │ Solution: x(t) = e^(At)x₀                                    │
│  │                                                              │
│  │ Matrix exponential via eigendecomposition:                   │
│  │ If A = VΛV⁻¹, then e^(At) = Ve^(Λt)V⁻¹                       │
│  │                                                              │
│  │ Stability: System stable iff all eigenvalues have            │
│  │            negative real parts (Re(λᵢ) < 0)                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Partial Differential Equations (PDEs)

```
┌─────────────────────────────────────────────────────────────────┐
│              CLASSICAL PDEs                                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  HEAT EQUATION (Parabolic) ─────────────────────────────────    │
│  │                                                              │
│  │ ∂u/∂t = α∇²u                                                 │
│  │                                                              │
│  │ • Models: Heat conduction, diffusion                         │
│  │ • Properties: Smoothing, maximum principle                   │
│  │ • Solution methods: Separation of variables, Fourier series  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  WAVE EQUATION (Hyperbolic) ────────────────────────────────    │
│  │                                                              │
│  │ ∂²u/∂t² = c²∇²u                                              │
│  │                                                              │
│  │ • Models: Vibrating strings, acoustics, electromagnetics     │
│  │ • Properties: Finite propagation speed c                     │
│  │ • Solution: d'Alembert's formula (1D)                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  LAPLACE'S EQUATION (Elliptic) ─────────────────────────────    │
│  │                                                              │
│  │ ∇²u = 0                                                      │
│  │                                                              │
│  │ • Models: Steady-state heat, electrostatics, potential flow  │
│  │ • Properties: Mean value property, maximum principle         │
│  │ • Solution: Boundary value problem                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  NAVIER-STOKES (Fluid Dynamics) ────────────────────────────    │
│  │                                                              │
│  │ ρ(∂v/∂t + v·∇v) = -∇p + μ∇²v + f                             │
│  │                                                              │
│  │ • Models: Fluid flow (air, water, blood)                     │
│  │ • Millennium Prize Problem: Existence & smoothness           │
│  │ • Solved numerically via CFD                                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Numerical Methods

### Solving Linear Systems

```
┌─────────────────────────────────────────────────────────────────┐
│              NUMERICAL LINEAR ALGEBRA                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  DIRECT METHODS ────────────────────────────────────────────    │
│  │                                                              │
│  │ Gaussian Elimination: O(n³)                                  │
│  │ ├── Forward elimination → Upper triangular U                 │
│  │ └── Back substitution → Solution x                           │
│  │                                                              │
│  │ LU Factorization: O(n³) once, O(n²) per solve                │
│  │ ├── A = LU (or PA = LU with pivoting)                        │
│  │ └── Solve: Ly = b, then Ux = y                               │
│  │                                                              │
│  │ Cholesky: O(n³/3) for symmetric positive definite            │
│  │ └── A = LLᵀ (half the work of LU)                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  ITERATIVE METHODS (for large sparse systems) ──────────────    │
│  │                                                              │
│  │ Jacobi: x^(k+1) = D⁻¹(b - (L+U)x^(k))                        │
│  │ Gauss-Seidel: x^(k+1) = (D+L)⁻¹(b - Ux^(k))                  │
│  │ SOR: Successive Over-Relaxation (accelerated G-S)            │
│  │                                                              │
│  │ Krylov Subspace Methods:                                     │
│  │ ├── Conjugate Gradient (CG): For SPD matrices                │
│  │ ├── GMRES: General matrices                                  │
│  │ └── BiCGSTAB: Non-symmetric systems                          │
│  │                                                              │
│  │ Convergence: ||x^(k) - x*|| ≤ ρ^k ||x^(0) - x*||             │
│  │ where ρ = spectral radius of iteration matrix                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CONDITIONING ──────────────────────────────────────────────    │
│  │                                                              │
│  │ Condition number: κ(A) = ||A|| · ||A⁻¹||                     │
│  │ For SVD: κ(A) = σ_max / σ_min                                │
│  │                                                              │
│  │ Rule of thumb: Lose log₁₀(κ) digits of accuracy              │
│  │ κ ≈ 10^k → lose k digits to rounding errors                  │
│  │                                                              │
│  │ Ill-conditioned: κ >> 1 (sensitive to perturbations)         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Numerical ODE Solvers

```
┌─────────────────────────────────────────────────────────────────┐
│              ODE NUMERICAL METHODS                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  INITIAL VALUE PROBLEMS: dy/dt = f(t,y), y(t₀) = y₀            │
│                                                                 │
│  EULER METHODS ─────────────────────────────────────────────    │
│  │                                                              │
│  │ Forward Euler (explicit): y_{n+1} = y_n + h·f(t_n, y_n)      │
│  │ ├── Order: O(h)                                              │
│  │ ├── Simple but requires small h for stability                │
│  │ └── Conditionally stable                                     │
│  │                                                              │
│  │ Backward Euler (implicit): y_{n+1} = y_n + h·f(t_{n+1}, y_{n+1})│
│  │ ├── Order: O(h)                                              │
│  │ ├── Requires solving nonlinear equation                      │
│  │ └── Unconditionally stable (good for stiff problems)         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  RUNGE-KUTTA METHODS ───────────────────────────────────────    │
│  │                                                              │
│  │ RK4 (Classic 4th order):                                     │
│  │ k₁ = f(t_n, y_n)                                             │
│  │ k₂ = f(t_n + h/2, y_n + h·k₁/2)                              │
│  │ k₃ = f(t_n + h/2, y_n + h·k₂/2)                              │
│  │ k₄ = f(t_n + h, y_n + h·k₃)                                  │
│  │ y_{n+1} = y_n + (h/6)(k₁ + 2k₂ + 2k₃ + k₄)                   │
│  │                                                              │
│  │ ├── Order: O(h⁴)                                             │
│  │ └── Workhorse of ODE solvers                                 │
│  │                                                              │
│  │ Adaptive RK (e.g., RK45, Dormand-Prince):                    │
│  │ ├── Embedded error estimation                                │
│  │ └── Automatic step size control                              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MULTISTEP METHODS ─────────────────────────────────────────    │
│  │                                                              │
│  │ Adams-Bashforth (explicit): Uses previous y values           │
│  │ Adams-Moulton (implicit): More stable                        │
│  │ BDF (Backward Differentiation): For stiff problems           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STIFFNESS ─────────────────────────────────────────────────    │
│  │                                                              │
│  │ A problem is "stiff" when:                                   │
│  │ • Explicit methods require impractically small step sizes    │
│  │ • Solution has components with vastly different time scales  │
│  │                                                              │
│  │ Solutions:                                                   │
│  │ ├── Implicit methods (Backward Euler, BDF)                   │
│  │ └── Specialized stiff solvers (e.g., LSODA, CVODE)           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Numerical PDE Methods

```
┌─────────────────────────────────────────────────────────────────┐
│              PDE NUMERICAL METHODS                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FINITE DIFFERENCE METHOD (FDM) ────────────────────────────    │
│  │                                                              │
│  │ Approximate derivatives on a grid:                           │
│  │                                                              │
│  │ Forward:  ∂u/∂x ≈ (u_{i+1} - u_i) / Δx         O(Δx)         │
│  │ Backward: ∂u/∂x ≈ (u_i - u_{i-1}) / Δx         O(Δx)         │
│  │ Central:  ∂u/∂x ≈ (u_{i+1} - u_{i-1}) / 2Δx    O(Δx²)        │
│  │                                                              │
│  │ Second derivative:                                           │
│  │ ∂²u/∂x² ≈ (u_{i+1} - 2u_i + u_{i-1}) / Δx²    O(Δx²)         │
│  │                                                              │
│  │ Heat equation (explicit):                                    │
│  │ u_i^{n+1} = u_i^n + (αΔt/Δx²)(u_{i+1}^n - 2u_i^n + u_{i-1}^n)│
│  │ Stability: αΔt/Δx² ≤ 1/2 (CFL condition)                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FINITE ELEMENT METHOD (FEM) ───────────────────────────────    │
│  │                                                              │
│  │ 1. Weak formulation: Multiply by test function, integrate    │
│  │ 2. Discretize domain into elements (triangles, tetrahedra)   │
│  │ 3. Approximate solution as sum of basis functions            │
│  │ 4. Assemble global stiffness matrix                          │
│  │ 5. Solve linear system                                       │
│  │                                                              │
│  │ Advantages:                                                  │
│  │ ├── Handles complex geometries                               │
│  │ ├── Natural boundary conditions                              │
│  │ └── Adaptive mesh refinement                                 │
│  │                                                              │
│  │ Common elements: P1 (linear), P2 (quadratic), Q1 (bilinear)  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FINITE VOLUME METHOD (FVM) ────────────────────────────────    │
│  │                                                              │
│  │ • Conservative by construction                               │
│  │ • Natural for fluid dynamics (CFD)                           │
│  │ • Integrates flux over cell boundaries                       │
│  │                                                              │
│  │ ∂/∂t ∫_V u dV + ∮_S F·n dS = ∫_V S dV                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  SPECTRAL METHODS ──────────────────────────────────────────    │
│  │                                                              │
│  │ • Expand solution in global basis (Fourier, Chebyshev)       │
│  │ • Exponential convergence for smooth solutions               │
│  │ • Excellent for periodic domains                             │
│  │                                                              │
│  │ u(x) = Σ û_k φ_k(x)                                          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Optimization Theory

### Convex Optimization (Boyd & Vandenberghe, Berkeley)

```
┌─────────────────────────────────────────────────────────────────┐
│              OPTIMIZATION FUNDAMENTALS                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PROBLEM FORMULATION ───────────────────────────────────────    │
│  │                                                              │
│  │ minimize    f(x)           (objective function)              │
│  │ subject to  gᵢ(x) ≤ 0      (inequality constraints)          │
│  │             hⱼ(x) = 0      (equality constraints)            │
│  │                                                              │
│  │ Convex problem: f, gᵢ convex; hⱼ affine                      │
│  │ Key property: Local minimum = Global minimum                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CONVEXITY ─────────────────────────────────────────────────    │
│  │                                                              │
│  │ Function f is convex iff:                                    │
│  │ f(θx + (1-θ)y) ≤ θf(x) + (1-θ)f(y) for θ ∈ [0,1]             │
│  │                                                              │
│  │ Equivalently (if differentiable):                            │
│  │ f(y) ≥ f(x) + ∇f(x)ᵀ(y-x)  (lies above tangent)              │
│  │                                                              │
│  │ Equivalently (if twice differentiable):                      │
│  │ ∇²f(x) ⪰ 0  (Hessian is positive semidefinite)               │
│  │                                                              │
│  │ Common convex functions:                                     │
│  │ ├── Linear: aᵀx + b                                          │
│  │ ├── Quadratic: xᵀQx (Q ⪰ 0)                                  │
│  │ ├── Norms: ||x||                                             │
│  │ ├── Log-sum-exp: log(Σ exp(xᵢ))                              │
│  │ └── Negative entropy: Σ xᵢ log(xᵢ)                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DUALITY ───────────────────────────────────────────────────    │
│  │                                                              │
│  │ Lagrangian: L(x,λ,ν) = f(x) + Σλᵢgᵢ(x) + Σνⱼhⱼ(x)            │
│  │                                                              │
│  │ Dual function: g(λ,ν) = inf_x L(x,λ,ν)                       │
│  │ Dual problem: maximize g(λ,ν) s.t. λ ≥ 0                     │
│  │                                                              │
│  │ Weak duality: d* ≤ p* (always)                               │
│  │ Strong duality: d* = p* (under constraint qualifications)    │
│  │                                                              │
│  │ KKT Conditions (necessary and sufficient for convex):        │
│  │ ├── Stationarity: ∇f + Σλᵢ∇gᵢ + Σνⱼ∇hⱼ = 0                  │
│  │ ├── Primal feasibility: gᵢ ≤ 0, hⱼ = 0                       │
│  │ ├── Dual feasibility: λᵢ ≥ 0                                 │
│  │ └── Complementary slackness: λᵢgᵢ = 0                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Optimization Algorithms

```
┌─────────────────────────────────────────────────────────────────┐
│              OPTIMIZATION ALGORITHMS                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FIRST-ORDER METHODS ───────────────────────────────────────    │
│  │                                                              │
│  │ Gradient Descent:                                            │
│  │ x^{k+1} = x^k - α∇f(x^k)                                     │
│  │ ├── Convergence: O(1/k) for convex, O(ρ^k) for strongly cvx  │
│  │ └── Step size α: Fixed, line search, or Barzilai-Borwein     │
│  │                                                              │
│  │ Accelerated Gradient (Nesterov):                             │
│  │ y^k = x^k + β(x^k - x^{k-1})                                 │
│  │ x^{k+1} = y^k - α∇f(y^k)                                     │
│  │ └── Convergence: O(1/k²) — optimal for first-order           │
│  │                                                              │
│  │ Proximal Gradient (for composite objectives):                │
│  │ x^{k+1} = prox_{αg}(x^k - α∇f(x^k))                          │
│  │ └── Handles non-smooth regularizers (L1, nuclear norm)       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  SECOND-ORDER METHODS ──────────────────────────────────────    │
│  │                                                              │
│  │ Newton's Method:                                             │
│  │ x^{k+1} = x^k - [∇²f(x^k)]⁻¹∇f(x^k)                          │
│  │ ├── Convergence: Quadratic near solution                     │
│  │ └── Cost: O(n³) per iteration (Hessian inverse)              │
│  │                                                              │
│  │ Quasi-Newton (BFGS, L-BFGS):                                 │
│  │ ├── Approximate Hessian from gradient differences            │
│  │ ├── L-BFGS: Limited memory, O(n) storage                     │
│  │ └── Standard choice for medium-scale problems                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CONSTRAINED OPTIMIZATION ──────────────────────────────────    │
│  │                                                              │
│  │ Interior Point Methods:                                      │
│  │ ├── Barrier function approach                                │
│  │ ├── Polynomial time for LP, QP, SDP                          │
│  │ └── Standard for convex optimization                         │
│  │                                                              │
│  │ Active Set Methods:                                          │
│  │ ├── Track active constraints                                 │
│  │ └── Efficient for QP with few constraints                    │
│  │                                                              │
│  │ Sequential Quadratic Programming (SQP):                      │
│  │ └── Nonlinear constraints via QP subproblems                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COMBINATORIAL / HEURISTICS ────────────────────────────────    │
│  │                                                              │
│  │ For NP-hard problems:                                        │
│  │ ├── Simulated Annealing                                      │
│  │ ├── Genetic Algorithms                                       │
│  │ ├── Particle Swarm Optimization                              │
│  │ └── Tabu Search                                              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Graph Theory and Network Algorithms

### Fundamental Algorithms

```
┌─────────────────────────────────────────────────────────────────┐
│              GRAPH ALGORITHMS                                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  GRAPH REPRESENTATIONS ─────────────────────────────────────    │
│  │                                                              │
│  │ Adjacency Matrix: A[i,j] = 1 if edge (i,j) exists            │
│  │ ├── Space: O(V²)                                             │
│  │ ├── Edge lookup: O(1)                                        │
│  │ └── Good for dense graphs                                    │
│  │                                                              │
│  │ Adjacency List: List of neighbors for each vertex            │
│  │ ├── Space: O(V + E)                                          │
│  │ ├── Edge lookup: O(degree)                                   │
│  │ └── Good for sparse graphs                                   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  TRAVERSAL ─────────────────────────────────────────────────    │
│  │                                                              │
│  │ BFS (Breadth-First Search): O(V + E)                         │
│  │ ├── Uses queue                                               │
│  │ ├── Shortest path in unweighted graphs                       │
│  │ └── Level-order exploration                                  │
│  │                                                              │
│  │ DFS (Depth-First Search): O(V + E)                           │
│  │ ├── Uses stack (or recursion)                                │
│  │ ├── Topological sort                                         │
│  │ ├── Cycle detection                                          │
│  │ └── Connected components                                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  SHORTEST PATHS ────────────────────────────────────────────    │
│  │                                                              │
│  │ Dijkstra's Algorithm: O((V + E) log V) with heap             │
│  │ ├── Single-source shortest path                              │
│  │ ├── Non-negative edge weights only                           │
│  │ └── Greedy: always expand closest unvisited vertex           │
│  │                                                              │
│  │ Bellman-Ford: O(VE)                                          │
│  │ ├── Handles negative weights                                 │
│  │ └── Detects negative cycles                                  │
│  │                                                              │
│  │ Floyd-Warshall: O(V³)                                        │
│  │ ├── All-pairs shortest paths                                 │
│  │ └── Dynamic programming approach                             │
│  │                                                              │
│  │ A* Search: O(E) best case                                    │
│  │ ├── Informed search with heuristic h(n)                      │
│  │ ├── f(n) = g(n) + h(n)                                       │
│  │ └── Optimal if h is admissible (never overestimates)         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MINIMUM SPANNING TREE ─────────────────────────────────────    │
│  │                                                              │
│  │ Prim's Algorithm: O(E log V) with heap                       │
│  │ └── Grow tree from single vertex                             │
│  │                                                              │
│  │ Kruskal's Algorithm: O(E log E)                              │
│  │ └── Sort edges, add if no cycle (union-find)                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  NETWORK FLOW ──────────────────────────────────────────────    │
│  │                                                              │
│  │ Max-Flow Min-Cut Theorem:                                    │
│  │ "Maximum flow = Minimum cut capacity"                        │
│  │                                                              │
│  │ Ford-Fulkerson: O(E · max_flow)                              │
│  │ Edmonds-Karp (BFS): O(VE²)                                   │
│  │ Dinic's Algorithm: O(V²E)                                    │
│  │                                                              │
│  │ Applications:                                                │
│  │ ├── Bipartite matching                                       │
│  │ ├── Resource allocation                                      │
│  │ └── Network reliability                                      │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Stochastic Methods and Monte Carlo

### Monte Carlo Simulation

```
┌─────────────────────────────────────────────────────────────────┐
│              MONTE CARLO METHODS                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FUNDAMENTALS ──────────────────────────────────────────────    │
│  │                                                              │
│  │ "Monte Carlo methods are mainly used in three problem        │
│  │  classes: optimization, numerical integration, and           │
│  │  generating draws from a probability distribution."          │
│  │                                                              │
│  │ Key insight: Use randomness to solve deterministic problems  │
│  │                                                              │
│  │ Error: O(1/√N) regardless of dimension                       │
│  │ (Deterministic methods: error depends exponentially on dim)  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MONTE CARLO INTEGRATION ───────────────────────────────────    │
│  │                                                              │
│  │ Estimate: I = ∫_Ω f(x) dx                                    │
│  │                                                              │
│  │ Method: Sample x₁, ..., x_N uniformly from Ω                 │
│  │         Î = (Volume of Ω) × (1/N) Σ f(xᵢ)                    │
│  │                                                              │
│  │ Variance: Var(Î) = σ²/N where σ² = Var(f)                    │
│  │                                                              │
│  │ Variance Reduction Techniques:                               │
│  │ ├── Importance Sampling: Sample from g(x) ∝ |f(x)|p(x)       │
│  │ ├── Stratified Sampling: Divide domain into strata           │
│  │ ├── Control Variates: Use correlated known quantities        │
│  │ └── Antithetic Variates: Use negatively correlated samples   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MARKOV CHAIN MONTE CARLO (MCMC) ───────────────────────────    │
│  │                                                              │
│  │ Goal: Sample from distribution π(x) (often posterior)        │
│  │                                                              │
│  │ Metropolis-Hastings:                                         │
│  │ 1. Propose x' ~ q(x'|x)                                      │
│  │ 2. Accept with probability min(1, π(x')q(x|x')/π(x)q(x'|x))  │
│  │ 3. If accept: x ← x'; else: stay at x                        │
│  │                                                              │
│  │ Gibbs Sampling:                                              │
│  │ ├── Sample each dimension from conditional distribution      │
│  │ └── Special case of M-H with acceptance = 1                  │
│  │                                                              │
│  │ Diagnostics:                                                 │
│  │ ├── Burn-in period (discard initial samples)                 │
│  │ ├── Thinning (reduce autocorrelation)                        │
│  │ ├── Convergence: Gelman-Rubin R̂ statistic                   │
│  │ └── Effective sample size (ESS)                              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  QUASI-MONTE CARLO ─────────────────────────────────────────    │
│  │                                                              │
│  │ Use low-discrepancy sequences instead of random:             │
│  │ ├── Sobol sequences                                          │
│  │ ├── Halton sequences                                         │
│  │ └── Niederreiter sequences                                   │
│  │                                                              │
│  │ Error: O(1/N) vs O(1/√N) for standard MC                     │
│  │ (Better for smooth integrands in moderate dimensions)        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Stochastic Simulation

```
┌─────────────────────────────────────────────────────────────────┐
│              STOCHASTIC SIMULATION                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  "There is ample evidence to prove that certain systems can     │
│   only be modeled accurately by stochastic processes."          │
│                                                                 │
│  RANDOM NUMBER GENERATION ──────────────────────────────────    │
│  │                                                              │
│  │ Uniform: Linear Congruential, Mersenne Twister               │
│  │ Normal: Box-Muller, Ziggurat algorithm                       │
│  │ General: Inverse transform, Rejection sampling               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STOCHASTIC DIFFERENTIAL EQUATIONS (SDEs) ──────────────────    │
│  │                                                              │
│  │ dX_t = μ(X_t, t)dt + σ(X_t, t)dW_t                           │
│  │                                                              │
│  │ Where W_t is Brownian motion (Wiener process)                │
│  │                                                              │
│  │ Euler-Maruyama: X_{n+1} = X_n + μΔt + σ√Δt·Z_n               │
│  │ Milstein: Higher-order method for multiplicative noise       │
│  │                                                              │
│  │ Applications:                                                │
│  │ ├── Financial models (Black-Scholes, interest rates)         │
│  │ ├── Population dynamics                                      │
│  │ ├── Physics (Langevin equation)                              │
│  │ └── Neuroscience (neural activity)                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DISCRETE EVENT SIMULATION ─────────────────────────────────    │
│  │                                                              │
│  │ Components:                                                  │
│  │ ├── Event list (priority queue by time)                      │
│  │ ├── System state                                             │
│  │ ├── Clock                                                    │
│  │ └── Statistical counters                                     │
│  │                                                              │
│  │ Applications:                                                │
│  │ ├── Queueing systems                                         │
│  │ ├── Manufacturing                                            │
│  │ ├── Computer networks                                        │
│  │ └── Healthcare operations                                    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Mathematical Modeling Process

### The Modeling Cycle

```
┌─────────────────────────────────────────────────────────────────┐
│              MATHEMATICAL MODELING CYCLE                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│           ┌─────────────────────────────────────┐               │
│           │        REAL-WORLD PROBLEM           │               │
│           └──────────────┬──────────────────────┘               │
│                          │                                      │
│                          ▼ (1) Abstraction                      │
│           ┌─────────────────────────────────────┐               │
│           │       MATHEMATICAL MODEL            │               │
│           │  • Variables and parameters         │               │
│           │  • Assumptions and constraints      │               │
│           │  • Governing equations              │               │
│           └──────────────┬──────────────────────┘               │
│                          │                                      │
│                          ▼ (2) Analysis/Computation             │
│           ┌─────────────────────────────────────┐               │
│           │         MATHEMATICAL SOLUTION       │               │
│           │  • Analytical solutions             │               │
│           │  • Numerical approximations         │               │
│           │  • Simulations                      │               │
│           └──────────────┬──────────────────────┘               │
│                          │                                      │
│                          ▼ (3) Interpretation                   │
│           ┌─────────────────────────────────────┐               │
│           │         REAL-WORLD PREDICTIONS      │               │
│           └──────────────┬──────────────────────┘               │
│                          │                                      │
│                          ▼ (4) Validation                       │
│           ┌─────────────────────────────────────┐               │
│           │  COMPARE WITH DATA / OBSERVATIONS   │               │
│           └──────────────┬──────────────────────┘               │
│                          │                                      │
│                     ┌────┴────┐                                 │
│                     ▼         ▼                                 │
│               [Acceptable] [Refine model]                       │
│                     │         │                                 │
│                     ▼         └──────────▶ Back to (1)          │
│                [DEPLOY]                                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Model Selection Guidelines

```
┌─────────────────────────────────────────────────────────────────┐
│              WHEN TO USE WHAT                                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PROBLEM TYPE              MATHEMATICAL APPROACH                │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Equilibrium/steady-state  Algebraic equations, Laplace PDE    │
│  Time evolution            ODEs, parabolic/hyperbolic PDEs     │
│  Optimization              Convex optimization, LP, QP          │
│  Networks/routing          Graph algorithms, network flow       │
│  Uncertainty               Stochastic models, Monte Carlo       │
│  High dimensions           Monte Carlo, dimensionality reduction│
│  Complex geometry          FEM, boundary element methods        │
│  Wave propagation          Wave equation, spectral methods      │
│  Fluid flow                Navier-Stokes, CFD (FVM)             │
│  Population dynamics       ODEs, stochastic processes           │
│  Finance                   SDEs, Black-Scholes, Monte Carlo     │
│                                                                 │
│  COMPLEXITY GUIDELINES:                                         │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  "All models are wrong, but some are useful." — George Box      │
│                                                                 │
│  1. Start simple: Linear before nonlinear                       │
│  2. Add complexity only when needed                             │
│  3. Validate at each step                                       │
│  4. Understand limitations and assumptions                      │
│  5. Document everything                                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Numerical Stability and Error Analysis

### Sources of Error

```
┌─────────────────────────────────────────────────────────────────┐
│              ERROR ANALYSIS                                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TYPES OF ERROR ────────────────────────────────────────────    │
│  │                                                              │
│  │ Modeling Error: Real system ≠ Mathematical model             │
│  │ Discretization Error: Continuous ≠ Discrete approximation    │
│  │ Truncation Error: From Taylor series truncation              │
│  │ Round-off Error: Finite precision arithmetic                 │
│  │                                                              │
│  │ Total Error = Modeling + Discretization + Round-off          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FLOATING-POINT ARITHMETIC ─────────────────────────────────    │
│  │                                                              │
│  │ IEEE 754 Double Precision:                                   │
│  │ ├── 64 bits: 1 sign, 11 exponent, 52 mantissa                │
│  │ ├── Machine epsilon: ε ≈ 2.2 × 10⁻¹⁶                         │
│  │ └── Range: ≈ 10⁻³⁰⁸ to 10³⁰⁸                                 │
│  │                                                              │
│  │ Catastrophic Cancellation:                                   │
│  │ When subtracting nearly equal numbers, relative error        │
│  │ can be magnified enormously.                                 │
│  │                                                              │
│  │ Example: (1 + 10⁻¹⁵) - 1 = 0 in float64 (should be 10⁻¹⁵)    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STABILITY ─────────────────────────────────────────────────    │
│  │                                                              │
│  │ Forward Stability:                                           │
│  │ Algorithm produces small forward error for exact input       │
│  │                                                              │
│  │ Backward Stability:                                          │
│  │ Algorithm produces exact answer to slightly perturbed input  │
│  │ (Preferred criterion — easier to achieve and verify)         │
│  │                                                              │
│  │ Condition Number:                                            │
│  │ Sensitivity of output to input perturbations                 │
│  │ │Δoutput/output│ ≤ κ × │Δinput/input│                        │
│  │                                                              │
│  │ Well-posed problem + Stable algorithm = Accurate results     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CONVERGENCE ───────────────────────────────────────────────    │
│  │                                                              │
│  │ Order of Convergence:                                        │
│  │ Error = O(h^p) means error ∝ h^p as h → 0                    │
│  │                                                              │
│  │ Verification:                                                │
│  │ Run with h and h/2; ratio of errors ≈ 2^p                    │
│  │                                                              │
│  │ Richardson Extrapolation:                                    │
│  │ Improve O(h^p) to O(h^{p+1}) using two grid sizes            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Computational Tools

### Software Ecosystem

```
┌─────────────────────────────────────────────────────────────────┐
│              COMPUTATIONAL TOOLS                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PYTHON SCIENTIFIC STACK ───────────────────────────────────    │
│  │                                                              │
│  │ NumPy:   Arrays, linear algebra, FFT                         │
│  │ SciPy:   Optimization, integration, ODEs, sparse matrices    │
│  │ SymPy:   Symbolic mathematics                                │
│  │ Matplotlib: Visualization                                    │
│  │ Pandas:  Data manipulation                                   │
│  │ NetworkX: Graph algorithms                                   │
│  │ FEniCS:  Finite element methods                              │
│  │ PyMC:    Bayesian inference, MCMC                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  KEY SCIPY MODULES ─────────────────────────────────────────    │
│  │                                                              │
│  │ scipy.linalg:      LU, QR, SVD, eigenvalues, solve           │
│  │ scipy.optimize:    minimize, root, curve_fit                 │
│  │ scipy.integrate:   quad, odeint, solve_ivp                   │
│  │ scipy.interpolate: interp1d, spline                          │
│  │ scipy.sparse:      Sparse matrices, iterative solvers        │
│  │ scipy.fft:         Fast Fourier Transform                    │
│  │ scipy.stats:       Distributions, statistical tests          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  SPECIALIZED TOOLS ─────────────────────────────────────────    │
│  │                                                              │
│  │ MATLAB/Octave:     Traditional scientific computing          │
│  │ Julia:             High-performance scientific computing     │
│  │ R:                 Statistics and data analysis              │
│  │ Mathematica:       Symbolic computation                      │
│  │ COMSOL/ANSYS:      Commercial FEM/multiphysics               │
│  │ OpenFOAM:          Open-source CFD                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Checklist for Mathematical Modeling

### Before Modeling
- [ ] Problem clearly defined
- [ ] Key variables identified
- [ ] Data available for validation
- [ ] Appropriate mathematical framework chosen
- [ ] Assumptions documented

### During Implementation
- [ ] Numerical method appropriate for problem type
- [ ] Stability conditions satisfied (CFL, etc.)
- [ ] Convergence verified with mesh/step refinement
- [ ] Units consistent throughout
- [ ] Edge cases handled

### Validation
- [ ] Compare with analytical solutions (if available)
- [ ] Compare with experimental/observational data
- [ ] Sensitivity analysis performed
- [ ] Uncertainty quantified
- [ ] Results physically meaningful

---

## Remember

> *"Essentially, all models are wrong, but some are useful."*
> — George E.P. Box

> *"The purpose of computing is insight, not numbers."*
> — Richard Hamming

> *"In mathematics you don't understand things. You just get used to them."*
> — John von Neumann

**The Golden Rules:**
1. Start simple, add complexity incrementally
2. Validate at every step
3. Understand your assumptions
4. Check numerical stability
5. Verify convergence order
6. Document everything
