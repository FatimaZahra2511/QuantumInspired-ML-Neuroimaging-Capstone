# Quantum-Inspired Machine Learning For Hyperparameter Optimization for Brain Disorder Neuroimaging

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Machine Learning](https://img.shields.io/badge/MachineLearning-ML-orange)
![Quantum Computing](https://img.shields.io/badge/QuantumComputing-QML-purple)
![PennyLane](https://img.shields.io/badge/PennyLane-QuantumFramework-blueviolet)
![TensorFlow](https://img.shields.io/badge/TensorFlow-DeepLearning-orange)
![Dataset](https://img.shields.io/badge/Dataset-UCLA%20LA5c-green)
![Dataset](https://img.shields.io/badge/Dataset-Kaggle%20EEG-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)


## Overview
This repository contains the full implementation of a **quantum-inspired and quantum-hybrid machine learning framework** for classifying brain disorders using **MRI (UCLA LA5c)** and **EEG (Kaggle)** neuroimaging datasets.  
The project investigates whether **quantum feature maps**, **Random Fourier Features**, and **hybrid classical–quantum kernels** improve separability, calibration reliability, and interpretability in medical ML tasks.

---

## Project Highlights
1. Two complete pipelines:
   - **UCLA MRI Pipeline** — RFF baseline, 4-qubit quantum feature map, calibration, Grad-CAM.
   - **Kaggle EEG Pipeline** — PCA → 8-qubit PennyLane circuit, hybrid quantum-classical kernels.
2. Quantum Feature Maps using **RY/RZ rotations + CNOT entanglement rings**.
3. Hybrid kernels blending classical RBF and quantum kernels.
4. Reliability assessment using **Expected Calibration Error (ECE)** + temperature scaling.
5. Interpretability via **Grad-CAM** (MRI) and **component analysis** (EEG).

---


---

## Methodology

### 1. Classical Baseline — Random Fourier Features (RFF)
RFF approximates an RBF kernel through random projections to simulate nonlinear decision boundaries efficiently.  
Used as the **quantum-inspired** classical reference model.

---

### 2. Quantum Feature Maps

#### MRI Pipeline — 4-Qubit Encoding
- PCA reduces MRI features to 4 components  
- Each qubit encodes one dimension using:
  - `RY(x)` for amplitude
  - `RZ(x²)` for phase
- CNOT ring introduces entanglement

#### EEG Pipeline — 8-Qubit Encoding
- PCA → 8 components  
- Same rotational encoding + entanglement ring

#### Quantum Kernel
The similarity between samples is computed using quantum state fidelity:
𝐾(𝑥_𝑖,𝑥_𝑗 )=|⟨𝜓(𝑥_𝑖 )│𝜓(𝑥_𝑗 ) ⟩|^2
<img width="400" height="62" alt="image" src="https://github.com/user-attachments/assets/27876854-8bc8-4aa1-8d64-0660d47110f1" />
Used to investigate synergy between classical embeddings and quantum feature maps.


---

### 3. Hybrid Kernel
A blend of classical and quantum geometries:

𝐾_ℎ𝑦𝑏𝑟𝑖𝑑=𝛼𝐾_𝑄+(1−𝛼) 𝐾_𝑅𝐵𝐹
<img width="479" height="54" alt="image" src="https://github.com/user-attachments/assets/6170a92b-baee-45a9-b62c-5be6ceccff06" />

---

### 4. Calibration (ECE)
SVM probability outputs are post-processed using **temperature scaling** to improve reliability, following Guo et al. (2017).

---

### 5. Explainability
- **MRI:** Grad-CAM visualizes anatomical regions influencing ADHD vs Control predictions.
- **EEG:** SHAP Analysis, UMAP for fused MRI + EEG.

---

## Results Summary

### MRI – UCLA (ADHD vs Control)
- Classical RBF collapses on multiclass UCLA structure.
- RFF + Logistic Regression yields **AUC = 0.912**, **ECE = 0.041**.
- **Quantum Kernel SVM** achieves:
  - **AUC = 0.957**
  - Calibration improves (ECE reduces from 0.1597 to 0.0943)
  - Clearer class separation in kernel space.

### EEG – Kaggle Dataset
- PCA→8-qubit embedding captures subtle temporal–spectral correlations.
- Hybrid kernel outperform classical-only kernels. **AUC = 0.841** **ECE = 0.015**, **Fusion ECE** = 0.008** nearly perfect 

- More stable cross-validation performance under low-sample conditions.

---

## Datasets
### UCLA LA5c MRI Dataset

Public dataset with MRI and behavioral scores

Preprocessing:

Skull stripping

Intensity normalization

PCA dimensionality reduction

ADHD vs control re-labeling

### Kaggle EEG Dataset

14-channel EEG signals

Sliding windows

PCA to 8-dimensional embedding suitable for qubit mapping

---
## Key Features

Quantum-Inspired RFF pipeline

4- and 8-qubit quantum feature maps

Hybrid classical–quantum kernel learning

Temperature scaling calibration

MRI Grad-CAM & EEG SHAP

Poster-ready figures included

---
##License

MIT License.

---
## Citation
Zhiri, F. (2025). Quantum-Inspired Machine Learning For Hyperparameter Optimzation for Brain Disorder Neuroimaging.

[Fatima Zahra Zhiri](https://www.linkedin.com/in/fatima-zahra-zhiri-722046274/)
