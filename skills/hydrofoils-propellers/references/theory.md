# Condensed Theory Reference — MIT 2.23 Hydrofoils and Propellers

Condensed from Kerwin, *Lecture Notes on Hydrofoils and Propellers* (2001)
and the Spring 2007 syllabus. Notation follows Kerwin. Use this for quick
recall; consult `kerwin_notes.pdf` for full derivations.

## 1. 2D foil geometry and performance (Session 1)

- Section: chord `c`, span `b`, area `S = b·c`, aspect ratio `AR = b/c`.
- Airfoil: camber line `z(x)`, thickness distribution `t(x)`.
- Key coefficients: `C_L`, `C_D`, `C_M` (moment about quarter chord).
- Lift slope: `dC_L/dα ≈ 2π` (thin airfoil, rad/slope per radian).
- B-series: open propeller performance data (B1–B4, B-scope); used for
  preliminary propeller selection. `J = V_A / (n·D)`, `C_T = T / (ρ n² D⁴)`,
  `C_Q = Q / (ρ n² D⁴)`, `η = C_T·J / (2π C_Q)`.

## 2. Actuator disk theory (Session 2)

Steady, incompressible, inviscid flow through a disk of area `A`:

- Axial induction factor `a`: `V_A = V₀(1 - a)` (downstream of disk).
- Momentum: `T = 2 ρ A V₀² a (1 - a)`.
- Energy (Bernoulli across disk): `T = ρ A V₀² (1 - a) · 2a V₀` →
  `V_A = V₀(1 - a)`, wake velocity `V_w = V₀(1 - 2a)`.
- Thrust coefficient: `C_T = 2a(1 - a)` (per unit disk area, `A = πR²/4`
  for a propeller of radius `R`).
- Power: `P = T·V_A = 2 ρ A V₀³ a(1 - a)²`.
- Efficiency: `η = V_A / V_w = (1 - a)/(1 - 2a)`.
- **Betz limit**: maximum extractable power (turbine, `a = 2/3`):
  `C_P,max = 16/27 ≈ 0.593`. For a propeller (power added), the
  corresponding minimum induced loss is at `a = 1/3`.

## 3. Kutta-Joukowski (Session 3)

- Potential flow around a cylinder with circulation `Γ`:
  `L' = ρ V∞ Γ` (lift per unit span).
- Kutta condition: flow leaves the trailing edge smoothly → fixes `Γ`.
- Thin airfoil: `C_L = 2π sin(α + β_camber) ≈ 2π(α + β)` (radians).
- Zero-lift angle `α₀` set by camber; `C_L = 2π(α - α₀)`.

## 4. Vortex fundamentals (Session 4)

- Biot-Savart: velocity induced at point `P` by a vortex segment:
  `dV = (Γ / 4π) (dl × r) / |r|³`.
- Finite straight segment of strength `Γ`, perpendicular distance `d`,
  subtending angles `θ₁`, `θ₂`:
  `V = (Γ / 4π d)(sin θ₁ + sin θ₂)`.
- Infinite line: `V = Γ / (2π d)`.
- Vortex ring of radius `R`, on-axis at distance `x`:
  `V = Γ R² / (2 (R² + x²)^{3/2})`.
- Helical tip vortex from a blade: induced velocity at the hub is the
  classic propeller hub-vortex problem (see course image: pre-swirl
  stator cancels the hub vortex).

## 5. Lifting surface theory (Sessions 5–7)

