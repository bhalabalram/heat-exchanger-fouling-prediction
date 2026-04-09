# Heat Exchanger Fouling Prediction Using Machine Learning

A machine learning project to predict Heat Exchanger Performance Ratio (HEPR)
using industrial process data from a crude oil preheat train exchanger.

Built as part of **CHE F315 - Machine Learning for Chemical Engineering**
at BITS Pilani, Goa Campus.

---

## Team Members
- Sarthak Srivastava (2022A1PS0889G)
- Khushboo Jain (2022A1PS1450G)
- Shaachi Khanna (2022A1PS1477G)
- Balram Bhala (2023A1PS0116G)

---

## Problem Statement
Heat exchanger fouling is a major operational issue in petroleum and chemical
industries. As tubes accumulate deposits over time, heat transfer efficiency
drops and energy consumption rises.

This project develops ML models to predict HEPR using crude properties,
process operating conditions, and engineered thermal features -
enabling early detection and maintenance scheduling.

---

## Dataset
- Industrial dataset from an E-03 preheat train heat exchanger
- ~64,000 rows (downsampled to every 10 hours)
- 14 input features + 1 output variable (HEPR)

**Input Features:**
- Crude API gravity, TAN, Chlorides
- Tube-side inlet/outlet temperatures
- Tube-side mass flow rate and Cp
- Shell-side temperatures and mass flow rate
- Engineered features: ΔT (tube), ΔT (shell)
- Operating time (hours and days)

**Output:**
- HEPR = Actual Heat Duty / Design Heat Duty
- HEPR ≈ 1 → clean conditions
- HEPR < 1 → fouling occurring

---

## Models Used
| Model | Reason |
|-------|--------|
| Multiple Linear Regression (MLR) | Baseline model |
| Support Vector Regression (SVR - RBF kernel) | Handles nonlinear fouling behavior |
| Principal Component Regression (PCR) | Handles multicollinearity in features |

---

## Results
| Model | Test R² | RMSE |
|-------|---------|------|
| MLR   | ~0.999  | very low (inflated due to engineered features) |
| SVR   | 0.9825  | 0.0055 |
| PCR   | 0.955   | - |

**Best Model: SVR** - most reliable and generalizable performance.

---

## How to Run

1. Clone this repository:
   git clone https://github.com/YOUR_USERNAME/heat-exchanger-fouling-prediction.git

2. Install dependencies:
   pip install -r requirements.txt

3. Open the notebook:
   jupyter notebook notebooks/ML_PROJECT.ipynb

---

## Project Structure
heat-exchanger-fouling-prediction/
├── data/
│   └── dataset.csv
├── notebooks/
│   └── ML_PROJECT.ipynb
├── presentation/
│   └── ML_PROJECT.pptx
├── requirements.txt
└── README.md
