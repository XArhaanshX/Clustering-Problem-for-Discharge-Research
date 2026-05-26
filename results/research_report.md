# RESEARCH REPORT: FEATURE SEPARABILITY AND RULE-BASED CLASSIFICATION

## 1. Objective
To systematically determine the most discriminative feature combinations from extracted CST features (F1–F8) and build an interpretable, reproducible, simple rule-based classifier (one-vs-rest) to separate four engineering defect classes under reference and 20 dB noise conditions.

## 2. Dataset Summary
The dataset comprises four classes: Sharp Point, Void, Surface, and Simulated. Following a rigorous integrity audit, valid rows were extracted without missing values. A highest-SNR reference condition was established using 50 dB for Sharp Point, Void, and Surface, and 40 dB for Simulated, against a noisy condition of 20 dB.

## 3. Best Plot Identification & Recommended Classifier Space
**Globally Best Plot:** `F1-F6` (0.8828 avg accuracy)
This feature pair consistently yielded the strongest macroscopic linear separability boundaries across all classes.

**Class-wise Recommendations (Where to run the classifier):**
- **Sharp Point**: Run on `F1-F2` (Accuracy: 0.9990)
- **Void**: Run on `F1-F6` (Accuracy: 0.7798)
- **Surface**: Run on `F2-F6` (Accuracy: 0.7642)
- **Simulated**: Run on `F1-F2` (Accuracy: 1.0000)

## 4. Quantitative Feature Ranking (Top 5 per class)

### Sharp Point vs Rest
| Rank | Feature Pair | Accuracy | Precision | Recall | F1 | Threshold Simplicity |
|---|---|---|---|---|---|---|
| 1 | F1-F2 | 0.9990 | 1.0000 | 0.9914 | 0.9957 | Single-Feature (Depth 1) |
| 2 | F1-F3 | 0.9990 | 1.0000 | 0.9914 | 0.9957 | Single-Feature (Depth 1) |
| 3 | F1-F4 | 0.9990 | 1.0000 | 0.9914 | 0.9957 | Single-Feature (Depth 1) |
| 4 | F1-F5 | 0.9990 | 1.0000 | 0.9914 | 0.9957 | Single-Feature (Depth 1) |
| 5 | F1-F6 | 0.9990 | 1.0000 | 0.9914 | 0.9957 | Single-Feature (Depth 1) |

### Void vs Rest
| Rank | Feature Pair | Accuracy | Precision | Recall | F1 | Threshold Simplicity |
|---|---|---|---|---|---|---|
| 1 | F1-F6 | 0.7798 | 0.5295 | 0.9921 | 0.6905 | Two-Feature (Depth 2) |
| 2 | F1-F7 | 0.7769 | 0.5262 | 0.9921 | 0.6877 | Two-Feature (Depth 2) |
| 3 | F3-F6 | 0.7691 | 0.5180 | 0.9644 | 0.6740 | Two-Feature (Depth 2) |
| 4 | F1-F3 | 0.7583 | 0.5060 | 1.0000 | 0.6720 | Two-Feature (Depth 2) |
| 5 | F3-F7 | 0.7661 | 0.5148 | 0.9644 | 0.6713 | Two-Feature (Depth 2) |

### Surface vs Rest
| Rank | Feature Pair | Accuracy | Precision | Recall | F1 | Threshold Simplicity |
|---|---|---|---|---|---|---|
| 1 | F2-F6 | 0.7642 | 0.5127 | 0.9565 | 0.6676 | Two-Feature (Depth 2) |
| 2 | F2-F7 | 0.7642 | 0.5127 | 0.9565 | 0.6676 | Two-Feature (Depth 2) |
| 3 | F3-F6 | 0.7642 | 0.5127 | 0.9565 | 0.6676 | Two-Feature (Depth 2) |
| 4 | F3-F7 | 0.7642 | 0.5127 | 0.9565 | 0.6676 | Two-Feature (Depth 2) |
| 5 | F4-F6 | 0.7642 | 0.5127 | 0.9565 | 0.6676 | Two-Feature (Depth 2) |

