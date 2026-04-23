# TFG Final Models: Deep Learning for Air-to-Ground Propagation

This directory serves as the centralized repository for the core models and architectures developed during this TFG (Trabajo de Fin de Grado). It includes both the final proposed solution and key legacy baselines that remain useful for future research.

## Directory Structure

### 1. [TFGEightiethTry80_preliminary_code](./TFGEightiethTry80_preliminary_code)
This is the **Final Proposed System (Try 80)**.
- **Architecture**: A hybrid, prior-anchored multi-task network.
- **Key Innovation**: Uses "frozen" physical priors (coherent two-ray path loss, regime-wise spread regressions) and learns bounded residual corrections via a shared U-Net backbone with Gaussian Mixture Model (GMM) heads.
- **Purpose**: Provides the most accurate, probabilistic predictions for path loss, delay spread, and angular spread.
- **Contents**: Training scripts (`train_try80.py`), evaluation logic (`evaluate_try80.py`), and documentation (`DESIGN_TRY80.md`).

### 2. [model_pmhhnet.py](./other_good_tries/model_pmhhnet.py)
A **Legacy Baseline (Try 68/PMHHNet)**.
- **Architecture**: A point-estimate residual regressor based on **PMNet** (Rappaport, 2023).
- **Key Features**: High-Frequency (HF) stem for building edge preservation and sinusoidal FiLM for UAV height conditioning.
- **Purpose**: While superseded by the GMM approach, it remains a lightweight and highly effective baseline for standard point-regression tasks or real-time implementations.
- **Note**: See the detailed description in the [PMHHNet section below](#pmhhnet-details).

### 3. [dataset](./dataset)
Placeholder directory for the **CKM (Channel Knowledge Map)** dataset or mapping scripts used during training and validation.

---

## Technical Summary of Models

| Feature | PMHHNet (Baseline) | Try 80 (Final) |
| :--- | :--- | :--- |
| **Output Type** | Point estimate (scalar) | Probabilistic (GMM parameters) |
| **Prior Anchor** | Soft / Learned | Frozen / Hard-coded |
| **Height Conditioning** | Sinusoidal FiLM | Sinusoidal FiLM + h-features |
| **Edge Preservation** | Laplacian HF Stem | Shared U-Net hierarchy |
| **Best Use Case** | Real-time / Point prediction | Full distributional analysis / High accuracy |

## How to use
For detailed instructions on running each model, please refer to their respective subdirectories or the technical documentation in the main thesis repository.
