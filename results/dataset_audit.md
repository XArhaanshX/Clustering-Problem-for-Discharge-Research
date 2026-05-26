# SECTION A — DATASET AUDIT

## A1. Sheet Inventory Table

| Sheet | Class | SNR | Rows |
|-------|-------|-----|------|
| Void20 | Void | 20 dB | 253 |
| Void30 | Void | 30 dB | 253 |
| Void40 | Void | 40 dB | 253 |
| void50 | Void | 50 dB | 253 |
| Sharp20 | Sharp Point | 20 dB | 116 |
| Sharp30 | Sharp Point | 30 dB | 116 |
| Sharp40 | Sharp Point | 40 dB | 116 |
| Sharp50 | Sharp Point | 50 dB | 116 |
| Surface20 | Surface | 20 dB | 253 |
| Surface30 | Surface | 30 dB | 253 |
| Surface40 | Surface | 40 dB | 253 |
| Surface50 | Surface | 50 dB | 253 |
| Simulate20 | Simulated | 20 dB | 400 |
| simulated30 | Simulated | 30 dB | 400 |
| Simualated40 | Simulated | 40 dB | 400 |

## A2. Missing Value Report

No missing values detected across any feature columns in all sheets.


## A3. Column Consistency Report

- **Void20**: Contains 9 columns. First column will be ignored as an identifier (e.g., 'v' or 'CST' or NaN).
- **Void30**: Contains 9 columns. First column will be ignored as an identifier (e.g., 'v' or 'CST' or NaN).
- **Void40**: Contains exactly 8 feature columns.
- **void50**: Contains exactly 8 feature columns.
- **Sharp20**: Contains 9 columns. First column will be ignored as an identifier (e.g., 'v' or 'CST' or NaN).
- **Sharp30**: Contains exactly 8 feature columns.
- **Sharp40**: Contains exactly 8 feature columns.
- **Sharp50**: Contains exactly 8 feature columns.
- **Surface20**: Contains exactly 8 feature columns.
- **Surface30**: Contains exactly 8 feature columns.
- **Surface40**: Contains exactly 8 feature columns.
- **Surface50**: Contains exactly 8 feature columns.
- **Simulate20**: Contains exactly 8 feature columns.
- **simulated30**: Contains exactly 8 feature columns.
- **Simualated40**: Contains exactly 8 feature columns.

## A4. Unified Schema

The unified dataframe has the following schema:
```
sample_id       object
class_label     object
snr_level       object
F1             float64
F2             float64
F3             float64
F4             float64
F5             float64
F6             float64
F7             float64
F8             float64
```

## A5. Feature Statistics

|    |          mean |          std |          min |           max |          25% |           50% |           75% |
|:---|--------------:|-------------:|-------------:|--------------:|-------------:|--------------:|--------------:|
| F1 |   0.000184267 |  0.000182985 |  1.31148e-05 |   0.00172794  |  3.14697e-05 |   0.000167057 |   0.000195948 |
| F2 |   2.90675e-07 |  9.16111e-07 |  9.09473e-10 |   1.18063e-05 |  2.9461e-09  |   6.48909e-08 |   1.26082e-07 |
| F3 |   0.000340918 |  0.000417729 |  3.01575e-05 |   0.00343602  |  5.4278e-05  |   0.000254737 |   0.000355081 |
| F4 |   9.21501     |  2.53884     |  2.73749     |  15.0413      |  7.45869     |   9.87942     |  11.0883      |
| F5 | 130.121       | 54.2899      | 11.9879      | 307.841       | 87.0866      | 139.072       | 170.507       |
| F6 |   0.00768609  |  0.00969189  |  0.000353294 |   0.0695931   |  0.00111005  |   0.00558463  |   0.00808436  |
| F7 |   0.000152983 |  0.000462436 |  1.24817e-07 |   0.00484319  |  1.23222e-06 |   3.11881e-05 |   6.53569e-05 |
| F8 |  18.4102      |  3.0063      |  8.47132     |  27.0066      | 16.7694      |  18.7377      |  20.3943      |

## A6. Reference-vs-20 dB Mapping Decision

> [!IMPORTANT]
> **Decision:** Since a truly noiseless dataset is unavailable and the `Simulated` class lacks 50 dB samples, the highest available SNR for each class is treated as the reference condition for comparison against 20 dB noise.

- **Sharp Point Reference:** 50 dB
- **Void Reference:** 50 dB
- **Surface Reference:** 50 dB
- **Simulated Reference:** 40 dB

The **20 dB datasets** for all classes will be used as the noisy condition.
