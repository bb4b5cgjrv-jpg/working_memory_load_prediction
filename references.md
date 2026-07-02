一、数据来源

1.1 原始数据论文

Kyzar, M., Kamiński, J., Brzezicka, A., Reed, C. M., Chung, J. M., Mamelak, A. N., \& Rutishauser, U. (2024). Dataset of human-single neuron activity during a Sternberg working memory task. *Scientific Data*, *11*(1), 89.

DOI: https://doi.org/10.1038/s41597-024-02943-8

PMID: 38238342

该论文描述了数据集的设计、采集流程、数据格式及技术验证结果。数据集包含来自21名患者的1809个单神经元记录，涵盖内侧颞叶和内侧额叶脑区。



1.2 数据存储仓库

本研究所用原始数据存储于 DANDI Archive，dandiset 编号 469。

DANDI 数据集 ID: 000469

访问地址: https://dandiarchive.org/dandiset/000469

版本: 0.231213.2047

数据集以 Neurodata Without Borders: Neurophysiology 2.0 (NWB:N) 格式发布，包含筛查任务和Sternberg工作记忆任务两个部分。***本研究仅使用Sternberg工作记忆任务数据***（文件名包含 ses-2）。



二、参考文献

Baddeley, A. (2012). Working memory: Theories, models, and controversies. *Annual review of psychology*, *63*(1), 1-29.

Eriksson, J., Vogel, E. K., Lansner, A., Bergström, F., \& Nyberg, L. (2015). Neurocognitive architecture of working memory. *Neuron*, *88*(1), 33-46.

Goldman-Rakic, P. S. (1995). Cellular basis of working memory. *Neuron*, *14*(3), 477-485.

Kamiński, J., \& Rutishauser, U. (2020). Between persistently active and activity‐silent frameworks: novel vistas on the cellular basis of working memory. *Annals of the New York Academy of Sciences*, *1464*(1), 64-75.

Kyzar, M., Kamiński, J., Brzezicka, A., Reed, C. M., Chung, J. M., Mamelak, A. N., \& Rutishauser, U. (2024). Dataset of human-single neuron activity during a Sternberg working memory task. *Scientific Data*, *11*(1), 89.

Sternberg, S. (1966). High-speed scanning in human memory. *Science*, *153*(3736), 652–654.





三、参考代码

3.1 原始论文官方代码

Rutishauser Laboratory. *workingmem-release-NWB*. GitHub.

仓库地址: https://github.com/rutishauserlab/workingmem-release-NWB

说明: 包含 MATLAB 示例代码，用于复现 Kyzar 等（2024）论文中的图表和分析，并演示如何使用 NWB 格式数据。



3.2 本项目代码

本项目所有分析代码均使用 Python 编写，存放于项目 'src/' 目录下：

main.py: 主程序入口，串联完整分析流程

data\_loader.py: 解析 NWB 文件，提取 trial 信息和 spike 数据

train\_models.py: 训练 5 种机器学习模型，执行交叉验证

visualize.py: 生成性能对比图和混淆矩阵

data\_description.py: 生成数据说明报告



3.3 数据处理流程

本研究的分析流程基于 PyNWB 官方示例和 scikit-learn 用户指南中的交叉验证标准实现，并根据本数据集特点进行了适配。

PyNWB 官方示例: https://pynwb.readthedocs.io/en/stable/getting\_started.html

scikit-learn 交叉验证指南: https://scikit-learn.org/stable/modules/cross\_validation.html



四、教程与文档

4.1 NWB 与 DANDI

PyNWB 文档: https://pynwb.readthedocs.io/

NWB 格式规范: https://nwb-schema.readthedocs.io/



4.2 机器学习与数据处理

scikit-learn 文档: https://scikit-learn.org/stable/

XGBoost 文档: https://xgboost.readthedocs.io/

NumPy 文档: https://numpy.org/doc/

Pandas 文档: https://pandas.pydata.org/docs/

Matplotlib 文档: https://matplotlib.org/stable/contents.html

Seaborn 文档: https://seaborn.pydata.org/



五、工具与软件

5.1 编程语言与开发环境

工具          版本        用途

Python        3.8 以上    数据分析与建模

PyCharm       —           代码开发与调试

Git           —           版本控制



5.2 Python 依赖库

库名称          版本要求       用途

pynwb           2.3.0 以上     读取 NWB 格式神经数据

h5py            3.7.0 以上     HDF5 文件底层支持

numpy           1.21.0 以上    数值计算与数组操作

pandas          1.3.0 以上     数据处理与表格操作

scikit-learn    1.0.0 以上     机器学习模型

xgboost         1.5.0 以上     XGBoost 分类模型

matplotlib      3.4.0 以上     数据可视化

seaborn         0.11.0 以上    统计图表绘制

tqdm            4.62.0 以上    进度条显示

dandi           0.55.0 以上    DANDI 数据集下载



六、网页资源

DANDI Archive: https://dandiarchive.org/

DANDI 469号数据集: https://dandiarchive.org/dandiset/000469

GitHub: https://github.com/

PyPI: https://pypi.org/



七、补充说明

7.1 第三方代码许可

本项目使用的 Python 库均为开源软件，遵循各自的开源许可协议（MIT、BSD、Apache 2.0 等）。原始数据基于 DANDI Archive 的使用条款进行使用，仅用于非商业研究目的。



7.2 复现说明

本研究的代码和数据处理流程已尽量保证可复现性。如需复现完整结果，请按照项目说明文档中的步骤安装依赖、下载数据并运行主程序。特征矩阵和标签数组可通过重新运行 main.py 生成。

