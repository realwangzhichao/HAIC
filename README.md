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
- [2026-06-08] Initial public release: environment and task configurations, dynamics-aware world model, training code, and evaluation/play scripts.

## TODO

- [x] Release the asset module (G1 robot USDs, object USDs, and asset configuration)
- [x] Release the environment and task configurations
- [x] Release the dynamics-aware world model implementation
- [x] Release the training code
- [x] Release the evaluation and play scripts
- [ ] Release the sim-to-real deployment code
- [ ] Provide setup instructions and usage documentation

## 🚀 Quick Start

```bash
# setup conda environment
conda create -n haic python=3.11 -y
conda activate haic

# install isaacsim
pip install "isaacsim[all,extscache]==5.1.0" --extra-index-url https://pypi.nvidia.com
isaacsim # test isaacsim

# install isaaclab
cd ..
git clone git@github.com:isaac-sim/IsaacLab.git
cd IsaacLab
git checkout v2.3.2
./isaaclab.sh -i none

# install haic
cd ..
git clone https://github.com/ldt29/HAIC
cd HAIC
pip install -e .
```

## Verify Your Data
Visualize motions in Isaac Sim with `+task.command.replay_motion=true`:

```bash
python scripts/play.py algo=ppo_haic_train task=G1/haic/skateboard +task.command.replay_motion=true
```

Or visualize a `motion.npz` in MuJoCo:

```bash
# one terminal
python scripts/vis/mujoco_mocap_viewer.py
# another terminal
python scripts/vis/motion_data_publisher.py <path-to-motion-folder>
```

## Train and Evaluate

Teacher policy

```bash
# train policy
python scripts/train.py algo=ppo_haic_train task=G1/haic/skateboard
# evaluate policy
python scripts/play.py algo=ppo_haic_train task=G1/haic/skateboard checkpoint_path=run:<wandb-run-path>
```

Student policy

```bash
# train policy
python scripts/train.py algo=ppo_haic_finetune task=G1/haic/skateboard checkpoint_path=run:<student_wandb-run-path>
# evaluate policy
python scripts/play.py algo=ppo_haic_finetune task=G1/haic/skateboard checkpoint_path=run:<student_wandb-run-path>
```
To export trained policies, add `export_policy=true` to the play script.


## Assets

The simulation assets live under `active_adaptation/assets`: the G1 robot USDs, the interaction object USDs, and the Python configuration code that wires them up for simulation. See [`active_adaptation/assets/README.md`](active_adaptation/assets/README.md) for the full asset list and usage details.

## Acknowledgments

This repository is built on top of [HDMI: Learning Interactive Humanoid Whole-Body Control from Human Videos](https://github.com/LeCAR-Lab/HDMI). We thank the authors for open-sourcing their work.

## Citation

If you find our work useful for your research, please consider citing us:

```bibtex
@article{li2026haic,
  title = {HAIC: Humanoid Agile Object Interaction Control via Dynamics-Aware World Model},
  author = {Li, Dongting and Chen, Xingyu and Wu, Qianyang and Chen, Bo and Wu, Sikai and Wu, Hanyu and Zhang, Guoyao and Li, Liang and Zhou, Mingliang and Xiang, Diyun and Ma, Jianzhu and Zhang, Qiang and Xu, Renjing},
  journal = {arXiv preprint arXiv:2602.11758},
  year = {2026}
}
```
