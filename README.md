# ⚡️ Electric Load Forecasting System

> A production‑ready 24‑hour electricity load forecasting pipeline based on a lightweight SARIMA model.

![Build](https://img.shields.io/github/actions/workflow/status/nnnnn/load-forecast-sys/ci.yml?branch=main&style=flat-square)
![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=flat-square)
![License](https://img.shields.io/github/license/nnnnn/load-forecast-sys?style=flat-square)

## 📊 Key Benchmark
| Metric | Value | Baseline | Δ |
|--------|-------|----------|---|
| **MAE (MW)** | **1 678** | 2 500 | **‑33 %** |
| **MAPE (%)** | 4.2 | 6.1 | **‑31 %** |
| **AIC** | 1 245 | 1 310 | **‑5 %** |

> *Peak‑hour forecast error < 5 % (IEEE PES standard).*

> 👉 Take a look at the [example output](load_forecast_result.png).

---

## 🚀 Quick Start

```bash
git clone https://github.com/jacsiu/electricity-load-prediction/tree/main
cd electricity-load-prediction  

python -m venv env
source env/bin/activate

# .\env\Scripts\activate

pip install -r requirements.txt

# 5️⃣ 启动 Jupyter 笔记本
jupyter notebook electricity-load-prediction.ipynb
```
## 📦 Project Overview

| Item | Description |
|------|------|
| Goal | 24‑hour electricity load forecasting with < 5 % peak‑hour error|
| Core algorithm | SARIMA(1,0,1) × (1,0,1,24) (ADT‑controlled differencing) |
| Data | `data/hourly_load_data.csv`10 k+ hourly samples (2002‑2018) |
| Dependencies | pandas、statsmodels、scikit‑learn、joblib、matplotlib |

# 📈 Results & Visualisation

| Plot | Description |
|------|-------------|
| series.png | Raw load with trend & seasonal components |
| acf_analysis.png | Residual ACF  diagnostics |
| load_forecast_result.png | 24‑hour forecast & 95 % confidence band |
| periodic_check.png | Plot the data from the past 48 hours to visually check for periodicity. |

## 🤝 Contributing

1. Fork & clone
2. Create feature branch
3. Run tests: `pytest`
4. Submit PR

## ❓ FAQ

| Question | Answer |
|----------|--------|
| How to add data? | Edit `raw_load_data.csv` and run again. |
| Why not use all data ? | All data is heavier and not needed for 24‑h horizon. |

## 📞 Contact

- Email: 3474172877@qq.com  
- Issue tracker: https://github.com/owner/repo/issues