### Simulated vs Rest
| Rank | Feature Pair | Accuracy | Precision | Recall | F1 | Threshold Simplicity |
|---|---|---|---|---|---|---|
| 1 | F1-F2 | 1.0000 | 1.0000 | 1.0000 | 1.0000 | Single-Feature (Depth 1) |
| 2 | F1-F3 | 1.0000 | 1.0000 | 1.0000 | 1.0000 | Single-Feature (Depth 1) |
| 3 | F1-F4 | 1.0000 | 1.0000 | 1.0000 | 1.0000 | Single-Feature (Depth 1) |
| 4 | F1-F5 | 1.0000 | 1.0000 | 1.0000 | 1.0000 | Single-Feature (Depth 1) |
| 5 | F1-F6 | 1.0000 | 1.0000 | 1.0000 | 1.0000 | Single-Feature (Depth 1) |

## 5. Rule Derivation & Final Rule-Based Classifiers
Optimal rule extraction utilized depth-1 or depth-2 Decision Stumps constrained to the best feature pair. Rules are mathematically verifiable and threshold-based.

| Class | Rule | Features Used | Reason |
|---|---|---|---|
| Sharp Point | `IF F1 > 0.000397179` | F1-F2 | Yields 99.9% accuracy on reference set minimizing class overlap. |
| Void | `IF F6 > 0.00469953 AND F1 <= 0.000241502` | F1-F6 | Yields 78.0% accuracy on reference set minimizing class overlap. |
| Surface | `IF F6 > 0.00238655 AND F6 <= 0.0111839` | F2-F6 | Yields 76.4% accuracy on reference set minimizing class overlap. |
| Simulated | `IF F1 <= 9.01379e-05` | F1-F2 | Yields 100.0% accuracy on reference set minimizing class overlap. |

### Feature Usage Summary
| Feature | Times Selected in Best Classifiers |
|---|---|
| F1 | 3 |
| F6 | 2 |
| F2 | 0 |
| F3 | 0 |
| F4 | 0 |
| F5 | 0 |
| F7 | 0 |
| F8 | 0 |

## 6. Classification Tables for Reference and 20 dB Conditions

### Sharp Point vs Rest — Reference Condition
**Final rule used:** `IF F1 > 0.000397179`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 115 (TP) | 1 (FN) |
| **Negative** | 0 (FP) | 906 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 0.9990 | 1.0000 | 0.9914 | 0.9957 |

**Interpretation**
The single-feature threshold accurately identified almost all Sharp Point samples with zero false positives. A single false negative suggests a minor outlier. The rule behavior is exceptional under the highest available SNR reference condition.

### Sharp Point vs Rest — 20 dB Condition
**Final rule used:** `IF F1 > 0.000397179`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 115 (TP) | 1 (FN) |
| **Negative** | 3 (FP) | 903 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 0.9961 | 0.9746 | 0.9914 | 0.9829 |

**Interpretation**
Under 20 dB noise, the rule yields a slight increase in false positives (3 samples), indicating that noise pushes a few non-Sharp Point samples across the threshold. However, overall behavior remains highly stable.

### Void vs Rest — Reference Condition
**Final rule used:** `IF F6 > 0.00469953 AND F1 <= 0.000241502`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 251 (TP) | 2 (FN) |
| **Negative** | 223 (FP) | 546 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 0.7798 | 0.5295 | 0.9921 | 0.6905 |

**Interpretation**
In the highest available SNR reference condition, the classifier successfully captures nearly all Void samples (251 TP, 2 FN), meaning high sensitivity. However, 223 false positives indicate significant overlap with other classes in this feature space.

### Void vs Rest — 20 dB Condition
**Final rule used:** `IF F6 > 0.00469953 AND F1 <= 0.000241502`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 209 (TP) | 44 (FN) |
| **Negative** | 185 (FP) | 584 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 0.7759 | 0.5305 | 0.8261 | 0.6461 |

**Interpretation**
Noise causes a notable increase in false negatives (from 2 to 44), reducing recall as Void samples spread outside the established bounds. Interestingly, false positives slightly drop, keeping accuracy roughly similar, but the core target sensitivity degrades.

### Surface vs Rest — Reference Condition
**Final rule used:** `IF F6 > 0.00238655 AND F6 <= 0.0111839`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 242 (TP) | 11 (FN) |
| **Negative** | 230 (FP) | 539 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 0.7642 | 0.5127 | 0.9565 | 0.6676 |

**Interpretation**
Evaluated on the highest available SNR reference condition, the classifier isolates Surface effectively with 242 TP. However, similar to Void, it captures a large number of false positives (230), reflecting the inherent overlap in these defect signatures.

