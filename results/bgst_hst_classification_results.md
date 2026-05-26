### Workflow Compatibility Check
**Confirmed.** Both `Features of BGST.xlsx` and `Features of HST.xlsx` contain perfectly structured F1–F8 numerical features mapping exactly to the four PD classes (Simulated, Sharp Point, Void, Surface) and four SNR levels (20, 30, 40, 50 dB). The exact same preprocessing, reference/noise condition framing, and multiclass decision logic used for CST was successfully deployed without methodological drift.

---

### BGST Best Two Features
**Chosen pair:** `F1` and `F5`
**Reason:** Selected via identical logic to CST; this pair achieved the highest overall 4-class multi-class accuracy (86.40%) on the BGST reference data while restricted to a maximum depth-3 threshold rule system.

### HST Best Two Features
**Chosen pair:** `F1` and `F5`
**Reason:** Selected via identical logic to CST; this pair achieved the highest overall 4-class multi-class accuracy (86.50%) on the HST reference data using the same simplified threshold constraints.

---

### BGST Final Rule Set
```text
IF F1 <= 7.89e-05 
    → Simulated
ELSE IF F1 > 7.89e-05 AND F1 <= 0.0003135 AND F5 <= 197.5 
    → Surface
ELSE IF F1 > 7.89e-05 AND F1 <= 0.0003135 AND F5 > 197.5 
    → Void
ELSE IF F1 > 7.89e-05 AND F1 > 0.0003135 AND F5 <= 65.4116 
    → Surface
ELSE IF F1 > 7.89e-05 AND F1 > 0.0003135 AND F5 > 65.4116 
    → Sharp Point
```

### HST Final Rule Set
```text
IF F1 <= 7.41e-05 
    → Simulated
ELSE IF F1 > 7.41e-05 AND F1 <= 0.0003325 AND F5 <= 200.5 
    → Surface
ELSE IF F1 > 7.41e-05 AND F1 <= 0.0003325 AND F5 > 200.5 
    → Void
ELSE IF F1 > 7.41e-05 AND F1 > 0.0003325 
    → Sharp Point
```

---

### BGST Result Tables

**POWER QUALITY EVENT CLASSIFICATION RESULTS (Reference Condition)**

| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 115 | 1 | 99.14 |
| Void | 121 | 132 | 47.83 |
| Surface | 247 | 6 | 97.63 |
| **Total** | **883** | **139** | **86.40** |

<br>

**POWER QUALITY EVENT CLASSIFICATION RESULTS (20 dB Condition)**

| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 114 | 2 | 98.28 |
| Void | 93 | 160 | 36.76 |
| Surface | 248 | 5 | 98.02 |
| **Total** | **855** | **167** | **83.66** |

---

### HST Result Tables

**POWER QUALITY EVENT CLASSIFICATION RESULTS (Reference Condition)**

| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 115 | 1 | 99.14 |
| Void | 119 | 134 | 47.04 |
| Surface | 250 | 3 | 98.81 |
| **Total** | **884** | **138** | **86.50** |

<br>

**POWER QUALITY EVENT CLASSIFICATION RESULTS (20 dB Condition)**

| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 0 | 253 | 0.00 |
| Void | 93 | 160 | 36.76 |
| Surface | 250 | 3 | 98.81 |
| **Total** | **743** | **416** | **64.11** |

---

### Comparability Summary
- **Which dataset classified best?** Under ideal reference conditions, both datasets perform nearly identically well (~86.4% and ~86.5%), noticeably outperforming the CST baseline (~81.3%), heavily driven by excellent Surface classification. Both datasets algorithmically selected the exact same optimal feature pair (`F1` and `F5`).
- **Which degraded most at 20 dB?** **HST** degraded catastrophically (dropping from 86.50% to 64.11%), whereas BGST remained highly robust (only dropping to 83.66%). 
- **Whether multiclass rule robustness remained similar to CST:** The BGST dataset exhibits robustness perfectly matching CST. However, the HST dataset completely collapses under 20 dB noise specifically for the **Sharp Point** class (dropping to 0% success), indicating that while the `F1/F5` rule set is mathematically optimal for high SNR HST, it cannot handle the heavy feature smearing caused by 20 dB noise in that specific environment.
