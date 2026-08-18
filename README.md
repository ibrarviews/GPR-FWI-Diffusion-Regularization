# Physics-Guided Diffusion-Regularized Time-Lapse GPR Full-Waveform Inversion

**Code and reproducibility notebooks for:**
*"Physics-Guided Diffusion-Regularized Time-Lapse GPR Full-Waveform Inversion: NAPL Contamination Imaging with Generalization to Karst Systems"*

Dr. Ibrar Iqbal, College of Earth Sciences, Guilin University of Technology (GLUT), Guilin, China
ORCID: [0000-0001-6932-7819](https://orcid.org/0000-0001-6932-7819)

---

## Overview

This repository contains the complete code, trained model weights, and figure-reproduction notebooks used in the study above. The method couples a physics-based electromagnetic forward model (FDTD/Maxwell simulation via gprMax) with a diffusion-model prior, regularizing full-waveform inversion of ground-penetrating radar (GPR) data for time-lapse NAPL contamination monitoring, with a generalization test against real karst cave field data.

The framework is **physics-guided**, not physics-informed: physical realism enters through FDTD-simulated training data and a physics-based forward operator (Born approximation) with its adjoint-state gradient — not through a physics-residual term in the diffusion model's own training loss. See Section 2.6 of the manuscript for the full distinction.

## Repository structure

| File | Figure(s) | Description |
|---|---|---|
| `Figure_1_and_9.ipynb` | 1, 9 | Three-state tank simulation (dry sand / water-saturated / NAPL-contaminated) and real NAPL sand tank forward-model validation |
| `Figure_2.ipynb` | 2 | U-Net architecture schematic (diffusion model backbone) |
| `Figure_3.ipynb` | 3 | Forward-model validation: simulated vs. real GPR data (dry sand) |
| `Figure_4.pt` | 4 | Trained diffusion model weights (U-Net, 6,442,626 parameters; see manuscript Section 2.6 for training configuration and diagnostics) |
| `Figure_5.ipynb` | 5 | Single-state inversion comparison (No Regularization / Tikhonov / TV / Diffusion) |
| `Figure_6.ipynb` | 6 | Time-lapse inversion across three contamination states |
| `Figure_7.ipynb` | 7 | Ensemble-based uncertainty quantification |
| `Figure_8.ipynb` | 8 | Generalization to out-of-distribution karst conduit geometry |
| `Figure_10.ipynb` | 10 | Real Guilin karst cave field GPR data validation |

Each notebook is self-contained and, where applicable, loads `Figure_4.pt` as the pretrained diffusion prior rather than retraining from scratch.

## Requirements

- Python 3.10
- [gprMax](https://www.gprmax.com/) (forward FDTD electromagnetic simulation)
- PyTorch (diffusion model training/inference)
- NumPy, SciPy, Matplotlib
- scikit-image (SSIM metric)

A Google Colab environment (T4 GPU) was used for all diffusion model training and inference. gprMax simulations were run in a dedicated conda environment (`gprmax`). If running gprMax steps in Colab, set the GPU runtime **before** mounting Google Drive.

## Reproducing figures

Each notebook can be run independently, provided:
1. The required raw data (real VNA laboratory traces, real GSSI SIR-4000 field data) is placed in the paths indicated at the top of each notebook — see **Data Availability** below.
2. `Figure_4.pt` is present in the working directory for any notebook that uses the trained diffusion prior (Figures 5–8).

## Data availability

The real laboratory NAPL tank GPR data (Keysight/Agilent N9925A FieldFox, SFCW acquisition) and real field GPR data from the Guilin karst cave system (GSSI SIR-4000, 400 MHz) used in this study are available at: **[Zenodo DOI — to be added]**.

## Citation

If you use this code, please cite:

> Iqbal, I. et al. "Physics-Guided Diffusion-Regularized Time-Lapse GPR Full-Waveform Inversion: NAPL Contamination Imaging with Generalization to Karst Systems." *Communications Physics* (in review).

Code archive DOI: **[Zenodo DOI — to be added]**

## Funding

This work was supported by the National Natural Science Foundation of China under Grant No. 42174080.

## License

This project is released under the MIT License — see [LICENSE](LICENSE) for details.

## Contact

Dr. Ibrar Iqbal — ibrariqbal@glut.edu.cn
College of Earth Sciences, Guilin University of Technology, Guilin, China
