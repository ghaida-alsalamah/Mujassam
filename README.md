<div align="center">

Mujassam · مجسّم

From a sentence to a measured, editable, printable CAD part

<p>
  <a href="LIVE_DEMO_URL">
    <img src="https://img.shields.io/badge/LIVE_DEMO-FF6B00?style=for-the-badge&logo=rocket&logoColor=white" alt="Live Demo">
  </a>
  &nbsp;
  <a href="DEMO_VIDEO_URL">
    <img src="https://img.shields.io/badge/DEMO_VIDEO-0B1F3A?style=for-the-badge&logo=youtube&logoColor=white" alt="Demo Video">
  </a>
</p>

<p>
  <img src="https://img.shields.io/badge/Qwen2.5--Coder--7B-0B1F3A?style=flat-square" alt="Qwen2.5-Coder-7B">
  <img src="https://img.shields.io/badge/QLoRA-r16-FF6B00?style=flat-square" alt="QLoRA">
  <img src="https://img.shields.io/badge/RAG-Chroma_%2B_MiniLM-0B1F3A?style=flat-square" alt="RAG">
  <img src="https://img.shields.io/badge/CAD-CadQuery-FF6B00?style=flat-square" alt="CadQuery">
  <img src="https://img.shields.io/badge/Export-STEP_%7C_STL_%7C_GLB-0B1F3A?style=flat-square" alt="Exports">
</p>

Tuwaiq Academy · Generative AI Application Engineering Bootcamp · October 2026

</div>

At a glance

<table>
<tr>
<td width="25%" align="center"><b>INPUT</b><br><sub>Natural-language part description + overall dimensions</sub></td>
<td width="25%" align="center"><b>GENERATE</b><br><sub>Fine-tuned Qwen writes parametric CadQuery</sub></td>
<td width="25%" align="center"><b>VERIFY</b><br><sub>Execute, measure, validate, retry</sub></td>
<td width="25%" align="center"><b>EXPORT</b><br><sub>STEP · STL · GLB</sub></td>
</tr>
</table>

Mujassam is a generative CAD tool for students, robotics teams, fab labs, and small workshops that need custom mechanical parts without modelling them manually in CAD.

The model generates the CadQuery program for every request. The surrounding pipeline handles retrieval, safety, execution, measurement, validation, repair, preview, and export.

A part is not accepted just because it looks right. It has to execute, form a valid solid, and match the requested overall size before export.

<!--
PRODUCT SCREENSHOTS
Use screenshots from the final Mujassam website here after backend integration.

Recommended:
docs/assets/home.png
docs/assets/generated-part.png
docs/assets/physical-fit-demo.jpg

Example:
<p align="center">
  <img src="docs/assets/home.png" width="49%">
  <img src="docs/assets/generated-part.png" width="49%">
</p>
-->

The problem → our solution

<table>
<tr>
<td width="50%" valign="top">

The problem

A student may only need a small bracket, mount, spacer, bearing holder, or replacement part—but creating it traditionally still requires CAD knowledge.

General-purpose LLMs can write CAD-like code, but:

the code may not execute;

the scale may be wrong;

the part may contain disconnected solids;

requested features may be missing even when the preview looks plausible.

</td>
<td width="50%" valign="top">

What Mujassam changes

The request is turned into parametric CAD code, not just a mesh or image.

Before the file is returned, Mujassam:

retrieves engineering guidance;

generates CadQuery;

runs the code;

measures the geometry;

checks the solid;

retries failed outputs;

exports editable and printable formats.

</td>
</tr>
</table>

How it works

