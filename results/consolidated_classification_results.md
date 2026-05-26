# Consolidated Power Quality Event Classification Results

## 1. Optimal Feature Selection Summary
The following feature pairs were mathematically selected as the single best common pair for 4-class multi-class rule-based classification across each respective dataset:

- **CST Dataset:** `F3` and `F4`
- **BGST Dataset:** `F1` and `F5`
- **HST Dataset:** `F1` and `F5`

---

## 2. Rules Used for Each Type (Base Classifier)

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

## 3. CST Dataset Classification Tables

### POWER QUALITY EVENT CLASSIFICATION RESULTS (Reference Condition)
| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 112 | 4 | 96.55 |
| Void | 205 | 48 | 81.03 |
| Surface | 114 | 139 | 45.06 |
| **Total** | **831** | **191** | **81.31** |

### POWER QUALITY EVENT CLASSIFICATION RESULTS (20 dB Condition)
| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 112 | 4 | 96.55 |
| Void | 158 | 95 | 62.45 |
| Surface | 167 | 86 | 66.01 |
| **Total** | **837** | **185** | **81.90** |

---

## 4. BGST Dataset Classification Tables

### POWER QUALITY EVENT CLASSIFICATION RESULTS (Reference Condition)
| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 115 | 1 | 99.14 |
| Void | 121 | 132 | 47.83 |
| Surface | 247 | 6 | 97.63 |
| **Total** | **883** | **139** | **86.40** |

### POWER QUALITY EVENT CLASSIFICATION RESULTS (20 dB Condition)
| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 114 | 2 | 98.28 |
| Void | 93 | 160 | 36.76 |
| Surface | 248 | 5 | 98.02 |
| **Total** | **855** | **167** | **83.66** |

---

## 5. HST Dataset Classification Tables

### POWER QUALITY EVENT CLASSIFICATION RESULTS (Reference Condition)
| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 115 | 1 | 99.14 |
| Void | 119 | 134 | 47.04 |
| Surface | 250 | 3 | 98.81 |
| **Total** | **884** | **138** | **86.50** |

### POWER QUALITY EVENT CLASSIFICATION RESULTS (20 dB Condition)
| Power Quality Event | Correct | Wrong | % Success |
| :--- | :---: | :---: | :---: |
| Simulated | 400 | 0 | 100.00 |
| Sharp Point | 0 | 253 | 0.00 |
| Void | 93 | 160 | 36.76 |
| Surface | 250 | 3 | 98.81 |
| **Total** | **743** | **416** | **64.11** |
