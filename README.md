<div align="center">

Mujassam · مجسّم

Natural language → parametric CAD → verified geometry → printable files

<p>
  <a href="LIVE_DEMO_URL">
    <img src="https://img.shields.io/badge/Live_Demo-Open-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Live Demo">
  </a>
  &nbsp;
  <a href="DEMO_VIDEO_URL">
    <img src="https://img.shields.io/badge/Demo_Video-Watch-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Demo Video">
  </a>
</p>

<p>
  <img src="https://img.shields.io/badge/Model-Qwen2.5--Coder--7B-6B7280?style=flat-square&labelColor=0B1F3A" alt="Model">
  <img src="https://img.shields.io/badge/Adaptation-QLoRA_r16-6B7280?style=flat-square&labelColor=0B1F3A" alt="Adaptation">
  <img src="https://img.shields.io/badge/RAG-MiniLM_%2B_Chroma-6B7280?style=flat-square&labelColor=0B1F3A" alt="RAG">
  <img src="https://img.shields.io/badge/CAD-CadQuery-6B7280?style=flat-square&labelColor=0B1F3A" alt="CAD">
  <img src="https://img.shields.io/badge/Export-STEP_%7C_STL_%7C_GLB-6B7280?style=flat-square&labelColor=0B1F3A" alt="Exports">
</p>

Tuwaiq Academy · Generative AI Application Engineering Bootcamp · October 2026

</div>

The Problem

Small custom parts such as brackets, mounts, spacers, bearing holders, and replacement pieces still require CAD skills and manual modelling.

General-purpose LLMs can write CAD-like code, but the result may:

Risk

What can happen

Code failure

the generated CadQuery does not execute

Wrong dimensions

the preview looks plausible but the part does not fit

Invalid geometry

disconnected or non-watertight solids are produced

Missing features

holes or bores requested by the user are absent

Mujassam was built so a generated part is checked before it is exported.

The Solution

Mujassam is a generative CAD tool for students, robotics teams, fab labs, and small workshops.

The user describes a mechanical part and states its overall dimensions in millimetres. Mujassam retrieves engineering guidance, generates CadQuery, executes it, validates the result, retries rejected outputs, and returns editable and printable files.

Input

Generation

Verification

Output

Natural-language part description + overall size

Fine-tuned Qwen generates CadQuery

Safety · execution · geometry · dimensions · supported holes

STEP · STL · GLB

<!--
ADD FINAL WEBSITE SCREENSHOTS HERE

<p align="center">
  <img src="docs/assets/home.png" width="49%" alt="Mujassam home">
  <img src="docs/assets/result.png" width="49%" alt="Mujassam generated part">
</p>

Optional physical fit image:
<p align="center">
  <img src="docs/assets/physical-fit.jpg" width="65%" alt="Printed Mujassam part fitted to a real component">
</p>
-->

System Architecture

flowchart LR
    A["Web UI"] --> B["Pipeline Orchestrator"]
    B --> C["Specification Reader"]
    B --> D["RAG Retriever"]
    C --> E["Qwen2.5-Coder-7B + QLoRA"]
    D --> E
    E --> F["AST Safety Gate"]
    F --> G["CadQuery Executor"]
    G --> H["Geometry Validator"]
    H -->|PASS| I["STEP / STL / GLB"]
    H -->|REJECT| J["Failure Feedback"]
    J --> E
    G -.-> K["Monitoring"]
    H -.-> K

    style A fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style B fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style C fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style D fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style E fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style F fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style G fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style H fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style I fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style J fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style K fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff

Where is the generative AI?
The Qwen2.5-Coder-7B + QLoRA component writes the CadQuery program for every request. The rest of the system handles retrieval, safety, execution, validation, repair, monitoring, and export.

Request Flow

flowchart TD
    A["Describe the part + overall size"] --> B["Read measurable specification"]
    B --> C["Retrieve engineering context"]
    C --> D["Generate CadQuery"]
    D --> E{"Safe code?"}
    E -->|No| R["Send failure back to model"]
    E -->|Yes| F["Execute CadQuery"]
    F --> G{"One valid watertight solid?"}
    G -->|No| R
    G -->|Yes| H{"Overall size within tolerance?"}
    H -->|No| R
    H -->|Yes| I{"Supported holes / bores correct?"}
    I -->|No| R
    I -->|Yes| J["Preview + STEP + STL + GLB"]
    R --> D

    style A fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style B fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style C fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style D fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style E fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style F fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style G fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style H fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style I fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style J fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style R fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff

