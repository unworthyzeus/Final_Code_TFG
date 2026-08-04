# TFG Final Code: Deep Learning for Air-to-Ground Propagation

This repository contains the source code, technical documentation, and published checkpoints for the neural architectures developed during this TFG (Trabajo de Fin de Grado). It includes the final proposed training/evaluation pipeline and key legacy baseline implementations that remain useful for future research.

The CKM dataset is not bundled here. The final Try 80 checkpoint and the 12 Try 76 expert checkpoints are included so the reported models can be downloaded and reproduced.

## Published checkpoints

- [Final Try 80 checkpoint](./model/best_model.pt): `try80_joint_huge_pathloss_finetune`, verified on the complete 2,590-map official test split. See [model/README.md](./model/README.md) for its identity, checksum, and metrics.
- [Try 76 expert checkpoints](./try76_models): 12 morphology and LoS/NLoS experts, with checksums and loading instructions.

## Directory Structure

### 1. [TFGEightiethTry80_preliminary_code](./TFGEightiethTry80_preliminary_code)
This is the **Final Proposed Code Path (Try 80)**.
- **Architecture**: A hybrid, prior-anchored multi-task network.
- **Key Innovation**: Uses "frozen" physical priors (coherent two-ray path loss, regime-wise spread regressions) and learns bounded residual corrections via a shared U-Net backbone with Gaussian Mixture Model (GMM) heads.
- **Purpose**: Implements the final probabilistic prediction pipeline for path loss, delay spread, and angular spread.
- **Contents**: Training scripts (`train_try80.py`), evaluation logic (`evaluate_try80.py`), and documentation (`DESIGN_TRY80.md`).

### 2. [model_pmhhnet.py](./other_good_tries/model_pmhhnet.py)
A **Legacy Baseline (Try 68/PMHHNet)**.
- **Architecture**: A point-estimate residual regressor based on **PMNet** (Rappaport, 2023).
- **Key Features**: High-Frequency (HF) stem for building edge preservation and sinusoidal FiLM for UAV height conditioning.
- **Purpose**: While superseded by the GMM approach, it remains a lightweight and highly effective baseline for standard point-regression tasks or real-time implementations.
- **Note**: See the detailed description in the [PMHHNet section below](#pmhhnet-details).

---

## Technical Summary of Implementations

| Feature | PMHHNet (Baseline) | Try 80 (Final) |
| :--- | :--- | :--- |
| **Output Type** | Point estimate (scalar) | Probabilistic (GMM parameters) |
| **Prior Anchor** | Soft / Learned | Frozen / Hard-coded |
| **Height Conditioning** | Sinusoidal FiLM | Sinusoidal FiLM + h-features |
| **Edge Preservation** | Laplacian HF Stem | Shared U-Net hierarchy |
| **Best Use Case** | Real-time / Point prediction | Full distributional analysis / High accuracy |

## How to use
For detailed instructions on running each implementation, please refer to the corresponding subdirectory or the technical documentation in the main thesis repository.
