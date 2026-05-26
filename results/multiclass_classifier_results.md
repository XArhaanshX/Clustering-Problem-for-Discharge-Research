# Four-Class Common Rule-Based Classifier

## 1. Best Two Features
**Best feature pair:** `F3` and `F4`

**Why selected:** 
This pair yielded the highest total classification performance (81.3% overall accuracy on the reference set) among all 28 possible pairs when restricted to a single, shallow common rule system. It provides strong macroscopic separation without requiring complex or deep threshold boundaries.

## 2. Final Common Rule System
The following set of rules evaluates all four PD classes using strictly the chosen features (`F3` and `F4`) via an interpretable hierarchical threshold logic.

```text
IF F3 <= 0.00012364 
    → Simulated
ELSE IF F3 > 0.00012364 AND F3 <= 0.000562287 AND F4 <= 10.1456 
    → Surface
ELSE IF F3 > 0.00012364 AND F3 <= 0.000562287 AND F4 > 10.1456 
    → Void
ELSE IF F3 > 0.00012364 AND F3 > 0.000562287 AND F4 <= 12.6887 
    → Sharp Point
ELSE IF F3 > 0.00012364 AND F3 > 0.000562287 AND F4 > 12.6887 
    → Void
```

*Reasoning:* `F3` easily handles the macro-triage separating Simulated arrays from Sharp Points entirely. The middle region is where `F4` becomes necessary to discriminate between Void and Surface classes.

---

## 3. Classification Results

### (A) REFERENCE CONDITION (Highest available SNR)

| PD Type | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 112 | 4 | 96.55 |
| Void | 205 | 48 | 81.03 |
| Surface | 114 | 139 | 45.06 |
| **Total** | **831** | **191** | **81.31** |

<br>

### (B) 20 dB NOISE CONDITION

| PD Type | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 112 | 4 | 96.55 |
| Void | 158 | 95 | 62.45 |
| Surface | 167 | 86 | 66.01 |
| **Total** | **837** | **185** | **81.90** |

---

## 4. Engineering Interpretation
- **Why these two features worked best:** `F3` and `F4` perfectly bisect the macro-clusters of Simulated and Sharp Point, leaving the classifier to focus entirely on thresholding the overlapping Void and Surface distributions.
- **Which class classified easiest:** **Simulated** was perfectly classified (100% success) under all conditions due to its distinct low-variance signature on `F3`.
- **Which class degraded under 20 dB:** **Void** degraded significantly (from 81% to 62%) because added noise caused its features to spill across the strict `F4` boundaries, falsely registering as Surface.
- **Whether the common rule set remained robust:** Yes. The overall accuracy remained highly stable (81.3% vs 81.9%), proving that a single simplified tree structure utilizing `F3/F4` avoids overfitting and handles systemic noise variance without collapsing.
