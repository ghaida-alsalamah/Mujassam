<div align="center">

Mujassam · مجسّم

Natural language → verified parametric CAD

<p>
  <a href="LIVE_DEMO_URL"><img src="https://img.shields.io/badge/Live_Demo-Open-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Live Demo"></a>
  &nbsp;
  <a href="DEMO_VIDEO_URL"><img src="https://img.shields.io/badge/Demo_Video-Watch-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Demo Video"></a>
</p>

<p>
  <img src="https://img.shields.io/badge/Model-Qwen2.5--Coder--7B-6B7280?style=flat-square&labelColor=0B1F3A" alt="Model">
  <img src="https://img.shields.io/badge/Adaptation-QLoRA_r16-6B7280?style=flat-square&labelColor=0B1F3A" alt="Adaptation">
  <img src="https://img.shields.io/badge/RAG-MiniLM_%2B_Chroma-6B7280?style=flat-square&labelColor=0B1F3A" alt="RAG">
  <img src="https://img.shields.io/badge/CAD-CadQuery-6B7280?style=flat-square&labelColor=0B1F3A" alt="CAD">
  <img src="https://img.shields.io/badge/Output-STEP_%7C_STL_%7C_GLB-6B7280?style=flat-square&labelColor=0B1F3A" alt="Output">
</p>

Tuwaiq Academy · Generative AI Application Engineering Bootcamp · October 2026

</div>

The Problem

A custom bracket, mount, spacer, bearing holder, or replacement part may be small—but creating it still requires CAD knowledge and time.

General-purpose language models can write CAD-like code, but a generated part can still:

fail to execute;

come out at the wrong scale;

contain disconnected geometry;

miss requested holes or features while looking plausible in the preview.

Mujassam was built around one rule: a generated part should be checked before it is handed to the user.

The Solution

Mujassam is a generative CAD tool for students, robotics teams, fab labs, and small workshops.

A user describes a mechanical part and gives its overall dimensions in millimetres. Mujassam retrieves compact engineering guidance, generates CadQuery with a fine-tuned code model, executes the program, measures the result, validates the geometry, and exports the accepted part.

Outputs: STEP for editing · STL for printing · GLB for browser preview.

<!-- Add final website screenshots here after backend integration.

<p align="center">
  <img src="docs/assets/home.png" width="49%" alt="Mujassam home">
  <img src="docs/assets/result.png" width="49%" alt="Mujassam generated part">
</p>

Optional physical-fit image:
<p align="center">
  <img src="docs/assets/physical-fit.jpg" width="65%" alt="Printed Mujassam part fitted to a real component">
</p>
-->

System Architecture

<p align="center">
  <img src="docs/assets/architecture.svg" alt="Mujassam system architecture" width="100%">
</p>

The Qwen2.5-Coder-7B + QLoRA component is the generative part of the system. It writes the CadQuery program for every request. There is no deterministic CAD compiler generating the final shape behind the model.

Request Workflow

<p align="center">
  <img src="docs/assets/workflow.svg" alt="Mujassam request workflow" width="100%">
</p>

A rejected build is not silently returned. Execution errors or failed geometry checks are sent back to the model for another attempt.

Model, Training & RAG

<p align="center">
  <img src="docs/assets/training_rag.svg" alt="Mujassam fine-tuning and RAG" width="100%">
</p>

Model

Base: Qwen/Qwen2.5-Coder-7B-Instruct

Adaptation: QLoRA · rank 16 · alpha 32 · dropout 0.05

Quantization: 4-bit NF4 with double quantization

Trainable weights: ~40.4M (~0.53%)

Context length: 2,048 tokens

Training: 2 epochs · 836 steps · assistant-only loss

Training data

<p>
  <img src="https://img.shields.io/badge/Designed_Part_Types-85-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="85 part types">
  <img src="https://img.shields.io/badge/Training_Types-76-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="76 training types">
  <img src="https://img.shields.io/badge/Direct_Examples-5%2C860-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="5860 examples">
  <img src="https://img.shields.io/badge/Repair_Examples-963-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="963 repair examples">
</p>

The final fine-tuning set is project-generated procedural CAD data. Parameterized generators vary dimensions, optional features, and natural-language phrasing, then produce the target CadQuery program.

Before an example enters training, the target is executed and checked for:

safe executable CadQuery;

exactly one valid solid;

correct overall envelope;

watertight STL;

requested hole diameters where applicable;

expected solid / empty feature probes.

5,860 / 5,860 direct examples passed verification.

Feature composition

Six special generators create parts by combining 2–4 compatible CAD features:

composed_plate · composed_block · composed_disc · composed_l_bracket · composed_ring · composed_tray

This teaches reusable operations such as holes, patterns, slots, pockets, bosses, chamfers, and cut-outs instead of relying only on fixed named-part templates.

RAG

The runtime knowledge base contains:

16 engineering construction recipes

8 CadQuery API notes

sentence-transformers/all-MiniLM-L6-v2

