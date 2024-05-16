---
license: apache-2.0
task_categories:
- text-generation
language:
- zh
pretty_name: Yunji
size_categories:
- 100K<n<1M
configs:
- config_name: alpaca-gpt4-data-zh
  data_files:
  - split: train
    path: "dataset-zh/alpaca-gpt4-data-zh.jsonl"
- config_name: blossom-chat-v3-zh
  data_files:
  - split: train
    path: "dataset-zh/blossom-chat-v3-zh.jsonl"
- config_name: blossom-math-v4-zh
  data_files:
  - split: train
    path: "dataset-zh/blossom-math-v4-zh.jsonl"
- config_name: blossom-orca-v3-zh
  data_files:
  - split: train
    path: "dataset-zh/blossom-orca-v3-zh.jsonl"
- config_name: blossom-wizard-v3-zh
  data_files:
  - split: train
    path: "dataset-zh/blossom-wizard-v3-zh.jsonl"
- config_name: glaive-function-calling-v2-zh
  data_files:
  - split: train
    path: "dataset-zh/glaive-function-calling-v2-zh.jsonl"
- config_name: OpenHermes-2.5-zh
  data_files:
  - split: train
    path: "dataset-zh/OpenHermes-2.5-zh.jsonl"
- config_name: RefGPT-Fact-v2-zh
  data_files:
  - split: train
    path: "dataset-zh/RefGPT-Fact-v2-zh.jsonl"
- config_name: RefGPT-Code-cr-zh
  data_files:
  - split: train
    path: "dataset-zh/RefGPT-Code-cr-zh.jsonl"
- config_name: RefGPT-Code-bg-zh
  data_files:
  - split: train
    path: "dataset-zh/RefGPT-Code-bg-zh.jsonl"
- config_name: RefGPT-Code-ds-zh
  data_files:
  - split: train
    path: "dataset-zh/RefGPT-Code-ds-zh.jsonl"
---

![image/webp](https://cdn-uploads.huggingface.co/production/uploads/64ef2a96f2b8f40224d7b407/wpn8RyQzwheXqDB9l7fkm.webp)

# Yunji(云笈)

**[github Yunji(云笈)](https://github.com/liuyaojialiuyaojia/Yunji-v1)** 收集、整理、分类gpt4生成的高质量中英文指令精调语料，并提供自己翻译的高质量数据。

可以从 **[huggingface yaojialzc/Yunji-v1](https://huggingface.co/datasets/yaojialzc/Yunji-v1)** 直接加载

# dataset zh

高质量中文gpt4对话数据集：

| ID | name | source | count |
|----|--------------|----------|--------------|
| 1  | [llm-wizard/alpaca-gpt4-data-zh](https://huggingface.co/datasets/llm-wizard/alpaca-gpt4-data-zh) | 从Alpaca GPT-4数据中提取 | 49k |
| 2  | [Azure99/blossom-chat-v3](https://huggingface.co/datasets/Azure99/blossom-chat-v3) (中文部分) | 从ShareGPT中提取 | 3k |
| 3  | [Azure99/blossom-math-v4](https://huggingface.co/datasets/Azure99/blossom-math-v4) (中文部分) | 从GSM8K、Math23K中提取 | 7k |
| 4  | [Azure99/blossom-orca-v3](https://huggingface.co/datasets/Azure99/blossom-orca-v3) (中文部分) | 从OpenOrca中提取 | 20k |
| 5  | [Azure99/blossom-wizard-v3](https://huggingface.co/datasets/Azure99/blossom-wizard-v3) (中文部分) | 从WizardLM_evol_instruct_V2提取指令 | 10k |
| 6  | [glaive-function-calling-v2-zh](https://huggingface.co/datasets/wenbopan/OpenHermes-2.5-zh) | 从glaive-function-calling-v2中翻译，来自wenbopan/OpenHermes-2.5-zh | 5k |
| 7  | [OpenHermes-2.5-zh](https://huggingface.co/datasets/wenbopan/OpenHermes-2.5-zh) | 从OpenHermes-2.5中翻译，来自wenbopan/OpenHermes-2.5-zh | 86k |
| 8  | [Mutonix/RefGPT-Fact-v2](https://huggingface.co/datasets/Mutonix/RefGPT-Fact-v2?row=14) | 基于事实知识的对话 | 61k |
| 9  | [Mutonix/RefGPT-Code-cr](https://huggingface.co/datasets/Mutonix/RefGPT-Code-cr) | 代码生成 | 15k |
| 10 | [Mutonix/RefGPT-Code-bg](https://huggingface.co/datasets/Mutonix/RefGPT-Code-bg) | 修复代码bug | 10k |
| 11 | [Mutonix/RefGPT-Code-ds](https://huggingface.co/datasets/Mutonix/RefGPT-Code-ds) | 关于代码的讨论 | 14k |

# format

数据集格式处理：

1. 把收集的数据集都转化为sharegpt格式，其中alpaca格式的instruction和input在axolotl中使用`\n`连接放在user message中，Qwen推荐用`:`连接，这里为了表示内容的分割我用`\n\n`连接`.strip()`的instuction和input作为user message

2. [RefGPT](https://arxiv.org/pdf/2305.14994) 的相关数据集是根据外部知识指导gpt4生成的高质量数据集，旨在基于外部参考消除模型的幻觉构造更高质量的样本。paper中提及会使用gpt3.5快速筛选小众知识点，所以重点不是外部参考，这里直接去掉外部参考只使用其中的chat数据。

# others

在收集数据集中，发现了一些明显不是gpt生成的chat数据，但是同样有帮助：

| ID | name | source | count |
|----|--------------|----------|--------------|
| 1  | [Mutonix/RefGPT-Reason](https://huggingface.co/datasets/Mutonix/RefGPT-Reason?row=90) | 事实知识、逻辑类选择题 | 228k |
| 2  | [m-a-p/COIG-CQIA](https://huggingface.co/datasets/m-a-p/COIG-CQIA) | 基于LIMA，强调输入多样性的高质量中文知识问答 | 45k |
