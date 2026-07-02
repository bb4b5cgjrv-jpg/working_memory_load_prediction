# Working Memory Load Prediction
本项目基于 Kyzar 等人（2024）公开发布的人类单神经元工作记忆数据集，使用其中的 Sternberg 工作记忆任务数据，尝试通过监督式机器学习方法预测 trial 级别的工作记忆负荷水平。

## 项目简介

工作记忆（working memory, WM）是个体在短时间内暂时保持并加工信息的重要认知系统，与推理、决策、注意控制和问题解决等复杂认知活动密切相关。Sternberg 工作记忆任务是研究短时记忆保持、提取和工作记忆负荷的经典实验范式之一。

本项目使用 Kyzar 等人（2024）公开发布的数据集中的 Sternberg 工作记忆任务数据。该任务中，被试需要依次记忆 1–3 张图片，并在短暂维持阶段后判断探测图片是否属于当前 trial 中刚刚记忆的图片集合。本项目将每个 trial 中需要记忆的图片数量定义为工作记忆负荷水平，即 load 1、load 2 和 load 3。

与 Kyzar 等人（2024）的原始研究不同，本项目不主要关注单个神经元是否属于概念细胞、维持细胞或探测细胞，而是从监督式机器学习的角度，将 Sternberg 任务中的单神经元活动转换为 trial 级别的数值特征，并训练多分类模型，以检验人类单神经元群体活动中是否包含能够区分不同工作记忆负荷水平的可解码信息。

## 数据来源

本项目使用的数据来源于 Kyzar 等人（2024）发表于 *Scientific Data* 的公开数据集：

*Dataset of human-single neuron activity during a Sternberg working memory task*

原始数据集包含来自 21 名因难治性局灶性癫痫接受深部电极监测患者的 41 个记录 session，共记录到 1809 个单神经元。其中，907 个神经元来自筛选任务，902 个神经元来自 Sternberg 工作记忆任务。记录脑区包括内侧颞叶区域，如杏仁核和海马，以及内侧额叶区域，如前扣带皮层、前辅助运动区和腹内侧前额叶皮层。

需要说明的是，虽然原始公开数据集同时包含筛选任务和 Sternberg 工作记忆任务数据，但本项目仅使用其中的 Sternberg 工作记忆任务数据，不使用筛选任务数据进行模型训练或特征构建。

原始数据集以 Neurodata Without Borders: Neurophysiology 2.0（NWB:N）格式发布，并存储于 DANDI Archive，数据集编号为 dandiset #469。由于原始 NWB 数据文件体积较大，本仓库不上传完整原始数据文件，仅保留项目代码、分析结果、项目说明文档和必要的数据说明。

## 研究目标

本项目的主要目标是：

1. 基于 Sternberg 工作记忆任务数据构建 trial 级别神经活动特征；
2. 将每个 trial 的工作记忆负荷水平，即 load 1、load 2 和 load 3，作为多分类预测标签；
3. 使用监督式机器学习模型预测当前 trial 的工作记忆负荷水平；
4. 通过交叉验证和分类指标评估模型表现；
5. 探讨人类单神经元群体活动中是否包含与工作记忆负荷相关的可解码信息。

## 项目结构

```text
working_memory_load_prediction/
├── README.md
├── 项目说明文档.pdf
├── data/
├── src/
├── results/
├── requirements.txt
└── references.md
```

## 文件说明

- `README.md`：项目简介、数据来源、项目结构和运行说明。
- `项目说明文档.pdf`：项目背景、数据来源、方法、结果和讨论等正式说明文档。
- `data/`：存放数据说明文件或经过整理后的轻量级数据文件。由于原始 NWB 文件体积较大，本仓库不上传完整原始数据。
- `src/`：存放数据读取、特征构建、模型训练与结果评估相关代码。
- `results/`：存放模型输出结果、图表或表格。
- `requirements.txt`：记录运行本项目所需的 Python 第三方库。
- `references.md`：记录本项目参考文献。

## 方法概述

本项目采用监督式机器学习框架，对 Sternberg 工作记忆任务中的 trial 级别神经活动进行分类分析。整体流程包括：

1. 读取 Sternberg 任务对应的 NWB 数据文件；
2. 提取 trial 信息，包括工作记忆负荷水平、编码阶段图片编号、探测图片编号、反应正确性和各阶段时间戳；
3. 基于单神经元 spike activity 构建 trial 级别神经活动特征；
4. 将工作记忆负荷水平设定为分类标签，取值为 1、2 或 3；
5. 训练多分类机器学习模型；
6. 使用交叉验证评估模型分类表现。

## 运行环境

本项目主要使用 Python 完成数据处理与机器学习分析。运行前可根据 `requirements.txt` 安装所需依赖：

```bash
pip install -r requirements.txt
```

## 注意事项

本仓库仅用于课程项目展示和代码管理。由于原始 NWB 数据文件体积较大，本仓库不包含完整原始数据文件。若需复现实验分析，请从 DANDI Archive 获取 Kyzar 等人（2024）公开发布的原始数据集，并根据项目代码中的路径设置进行读取。

本项目属于对公开数据集中 Sternberg 工作记忆任务部分的二次分析与方法扩展，不涉及新的被试招募或新的实验数据采集。

## 主要参考文献

本 README 仅列出项目最核心的数据来源文献；完整参考文献见 `references.md` 或项目说明文档。

Kyzar, M., Kamiński, J., Brzezicka, A., Reed, C. M., Chung, J. M., Mamelak, A. N., & Rutishauser, U. (2024). Dataset of human-single neuron activity during a Sternberg working memory task. *Scientific Data, 11*(1), 89.