Chroma vector retrieval

Per request, Mujassam retrieves up to one engineering recipe and two API notes. The RAG context guides the model; it does not contain the finished CAD answer.

Evaluation

All figures below are from the saved final run using the frozen model and one greedy first attempt per case.

Evaluation set

What it tests

Overall-size pass

Size + requested holes

In-domain regression

familiar learned CAD operations

20/20 · 100%

20/20 · 100%

Second in-domain regression

additional familiar cases

12/12 · 100%

12/12 · 100%

Sealed user test

30 new requests not used for tuning

13/30 · 43.3%

13/30 · 43.3%

Held-out part types

28 cases from 7 types excluded from training

10/28 · 35.7%

10/28 · 35.7%

Independent reserve

separate 20-case set

5/20 · 25.0%

5/20 · 25.0%

What the numbers tell us

Mujassam is strongest on simple-to-moderate mechanical designs that use CAD operations represented in training. Performance drops on unfamiliar topology and harder feature interactions.

On the sealed test, the main remaining failure modes were:

code-generation errors;

wrong overall dimensions;

invalid geometry.

The project reports this generalization gap directly rather than hiding it behind only familiar examples.

Validation & Safety

Automatically checked

generated code passes AST safety rules;

CadQuery executes in an isolated process with a timeout;

exactly one valid solid is produced;

STL is watertight;

overall dimensions match the request within tolerance;

requested holes / bores are checked where supported;

rejected outputs are not exported.

Still requires human inspection

uncommon slot geometry;

advanced lofts / sweeps;

subtle feature orientation;

every pocket / chamfer relationship;

structural suitability and real mechanical fit.

Mujassam is a capstone prototype, not an engineering-certification system. Generated parts should not be used for safety-critical applications without proper engineering review.

Live Demo

Open Mujassam →

Demo Video

Watch the demo →

Run the Project

Quickest option · Colab

Open Mujassam_demo.ipynb.

Select a T4 GPU or better.

Run the cells in order.

Upload Mujassam_QWEN7B_V5_project.zip when requested.

Upload mujassam_v5_A_7B_r16_adapter.zip when requested.

Wait for the base model + trained adapter to load.

Launch the application from the final cell.

Example request:

Flanged bearing mount, overall 48 x 48 x 18 mm,
24 mm central bore, four 4 mm mounting holes
on a 36 mm square pattern.

Local setup

git clone REPOSITORY_URL
cd mujassam_mvp_project

python -m venv .venv

Windows

.venv\Scripts\activate

macOS / Linux

source .venv/bin/activate

Then:

pip install -r requirements.txt

A CUDA-capable GPU is recommended for local 7B inference.

Repository Structure

mujassam_mvp_project/
├── README.md
├── requirements.txt
├── app.py
├── Mujassam_demo.ipynb
│
├── mujassam/
│   ├── engineering_rag.py
│   ├── rag.py
│   ├── loop.py
│   ├── executor.py
│   ├── safety.py
│   ├── validate.py
│   ├── features.py
│   ├── monitor.py
│   └── gen_v5/
│
├── data/
├── scripts/
├── tests/
├── results/
└── docs/

Data Sources & Licences

Qwen2.5-Coder-7B-Instruct — base model · Apache-2.0

Project-generated procedural CAD dataset — final fine-tuning supervision

all-MiniLM-L6-v2 — RAG embeddings · see upstream model card

CadQuery — parametric CAD execution · see upstream project licence

Chroma — vector retrieval · see upstream project licence

Transformers · PEFT · bitsandbytes — model loading, QLoRA, and quantized inference · see upstream licences

No external CAD dataset is used to train the final adapter.

Monitoring

Each build records the information needed to understand failures and performance:

request · model · retrieval scores · pass/fail · rejected gate · error type · attempts · dimension error · latency · output paths

The application also rejects weapon / ammunition-part requests before CAD generation and warns users not to submit personal data because requests may be logged.

Lessons & Next Steps

What worked

Verified procedural training data, code-focused QLoRA, compact RAG guidance, and execution-based validation.

Main limitation

Generalization to genuinely new geometry is still much weaker than performance on familiar CAD operations.

Next

Stronger semantic feature validation · broader topology coverage · persistent GPU deployment · Arabic input · more real-world fit tests.

Team

<div align="center">

👤          👤          👤

Alreem Rashed Aldossary      Fahad Alshehri      Ghaida Alsalamah

</div>

Project Links

Live application: LIVE_DEMO_URL

Demo video: DEMO_VIDEO_URL

Repository: REPOSITORY_URL

<details>
<summary><b>AI-assisted development disclosure</b></summary>

AI tools were used during development for brainstorming, implementation support, debugging, code review, generator review, documentation, and interface prototyping.

Training targets were executed and programmatically verified before inclusion in the training set. Reported evaluation figures come from saved project runs.

</details>

<div align="center">

Mujassam · مجسّم

Describe it · Generate it · Check it · Print it

</div>
