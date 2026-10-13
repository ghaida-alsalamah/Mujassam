---
base_model: Qwen/Qwen2.5-Coder-7B-Instruct
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:Qwen/Qwen2.5-Coder-7B-Instruct
- lora
- qlora
- transformers
- cadquery
- text-to-cad
- generative-cad
---

# Mujassam QLoRA Adapter

This repository contains the trained QLoRA adapter used by **Mujassam · مجسّم**, a generative CAD system that converts natural-language mechanical-part descriptions into parametric CadQuery programs.

The adapter is loaded on top of:

`Qwen/Qwen2.5-Coder-7B-Instruct`

Mujassam then executes the generated CadQuery code, validates the resulting geometry, and exports supported results as STEP, STL, and GLB files.

---

## Model Details

- **Project:** Mujassam · مجسّم
- **Base model:** `Qwen/Qwen2.5-Coder-7B-Instruct`
- **Adaptation method:** QLoRA
- **Task:** Natural-language mechanical-part description → CadQuery code
- **Framework:** PEFT / Transformers
- **CAD engine:** CadQuery
- **Language:** English
- **Intended domain:** Simple-to-moderate mechanical CAD generation

---

## Training Configuration

| Parameter | Value |
|---|---|
| Base model | `Qwen/Qwen2.5-Coder-7B-Instruct` |
| Quantization | 4-bit NF4 |
| Double quantization | Enabled |
| Adaptation | QLoRA |
| LoRA rank | 16 |
| LoRA alpha | 32 |
| LoRA dropout | 0.05 |
| Context length | 2,048 tokens |
| Epochs | 2 |
| Training steps | 836 |
| Trainable parameters | ~40.4M |
| Trainable percentage | ~0.53% |
| Loss scope | Assistant response only |

---

## Training Data

The adapter was trained on project-generated procedural CAD supervision.

### Dataset size

- **5,860** verified direct-generation examples
- **963** repair examples
- **6,823** total supervised chat-format records
- **76** part types used for training
- **2** validation-only part types
- **7** completely held-out part types

### Training record format

Each direct-generation record follows a chat structure:

```text
SYSTEM
CadQuery generation rules and real-millimetre constraints

USER
Mechanical-part request + retrieved RAG context

ASSISTANT
Verified CadQuery program