Model & Technology Stack

Component

Technology

Purpose

Base model

Qwen/Qwen2.5-Coder-7B-Instruct

CadQuery code generation

Adaptation

QLoRA · r=16 · alpha=32

task-specific fine-tuning

Quantization

4-bit NF4

memory-efficient training / inference

Embeddings

all-MiniLM-L6-v2

semantic retrieval

Vector DB

Chroma

RAG storage and search

CAD engine

CadQuery

parametric solid modelling

Interface

final web UI + backend

user input, preview, downloads

Exports

STEP · STL · GLB

editing, printing, web preview

Training Data

The final adapter is trained on project-generated procedural CAD data. Parameterized generators create the request, dimensions, features, and exact CadQuery target, then the target is executed and verified before it enters training.

Dataset split

pie showData
    title Designed part types
    "Training" : 76
    "Validation only" : 2
    "Completely held out" : 7

Dataset item

Count

Designed part types

85

Training part types

76

Validation-only types

2

Held-out test types

7

Verified direct-generation examples

5,860

Repair examples

963

Total chat-format training records

6,823

Training-data pipeline

flowchart LR
    A["Part Generator"] --> B["Random Valid Dimensions + Features"]
    B --> C["Natural-Language Request"]
    B --> D["Target CadQuery"]
    D --> E["Execute Target"]
    E --> F{"Verification Pass?"}
    F -->|No| G["Reject Example"]
    F -->|Yes| H["Training Record"]
    C --> H
    H --> I["QLoRA Fine-Tuning"]

    style A fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style B fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style C fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style D fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style E fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style F fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style G fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style H fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style I fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A

What is verified before training?

Check

Required

CadQuery executes

✓

AST safety rules pass

✓

Exactly one valid solid

✓

Correct overall envelope

✓

Watertight STL

✓

Requested hole diameter where applicable

✓

Solid / empty feature probes match

✓

5,860 / 5,860 direct training targets passed verification.

Feature Composition

Six special generators teach the model to combine reusable CAD operations instead of learning only fixed named objects.

Generator

Example feature combinations

composed_plate

holes · bolt pattern · pocket · chamfer

composed_block

bore · slot · cut-out · mounting holes

composed_disc

center bore · polar holes · boss

composed_l_bracket

base slots · upright holes · chamfer

composed_ring

bore · radial holes · split / cut

composed_tray

walls · compartments · mounting features

Each composition uses 2–4 compatible features.

Fine-Tuning vs RAG

flowchart LR
    A["5,860 Direct Examples"] --> D["QLoRA Adapter"]
    B["963 Repair Examples"] --> D
    C["Feature Composition"] --> D

    E["16 Engineering Recipes"] --> H["RAG Retriever"]
    F["8 CadQuery API Notes"] --> H
    G["Current User Request"] --> H

    D --> I["Fine-Tuned Qwen"]
    H --> J["Generation Prompt"]
    G --> J
    I --> J
    J --> K["Generated CadQuery"]

    style A fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style B fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style C fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style D fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style E fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style F fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style G fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style H fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style I fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style J fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style K fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A

Fine-tuning

RAG

Changes the QLoRA adapter weights

Does not change model weights

Uses thousands of verified examples

Uses a compact knowledge base

Teaches text → CadQuery and repair behaviour

Gives context for the current request

Happens before deployment

Runs on every user request

5,860 direct + 963 repair examples

16 recipes + 8 API notes

RAG provides at most 1 engineering recipe + 2 API notes per request. It never returns the finished CAD program.

Evaluation

The final frozen model is evaluated on familiar and genuinely unseen cases.

Evaluation set

Purpose

Overall-size pass

Size + requested holes

In-domain regression

familiar learned operations

20/20 · 100%

20/20 · 100%

Second in-domain regression

additional familiar cases

12/12 · 100%

12/12 · 100%

Sealed user test

30 new requests not used for tuning

13/30 · 43.3%

11/30 · 36.7%

Held-out part types

28 cases from 7 excluded types

10/28 · 35.7%

7/28 · 25.0%

Independent reserve

separate 20-case set

5/20 · 25.0%

4/20 · 20.0%

Sealed-test performance by difficulty

Difficulty

Cases

Passed

Pass rate

Tier 1 · 1–2 features

10

6

60.0%

Tier 2 · 3–4 features

12

4

33.3%

Tier 3 · angled / revolved / curved / patterned

