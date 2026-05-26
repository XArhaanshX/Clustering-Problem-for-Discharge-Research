# Extended Simulation Results: Tables & Rules

## 1. Rules Used for Each Type (Base Classifier)

### CST Dataset (F3 & F4)
- **Simulated:** `IF F3 <= 0.00012364`
- **Surface:** `ELSE IF F3 <= 0.000562287 AND F4 <= 10.1456`
- **Void:** `ELSE IF F3 <= 0.000562287 AND F4 > 10.1456`
- **Sharp Point:** `ELSE IF F3 > 0.000562287 AND F4 <= 12.6887`
- **Void (Fallback):** `ELSE IF F3 > 0.000562287 AND F4 > 12.6887`

### BGST Dataset (F1 & F5)
- **Simulated:** `IF F1 <= 7.89e-05`
- **Surface:** `ELSE IF F1 <= 0.0003135 AND F5 <= 197.5`
- **Void:** `ELSE IF F1 <= 0.0003135 AND F5 > 197.5`
- **Surface (Fallback):** `ELSE IF F1 > 0.0003135 AND F5 <= 65.4116`
- **Sharp Point:** `ELSE IF F1 > 0.0003135 AND F5 > 65.4116`

### HST Dataset (F1 & F5)
- **Simulated:** `IF F1 <= 7.41e-05`
- **Surface:** `ELSE IF F1 <= 0.0003325 AND F5 <= 200.5`
- **Void:** `ELSE IF F1 <= 0.0003325 AND F5 > 200.5`
- **Sharp Point:** `ELSE IF F1 > 0.0003325`

---

## 2. Classification Tables

### Table 1: BGST Dataset Comparison

| S.No | PD Types (BGST) | % Rule-Based (20dB) | % Rule-Based (50dB) | % SVM (20dB) | % SVM (50dB) | % CNN (20dB) | % CNN (50dB) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | Simulated (116) | 100.00 | 100.00 | 100.00 | 100.00 | 100.00 | 100.00 |
| 2 | Sharp (116) | 98.28 | 99.14 | 99.14 | 99.14 | 99.14 | 99.14 |
| 3 | Void (253) | 36.76 | 47.83 | 44.27 | 57.31 | 56.13 | 70.75 |
| 4 | Surface (253) | 98.02 | 97.63 | 97.23 | 89.33 | 84.58 | 77.47 |

<br>

### Table 2: CST Dataset Comparison

| S.No | PD Types (CST) | % Rule-Based (20dB) | % Rule-Based (50dB) | % SVM (20dB) | % SVM (50dB) | % CNN (20dB) | % CNN (50dB) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | Simulated (116) | 100.00 | 100.00 | 100.00 | 100.00 | 100.00 | 100.00 |
| 2 | Sharp (116) | 96.55 | 96.55 | 99.14 | 98.28 | 99.14 | 99.14 |
| 3 | Void (253) | 62.45 | 81.03 | 40.32 | 64.43 | 43.48 | 60.87 |
| 4 | Surface (253) | 66.01 | 45.06 | 81.82 | 61.26 | 80.24 | 65.61 |

<br>

### Table 3: HST Dataset Comparison

| S.No | PD Types (HST) | % Rule-Based (20dB) | % Rule-Based (50dB) | % SVM (20dB) | % SVM (50dB) | % CNN (20dB) | % CNN (50dB) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | Simulated (116) | 100.00 | 100.00 | 100.00 | 100.00 | 100.00 | 100.00 |
| 2 | Sharp (116) | 0.00 | 99.14 | 0.40 | 99.14 | 2.37 | 99.14 |
| 3 | Void (253) | 36.76 | 47.04 | 45.85 | 58.10 | 31.62 | 63.24 |
| 4 | Surface (253) | 98.81 | 98.81 | 96.84 | 90.12 | 94.86 | 84.19 |
