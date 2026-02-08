graph TD
%% 模块一：临床试验设计与样本采集
subgraph Clinical_Trial [模块一：临床试验设计与样本采集]
A[AIS患者入组 N=358] --> B{随机双盲分组}
B -->|序贯治疗组| C1[D1-D14: 灯盏细辛注射液 D15-D90: 灯盏生脉胶囊]
B -->|安慰剂对照组| C2[全过程安慰剂/模拟剂 基础治疗一致]
C1 & C2 --> D[生物样本采集 生物样本库]
D --> D0[T0 基线: 未用药前]
D --> D1[T1 急性期末: 第7±2天]
D --> D2[T2 恢复期末: 第90±7天]
end
style Clinical_Trial fill:#f9f,stroke:#333,stroke-width:2px

%% 模块二：双组学机制研究
subgraph Multi_Omics [模块二：双组学机制研究]
E[筛选典型样本 N=60/180份] --> F[双组学测序]
F --> F1[DNA甲基化组: 850K芯片]
F --> F2[转录组: RNA-Seq]
F1 & F2 --> G[1. 时空靶点鉴定]
G --> G_A["清毒"集 (T1): 炎症/氧化应激相关]
G --> G_B["补虚"集 (T2): 神经营养/突触可塑性]
F1 & F2 --> H[2. MOFA+ 多组学因子分析]
H --> H1[关联中医证候/临床指标评分]
H --> H2[锁定 Hub Markers]
F1 & F2 --> I[3. 顺式调控分析]
I --> I1[DMPs-DEGs 强负相关对筛选]
end
style Multi_Omics fill:#e1f5fe,stroke:#01579b,stroke-width:2px

%% 模块三：细胞学验证研究
subgraph Cell_Validation [模块三：细胞学验证研究]
J[构建神经元-小胶质细胞共培养体系] --> K[OGD/R 造模模拟缺血再灌注]
K --> L[模拟序贯给药方案]
L --> L1[阶段一 急性期: 灯盏花素 24h]
L1 --> L2{4-6h 药物洗脱期}
L2 --> L3[阶段二 恢复期: 入血成分模拟 72-120h]
L3 --> M[多维度检测]
M --> M1[功能指标: 活力/毒性/突触密度]
M --> M2[分子指标: WB/蛋白表达]
M --> M3[甲基化验证: 焦磷酸测序]
M3 --> N[干扰实验: 5-Aza-dC 激动/抑制]
N --> O[确证甲基化修饰的因果地位]
end
style Cell_Validation fill:#fff3e0,stroke:#ffb300,stroke-width:2px

%% 模块间逻辑连接
Clinical_Trial -.-|提供样本| Multi_Omics
Multi_Omics -->|筛选核心Hub| Cell_Validation