8

3

37.5%

Main sealed-test failure modes

Failure mode

Cases

Code error

9

Wrong size

5

Invalid geometry

3

The results show strong performance on learned CAD operations and a clear generalization gap on unfamiliar topology. That gap is reported directly rather than hidden behind only familiar examples.

Validation Pipeline

flowchart LR
    A["Generated CadQuery"] --> B{"AST Safe?"}
    B -->|No| X["Reject"]
    B -->|Yes| C{"Executes?"}
    C -->|No| X
    C -->|Yes| D{"One Valid Solid?"}
    D -->|No| X
    D -->|Yes| E{"Watertight?"}
    E -->|No| X
    E -->|Yes| F{"Size Correct?"}
    F -->|No| X
    F -->|Yes| G{"Supported Holes Correct?"}
    G -->|No| X
    G -->|Yes| H["Export"]

    style A fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style B fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style C fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style D fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style E fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style F fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style G fill:#FF6B00,stroke:#FF6B00,color:#0B1F3A
    style H fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff
    style X fill:#0B1F3A,stroke:#0B1F3A,color:#ffffff

Automatically checked

Still needs human review

code safety

unusual slot geometry

execution

advanced sweeps / lofts

one valid solid

subtle feature orientation

watertightness

every pocket / chamfer relationship

overall dimensions

structural suitability

supported holes / bores

real-world mechanical fit

Mujassam is a capstone prototype, not an engineering-certification system.

Monitoring & Responsible AI

Area

What we record / enforce

Monitoring

request · model · retrieval scores · pass/fail · gate · error · attempts · dimension error · latency

Generated-code safety

AST filter + isolated process + timeout

Export safety

failed geometry is not exported

Weapon requests

unambiguous weapon / ammunition requests are rejected before generation

Privacy

users are asked not to enter personal data because requests may be logged

Usage warning

generated parts are not engineering-certified

Run the Project

Quickest route · Colab

Open Mujassam_demo.ipynb.

Select a T4 GPU or better.

Run the cells in order.

Upload Mujassam_QWEN7B_V5_project.zip.

Upload mujassam_v5_A_7B_r16_adapter.zip.

Wait for the model + adapter to load.

Launch the application.

Example:

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

pip install -r requirements.txt

A CUDA-capable GPU is recommended for local 7B inference.

Repository Structure

mujassam_mvp_project/
├── README.md
├── requirements.txt
├── app.py
├── Mujassam_demo.ipynb
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
├── data/
├── scripts/
├── tests/
├── results/
└── docs/

Data Sources & Licences

Resource

Role

Licence / note

Qwen/Qwen2.5-Coder-7B-Instruct

base code model

Apache-2.0

Project-generated procedural CAD data

fine-tuning

generated and verified in this project

all-MiniLM-L6-v2

RAG embeddings

Apache-2.0

CadQuery

CAD execution

Apache-2.0

Chroma

vector retrieval

Apache-2.0

Transformers · PEFT · bitsandbytes

model loading / QLoRA

upstream licences

No external CAD dataset is used to train the final adapter.

Lessons & Next Steps

What worked

Main limitation

Next step

verified procedural training data

unfamiliar topology generalizes poorly

broaden verified topology coverage

code-focused QLoRA

feature semantics are not fully checked

stronger feature validators

compact engineering RAG

complex geometry can repeat the same bad program

more diverse repair strategy

execution-based validation

current user input is English-first

Arabic input support

physical-fit testing

deployment needs persistent GPU compute

production backend deployment

Team

<table>
<tr>
<td align="center" width="33%">
<h2>👤</h2>
<b>Fahad Alshehri</b>
</td>
<td align="center" width="33%">
<h2>👤</h2>
<b>Ghaida Alsalamah</b>
</td>
<td align="center" width="33%">
<h2>👤</h2>
<b>Alreem Rashed Aldossary</b>
</td>
</tr>
</table>

Live Demo

Open Mujassam →

Demo Video

Watch the project demo →

Repository

GitHub repository →

<details>
<summary><b>AI-assisted development disclosure</b></summary>

AI tools were used during development for implementation support, debugging, code review, generator review, documentation, and interface prototyping.

The team directed the work, ran the training and evaluations, and reviewed the outputs. Training targets were executed and programmatically verified before inclusion in the fine-tuning set.

</details>

<div align="center">

Mujassam · مجسّم

Describe it · Generate it · Check it · Print it

</div>