- Bound vorticity `Γ(x, y)` on the lifting surface; free vorticity shed
  into the wake (Kelvin's 2nd theorem: vortex lines cannot end).
- Linearized lifting surface: small angle of attack, thin airfoil,
  `Γ` small → linear integral equation.
- **Lifting line** (high AR): wing represented by bound vortex along the
  span with circulation distribution `Γ(y)`.
  - Induced downwash `w(y)` from the trailing vortex sheet.
  - Local AoA: `α_eff = α - α₀ - w/V∞`.
  - `Γ(y) = π c(y) V∞ (α_eff)` (thin airfoil, per unit span).
  - Solve for `Γ(y)` → `C_L`, induced drag `C_{Di} = C_L² / (π e AR)`.
  - Elliptical `Γ(y)` minimizes induced drag (`e = 1`).
- **Vortex lattice method (VLM)**:
  - Discretize the bound vortex into segments; each segment sheds a
    trailing vortex to the next station.
  - Collocation: enforce the Kutta condition / no-penetration at
    collocation points (typically 1/4-chord points).
  - Linear system: `A Γ = b`, where `A` contains Biot-Savart influence
    coefficients.
  - 3D lifting surface: panel the meanline into a grid of `m` spanwise ×
    `n` chordwise stations; solve for `Γ_{i,j}`.
- **Glauert's method** (Session 7): Fourier series solution of the
  lifting line integral equation:
  `Γ(θ) = 2 b V∞ Σ Aₙ sin(nθ)`, `y = (b/2) cos θ`.
  - `A₁` (and higher `Aₙ`) from the collocation equations.
  - `C_L = π AR (A₁ + ½ A₂)`, `C_{Di} = π AR (A₁² + ½ A₂² + ...)`.
  - Recovers elliptical loading for a rectangular wing at moderate AR.

## 6. Propeller lifting line (Sessions 8–9)

- Blade element + momentum (BEM) or lifting line in a rotating frame.
- Annular element at radius `r`, width `dr`:
  - Local advance ratio: `J_r = V_A / (Ω r)`.
  - Axial induction `a(r)`, tangential induction `a'(r)`.
  - Local AoA: `α = arctan(V_A(1-a) / (Ω r (1 - a'))) - β_pitch`.
  - Force balance: `dT = ½ ρ Ω² r (1-a')² c C_L dr · B` (per blade row),
    `dQ = ½ ρ Ω² r² (1-a') c C_D dr · B + ...`.
- **Betz/Lerbs criteria**: optimal loading for minimum induced loss.
  - Betz: uniform axial induction `a = 1/3` (propeller) → minimum
    induced power for given thrust.
  - Lerbs: optimal radial distribution of circulation for a given
    thrust and torque (finite disk, tip losses).
- **Kramer diagram**: propeller performance map (`C_T` vs `J` at fixed
  `C_Q` or `η`); used for selection.
- Tip loss factor (Prandtl): `F(r) = (2/π) arccos( e^{-f} / cos(π r / B) )`,
  `f = B R / (2 π r sin φ)`.

## 7. 2D linear theory (Sessions 11–13)

- **Circulation distribution**: `γ(x)` along the chord;
  `Γ = ∫ γ dx`; `C_L = 2 ∫₀¹ γ(x/c) dx / V∞` (normalized).
- **Glauert's 2D theory**: Fourier series `γ(θ) = 2 V∞ Σ (A₀ + Aₙ) sin(nθ)`,
  `x = (c/2)(1 - cos θ)`.
  - Flat plate: `A₀ = α`, `Aₙ = 0` → `C_L = 2π α`.
  - Camber: `Aₙ` from the camber line slope.
- **Flat plate**: `C_L = 2π α`, `C_{D,ind} = 0` (inviscid), center of
  pressure at quarter chord.
- **Parabolic meanline**: `C_L = 2π(α - α₀)`, `α₀` from camber;
  `C_M` constant (independent of `α`) for a symmetric parabolic arc.
- **NACA data**: 4-digit series `NACA 2412` → max camber 2% at 40% chord,
  thickness 12%. Use for `C_L(α)`, `C_D`, `C_M` baselines.
- **Linearized thickness** (Session 13): thickness distribution adds a
  doublet-like source; `C_{D,th}` (wave drag precursor) from the
  thickness Fourier coefficients.
- **Lighthill's rule**: for a thin airfoil, the lift is determined by the
  camber line; thickness affects drag and moment but not `C_L` slope.
- **Leading edge suction**: the pressure peak at the LE contributes a
  suction moment; `C_M` about the LE = `C_M,AC/4 - ¼ C_L`.

## 8. 2D foil design and cavitation (Session 14)

- **Cavitation number**: `σ = (p∞ - p_v) / (½ ρ V²)`.
- Local cavitation: `σ_local = (p_local - p_v) / (½ ρ V²)`;
  cavitation begins when `σ_local < 0` (i.e., `p_local < p_v`).
- **Cavitation buckets**: `σ` vs `α` (or `C_L`) curves for a foil;
  the bucket shape shows the range of `α` over which the foil is
  cavitation-free at a given `σ`.
- **Brockett diagrams**: family of `C_L` vs `α` curves parameterized by
  `σ`; used to select the operating point for a given cavitation margin.
- Design goal: maximize `C_L` while keeping `σ_local > σ_margin` over
  the operating range.

## 9. 2D panel and vortex lattice methods (Sessions 15–16)

- **Panel method**: discretize the airfoil surface into flat panels;
  place source (and doublet) distributions on each panel; enforce
  no-penetration at panel collocation points + Kutta condition at TE.
  - Source panel: `Q_i` unknowns; influence coefficients from the
    2D source solution.
  - Doublet panels: enforce constant pressure (or use the
    source+doublet formulation).
- **2D vortex lattice**: bound vortex segments along the meanline +
  trailing vortex to the TE; collocation at 1/4-chord points;
  solve `A Γ = b` for segment strengths.
  - `C_L = 2 Γ_total / (c V∞)` (normalized).
  - Pressure distribution from the induced velocities → `C_p(x)`.
- Both methods are linear in `Γ`/`Q` for small AoA; iterate for
  finite AoA (update the geometry or use a nonlinear Kutta condition).

## 10. Boundary layers and XFOIL (Session 18)

- 2D BL: momentum thickness `θ`, displacement thickness `δ*`,
  shape factor `H = δ*/θ`.
- Separation: adverse pressure gradient + low `Re` → separation;
  `C_{D,fr}` from the BL integral equation.
- **XFOIL**: 2D viscous/inviscid interaction code.
  - Panel method (vortex lattice) for the inviscid flow.
  - BL integral method (Thwaites / Markeloff) coupled to the panels.
  - Outputs: `C_L(α)`, `C_D(α)`, `C_M(α)`, separation point,
    pressure distribution.
- Use XFOIL (or a modern equivalent like FLOPS/ALF) to get the
  `C_L, C_D, C_M` data that feed into 3D BEM/VLM propeller codes.

## 11. 3D methods (Sessions 20–21)

- **Vortex lattice propeller (PBD)**: panel the blade meanline in 3D;
  bound vortex lattice + trailing vortices; solve in the rotating frame
  (include the rotational velocity `Ω × r` in the local flow).
  - Unsteady: the wake convects; use a **free wake** (vortex filaments
    advected by the local flow) for accurate thrust/torque.
- **3D panel methods**: source/doublet panels on the blade surface;
  enforce no-penetration + Kutta; solve the linear system.
  - More accurate than VLM for thick blades / high AoA.
  - Heavier: `O(N²)` or `O(N log N)` with FMM.

## 12. Unsteady inflow and throughflow (Sessions 22–23)

- **Effective wake**: the wake is not a simple helix; it is distorted
  by the blade loading and the surrounding flow. Model it as a
  **free vortex sheet** advected by the local velocity.
- **Unsteady inflow**: `a(r, θ, t)`, `a'(r, θ, t)` vary with azimuth;
  solve the BEM/VLM equations at each azimuthal station, marching
  around the disk.
- **Throughflow solvers**: solve the throughflow (streamtube) equations
  for `V_r(r)`, `V_θ(r)`, `V_z(r)` across the disk; couple to the
  blade element forces.
  - Coupled methods: iterate between throughflow and BEM/VLM until
    convergence.
- **Stochastic wind** (turbines): `V(t)` is a random process;
  compute the expected `C_P` and the variance of the power output.

## 13. Wind turbines (Session 24)

- Same BEM/VLM machinery as propellers, with sign conventions flipped:
  - Power **extracted**: `P = T · V_A` (turbine slows the flow).
  - `C_P = P / (½ ρ A V₀³)`, `C_T = T / (½ ρ A V₀²)`.
  - Betz limit: `C_P,max = 16/27` at `a = 2/3`.
- Tip loss and hub loss factors as for propellers.
- **Optimal blade shape**: `C_L/C_D` maximized at each `r`;
  `Γ(r)` from the Lerbs/Betz optimal loading.
- **Stochastic wind**: `V(t) = V_mean + V_turb(t)`;
  `E[C_P]` and `σ_{C_P}` from the turbulence spectrum.

## 14. Waterjets (Session 25)

- Ducted propeller: the duct (stator) adds lift and modifies the
  inflow to the rotor.
- Thrust: `T = T_rotor + T_duct`; the duct can add 10–30% thrust.
- Open water characteristics: `C_T`, `C_Q`, `η` vs `J` for the
  combined unit.
- Cavitation: the duct LE is a cavitation-prone region; use the
  same `σ` analysis as for 2D foils.

## 15. Advanced propulsion (Session 26)

- Pre-swirl stators: cancel the hub vortex (see course image).
- Counter-rotating propellers: recover the swirl energy.
- Flettner rotors, cross-flow rotors: lift-based propulsion.
- Design trade: thrust, torque, efficiency, cavitation margin,
  structural loads, noise.

## Key equations quick sheet

| Quantity | Equation |
|---|---|
| Kutta-Joukowski | `L' = ρ V∞ Γ` |
| Biot-Savart (finite segment) | `V = (Γ / 4π d)(sin θ₁ + sin θ₂)` |
| Actuator disk thrust | `T = 2 ρ A V₀² a(1 - a)` |
| Betz limit | `C_P,max = 16/27` |
| Lift slope (2D) | `dC_L/dα = 2π` |
| Induced drag (3D) | `C_{Di} = C_L² / (π e AR)` |
| Glauert (lifting line) | `C_L = π AR (A₁ + ½ A₂)` |
| Cavitation number | `σ = (p∞ - p_v) / (½ ρ V²)` |
| Advance ratio | `J = V_A / (n D)` |
| Thrust coefficient | `C_T = T / (ρ n² D⁴)` |
| Propeller efficiency | `η = C_T J / (2π C_Q)` |
| Tip loss (Prandtl) | `F = (2/π) arccos(e^{-f} / cos(π r / B))` |

## Common pitfalls

- Mixing up propeller and turbine sign conventions (power added vs.
  extracted).
- Forgetting the tip loss factor in BEM → overpredicting `C_T` near
  the tip.
- Using `C_L = 2π α` for a cambered foil without subtracting `α₀`.
- Collocation at the wrong point in VLM (use 1/4-chord, not mid-chord).
- Ignoring the wake distortion in unsteady inflow → wrong `a'(r)`.
- Units: `Γ` in m²/s, `Ω` in rad/s, `n` in rev/s (`Ω = 2π n`).
