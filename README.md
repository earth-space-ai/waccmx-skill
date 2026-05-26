# WACCM-X Skill

Progressive-disclosure skill for WACCM-X, the extended Whole Atmosphere Community Climate Model that reaches into the ionosphere and thermosphere (~500–700 km).

> **WACCM-X is not a separate repo.** It lives inside [ESCOMP/CAM](https://github.com/ESCOMP/CAM). Use [cesm-skill](https://github.com/earth-space-ai/cesm-skill) and [cam-skill](https://github.com/earth-space-ai/cam-skill) for build mechanics.

> **Skill author:** Koutian Wu (ktwu01@gmail.com)
> **Skill version:** 0.1.0-scaffold

> ⚠️ **Disclaimer — please read before using this skill.**
> This skill is **not a gold-standard reference**. It is a helper that lowers
> the barrier for new users to **get their hands dirty** with the model. AI
> agents (and the humans drafting this material) make mistakes; commands, file
> paths, namelist options, and physics explanations here can be wrong,
> incomplete, or out of date. **Always cross-check with the official model
> documentation, the source code, and a human expert before trusting any
> output for research, publication, or operational use.**

## What This Is

A guide for researchers who want to run CESM/CAM with a WACCM-X compset for ionosphere–thermosphere–mesosphere coupling studies, space weather, or upper-atmosphere science.

## Status

Scaffold. Source-grounded routing verified. Operational depth (compset enumeration, IT-region debugging gotchas, geomagnetic input setup) being filled in.

## Related skills in this org

- [waccm-skill](https://github.com/earth-space-ai/waccm-skill)
- [cam-skill](https://github.com/earth-space-ai/cam-skill)
- [cesm-skill](https://github.com/earth-space-ai/cesm-skill)

## Acknowledgments

**Gold-standard references for WACCM-X** (use these to cross-check anything in this skill):
- WACCM-X project page (NCAR HAO): https://www2.hao.ucar.edu/modeling/waccm-x
- ESCOMP/CAM repository (WACCM-X lives here): https://github.com/ESCOMP/CAM
- CAM User's Guide (covers WACCM-X compsets): https://ncar.github.io/CAM/doc/build/html/
- CEDAR community portal (ionosphere-thermosphere-mesosphere): https://cedarscience.org/

This scaffold exists only because of the work of other people, and any value
it has is borrowed from theirs.

- **NSF NCAR** and the **High Altitude Observatory (HAO)** for developing
  the extended Whole Atmosphere Community Climate Model (WACCM-X) inside
  [ESCOMP/CAM](https://github.com/ESCOMP/CAM), including the
  ionosphere-thermosphere coupling, geomagnetic input handling, and the
  upper-atmosphere compsets this skill documents.
- The **CEDAR** community and the broader ionosphere-thermosphere-mesosphere
  research community whose use of WACCM-X drives its development.
- The maintainers of `waccm-skill`, `cam-skill`, and `cesm-skill` for the
  upstream build / run mechanics this skill routes users to.
- **Zesen Huang** for [laps-skill](https://github.com/huangzesen/laps-skill),
  the progressive-disclosure layout this repo borrows.

Any errors, oversimplifications, or out-of-date claims in this skill are the
skill author's responsibility, not the upstream community's. This is a
scaffold; operational depth is being filled in iteratively.

## License

MIT (skill content). WACCM-X source is governed by the CAM/CESM license.