1 · System architecture

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#FF6B00",
  "primaryTextColor":"#071525",
  "primaryBorderColor":"#FF6B00",
  "secondaryColor":"#0B1F3A",
  "secondaryTextColor":"#FFFFFF",
  "secondaryBorderColor":"#163B66",
  "tertiaryColor":"#EAF0F6",
  "tertiaryTextColor":"#0B1F3A",
  "tertiaryBorderColor":"#A8B6C7",
  "lineColor":"#FF6B00",
  "fontFamily":"Inter, Arial, sans-serif"
}}}%%
flowchart LR
    UI["Web UI"] --> ORCH["Pipeline<br/>Orchestrator"]
    ORCH --> SPEC["Specification<br/>Reader"]
    ORCH --> RAG["RAG<br/>Retriever"]
    SPEC --> GEN["Qwen2.5-Coder-7B<br/>+ QLoRA"]
    RAG --> GEN
    GEN --> SAFE["AST<br/>Safety Gate"]
    SAFE --> EXEC["CadQuery<br/>Executor"]
    EXEC --> VAL["Geometry<br/>Validator"]
    VAL -->|PASS| OUT["STEP · STL · GLB"]
    VAL -->|REJECT| REPAIR["Failure Feedback"]
    REPAIR --> GEN
    EXEC -. logs .-> MON["Monitoring"]
    VAL -. metrics .-> MON

    classDef navy fill:#0B1F3A,stroke:#163B66,color:#fff;
    classDef orange fill:#FF6B00,stroke:#FF6B00,color:#071525;
    classDef light fill:#EAF0F6,stroke:#A8B6C7,color:#0B1F3A;

    class UI,ORCH,SPEC,RAG navy;
    class GEN,VAL orange;
    class SAFE,EXEC,REPAIR,OUT,MON light;

2 · One request from input to output

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#0B1F3A",
  "primaryTextColor":"#FFFFFF",
  "primaryBorderColor":"#163B66",
  "secondaryColor":"#FF6B00",
  "secondaryTextColor":"#071525",
  "lineColor":"#FF6B00",
  "fontFamily":"Inter, Arial, sans-serif"
}}}%%
flowchart TD
    A["Describe the part<br/>+ state overall size in mm"] --> B["Read measurable specification"]
    B --> C["Retrieve ≤1 engineering recipe<br/>+ ≤2 CadQuery API notes"]
    C --> D["Fine-tuned model generates CadQuery"]
    D --> E{"Safe code?"}
    E -->|No| R["Return failure feedback"]
    E -->|Yes| F["Execute CadQuery"]
    F --> G{"Valid one-solid geometry?"}
    G -->|No| R
    G -->|Yes| H{"Overall size within tolerance?"}
    H -->|No| R
    H -->|Yes| I{"Supported requested holes / bores correct?"}
    I -->|No| R
    I -->|Yes| J["Preview + STEP + STL + GLB"]
    R --> D

3 · What is learned vs. what is retrieved

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#0B1F3A",
  "primaryTextColor":"#FFFFFF",
  "primaryBorderColor":"#163B66",
  "secondaryColor":"#FF6B00",
  "secondaryTextColor":"#071525",
  "lineColor":"#FF6B00",
  "fontFamily":"Inter, Arial, sans-serif"
}}}%%
flowchart LR
    subgraph FT["QLoRA — learned before deployment"]
      A["5,860 verified<br/>direct examples"]
      B["963 repair<br/>examples"]
      C["Feature-composition<br/>examples"]
      A --> M["Fine-tuned<br/>Qwen2.5-Coder-7B"]
      B --> M
      C --> M
    end

    subgraph RT["RAG — retrieved for each request"]
      D["16 engineering<br/>recipes"]
      E["8 CadQuery<br/>API notes"]
      D --> R["MiniLM + Chroma"]
      E --> R
    end

    U["Current user request"] --> R
    U --> P["Generation prompt"]
    R --> P
    M --> P
    P --> O["Generated CadQuery"]

Fine-tuning teaches the model the text → CadQuery task.
RAG gives compact engineering context for the current request.
RAG does not return the finished CAD program.

Model & data

Model

<table>
<tr>
<td><b>Base model</b></td><td><code>Qwen/Qwen2.5-Coder-7B-Instruct</code></td>
<td><b>Adaptation</b></td><td>QLoRA</td>
</tr>
<tr>
<td><b>Quantization</b></td><td>4-bit NF4</td>
<td><b>LoRA rank</b></td><td>16</td>
</tr>
<tr>
<td><b>LoRA alpha</b></td><td>32</td>
<td><b>Dropout</b></td><td>0.05</td>
</tr>
<tr>
<td><b>Context</b></td><td>2,048 tokens</td>
<td><b>CAD engine</b></td><td>CadQuery</td>
</tr>
</table>

