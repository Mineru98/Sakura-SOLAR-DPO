# PlatYi-34
<img src='./PlatYi.png' width=256>    

**PlatYi-34B project; Purpose is `the global LLM rank 1.`**    
I noted that all most of things about the PlatYi models, which is `the global LLM Rank 1 on December, 2023`.  
⭐So, please give me a star⭐~~!!   

I hope, the opensource more and more develop!😄😄  

# Contents  
- [Model Performance](https://github.com/KyujinHan/PlatYi-34?tab=readme-ov-file#model-performance)  
- [Hyperparameters & Prompt](https://github.com/KyujinHan/PlatYi-34?tab=readme-ov-file#hyperparameters--prompt)  
- [Some Insight](https://github.com/KyujinHan/PlatYi-34?tab=readme-ov-file#some-insight)  
- [References](https://github.com/KyujinHan/PlatYi-34?tab=readme-ov-file#references)  
  
# (Quick) Model lists
- (Coming soon...)
- [PlatYi-34B-Llama-Q](https://huggingface.co/kyujinpy/PlatYi-34B-Llama-Q)  
- [PlatYi-34B-Q](https://huggingface.co/kyujinpy/PlatYi-34B-Q)
- [PlatYi-34B-LoRA](https://huggingface.co/kyujinpy/PlatYi-34B-LoRA)

# Introduction
- Recently, I created the [Ko-platypus🥮](https://github.com/Marker-Inc-Korea/KO-Platypus) LLM, which was `Korean LLM Rank 1`.  
- I wanted to take it a step further and make the global number one as well!!  
- So, using [Yi-34B](https://huggingface.co/01-ai/Yi-34B) based LLM, I tried fine-tuning😓.  
- Through a lot of trial and error, I found my way.
- Recently, all most of model used DPO. But I want to prove that `pure instruction-tuning method with LoRA can reach Rank 1, in December, 2023.`
- In this project, I only used the **instruction-tuning with PEFT.** Because I want to show that `LoRA is very powerful, also the platypus method is also good!`.
- (And also, `LoRA is very simply`, is it right?😄)  
- **This repository almost releases the knowledge base for that model!!😚😚**  
- (Because, I love opensource.❤️)  
   
# News
(Coming soon...)🤗🤗

# Model Performance
| Model | Average | ARC | HellaSwag | MMLU | TruthfulQA | Winogrande | GSM8K |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [PlatYi-34B-Llama-Q](https://huggingface.co/kyujinpy/PlatYi-34B-Llama-Q) | 71.13 | 65.70 | 85.22 | 78.78 | 53.64 | 83.03 | 60.42 |
| [PlatYi-34B-Q](https://huggingface.co/kyujinpy/PlatYi-34B-Q) | 69.86 | 66.89 | 85.14 | 77.66 | 53.03 | 82.48 | 53.98 |
| [PlatYi-34B-LoRA](https://huggingface.co/kyujinpy/PlatYi-34B-LoRA) | 68.1 | 67.15 | 85.37 | 78.46 | 53.32 | 83.66 | 40.64 |  
| [Yi-34B-Llama](https://huggingface.co/chargoddard/Yi-34B-Llama) | 70.95 | 64.59 | 85.63 | 76.31 | 55.60 | 82.79 | 60.80 |
| [Yi-34B](https://huggingface.co/01-ai/Yi-34B) | 69.42 | 64.59 | 85.69 | 76.35 | 56.23 | 83.03 | 50.64 |
> Follow up as [link](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard).  

# Hyperparameters & Prompt
- 😎PlatYi-34B-Llama-Q
   
| Hyperparameter      | PlatYi-34B-Llama-Q  |
|---------------------|--------|
| LoRA method         | LoRA   |
| load_in_4bit        | True   |
| learning rate       | 3e-4   |
| batch size          | 16     |
| microbatch  size    | 1      |
| warmup steps        | 100    |
| epochs              | 1      |
| weight decay        | 0.     |
| lr scheduler        | cosine |
| lora alpha          | 16     |
| lora rank           | 16     |
| lora dropout        | 0.05   |
| lora target modules | gate_proj, up_proj, down_proj |
| cutoff length       | 4096   |
| train on inputs     | False  |
| group by length     | False  |
| add eos token       | False  |
| Datasets            | [Open-Platypus](https://huggingface.co/datasets/garage-bAInd/Open-Platypus) |  
```
{
    "description": "Template used by Alpaca-LoRA.",
    "prompt_input": "Below is an instruction that describes a task, paired with an input that provides further context. Write a response that appropriately completes the request.\n\n### Instruction:\n{instruction}\n\n### Input:\n{input}\n\n### Response:\n",
    "prompt_no_input": "Below is an instruction that describes a task. Write a response that appropriately completes the request.\n\n### Instruction:\n{instruction}\n\n### Response:\n",
    "response_split": "### Response:"    
}
```
> [Alpaca templates.](https://github.com/arielnlee/Platypus/blob/main/templates/alpaca.json)
---  
- 😎PlatYi-34B-Q
  
| Hyperparameter      | PlatYi-34B-Q  |
|---------------------|--------|
| LoRA method         | LoRA   |
| load_in_4bit        | True   |
| learning rate       | 4e-4   |
| batch size          | 16     |
| microbatch  size    | 1      |
| warmup steps        | 0      |
| epochs              | 1      |
| weight decay        | 0.     |
| lr scheduler        | cosine |
| lora alpha          | 16     |
| lora rank           | 16     |
| lora dropout        | 0.05   |
| lora target modules | gate_proj, up_proj, down_proj |
| cutoff length       | 4096   |
| train on inputs     | False  |
| group by length     | False  |
| add eos token       | False  |
| Datasets            | [Open-Platypus](https://huggingface.co/datasets/garage-bAInd/Open-Platypus) |  
```
{
    "description": "Template used by Alpaca-LoRA.",
    "prompt_input": "Below is an instruction that describes a task, paired with an input that provides further context. Write a response that appropriately completes the request.\n\n### Instruction:\n{instruction}\n\n### Input:\n{input}\n\n### Response:\n",
    "prompt_no_input": "Below is an instruction that describes a task. Write a response that appropriately completes the request.\n\n### Instruction:\n{instruction}\n\n### Response:\n",
    "response_split": "### Response:"    
}
```
> [Alpaca templates.](https://github.com/arielnlee/Platypus/blob/main/templates/alpaca.json)
---  
- 😎PlatYi-34B-LoRA
  
| Hyperparameter      | PlatYi-34B-LoRA  |
|---------------------|--------|
| LoRA method         | LoRA   |
| load_in_8bit        | True   |
| learning rate       | 4e-4   |
| batch size          | 16     |
| microbatch  size    | 1      |
| warmup steps        | 0      |
| epochs              | 1      |
| weight decay        | 0.     |
| lr scheduler        | cosine |
| lora alpha          | 16     |
| lora rank           | 16     |
| lora dropout        | 0.05   |
| lora target modules | gate_proj, up_proj, down_proj |
| cutoff length       | 4096   |
| train on inputs     | False  |
| group by length     | False  |
| add eos token       | False  |
| Datasets            | [Open-Platypus](https://huggingface.co/datasets/garage-bAInd/Open-Platypus) |  
```
{
    "description": "Template used by Alpaca-LoRA.",
    "prompt_input": "Below is an instruction that describes a task, paired with an input that provides further context. Write a response that appropriately completes the request.\n\n### Instruction:\n{instruction}\n\n### Input:\n{input}\n\n### Response:\n",
    "prompt_no_input": "Below is an instruction that describes a task. Write a response that appropriately completes the request.\n\n### Instruction:\n{instruction}\n\n### Response:\n",
    "response_split": "### Response:"    
}
```
> [Alpaca templates.](https://github.com/arielnlee/Platypus/blob/main/templates/alpaca.json)  
  
# Some Insight
(Coming soon)🤩🤩

# TODO
- [ ] Share code
- [ ] Share hyperparameters
- [ ] Share insight
- [ ] Share datasets

# References
- [Yi-34B](https://huggingface.co/01-ai/Yi-34B)  
- [Yi-34B-Llama](https://huggingface.co/chargoddard/Yi-34B-Llama)  
- [Platypus](https://platypus-llm.github.io/)  
- [Ko-platypus](https://github.com/Marker-Inc-Korea/KO-Platypus)  
