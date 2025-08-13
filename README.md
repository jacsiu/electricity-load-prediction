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
跑步scripts/run_all.py将会：

加载data/hourly_load_data.csv。
估算缺失值，添加基本的时间特征。
d/D通过 ADF自动检测。
计算 ACF/PACF – 如果第一个显著滞后 > 0.4，则训练默认的
SARIMA(1,0,1) × (1,0,1,24)。
在 20% 保留率上进行评估并输出 MAE、MAPE、AIC。
以 95% 的置信区间预测未来 24 小时。
所有工件均出现在results/（图表、CSV 报告、joblib模型）下。
📚 项目结构

├─ data/                # raw & pre‑processed csv
├─ src/
│  ├─ preprocess.py     # data cleaning & feature engineering
│  ├─ sarima_search.py  # ACF‑guided fitting routine
│  ├─ train.py          # training wrapper
│  ├─ evaluate.py       # metrics and residual diagnostics
│  └─ forecasting.py    # 24‑hour horizon + CI
├─ scripts/
│  └─ run_all.py        # command‑line entry point
├─ results/
│  ├─ images/           # figures (PNG, PDF)
│  ├─ model.joblib       # trained SARIMA model
│  ├─ summary.csv        # MAE/MAPE/AIC table
│  └─ forecast_24h.csv   # future prediction table
└─ README.md
🔧 技术亮点
特征	执行	益处
没有详尽的网格搜索	ACF(>0.4) → 默认SARIMA(1,0,1)×(1,0,1,24)	速度快 3 倍，笔记本电脑上耗时不到 10 分钟
自动差分	ADF 检验 → 选择d/meta(≤ 2)	保证平稳性
季节性处理	P,D,Q上限为 2	捕捉 24 小时周期，不会过度拟合
并行评估	joblib+loky	4 核机器上≤5 分钟
可重复	joblib.dump+ 配置	轻松回滚和部署
📈 结果与可视化
阴谋	描述
results/peak_hour_comparison.png	1-3月高峰时段MAE对比基线
results/residual_acf_pacf.png	残差 ACF/PACF 诊断
results/forecast_24h.png	24 小时范围，95% CI
results/metrics_summary.png	MAE、MAPE、AIC 表
所有图像都存储在管道中results/并在管道运行时自动生成。

🤝 贡献
分叉 repo。
创建功能分支（git checkout -b feat/xyz）。
运行测试（pytest）。
提交 PR。
拉取请求地址：

新的数据解析器
替代模型（Prophet、LSTM）
CI/集成改进
请参阅CONTRIBUTING.md编码风格指南和提交约定。

📄 许可证
MIT © 2025 nnnnn – 查看许可证文件了解完整条款。

📞 联系方式
电子邮件：zhangxi@example.com
Discord：@loadforecast
祝您预测顺利！🚀
# OR, for editable install
pip install -e .

# 5️⃣ Run end‑to‑end demo
python scripts/run_all.py
