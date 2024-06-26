<div align="center">
<h1>
  MiniMATH
</h1>
</div>

<h4 align="center">
    <p>
        <b>中文</b> | <a href="https://github.com/jzx-ai-lab/MiniMATH/blob/main/README.md">English</a>
    <p>
</h4>


<p align="center">
<a href="report.md" target="_blank">MiniMath 技术报告</a> | 
<a href = "https://www.modelscope.cn/models/jzx-ai-lab/MiniMATH/summary"
target = "_blank">modelscope</a>

MiniMATH-1.5B-base 是基于19B 精选的数学相关题目、文字、对话数据的预训练模型，在未经过SFT， DPO等流程，并且严格隔离了测试数据的前提下，在中文数学题目的逻辑推理上取得了较好的效果，且与对齐后的模型具有类似的对话、指令跟随能力。同时，模型训练过程中也未采用学习率调度等技术行为，仅使用了两阶段的batchsize调度及四阶段的数据配比调整，通过不同阶段的性能实验，验证了高质量、合理配比的数据对模型生成效果的重要性。

### 局限性:
- 受限于模型规模和单纯的pretrain 训练方法，模型可能出现幻觉性问题和回声问题。
- 受限于数据规模，模型主要在中文的高质量内部题目上进行训练，因此英文题目的表现可能不佳。
- 受限于pretrain 训练方法，模型在多轮对话中的表现可能不佳。
- 受限于pretrain 训练方法，模型回复内容偏向于冗长，同时由于规模的限制，幻觉性问题可能进一步加重。

## 目录

- [更新日志](#0)
- [模型下载](#1)
- [评测结果](#2)

<p id="0"></p>

## 更新日志
- 2024/04/01 初始发布。

<p id="1"></p>

## 模型下载
- coming soon

<p id="2"></p>

## 评测结果

#### 评测设置

* 由于MiniMATH是使用大量数学相关知识训练的特化模型，因此我们仅在数学相关的任务以及两个通用文本任务上进行了评测，为了最大限度保证评估结果的准确性，我们使用了较为严格的正则匹配来评估模型在不同任务上的表现
* **同时我们也将评估脚本全部开源，为评估提供可靠的复现**

#### 文本模型评测

**同级比较：**
|模型|Non-Emb Params|C-Eval|CMMLU|MMLU|GSM8K|MATH|MATH23K|数学均分|training-token|
|-|-|-|-|-|-|-|-|-|-|
|TinyLlama-1.1B|1.1B|25.02|24.03|24.3|2.27|0.74|-|1.5|~1T
|Qwen1.5-1.8B|1.2B|59.7|57.8|46.8|38.4|10.1|58.3|35.6|-|
|Gemini Nano-3B|-|-|-|-|22.8(report)|-|-|-|-|
|StableLM-Zephyr-3B|2.7B|30.34|30.89|45.9|52.54|12.49|37.68|32.5|-|
|Phi-1.5|-|-|-|42.87|40.2|-|-|-|150B 
|Phi-2-2B|2.5B|23.37|24.18|52.66|57.16|3.5|43.39|30.35|1.4T
|MiniCPM-2B|2.4B|51.13|51.07|53.46|53.83|10.24|67.5|43.83|~1T
|MiniMATH-1.5B|1.2B|41.64|42.70|29.13|43.34|14.5|60.04|39.29|64B
