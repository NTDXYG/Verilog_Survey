## 相关数据集对比

| 数据集名称 | 发表时间 | 编程语言 | 训练集规模 | 测试集规模 | 开源情况 | 评估指标 |
|------------|----------|----------|------------|------------|----------|----------|
| DAVE | 2020 | Verilog | 未公开 | 未公开 | 闭源 | Ratcliff-Obershelp 相似度 |
| VeriGen | 2023 | Verilog | 109k | 17条（手工编写） | 训练集开源<br>测试集开源 | 语法/pass@k |
| VerilogEval | 2023 | System Verilog | 800+ | VerilogEval-machine: 143条（LLM合成）<br>VerilogEval-human: 156条（手工编写） | 训练集闭源<br>测试集开源 | 语法/pass@k |
| Rtllm | 2024 | Verilog | 无 | RTLLM V1.1: 30条（手工编写）<br>RTLLM V2.0: 50条（手工编写） | 测试集开源 | 语法/pass@k/PPA |
| RTLCoder | 2024 | Verilog | RTLCoder-27K（LLM合成） | 无 | 开源 | 语法（无测试用例） |
| OriGen | 2024 | Verilog | OriGen 222k (verilog生成)<br> OriGen_debug (语法错误的verilo修复) 5.44k| VerilogFixEval (verilog修复) | 开源 | 语法/pass@k |
| RTLFixer | 2024 | System Verilog | 无 | VerilogEval-Syntax  <br>VerilogEval-Simulate | 开源 | 语法/pass@k |
| chipgptft| 2024 |
| OpenLLM-RTL| 2024|
| BetterV| 2024|
| MG-Verilog| 2024|
| RTLRewriter| 2024|
| RTL-Repo| 2024|
| VHDL-Eval| 2024 | VHDL|
| CreativEval| 2024|
| AutoVCoder | 2024|
| CraftRTL | 2024 |
| From English to ASIC: Hardware Implementation with Large Language Model| 2024|
| AutoChip | 2025 | Verilog | 无 | 120 | 开源 | 语法/pass@k |
| Revisiting VerilogEval | 2025 | System Verilog | 无 | VerilogEvalV2 |
| DeepRTL| 2025 |
| CodeV| 2025|
| HaVen| 2025|
| VeriPrefer| 2025|
| ResBench | 2025 |
| RTL++ | 2025
| TuRTLe| 2025

### 数据集特点
- **DAVE**：首个将GPT-2应用于自然语言到Verilog转换的数据集
- **VeriGen**：目前规模最大的开源数据集
- **VerilogEval**：提供人工编写的测试集，更贴近实际应用场景
- **Rtllm**：专注于PPA（性能、功耗、面积）评估
- **RTLCoder**：专注于训练集构建，无测试集