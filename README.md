# MAIC_mCRPC_Lu177_vs_Cabazitaxel

[![R](https://img.shields.io/badge/R-4.4.1-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

##  项目简介
本仓库包含本人本科毕业设计《Lu-177-PSMA-617对比卡巴他赛治疗转移性去势抵抗性前列腺癌的疗效评估》的相关R代码、数据及结果。研究旨在解决因缺乏头对头试验而导致的疗效比较难题，通过创新性地结合**IPD重构**、**外部PSMA阳性率假设**和**GBM倾向评分加权**，对两个关键III期临床试验（VISION vs. CARD）的数据进行校准后比较。

**核心亮点**:
- **方法学严谨**: 采用Guyot算法从KM曲线精确重构IPD，并通过多种指标验证其可靠性。
- **创新性校准**: 引入外部证据（如TheraP试验）假设PSMA阳性率，对CARD试验人群进行校准。
- **全面诊断**: 使用Love Plot和标准化均数差(SMD)严格评估加权后协变量平衡性。
- **稳健性验证**: 通过多场景敏感性分析（PSMA比例、E-value）评估结论的稳健性。

## 🗂️ 仓库结构
```text
MAIC_mCRPC_Lu177_vs_Cabazitaxel/
│
├── README.md                   # 项目总览、结果摘要、快速导航
├── LICENSE                     # 开源许可证 (MIT)
├── .gitignore                  # 忽略规则
├── mCRPC_MAIC.Rproj            # RStudio 项目文件
│
├── data/                       # 所有数据文件
│   ├── raw/                    # 原始提取数据 
│   │   └── README.md           # 原始数据来源及处理方式
│   ├── processed/              # 处理后的数据 (重构IPD等)
│   │   ├── IPD_OS_VISION.txt
│   │   └── IPD_rPFS_VISION.txt
│   └── external/               # 外部数据
│       └── PSMA_prevalence.csv # PSMA阳性率假设依据
│
├── code/                       # 所有分析脚本
│   ├── 01_data_reconstruction.R        # 从KM曲线重构IPD
│   ├── 02_data_validation.R            # 验证重构IPD
│   ├── 03_psma_status_assignment.R     # 为CARD分配PSMA状态
│   ├── 04_iptw_weighting.R             # 核心：GBM倾向评分加权
│   ├── 05_balance_diagnostics.R         # 平衡性检验 (Love Plot, SMD)
│   ├── 06_survival_analysis.R          # 加权Cox模型 & KM曲线
│   ├── 07_sensitivity_analysis.R       # 敏感性分析 (PSMA比例, E-value)
│   └── utils/                          # 自定义函数
│       └── helper_functions.R
│
├── results/                    # 分析产出
│   ├── figures/                # 所有图表
│   │   ├── KM_weighted.png
│   │   ├── love_plot.png
│   │   └── sensitivity_forest.png
│   └── tables/                 # 结果表格
│       ├── baseline_table.csv
│       └── cox_results.csv
│
├── reports/                    # 最终报告
│   └── analysis_report.html    # 由Rmd生成的完整HTML报告
│
└── doc/                        # 项目文档
    ├── study_protocol.pdf      # (可选) 研究方案/预注册
    └── references.bib          # 参考文献 (BibTeX格式)
