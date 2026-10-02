# 安全与隐私：代表研究、近期线索与证据边界

核验截至2026-10-02。以下按基础到近期排列，均给一手来源。它们提供不同研究问题的解释框架，不是完整领域清单，也不宣称当前最佳性能。首发日期、修订日期、正式会议年份分别记录；网页抓取时间不是论文发表时间。

| 研究与一手来源 | 时间与状态 | 应读的核心问题 | 已查证据与局限 |
|---|---|---|---|
| [Path ORAM](https://arxiv.org/abs/1202.5150) | arXiv首发2012-02-23；v3为2014-01-14；CCS 2013工作 | 怎样隐藏读写了哪个数据块 | 官方版本页及作者论文入口；不能把历史摘要中的“最实用”当2026结论 |
| [The Algorithmic Foundations of Differential Privacy](https://www.cis.upenn.edu/~aaroth/Papers/privacybook.pdf) | 2014正式专著 | 邻接、敏感度、噪声和组合怎样连接 | 已读第2.3节定义及相关组合段落；教学公式采用标准数据库DP |
| [FedAvg / Communication-Efficient Learning](https://proceedings.mlr.press/v54/mcmahan17a.html) | AISTATS 2017正式论文 | 分散数据怎样通过局部训练与聚合学习 | 官方会议页；它解释训练组织，不能替代隐私保证 |
| [Gyges](https://dev.ndss-symposium.org/wp-content/uploads/2025-268-paper.pdf) | NDSS 2025正式论文；[官方报告页材料](https://www.ndss-symposium.org/wp-content/uploads/5B-f0268-dong.pdf) | 匿名与选择性追责能否兼容 | PDF第3—7、11—12页；四方诚实多数、预处理、单轮保护是重要边界 |
| [H2O2RAM](https://www.usenix.org/conference/usenixsecurity25/presentation/zheng) | USENIX Security 2025正式；会议2025-08-13至15 | TEE内外访存怎样同时隐藏且保持效率 | PDF第3—7、13页；信任安全处理器，最大加速比绑定操作和规模 |
| [Do We Really Need Reference-Based Phishing Detection?](https://doi.org/10.23919/tma66427.2025.11096997) | TMA 2025相关论文；仅核对PDF摘要，日级会议/出版日期待确认 | 域名和DOM的图模型能否替代品牌参考库依赖 | PDF第1页支持GNN二分类方向；DOI入口未成功获取，未用其确认具体出版日 |
| [PrivTune](https://arxiv.org/abs/2512.08809) | 首发2025-12-09；v3为2026-01-21；官方标注INFOCOM 2026录用 | 中间表示噪声怎样兼顾微调与防反演 | PDF第3—9页，官方版本历史；$d_\chi$条件需与标准DP区别 |
| [SpecularNet](https://arxiv.org/abs/2603.01874) | 首发2026-03-02；本次按预印本标识 | DOM层次图自编码与轻量无参考检测 | PDF第3—8页；包括2026现场数据，不能扩大到任意白盒重设计攻击 |
| [Frequency-Aware Continual Learning for Smart Contract Vulnerability Detection](https://arxiv.org/abs/2608.19680) | 首发2026-08-20；预印本 | 新漏洞学习、旧知识保留、单模型部署怎样协同 | PDF第4—9页；全文数据统计存在内部差异，见下 |
| [JBShield](https://www.usenix.org/conference/usenixsecurity25/presentation/zhang-shenyi) | USENIX Security 2025正式；会议2025-08-13至15 | 模型表示中的越狱机制能否用于防御 | 跨入02可信ML；PDF第5—9页已核验，不能只测攻击而不测无害请求误拒 |

## 怎样看演进，而不是只看年份

ORAM路线从抽象访问轨迹不可区分走向硬件辅助应用；DP路线从单次机制走向复杂训练与反复查询的预算管理；联邦和拆分训练改变数据流转位置，但仍要逐项检查表示、梯度和参与行为泄漏。匿名系统把在线开销、离线预处理和追踪权分开，检测系统则把模型效果、输入资源依赖和部署成本放在同一张表里。

所选近期工作提供三种不同切入点：PrivTune关注端云边界；SpecularNet关注轻量检测的结构归纳偏置和时间泛化；合约持续学习关注知识更新与部署合并。不能把三者合为“LLM更安全”的单一趋势，也不能把新年份等同于更强证据。

## 正文阅读范围

| 论文 | 已读PDF页（按文件页序） | 方法证据 | 实验/范围证据 |
|---|---|---|---|
| [PrivTune](../papers/P003.md) | 3—9 | 反演目标、扰动优化、随机噪声、令牌权重 | 五数据集、两任务、三类反演及三类属性攻击；第4页攻击者知识限制 |
| [Gyges](../papers/P030.md) | 3—7、11—12 | BPC关联随机性、秘密共享洗牌、追踪 | 区分在线与预处理代价；第5页非目标、第12页批量规模影响 |
| [H2O2RAM](../papers/P038.md) | 3—7、13 | 分层设计、不经意哈希与规划器 | 块大小、规模和并行度改变访问成本；可信处理器假设 |
| [SpecularNet](../papers/P136.md) | 3—5、8 | DOM定向消息传递、图自编码和域名表示 | 时间变化、HTML规避与明确非目标 |
| [合约持续学习](../papers/P001.md) | 4—5、8—9 | 频域门控、回放、合并 | DIVE任务分割、模型和资源设置；数据量待核对 |

阅读范围限于表中正文页；未全面覆盖每篇证明、消融和附录。同名论文的多份记录不应重复计作独立成果。未取得正文的研究仅以题名或官方摘要标注。

## 核验发现与待确认项

1. **PrivTune日期口径不同。** 官方arXiv首发2025-12-09、v3修订2026-01-21，并标注INFOCOM 2026录用。会议年份不应改称预印本首发时间。
2. **P001数据统计有内部差异。** PDF第8页声称DIVE共22,330份合约，表1四任务总数6334、6308、6311、6561相加为25,514。不能猜测是重叠样本还是排版错误，未澄清前不据该表推断独立样本量；复现需核对数据定义。
3. **阅读范围不等于发表状态。** TimeProtect、VizardFL等未读正文的研究，不据题名推断协议或实验。缺少日期信息也不自动表示未发表。
4. **发表状态只用已核实证据。** 官方摘要写录用而未核对会议出版记录时，记“官方标注录用”；arXiv DOI不代表同行评审。引用或复现时仍需核对所用版本。
5. **联网获取局限。** P137的IEEE DOI入口本次工具无法访问，保留DOI链接及PDF摘要证据，未据此确认具体出版日。其余列出的可读官方入口提供各自的状态证据，不以抓取失败推断论文不存在。

## 可继续检验的研究假设

这些是本整理提出的假设：端云隐私防御在攻击者公开知道权重和噪声机制时可能有不同效用曲线；网页结构模型的时间泛化可能受模板复用影响；匿名广播的长期关联性与单轮效率需要联合评测。下一步先明确变量和基线，不把假设写成已证实结论。

## 扩展代表文献与版本

本表列出直接论文来源与版本状态。录用声明与正式出版分别记录。

| 论文 | 已核验来源 | 发表与版本状态 | 阅读依据 |
|---|---|---|---|
| [DEFUSE: Generalizable Backdoor Defense for Self-Supervised Encoders with Generative Priors](../papers/P052.md) | [直接来源](<https://arxiv.org/abs/2608.25851v1>) | arXiv 作者备注：Accepted at ACM Multimedia 2026；录用声明已核，未独立核会议正式出版日期。 | fulltext |
| [The Platonic Defense: Backdoor Defense for Self-Supervised Encoders in the Era of Large Scale Pre-training](../papers/P055.md) | [直接来源](<https://arxiv.org/abs/2606.29451v1>) | 已核 arXiv 预印本；官方摘要页未见会议/期刊发表声明，本次未确认正式发表。 | abstract |
| [PA-Attack: Guiding Gray-Box Attacks on LVLM Vision Encoders with Prototypes and Attention](../papers/P061.md) | [直接来源](<https://arxiv.org/abs/2602.19418v1>) | 作者主页列 CVPR 2026；已核 arXiv，尚未在本次检索定位单篇 CVF proceedings。 | abstract |
| [Symbiotic Game and Foundation Models for Cyber Deception Operations in Strategic Cyber Warfare](../papers/P148.md) | [直接来源](<https://arxiv.org/abs/2403.10570>) | Foundations of Cyber Deception正式书章2025-10-21；arxiv首发2024-03-14。 | fulltext |
| [Adaptive security response strategies through conjectural online learning](../papers/P151.md) | [直接来源](<https://arxiv.org/abs/2402.12499>) | IEEE TIFS正式期刊2025卷20页4055–4070；arxiv首发2024-02-19。 | fulltext |
| [Decision-dominant strategic defense against lateral movement for 5G zero-trust multi-domain networks](../papers/P154.md) | [直接来源](<https://link.springer.com/chapter/10.1007/978-3-031-53510-9_2>) | Network Security Empowered by Artificial Intelligence正式书章2024-02-24；arxiv首发2023-10-02。 | abstract |
