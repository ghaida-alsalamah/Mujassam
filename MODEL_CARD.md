# Mujassam QLoRA Adapter

## Base Model
Qwen/Qwen2.5-Coder-7B-Instruct

## Purpose
This adapter specializes Qwen2.5-Coder-7B-Instruct for generating
parametric CadQuery code from natural-language mechanical-part requests.

## Adaptation
- Method: QLoRA
- Rank: 16
- Alpha: 32
- Dropout: 0.05
- Quantization: 4-bit NF4
- Context length: 2048 tokens
- Training epochs: 2

## Training Data
The adapter was trained on project-generated and programmatically verified CAD data.

- 5,860 direct generation examples
- 963 repair examples
- 6,823 total supervised records
- 76 training part types
- 2 validation-only part types
- 7 completely held-out part types

## Runtime
The adapter is loaded on top of:

`Qwen/Qwen2.5-Coder-7B-Instruct`

Mujassam also uses RAG with engineering construction recipes and CadQuery API notes.

## Intended Use
Generation of simple-to-moderate parametric mechanical CAD parts for educational and prototyping use.

## Limitations
The model is less reliable on unfamiliar topology, complex sweeps, lofts,
angled geometry, and unusual feature combinations.

Generated parts should be inspected before printing or real-world use.

## Team
- Ghaida Alsalamah
- Alreem Aldossary
- Fahad Alshehri
