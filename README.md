# Use-of-CLAHE-for-Ocular-Disease-Recognition

## Abstract

This artifact accompanies the paper **"Use of CLAHE for Ocular Disease Recognition"** and provides the implementation, preprocessing pipelines, and experimental configuration required to reproduce the results reported in the paper.

The artifact focuses on evaluating the impact of adaptive contrast enhancement (CLAHE) on multi-label retinal disease classification, including controlled ablation, statistical validation, and explainable AI–based analysis.

---

## 1. Artifact Scope

The artifact enables reproduction of the following claims:

- CLAHE yields a statistically significant improvement in macro F1-score compared to baseline preprocessing
- CLAHE provides larger performance gains than data augmentation and border cropping
- Performance improvements correspond to clinically meaningful attention shifts, as verified by Grad-CAM
- Lightweight architectures benefit substantially from optimized preprocessing

---

## 2. Included Components

The artifact includes:

- Preprocessing implementations (cropping, CLAHE, augmentation)
- Model architectures and training scripts
- Evaluation and statistical analysis code
- Grad-CAM explainability analysis
- Fixed dataset splits and metadata

The artifact does not include raw retinal images due to dataset licensing constraints.

---

## 3. Dataset

- Dataset: ODIR-5K
- Number of images: 5,000
- Labels: 8 (multi-label setting)
- Splits: Train / Validation / Test (70% / 15% / 15%)
- Stratified sampling to preserve class imbalance

---

## 4. Experimental Configuration

### Preprocessing Variants

- V1: Resize + normalization
- V2: V1 + data augmentation
- V3: V2 + border cropping
- V4: V3 + adaptive CLAHE

### CLAHE Parameters

- Contrast threshold: 50
- Clip limit: 3.0
- Tile grid size: 8×8
- LAB color space (L channel only)

---

## 5. Models

The following architectures are evaluated:

- ResNet-50
- EfficientNet-B0
- Ensemble (EfficientNet-B0 + MobileNetV3-Large)

All models use identical training protocols and data splits to ensure fair comparison.

---

## 6. Evaluation Metrics

- Accuracy
- Macro F1-score
- Per-class F1-score
- Paired t-tests for statistical significance
- Effect size measured using Cohen’s d

Explainable AI analysis is performed using Grad-CAM.

---

## 7. Reproducibility Statement

All experiments are reproducible under the following conditions:

- Fixed random seeds
- Fixed data splits
- Deterministic preprocessing
- No hyperparameter tuning performed on the test set

The artifact fully supports independent verification of all quantitative and qualitative claims reported in the paper.

---

## 8. Expected Runtime

Training time depends on hardware configuration.  
EfficientNet-B0 provides the best trade-off between runtime and performance and is recommended for artifact evaluation.

---

## 9. Limitations

- Class imbalance remains a challenge for minority disease categories
- The artifact relies solely on fundus images without patient metadata
- External dataset validation is not included

---

## 10. Usage Disclaimer

This artifact is provided strictly for research reproducibility.  
It is not intended for clinical use or diagnostic deployment.
