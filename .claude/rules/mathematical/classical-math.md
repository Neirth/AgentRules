# Classical Mathematical Modeling Rules

When building mathematical models or numerical solutions:

## Modeling Process

1. **Define problem clearly** - Variables, parameters, constraints
2. **Start simple** - Linear before nonlinear
3. **Document assumptions** - Be explicit about limitations
4. **Validate at each step** - Compare with known solutions

## Linear Algebra

- Use appropriate decomposition: LU, QR, SVD, Cholesky
- Check condition number (κ >> 1 = ill-conditioned)
- Prefer stable algorithms (QR over normal equations)

## Differential Equations

- ODEs: RK4 for general, implicit for stiff problems
- PDEs: FDM (simple), FEM (complex geometry), FVM (conservation)
- Always verify stability conditions (CFL number)

## Optimization

- Convex problems: Interior point methods
- Unconstrained: L-BFGS for medium scale
- Check KKT conditions for constrained problems
- Verify convergence order with mesh refinement

## Graph Algorithms

- Shortest path: Dijkstra (non-negative), Bellman-Ford (negative)
- All pairs: Floyd-Warshall
- MST: Prim (dense) or Kruskal (sparse)

## Stochastic Methods

- Monte Carlo: O(1/√N) error regardless of dimension
- MCMC: Check burn-in, thinning, convergence (Gelman-Rubin)
- Use quasi-Monte Carlo for smooth integrands

## Numerical Stability

- Avoid catastrophic cancellation
- Check convergence order empirically
- Use Richardson extrapolation when possible

**For detailed methods:** Use `/classical-mathematical` skill
