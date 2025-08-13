# ⚡ Electric Load Forecasting with SARIMA

[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue)](https://python.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

![Project Preview](results/model_comparison.png)

> **短期电力负荷预测系统** | 课程项目 · 2024年Spring  
> **核心亮点**：基于科学方法论的SARIMA参数选择（非盲目搜索），**仅用7天数据**实现高精度预测

## 📌 背景与目标

电力系统调度需要**精准短期负荷预测**。传统方法常依赖全量历史数据，但本项目证明：**选择性小数据**结合**科学参数选择**，能达到更优的工程实用效果。

- ✅ **24小时负荷预测**，满足电网调度关键需求
- ✅ **MAE=1678 MW**，峰时段误差<5%（超行业基准8%）
- ✅ **仅用168小时(7天)** 代表性数据，训练速度**12秒**（vs 全数据30分钟）

## 🔑 项目亮点

### 💡 **方法论创新**（面试官最爱问！）
- **拒绝盲目网格搜索**：基于ACF分析(r=0.58)科学确定SARIMA(0,0,0)×(1,0,1,24)
- **数据选择有理有据**：为什么只用7天数据（不是"我就这么多"）:
  - 电力负荷**时效性 > 历史长度**（相关性衰减实证）
  - 完整覆盖**5个工作日+2周末**（最小有效周期）
  - **计算效率↑152倍**，保证部署可行性
- **峰值误差优先**：专攻电网最关注的峰时段预测（非全局MAE最优）

### 📊 性能对比
| 指标 | 本方案 | 基准方案 | 提升 |
|------|--------|---------|------|
| MAE | 1678 MW | 2209 MW | 24.0%↓ |
| 训练时间 | 12秒 | 1824秒 | 152x↑ |
| 峰时段误差 | 4.7% | 12.3% | 61.8%↓ |

## 🚀 快速开始

### 环境准备
```bash
# 创建虚拟环境
python -m venv env
source env/bin/activate  # Linux/Mac
# env\Scripts\activate   # Windows

# 安装依赖
pip install -r requirements.txt
