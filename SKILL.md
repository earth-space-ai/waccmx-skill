---
name: waccmx
description: >
  Progressive-disclosure skill for WACCM-X (extended Whole Atmosphere
  Community Climate Model), a configuration of CAM in CESM that extends
  the model top to ~500–700 km, into the ionosphere and thermosphere,
  with self-consistent ionospheric chemistry and electrodynamics.
  Used for ionosphere–thermosphere–mesosphere coupling studies, space
  weather, and lower-atmosphere forcing of the upper atmosphere.
version: 0.1.0-scaffold
tags:
  - earth-science
  - space-weather
  - ionosphere
  - thermosphere
  - mesosphere
  - waccm-x
  - cesm
  - cam
  - ncar
---

# WACCM-X (Extended WACCM) Guide

> **WACCM-X** extends WACCM upward into the ionosphere and thermosphere (~500–700 km), with prognostic ion species, neutral–ion chemistry, ambipolar diffusion, ion drag on the neutrals, and self-consistent ionospheric electrodynamics.
> Maintainer: NSF NCAR / HAO + ACOM, working inside ESCOMP/CAM
> Source: WACCM-X lives **inside** [ESCOMP/CAM](https://github.com/ESCOMP/CAM) (no separate repo)
> Companion analysis tool: [NCAR/gcmprocpy](https://github.com/NCAR/gcmprocpy) (post-processing for TIE-GCM and WACCM-X)
> Docs: https://www2.hao.ucar.edu/modeling/waccm-x
> Skill author: Koutian Wu (ktwu01@gmail.com)
> Skill version: 0.1.0-scaffold

**Important:** WACCM-X is **not a separate code repository**. It is a CAM compset and namelist option set, with WACCM-X-specific physics modules under `src/physics/waccm/`. To run it you follow the standard CESM/CAM workflow and select a WACCM-X compset.

**What WACCM-X does:** Adds an ionosphere–thermosphere extension to WACCM. Solves prognostic equations for major neutral species (O, O2, N2) with major ion species (O+, NO+, O2+, N2+) and electrons; computes ambipolar diffusion and ion drag self-consistently; couples to a dynamo electric-field solver. Used to study lower-atmosphere driving of the upper atmosphere (SSWs, planetary waves, tides), space weather, and IT-region density structures.

**Who this skill is for:** Researchers in space physics, aeronomy, and IT coupling who want to use WACCM-X for science runs.

---

## Quick Decision Tree

```
"What do I need?"
│
├─ 🆕 What is WACCM-X, and how is it different from WACCM?
│  └─ Read: reference/what-is-waccmx.md
│
├─ 🚀 Build and run WACCM-X
│  └─ Use cesm-skill for case mechanics; reference/compsets.md here for compset selection
│
├─ ⚛️ Ionosphere chemistry and electrodynamics
│  └─ Read: reference/ionosphere-electrodynamics.md
│
├─ 📊 WACCM-X-specific output fields (electron density, ion drift, NmF2, hmF2)
│  └─ Read: reference/output-fields.md
│
├─ ⏱️ Time stepping in the upper atmosphere (sub-stepping ion chemistry)
│  └─ Read: reference/time-stepping.md
│
└─ 🐛 Crashes in the IT region (large gradients, polar cap)
   └─ Read: reference/debugging.md
```

---

## Where the Code Lives

- `src/physics/waccm/`, WACCM-X-specific physics (ion drag, ambipolar diffusion, electrodynamics interface)
- `src/chemistry/pp_waccm_*`, WACCM-X-relevant chemistry preprocessor outputs
- `src/dynamics/...`, increased vertical levels for WACCM-X (typically 130+ levels)
- `bld/namelist_files/`, look for `waccmx` keyword in default namelist files

---

## Critical Rules

1. **WACCM-X is much more expensive than WACCM.** Plan accordingly: more vertical levels, ion chemistry sub-stepping, additional output fields.
2. **CFL constraints in the upper atmosphere are different.** Sub-stepping settings and time-step constraints differ from WACCM.
3. **Output to compare with TIE-GCM:** use `gcmprocpy` (NCAR/gcmprocpy) for shared post-processing.
4. **Lower-atmosphere forcing matters.** Specified-dynamics nudging in the troposphere/stratosphere is a common WACCM-X mode for tide and planetary-wave studies.
5. **Geomagnetic forcing inputs.** WACCM-X needs Kp, F10.7, and high-latitude convection inputs configured.

---

## Reference Index

| File | Topic |
|---|---|
| reference/what-is-waccmx.md | Scope, vertical extent, history |
| reference/compsets.md | WACCM-X compsets in CESM |
| reference/ionosphere-electrodynamics.md | Ion chemistry, electrodynamics |
| reference/output-fields.md | IT-region output variables |
| reference/time-stepping.md | Sub-stepping, CFL |
| reference/debugging.md | Common WACCM-X failure modes |

## Status

Scaffold (v0.1.0-scaffold). Routing and source-grounded surface verified. Operational depth being filled in.
