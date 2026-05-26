# Feature Separability and Rule-Based Classification Study

This document outlines the rigorous, reproducible workflow for the feature-separability and rule-based classification study on the extracted CST features.

## User Review Required

> [!IMPORTANT]
> **Definition of "Normal" Dataset:** The dataset contains noise levels 20, 30, 40, and 50 dB for Void, Sharp, and Surface, but only 20, 30, and 40 dB for Simulated. 
> To ensure a fair comparison across all 4 classes, I propose using **40 dB as the "Normal" dataset** (highest common SNR) and **20 dB as the "Noisy" dataset**. Please confirm if this is acceptable, or if 50 dB should be used for the first three classes and 40 dB for Simulated.

> [!IMPORTANT]
> **Visual Inspection Proxy:** Since I am an AI agent operating in a headless environment, I have extracted the EMF images from the DOCX but cannot seamlessly view them directly. Instead, I will **programmatically reconstruct all 28 pairwise scatter plots** from the raw Excel data and compute quantitative separability metrics (cluster overlap, decision stump margins) to robustly assign the qualitative visual scores (Excellent, Strong, Moderate, Weak, Poor) as requested. This guarantees 100% fidelity to the data without OCR hallucinations.

## Proposed Changes

The study will be executed systematically via Python scripts to ensure full reproducibility. No black-box ML models will be used.

### 1. Dataset Audit (SECTION A)
- **Data Loading:** Read `Feature of CST.xlsx` with `header=None`.
- **Feature Extraction:** Ignore the first column if a sheet contains 9 columns (which contains NaN/'v'/'CST'). Treat the last 8 columns as F1–F8 consistently.
- **Mapping:** Map sheets to their respective classes (Void, Sharp Point, Surface, Simulated) and noise conditions.

### 2. Visual Feature Analysis & Scatter Plots (SECTION B)
- **Plot Reconstruction:** Generate high-DPI, publication-quality PNG scatter plots for all 28 pairwise combinations (F1-F8) using the "Normal" dataset.
- **Qualitative Ranking:** Analyze cluster overlap and threshold-friendliness to rank pairs (Excellent to Poor).

### 3. Quantitative Plot Ranking (SECTION C)
- **One-vs-Rest Framing:** For each class (Sharp Point, Void, Surface, Simulated), treat the remaining three classes as the negative class.
- **Decision Stump Evaluation:** Evaluate all 28 feature pairs using simple axis-aligned threshold boundaries (Depth 1 or 2 rule-based splits).
- **Ranking:** Rank pairs based on F1-score and Accuracy.

### 4. Rule-Based Classifier Design (SECTION D)
- **Rule Extraction:** For each class-vs-rest problem, extract the optimal threshold rule from the best-performing feature pair (e.g., `IF F4 > a AND F6 < b THEN Sharp Point`).
- **Interpretability Check:** Ensure rules use ≤ 2 features and remain perfectly explainable.

### 5. Classification Results & Robustness Analysis (SECTION E & F)
- **Normal vs. Noisy Evaluation:** Apply the extracted rules to both the Normal (40 dB) and Noisy (20 dB) datasets.
- **Metrics:** Compute Accuracy, Precision, Recall, F1-score, and Confusion Matrices for both conditions.
- **Robustness:** Analyze degradation in performance to determine which features/rules are noise-sensitive.

### 6. Final Research Report (SECTION G)
- **Synthesis:** Compile Sections A through F into a rigorous, academic-grade markdown report containing tables, rules, and engineering interpretations.

## Verification Plan

### Automated Tests
- Python scripts will validate row counts, missing values, and column consistency before modeling.
- Exact bounds and constraints for the rules will be logged and verified against the raw data points.

### Manual Verification
- The user will review the final `research_report.md` artifact to ensure it meets the publication-quality requirements and strictly follows the rule-based constraint.
