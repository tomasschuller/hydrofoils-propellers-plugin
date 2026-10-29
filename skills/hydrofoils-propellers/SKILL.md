---
name: hydrofoils-propellers
description: 'Companion for MIT 2.23 Hydrofoils and Propellers (Kerwin). Use when the user asks about hydrofoil or propeller theory (lifting line/surface, vortex lattice, panel methods, actuator disk, Glauert, Betz, cavitation, 2D foil design), wants a course-style problem solved step by step, or needs to find the right course resource (problem sets, solutions, MPVL, exams, design projects).'
---

# Hydrofoils and Propellers (MIT 2.23)

Companion skill for the MIT OCW course **2.23 Hydrofoils and Propellers**
(Spring 2007, based on Prof. Justin Kerwin's lecture notes).

## When to use

- The user asks to **explain a concept** from the course: 2D foil theory,
  lifting line/surface theory, vortex lattice methods, panel methods,
  actuator disk, propeller/wind turbine performance, cavitation,
  boundary layers, unsteady inflow, waterjets, etc.
- The user asks to **solve a problem** in the style of the course problem
  sets or exams (vortex lattice setup, Glauert distributions, B-series
  selection, actuator disk, Fourier series, etc.).
- The user asks **where to find** a course resource (problem set, solution,
  MPVL code, exam, design project brief).

## Course root

The course materials live in the folder that contains this plugin:

```
<course-root>/
  pages/            # syllabus, assignments, exams, tools, course-notes (data.json)
  resources/
    kerwin_notes/   # kerwin_notes.pdf — the full lecture notes (primary text)
    ps1..ps6/       # problem set PDFs
    sol1..sol5/     # solutions (MATLAB .m files in zips; sol4 is a PDF)
    mpvl/           # MPVL.m + usermanual.zip — the course's vortex lattice code
    matlab_help/    # matlab_help.m — general MATLAB intro
    bisection/      # bisection.m
    fourier_series/ # fourier_series.m
    tidal_turbine/  # design project brief (PDF)
    sdv/            # design project brief (PDF)
    exam1/ exam2/   # exam PDFs
```

If the course root is not in the working directory, ask the user for its
path before reading files.

## How to answer

### 1. Concept questions

1. Check `references/theory.md` (in this skill folder) for the condensed
   theory: key equations, definitions, and method summaries.
2. If the question needs more depth, read the relevant section of
   `resources/kerwin_notes/kerwin_notes.pdf` (the primary text).
3. Explain with the course's notation and conventions (Kerwin's notes).
   Derive or state the governing equation, then walk through the physics.
4. Cite the session number from the syllabus calendar when it helps
   (e.g., "this is session 6 material — vortex lattice lifting surface").

### 2. Problem solving

1. Identify which problem set or exam the problem resembles
   (see the resource map below) and, if the user has the course folder,
   read the corresponding `ps*.pdf` for the exact statement and
   `sol*` for the reference approach.
2. Solve **step by step**: state assumptions, write the governing
   equations, set up the discretization (vortex lattice, panel, or
   Fourier series as appropriate), then compute.
3. For numerical problems, prefer Python (NumPy) unless the user asks
   for MATLAB. The course solutions are MATLAB; translate the logic,
   don't just restate it.
4. Always sanity-check: limits (e.g., AR → ∞ recovers 2D result),
   units, and comparison against known benchmarks (Betz limit,
   Glauert lift curve, B-series data).
5. If a solution exists in `sol*`, compare your result against it and
   say where they agree or differ.

### 3. Resource lookup

Use this map (all paths relative to the course root):

