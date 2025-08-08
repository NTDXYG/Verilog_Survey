# ChipGPT: How far are we from natural language hardware design

## 基本信息
- **会议/期刊**: arxiv
- **发表时间**: 2023
- **作者**: Kaiyan Chang, Ying Wang, Haimeng Ren, Mengdi Wang, Shengwen Liang, Yinhe Han, Huawei Li, Xiaowei Li
- **作者单位**: Chinese Academy of Sciences, University of Chinese Academy of Sciences, ShanghaiTech University
  
## 摘要
提出首个基于大语言模型（LLM）的自然语言硬件设计框架ChipGPT，通过四阶段零代码流程（Prompt管理→LLM生成→输出管理→PPA搜索）将自然语言规格自动转换为Verilog代码，无需微调模型。实验表明，相比传统方法，代码量减少5.32-9.25倍，复杂设计的面积优化达47%。

## 研究背景
- 硬件设计痛点：传统RTL设计（如Verilog）需手动编码，耗时且易出错；现有敏捷方法（Chisel/HLS）仍需编程技能。
- LLM潜力：ChatGPT等模型在代码生成中表现优异，但直接用于硬件设计存在三大挑战：
  - 自然语言输入模糊，难以精准映射到硬件规范；
  - LLM输出缺乏PPA（功耗/面积/性能）感知；
  - 无法生成可扩展的层次化架构。

## 研究动机
探索自然语言硬件设计的可行性，解决LLM在硬件领域的适应性瓶颈，使非专家能通过自然语言描述快速生成可综合的硬件模块。

## 主要贡献
- **贡献 1**：首个系统性评估LLM（ChatGPT）在硬件逻辑设计中的能力。
- **贡献 2**：提出四阶段零代码框架（Prompt Manager→LLM→Output Manager→搜索优化），无需微调LLM即可生成PPA优化的Verilog代码。
- **贡献 3**：设计三项Prompt工程原则（接口模型、后置添加、模块组合），将LLM输出正确性从“概率正确”提升至“规则正确”。

### 方法细节
1. Prompt Manager：
- 规格分割：将自然语言规范拆解为接口（iface）、功能（func）、组合（compose）三部分。
- 模板化生成：通过上下文学习构建Prompt序列，示例：
"作为Verilog专家，生成一个满足以下接口的模块：[接口定义]..."  
2. Output Manager：
- 自动纠错：先通过仿真器（如ModelSim）验证功能，再人工修正少量错误（平均<10行）。
- PPA优化：用Design Compiler评估功耗/面积，枚举搜索最优设计。
3. 分层生成：采用“自底向上”策略，先生成子模块再组合为顶层模块。

## 实验设计
- **评估指标**：
  - 代码量（LOC）减少倍数。
  - PPA优化率（以面积为主）。
  - 人工纠错行数
- **实验数据集**：7个基准设计（矩阵乘法、简单CPU、多路选择器等），分三类复杂度（SSM/CSM/CM）。。
- **实验模型**：OpenAI GPT-3.5（ChatGPT）。
- **方法细节实现**：65nm工艺，Design Compiler综合。

## 实验结果
- **RQ1**：（相比传统方法的优势）：ChipGPT代码量比HLS减少9.25倍，比Chisel减少5.32倍（图12）。
- **RQ2**：（框架有效性）：
  - 面积优化：复杂设计（如矩阵乘法）面积减少47%（表VII）。
  - 代码质量：人工纠错行数从ChatGPT的50+行降至<10行（图14）。

## 创新点
- 首个自然语言到硬件的端到端零代码框架。
- 通过Prompt工程解决LLM硬件适应性难题，无需微调。
- 引入PPA感知搜索，突破LLM“直觉设计”的局限性。

## 局限性
- 规模限制：当前仅支持数字逻辑设计，未验证模拟/混合信号电路。
- 依赖人工规则：Prompt模板需手工设计，泛化性待提升。
- 搜索效率：枚举搜索在复杂设计（如CPU）中耗时较高。
  
## 未来工作
- 扩展至模拟电路和时序约束自动生成。
- 探索多模态输入（如自然语言+时序图）。
- 集成强化学习优化搜索效率（替代枚举法）。

## 笔记
[待补充]