### Surface vs Rest — 20 dB Condition
**Final rule used:** `IF F6 > 0.00238655 AND F6 <= 0.0111839`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 242 (TP) | 11 (FN) |
| **Negative** | 230 (FP) | 539 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 0.7642 | 0.5127 | 0.9565 | 0.6676 |

**Interpretation**
The rule behavior for Surface vs Rest remains identically mapped in the 20 dB noise condition. The feature F6 within these specific thresholds appears entirely unperturbed by the simulated noise level for these specific samples.

### Simulated vs Rest — Reference Condition
**Final rule used:** `IF F1 <= 9.01379e-05`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 400 (TP) | 0 (FN) |
| **Negative** | 0 (FP) | 622 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 1.0000 | 1.0000 | 1.0000 | 1.0000 |

**Interpretation**
The classifier perfectly segregates Simulated data from all other sets using a single threshold on F1. In the highest available SNR reference condition (40 dB for Simulated), there are zero false positives and zero false negatives.

### Simulated vs Rest — 20 dB Condition
**Final rule used:** `IF F1 <= 9.01379e-05`

**Classification Table**
| Actual | Predicted Positive | Predicted Negative |
|---|---|---|
| **Positive** | 400 (TP) | 0 (FN) |
| **Negative** | 0 (FP) | 622 (TN) |

**Metrics**
| Accuracy | Precision | Recall | F1 |
|---|---|---|---|
| 1.0000 | 1.0000 | 1.0000 | 1.0000 |

**Interpretation**
The threshold logic is exceptionally robust. Even under 20 dB noise, the Simulated data cluster maintains complete macroscopic separation from Sharp, Void, and Surface samples.

## 7. Reference vs 20 dB Classification Summary

| Class | Reference Accuracy | 20 dB Accuracy | Difference | Robustness Comment |
|---|---|---|---|---|
| Sharp Point | 0.9990 | 0.9961 | 0.0029 | The classifier remained exceptionally robust. A tiny noise-induced boundary overlap caused a negligible 0.29% accuracy difference. |
| Void | 0.7798 | 0.7759 | 0.0039 | Void was the most sensitive class, though accuracy changes slightly (0.39%), its recall severely degraded (noise shifted TPs to FNs), showing noise sensitivity. |
| Surface | 0.7642 | 0.7642 | 0.0000 | Complete performance stability (0 difference). The boundaries of F6 defining Surface remained perfectly unaffected by 20 dB noise. |
| Simulated | 1.0000 | 1.0000 | 0.0000 | Easiest class to separate. F1 rule provides total noise immunity resulting in 0 difference in accuracy. |

### Robustness Engineering Commentary
- **Most Robust Classifier:** The Simulated vs Rest classifier (using `F1 <= 9.01379e-05`) remained completely unperturbed by noise, maintaining a 1.00 F1 score. Surface vs Rest also proved fully stable.
- **Most Degraded Classifier:** Void vs Rest suffered the worst performance change internally (notably in recall dropping from 99% to 82%), reflecting that `F1` and `F6` thresholds for Void tightly border the noisy distributions of other classes.
- **Noise Sensitive Rules:** The dual-threshold rule for Void (`IF F6 > 0.00469953 AND F1 <= 0.000241502`) is highly noise sensitive. As variance increases under 20 dB, Void samples easily cross the `F1` boundary.
- **Easiest/Hardest Classes:** Simulated is the absolute easiest class to separate (100% accuracy). Surface and Void remain the hardest due to significant physical overlap in features F1 and F6, leading to high baseline false positives.
- **Why performance changed:** Performance degradation strictly follows feature overlap. Sharp Point and Simulated occupy distant macro-clusters, meaning 20 dB variance is insufficient to bridge the gap. Conversely, Void and Surface occupy adjacent micro-clusters; adding 20 dB noise expands their variance across the strict decision stump boundaries, turning True Positives into False Negatives.

## 8. Limitations & Recommendations
- **Limitations**: The strict limit on rule complexity (max depth 1-2) sacrifices minor accuracy for pure explainability. Furthermore, 20 dB noise heavily occludes certain linear boundaries.
- **Recommendations**: The engineering system should deploy the globally robust features to execute early-stage triage of Simulated vs Sharp/Void/Surface defects, cascading into localized thresholds to separate the remainder.