| Need | Path |
|---|---|
| Full lecture notes (primary text) | `resources/kerwin_notes/kerwin_notes.pdf` |
| Syllabus + session calendar | `pages/syllabus/data.json` |
| Problem set N | `resources/psN/psN.pdf` (N = 1..6) |
| Solution to problem set N | `resources/solN/` (N = 1,2,3,5 are MATLAB zips; N = 4 is a PDF) |
| MPVL vortex lattice code + manual | `resources/mpvl/` (zip: MPVL.m, usermanual.pdf) |
| MATLAB intro | `resources/matlab_help/matlab_help.m` |
| Bisection helper | `resources/bisection/bisection.m` |
| Fourier series helper | `resources/fourier_series/fourier_series.m` |
| Tidal turbine design project | `resources/tidal_turbine/tidal_turbine.pdf` |
| SDV propeller design project | `resources/sdv/sdv.pdf` |
| Exam 1 / Exam 2 | `resources/exam1/exam1.pdf`, `resources/exam2/exam2.pdf` |
| OpenProp (external) | http://web.mit.edu/openprop/www/Welcome.html |

## Session-to-topic map (from the syllabus)

| Sessions | Topic |
|---|---|
| 1 | Intro: propeller geometry, 2D foil geometry, performance selection, B-series |
| 2 | Actuator disk theory |
| 3 | Potential flow around a circle with lift, circulation, Kutta-Joukowski |
| 4 | Vortex lines, Biot-Savart law, velocity induced by a vortex segment |
| 5 | Linearized lifting surface theory, bound/free vorticity, Kelvin's theorem |
| 6 | Vortex lattice lifting line, 3D vortex lattice lifting surface |
| 7 | Lift and drag on a linear lifting surface, Glauert's method |
| 8 | Propeller lifting line theory, Betz/Lerbs criteria, Kramer diagram |
| 9 | Propeller vortex lattice lifting line |
| 10 | Quiz 1 |
| 11 | Linear 2D theory, circulation distributions, Glauert's theory |
| 12 | Flat plates, parabolic meanlines, NACA data |
| 13 | Linearized thickness, Lighthill's rule, leading edge suction |
| 14 | 2D foil design, cavitation buckets, Brockett diagrams |
| 15 | 2D panel methods |
| 16 | 2D vortex lattice method |
| 18 | 2D boundary layer theory, XFOIL |
| 19 | Quiz 2 |
| 20 | Vortex lattice propeller lifting surface, PBD |
| 21 | 3D panel methods |
| 22 | Effective wake, unsteady inflow, vortex lattice solvers |
| 23 | Throughflow solvers and coupled methods |
| 24 | Windmills (wind turbines) |
| 25 | Waterjets |
| 26 | Advanced propulsion |

## Problem set themes (for matching problems)

- **PS1** (sol1: 6 .m files + 2 .dat): actuator disk / basic propeller performance
- **PS2** (sol2: 8 .m files): vortex lattice lifting line / lifting surface setup
- **PS3** (sol3: 6 .m files): propeller vortex lattice lifting line
- **PS4** (sol4: PDF solution): 2D foil theory / Glauert
- **PS5** (sol5: 1 .m + PDF): 2D panel / vortex lattice method
- **PS6**: 3D methods / design (no published solution)

If the user pastes a problem, match it to the closest PS theme and use
that solution's structure as a reference.

## Conventions

- Use Kerwin's notation (e.g., `Γ` circulation, `a`/`a'` axial/tangential
  induction factors, `J` advance ratio, `C_T`/`C_Q` thrust/torque
  coefficients, `B` number of blades, `R` radius, `r` radial station).
- SI units unless the problem states otherwise.
- For wind turbines, note the sign convention difference vs. propellers
  (power extracted vs. power added).
- When a result depends on an assumption (thin airfoil, linearized,
  infinite AR), state it explicitly.

## Principles

- The lecture notes PDF is the authority. When in doubt, read it.
- Show the derivation, not just the final formula — the course is
  derivation-heavy.
- Numerical answers need a sanity check against a known limit or
  benchmark before being presented as final.
- If the user is preparing for an exam, point them at the matching
  exam PDF and the relevant sessions, not just the answer.
