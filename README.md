# Partial Discharge Classification Under Noise Degradation
## Overview
This repository contains the methodology, analysis, and results for a comparative study on classifying Partial Discharge (PD) events. The primary objective of the research is to evaluate the robustness of multi-class classification algorithms when subjected to heavy signal noise (20 dB) compared to clean reference conditions (50 dB).
The study focuses on four primary PD event classes:
1. **Simulated**
2. **Sharp Point**
3. **Void**
4. **Surface**
## Datasets
The study evaluates tabular feature extractions across three distinct dataset environments:
* **CST Dataset**
* **BGST Dataset**
* **HST Dataset**
Each dataset contains a standardized 8-feature representation (F1–F8) derived from raw electrical signals.
## Methodology
### 1. Optimal Feature Selection
To prioritize engineering interpretability and avoid the "curse of dimensionality," the feature space was systematically reduced. For each dataset, a single optimal feature pair (e.g., `F1 & F5` or `F3 & F4`) was mathematically selected to act as the global inputs for the multi-class classifiers.
### 2. Multi-Class Rule-Based Classification
A highly interpretable, axis-aligned rule-based classifier (Decision Tree Stumps, max depth 3-4) was developed. This allowed for the generation of human-readable `IF-THEN` conditional rules, establishing a transparent baseline for PD classification.
### 3. Black-Box Benchmarking (SVM & 1D-CNN)
To determine if classification accuracy—specifically the ambiguous overlap between Void and Surface classes—could be improved, the rule-based baseline was benchmarked against:
* **Support Vector Machines (SVM):** Utilizing RBF kernels on standardized features.
* **1D Convolutional Neural Networks (CNN):** A lightweight dense/CNN hybrid architecture suitable for tabular inputs.
Both models were strictly evaluated using the same feature constraints to ensure a fair, apples-to-apples comparison.
### 4. Noise Robustness & Error Cross-Checking
Models were trained on the clean Reference data (50 dB) and generalized to the noisy condition (20 dB). The study rigorously documented performance collapse scenarios (e.g., the complete drift of the Sharp Point class at 20 dB) and analyzed the mathematical ceiling of feature separability.
## Repository Structure
* `/results/`: Contains the final validated classification contingency tables, extracted rule sets, and formatted PDF reports documenting the findings.
* `*.xlsx` / `*.csv`: Tabular feature datasets containing the signal extractions used for model training and evaluation.
## Key Findings
* **Interpretability vs. Complexity:** Advanced non-linear models (SVM, CNN) provided only marginal, class-specific improvements over the simple rule-based system, often trading off accuracy in highly separable classes (Surface) to boost ambiguous ones (Void).
* **Noise Degradation:** All algorithms experienced severe performance degradation under 20 dB noise. The feature distributions physically shifted beyond the learned thresholds, demonstrating a fundamental limit to separability using solely tabular amplitude/energy features under high noise.
