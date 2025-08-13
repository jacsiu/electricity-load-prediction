# ⚡️ Electric Load Forecasting System

> A production‑ready 24‑hour electricity load forecasting pipeline based on a lightweight SARIMA model.

![Build](https://img.shields.io/github/actions/workflow/status/nnnnn/load-forecast-sys/ci.yml?branch=main&style=flat-square)  
![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=flat-square)  
![License](https://img.shields.io/github/license/nnnnn/load-forecast-sys?style=flat-square)

📊 **Key Benchmark**  
| Metric | Value | Baseline | Δ |  
|--------|-------|----------|---|  
| MAE (MW) | **1 678** | 2 500 | -33% |  
| MAPE (%) | 4.2 | 6.1 | -31% |  
| AIC | 1 245 | 1 310 | -5% |  

> *Peak‑hour forecast error < 5 % (IEEE PES standard).*

> 👉 Take a look at the [example output](results/peak_hour_comparison.png).

---

## 🚀 Quick Start

```bash
# 1️⃣ Clone repo
git clone https://github.com/nnnnn/load-forecast-sys.git
cd load-forecast-sys

# 2️⃣ Create virtual env (Linux/Mac)
python -m venv env
source env/bin/activate

# 3️⃣ Create virtual env (Windows)
# .\env\Scripts\activate

# 4️⃣ Install dependencies
pip install -r requirements.txt
# OR, for editable install
pip install -e .

# 5️⃣ Run end‑to‑end demo
python scripts/run_all.py
