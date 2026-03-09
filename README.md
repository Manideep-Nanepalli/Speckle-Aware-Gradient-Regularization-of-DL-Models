# Speckle-Aware Gradient Regularization for Cross-Device Robustness in Retinal SD-OCT

This repository contains the implementation of **Speckle-Aware Gradient Augmentation (GradAug)** for improving **cross-device generalization and reliability** in retinal spectral-domain optical coherence tomography (SD-OCT) classification.

The method integrates **physics-inspired speckle perturbations** and **gradient-based regularization** to learn representations that are robust to **scanner-specific photonic variability** across OCT datasets.

---

## Overview

Deep learning models trained on a single OCT dataset often suffer from **cross-device domain shift**, caused by variations in:

- Imaging hardware
- Optical configurations
- Sampling density
- Reconstruction pipelines
- Speckle statistics

This work proposes a **speckle-aware gradient regularization framework** that encourages **device-invariant representation learning** by incorporating OCT-specific perturbations during training.

The proposed approach is evaluated under:

- **Zero-shot cross-device deployment**
- **Limited-label adaptation**
- **Reliability and calibration analysis**

---

## Key Contributions

- Introduces **speckle-aware gradient augmentation** tailored to the physics of SD-OCT imaging.
- Improves **cross-dataset robustness** under severe domain shift.
- Demonstrates **faster adaptation with limited labeled target data**.
- Evaluates **probabilistic reliability and calibration** under deployment conditions.
- Integrates **Venn–Abers calibration** for well-calibrated prediction confidence.

---

## Method

The training framework incorporates:

### 1. Gradient Augmentation (GradAug)
Width-scaled subnetworks are trained alongside the full network to enforce representation consistency.

### 2. Photonic Perturbations
OCT-specific transformations simulate acquisition variability:

- **Multiplicative speckle perturbation**
- **Resolution scaling**

### 3. Consistency Regularization
Subnetwork predictions are aligned with the full network using **KL divergence loss**.

### 4. Reliability Evaluation
Calibration and uncertainty are analyzed using:

- Expected Calibration Error (ECE)
- Cohen's Kappa
- Prediction-set statistics

---

## Architecture

The backbone model is **ResNet-34** with ImageNet initialization.

Training components include:

- Full ResNet-34 network
- Two width-scaled subnetworks
- Photonic perturbation module
- KL-based consistency regularization

During inference, **only the full network is used**.

---

## Datasets

Experiments were conducted using four publicly available retinal OCT datasets:

| Dataset | Institution | Classes |
|-------|------|------|
| **NEH** | Noor Eye Hospital | Normal, AMD, DME |
| **UCSD** | University of California San Diego | Normal, CNV, Drusen, DME |
| **DHU** | Duke University | Normal, AMD, DME |
| **OCT-C8** | Kaggle curated dataset | Normal, AMD, DME |

All datasets are reformulated as a **binary classification task**:

---

## Data Sources

The datasets are publicly available:

- UCSD OCT Dataset  
  https://share.google/PMOkkYjVn9ek6Ye1y

- NEH OCT Dataset  
  https://sites.google.com/site/hosseinrabbanikhorasgani/available-datasets

- DHU OCT Dataset  
  https://people.duke.edu/~sf59/Srinivasan_BOE_2014_dataset.htm

- OCT-C8 Dataset  
  https://www.kaggle.com/datasets/obulisainaren/retinal-oct-c8/data

Please ensure compliance with each dataset's usage policies.