Training-data pipeline

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#0B1F3A",
  "primaryTextColor":"#FFFFFF",
  "primaryBorderColor":"#163B66",
  "secondaryColor":"#FF6B00",
  "secondaryTextColor":"#071525",
  "lineColor":"#FF6B00",
  "fontFamily":"Inter, Arial, sans-serif"
}}}%%
flowchart LR
    A["Parameterized<br/>part generator"] --> B["Random valid<br/>dimensions + features"]
    B --> C["Natural-language<br/>request"]
    B --> D["Target CadQuery"]
    D --> E["Execute target"]
    E --> F{"Pass verification?"}
    F -->|No| X["Reject example"]
    F -->|Yes| G["Training record"]
    C --> G
    G --> H["QLoRA fine-tuning"]

Dataset snapshot

<table>
<tr>
<td align="center"><b>85</b><br><sub>designed part types</sub></td>
<td align="center"><b>76</b><br><sub>training types</sub></td>
<td align="center"><b>2</b><br><sub>validation-only types</sub></td>
<td align="center"><b>7</b><br><sub>fully held-out types</sub></td>
</tr>
<tr>
<td align="center"><b>5,860</b><br><sub>verified direct examples</sub></td>
<td align="center"><b>963</b><br><sub>repair examples</sub></td>
<td align="center"><b>6,823</b><br><sub>chat-format training records</sub></td>
<td align="center"><b>5,860 / 5,860</b><br><sub>direct targets verified</sub></td>
</tr>
</table>

What a training record looks like

SYSTEM
CadQuery generation rules + real-mm constraints

USER
Part request + retrieved RAG context

ASSISTANT
Verified CadQuery program

Repair records additionally include a failed generation plus real executor / validator feedback before the corrected program.

Feature-composition supervision

Six generators deliberately combine 2–4 compatible CAD features instead of teaching only fixed named objects:

composed_plate · composed_block · composed_disc · composed_l_bracket · composed_ring · composed_tray

Typical combinations include:

base body + holes + pattern + chamfer
base body + pocket + boss + cut-out
base body + slot + bore + mounting holes

This gives the model repeated practice with reusable CAD operations and feature composition.

Evaluation

Test strategy

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#0B1F3A",
  "primaryTextColor":"#FFFFFF",
  "primaryBorderColor":"#163B66",
  "secondaryColor":"#FF6B00",
  "secondaryTextColor":"#071525",
  "lineColor":"#FF6B00"
}}}%%
flowchart LR
    MODEL["Frozen final model"] --> A["In-domain<br/>regression tests"]
    MODEL --> B["Sealed user<br/>requests"]
    MODEL --> C["Completely held-out<br/>part types"]
    MODEL --> D["Independent<br/>reserve set"]

Results

Evaluation set

Cases

Overall-size pass

Size + requested holes

In-domain regression

20

100%

100%

Second in-domain regression

12

100%

100%

Sealed user requests

30

43.3%

36.7%

Completely held-out part types

28

35.7%

25.0%

Independent reserve

20

25.0%

20.0%

Reading the results

Familiar CAD operations
████████████████████  strong

New combinations
█████████░░░░░░░░░░░  mixed

Completely unfamiliar topology
███████░░░░░░░░░░░░░  current limitation

The project is strongest on simple-to-moderate mechanical designs built from learned CAD operations. Performance drops on unfamiliar topology and more complex geometric relationships.

That gap is reported directly rather than hidden.

Validation

<table>
<tr>
<td width="50%" valign="top">

Checked automatically

CadQuery executes

AST safety rules pass

exactly one valid solid

watertight geometry

overall dimensions

requested holes / bores where supported

retry count and errors

latency and run status

</td>
<td width="50%" valign="top">

Still requires human inspection

uncommon slot geometry

advanced sweeps / lofts

subtle feature orientation

every chamfer / pocket relationship

real mechanical fit

structural suitability

