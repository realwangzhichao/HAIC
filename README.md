# HAIC: Humanoid Agile Object Interaction Control via Dynamics-Aware World Model

<div align="center">
<a href="https://haic-humanoid.github.io/">
	<img alt="Website" src="https://img.shields.io/badge/Website-Visit-blue?style=flat&logo=google-chrome"/>
</a>

<a href="https://arxiv.org/abs/2602.11758">
	<img alt="Arxiv" src="https://img.shields.io/badge/Paper-Arxiv-b31b1b?style=flat&logo=arxiv"/>
</a>

<a href="https://github.com/ldt29/HAIC/stargazers">
	<img alt="GitHub stars" src="https://img.shields.io/github/stars/ldt29/HAIC?style=social"/>
</a>

</div>

This repository hosts the open-source release for the RSS 2026 paper HAIC: Humanoid Agile Object Interaction Control via Dynamics-Aware World Model.

## News

- [2026-06-02] Release the asset module (`active_adaptation/assets`): the G1 robot USDs, the interaction object USDs, and the asset configuration code.

## TODO

We are organizing and cleaning up the codebase, and will release it in stages. Planned items:

- [x] Release the asset module (G1 robot USDs, object USDs, and asset configuration)
- [ ] Release the environment and task configurations
- [ ] Release the dynamics-aware world model implementation
- [ ] Release the training code
- [ ] Release the evaluation and play scripts
- [ ] Release the sim-to-real deployment code
- [ ] Provide setup instructions and usage documentation

## Released Assets

The first public update ships the asset module under `active_adaptation/assets`: the G1 robot USDs, the interaction object USDs, and the Python configuration code that wires them up for simulation. See [`active_adaptation/assets/README.md`](active_adaptation/assets/README.md) for the full asset list and usage details.

## Acknowledgments

This repository is built on top of [HDMI: Learning Interactive Humanoid Whole-Body Control from Human Videos](https://github.com/LeCAR-Lab/HDMI). We thank the authors for open-sourcing their work.
