# Yunji(云笈)

收集、整理、分类gpt4生成的高质量中英文指令精调语料，并提供自己翻译的高质量数据。

可以从 **[huggingface yaojialzc/Yunji-v1](https://huggingface.co/datasets/yaojialzc/Yunji-v1)** 直接加载

# format

数据集格式处理：

1. 把收集的数据集都转化为sharegpt格式，其中alpaca格式的instruction和input在axolotl中使用`\n`连接放在user message中，Qwen推荐用`:`连接，这里为了表示内容的分割我用`\n\n`连接`.strip()`的instuction和input作为user message

# dataset zh

| ID | name | source | count |
|----|--------------|----------|--------------|
| 1  | [llm-wizard/alpaca-gpt4-data-zh](https://huggingface.co/datasets/llm-wizard/alpaca-gpt4-data-zh) | 从Alpaca GPT-4数据中提取 | 49k |
| 2  | [Azure99/blossom-chat-v3](https://huggingface.co/datasets/Azure99/blossom-chat-v3) (中文部分) | 从ShareGPT中提取 | 3k |
| 3  | [Azure99/blossom-math-v4](https://huggingface.co/datasets/Azure99/blossom-math-v4) (中文部分) | 从GSM8K、Math23K中提取 | 7k |
| 4  | [Azure99/blossom-orca-v3](https://huggingface.co/datasets/Azure99/blossom-orca-v3) (中文部分) | 从OpenOrca中提取 | 20k |
| 5  | [Azure99/blossom-wizard-v3](https://huggingface.co/datasets/Azure99/blossom-wizard-v3) (中文部分) | 从WizardLM_evol_instruct_V2提取指令 | 10k |
| 6  | [glaive-function-calling-v2-zh](https://huggingface.co/datasets/wenbopan/OpenHermes-2.5-zh) | 从glaive-function-calling-v2中翻译，来自wenbopan/OpenHermes-2.5-zh | 5k |
| 7  | [OpenHermes-2.5-zh](https://huggingface.co/datasets/wenbopan/OpenHermes-2.5-zh) | 从OpenHermes-2.5中翻译，来自wenbopan/OpenHermes-2.5-zh | 86k |


