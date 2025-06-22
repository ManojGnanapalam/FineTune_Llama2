
# 🔥 Fine-Tuning LLaMA-2 on Wildfire Data

This project demonstrates how to fine-tune the [LLaMA-2-7b-chat](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf) model using wildfire related textual data. The goal is to build a domain adapted language model that can reason about wildfire incidents, improve emergency response insights, and answer fire related questions.

## 📚 Table of Contents

- [Demo](#-demo)
- [Project Overview](#-project-overview)
- [Model Architecture](#-model-architecture)
- [Dataset](#-dataset)
- [Fine-Tuning Process](#-fine-tuning-process)
- [Evaluation](#-evaluation)


---

## 🚀 Demo

Try the model in Colab: [FineTune_Llama_WildFire.ipynb](https://colab.research.google.com/drive/1mqByQYZOsLIE8_0IBnmW852SPFaF4vWS?usp=sharing)

---

## 📖 Project Overview

Wildfires pose a critical threat globally. This project fine-tunes the LLaMA-2-7b model on wildfire incident reports from Hawaii to build a question answering model capable of summarizing, reasoning, and responding to queries about wildfire events.

---

## 🧠 Model Architecture

- Base Model: `meta-llama/Llama-2-7b-chat-hf`
- Quantization: 4-bit using `bitsandbytes`
- LoRA Configuration:
  - `r=8`, `lora_alpha=64`
  - `dropout=0.05`
  - Target modules: `q_proj`, `k_proj`, `v_proj`, etc.

---

## 🗃️ Dataset

- Source: Manually collected wildfire text reports from Hawaii (August 2023)
- Format: Plain text (`.txt`) files
- Loader: `load_dataset("text")` via Hugging Face `datasets` library

---

## 🛠️ Fine-Tuning Process

- Tokenizer: `LlamaTokenizer`
- Adapter Training: LoRA via `peft` library
- Optimizer: `paged_adamw_8bit`
- Epochs: 3
- Training Framework: Hugging Face `transformers.Trainer`

---

## ✅ Evaluation

Sample Question:
> **Q**: *When did wildfires start?*  
> **A**: Lahaina fire was reported on August 8, 2023, at 2:55 p.m. and quickly spread...

Compare model performance:
- ✅ Fine-tuned model: More concise, domain-aware answers
- ❌ Base model: Generic, less contextual responses

---