</td>
</tr>
</table>

Mujassam is a capstone prototype, not an engineering-certification system. Generated parts should not be used in safety-critical applications without proper engineering review.

Demo

Live application

<div align="center">

Open the live Mujassam application

</div>

Demo video

<div align="center">

Watch the project demo

</div>

<!--
FINAL WEBSITE VISUALS
Replace these comments with screenshots from the deployed Mujassam website.

Suggested section:
<p align="center">
  <img src="docs/assets/home.png" width="48%" alt="Mujassam home screen">
  <img src="docs/assets/result.png" width="48%" alt="Generated CAD result">
</p>

For the strongest presentation, also add:
docs/assets/physical-fit-demo.jpg
showing a printed generated part fitted to a real object.
-->

Run it

Fastest route · Colab demo

Open Mujassam_demo.ipynb.

Select a T4 GPU or better.

Run the cells in order.

Upload the project ZIP when requested.

Upload the trained adapter ZIP when requested.

Wait for the 7B base model + adapter to load.

Launch the application from the final cell.

Example request:

Flanged bearing mount, overall 48 x 48 x 18 mm,
24 mm central bore, four 4 mm mounting holes
on a 36 mm square pattern.

Local environment

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

Repository structure

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

Data sources & licences

Resource

Role

Qwen/Qwen2.5-Coder-7B-Instruct

Base code model · Apache-2.0

Project-generated procedural CAD dataset

Fine-tuning supervision

sentence-transformers/all-MiniLM-L6-v2

RAG embeddings

Chroma

Vector retrieval

CadQuery

Parametric CAD execution

Hugging Face Transformers / PEFT / bitsandbytes

Model loading, QLoRA, quantized inference

No external CAD dataset is used to train the final adapter.

Monitoring & safeguards

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#0B1F3A",
  "primaryTextColor":"#FFFFFF",
  "primaryBorderColor":"#163B66",
  "secondaryColor":"#FF6B00",
  "secondaryTextColor":"#071525",
  "lineColor":"#FF6B00"
}}}%%
flowchart LR
    RUN["Every build"] --> LOG["JSONL log"]
    LOG --> M1["Execution status"]
    LOG --> M2["Rejected gate"]
    LOG --> M3["Dimension error"]
    LOG --> M4["Latency"]
    LOG --> M5["Attempt count"]
    M1 --> ALERT{"Repeated failure?"}
    ALERT -->|Yes| A["Automatic alert"]

Safeguards include:

weapon / ammunition-part requests are rejected before generation;

generated Python is checked by AST rules;

CadQuery runs in an isolated subprocess with a timeout;

failed outputs are not exported;

users are warned that parts are not engineering-certified;

users are asked not to submit personal data because requests may be logged.

What we learned

<table>
<tr>
<td width="33%" valign="top">

Worked well

Verified procedural training data, code-focused fine-tuning, compact RAG context, and execution-based validation.

</td>
<td width="33%" valign="top">

Still difficult

Unfamiliar topology, advanced feature composition, and fully checking every internal semantic feature.

</td>
<td width="33%" valign="top">

Next

Stronger semantic validators, broader geometry coverage, persistent GPU deployment, Arabic input, and more physical fit tests.

</td>
</tr>
</table>

Team

Replace the placeholders below with the final team names and role wording used in the individual reports.

Team member

Role / contribution

[Team Member 1]

[Role and main contribution]

[Team Member 2]

[Role and main contribution]

[Team Member 3]

[Role and main contribution]

Project links

Resource

Link

Live application

LIVE_DEMO_URL

Demo video

DEMO_VIDEO_URL

GitHub repository

REPOSITORY_URL

<details>
<summary><b>AI-assisted development disclosure</b></summary>

AI tools were used during development for brainstorming, implementation support, debugging, code review, generator review, documentation, and interface prototyping.

Training targets were not accepted solely because they were AI-assisted. The target CadQuery programs were executed and programmatically verified before being included in the training set, and the reported evaluation numbers come from saved project runs.

</details>

<div align="center">

Mujassam · مجسّم

Describe it · Generate it · Check it · Print it

</div>
