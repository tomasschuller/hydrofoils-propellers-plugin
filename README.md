# hydrofoils-propellers plugin

Companion skill for **MIT 2.23 Hydrofoils and Propellers** (Spring 2007,
based on Prof. Justin Kerwin's lecture notes).

## What it does

When invoked, the skill:

1. **Explains course topics** — 2D foil theory, lifting line/surface,
   vortex lattice, panel methods, actuator disk, Betz limit, cavitation,
   boundary layers, unsteady inflow, wind turbines, waterjets — using
   Kerwin's notation and a condensed theory reference.
2. **Solves course-style problems** step by step (vortex lattice setup,
   Glauert distributions, B-series selection, actuator disk, Fourier
   series), with sanity checks against known limits.
3. **Points to the right course resource** — problem sets, solutions,
   MPVL code, exams, design project briefs.

## Layout

```
plugin/
  plugin.json
  README.md
  skills/
    hydrofoils-propellers/
      SKILL.md              # the skill
      references/
        theory.md           # condensed theory reference
```

## Install

Copy or symlink this `plugin/` folder into your Copilot plugins
directory (e.g., `~/.copilot/installed-plugins/<publisher>/`), or install
it from a GitHub repo that contains this layout.

The skill expects the course materials (the parent folder of this
`plugin/` directory) to be available. If the course root is not in the
working directory, the skill will ask for its path.

## Course root layout (expected)

```
<course-root>/
  pages/            # syllabus, assignments, exams, tools, course-notes
  resources/
    kerwin_notes/   # kerwin_notes.pdf (primary text)
    ps1..ps6/       # problem set PDFs
    sol1..sol5/     # solutions
    mpvl/           # MPVL.m + usermanual
    matlab_help/    # matlab_help.m
    bisection/      # bisection.m
    fourier_series/ # fourier_series.m
    tidal_turbine/  # design project brief
    sdv/            # design project brief
    exam1/ exam2/   # exam PDFs
```

## License

MIT. Course materials are MIT OCW (CC BY-NC-SA 4.0).
