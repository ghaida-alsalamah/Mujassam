<div align="center">

Mujassam · مجسّم

Natural language → parametric CAD → checked geometry → printable files

<p>
  <a href="LIVE_DEMO_URL"><img src="https://img.shields.io/badge/OPEN_LIVE_DEMO-FF6B00?style=for-the-badge&logo=rocket&logoColor=white" alt="Live Demo"></a>
  <a href="https://claude.ai/artifact/PiL9DScHyTKGWyyNrriZXN"><img src="https://img.shields.io/badge/VIEW_INTERFACE-1F2329?style=for-the-badge&logo=anthropic&logoColor=white" alt="Interface"></a>
</p>

<p>
  <img src="https://img.shields.io/badge/Model-Qwen2.5--Coder--7B--Instruct-FF6B00?style=flat-square" alt="Model">
  <img src="https://img.shields.io/badge/Adaptation-QLoRA_r16-343A40?style=flat-square" alt="QLoRA">
  <img src="https://img.shields.io/badge/RAG-MiniLM_%2B_Chroma-343A40?style=flat-square" alt="RAG">
  <img src="https://img.shields.io/badge/CAD-CadQuery-343A40?style=flat-square" alt="CadQuery">
  <img src="https://img.shields.io/badge/Export-STEP_%7C_STL_%7C_GLB-343A40?style=flat-square" alt="Exports">
</p>

Tuwaiq Academy · Generative AI Application Engineering Bootcamp · October 2026

</div>

Mujassam is a generative-AI CAD assistant for students, robotics teams, fab labs, and small workshops.
A user describes a mechanical part in plain language and gives its dimensions. Mujassam retrieves compact engineering guidance, generates CadQuery code with a fine-tuned 7B model, executes the code, measures the resulting solid, validates it, and exports editable and printable files only when the current checks pass.

<!--
Add screenshots from the final Mujassam web interface here.
Recommended files:
docs/assets/interface-home.png
docs/assets/interface-result.png
docs/assets/printed-fit-demo.jpg

Example:
<p align="center">
  <img src="docs/assets/interface-home.png" width="48%">
  <img src="docs/assets/interface-result.png" width="48%">
</p>
-->

The problem

Creating a small custom part usually means opening CAD software, knowing how to model the geometry, and spending time turning dimensions into a printable design.

That is a real obstacle for people who own or have access to a 3D printer but do not use CAD regularly. A robotics student may only need a motor mount, sensor plate, spacer, bearing holder, or replacement bracket—but still has to model it manually.

General-purpose chatbots can generate CAD-like code, but two problems remain:

the generated program may not execute;

a part can look correct in a preview while still having the wrong dimensions or incomplete geometry.

Mujassam was built around a simple idea:

A generated part should not be accepted just because it looks plausible. It should run, measure correctly, and pass geometry checks before it is exported.

What the application does

<table>
<tr>
<td width="33%" valign="top">

01 · Describe

The user writes the part in normal language and states the overall dimensions in millimetres.

</td>
<td width="33%" valign="top">

02 · Generate & check

The model writes CadQuery. Mujassam executes it, checks the solid and sends failures back for another attempt.

</td>
<td width="33%" valign="top">

03 · Use

A passing part can be previewed in 3D and downloaded as STEP, STL, or GLB.

</td>
</tr>
</table>

Main features

natural-language mechanical-part requests;

real millimetre dimensions;

RAG over engineering construction guidance and CadQuery API rules;

fine-tuned code generation with QLoRA;

isolated CadQuery execution;

one-solid and watertightness checks;

overall-size validation;

requested hole / bore checks where supported;

automatic retry with executor or validator feedback;

interactive 3D preview;

STEP export for CAD editing;

STL export for 3D printing;

GLB export for browser preview;

request logging, monitoring and safety checks.

Architecture

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#FF6B00",
  "primaryTextColor":"#111111",
  "primaryBorderColor":"#FF6B00",
  "lineColor":"#8A8F98",
  "secondaryColor":"#202328",
  "tertiaryColor":"#F4F4F4",
  "fontFamily":"Inter, Arial, sans-serif"
}}}%%
flowchart LR
    A["User request<br/>part + overall dimensions"] --> B["Specification<br/>envelope + tolerance"]
    B --> C["RAG<br/>engineering recipe + API notes"]
    C --> D["Qwen2.5-Coder-7B<br/>+ QLoRA adapter"]
    D --> E["Generated CadQuery"]
    E --> F["AST safety filter"]
    F --> G["Isolated CadQuery execution"]
    G --> H{"Geometry validation"}
    H -->|Pass| I["STEP · STL · GLB"]
    H -->|Reject| J["Execution / measurement feedback"]
    J --> D
    G -.-> K["Monitoring + logs"]
    H -.-> K

Where the generative AI is

The generative component is Qwen2.5-Coder-7B-Instruct with our QLoRA adapter.

The model writes the CadQuery program for every request. The application does not use a deterministic CAD compiler to secretly construct the final shape.

Deterministic code is used around the model for safety, execution, measurement, validation, export and monitoring.

Model and adaptation

Component

Choice

Base model

Qwen/Qwen2.5-Coder-7B-Instruct

Adaptation

QLoRA

Quantization

4-bit NF4 + double quantization

LoRA rank

16

LoRA alpha

32

LoRA dropout

0.05

Trainable parameters

~40.4M (~0.53%)

Training epochs

2

Max context

2,048 tokens

Loss

assistant response only

CAD engine

CadQuery

Embeddings

sentence-transformers/all-MiniLM-L6-v2

Vector store

Chroma

We chose a code-focused 7B model because the main task is not general conversation: it is producing executable, structured Python/CadQuery while following dimensional constraints.

QLoRA lets us adapt the model to this task without full-model fine-tuning.

Training data

The final adapter is trained on project-generated, procedurally constructed CAD examples rather than an external CAD dataset.

Each part generator creates:

a natural-language request;

randomized but valid dimensions and optional features;

the exact target CadQuery program;

metadata describing the expected geometry.

The target program is executed and verified before that example is allowed into training.

Dataset design

85 designed part types
├── 76 part types used for training
├──  2 part types reserved for validation
└──  7 part types completely held out for final testing

Training contains:

5,860 verified direct-generation examples

963 repair examples

6,823 total chat-format training records

A “conversation” is simply one instruction-tuning record in Qwen chat format, for example:

system     → CadQuery generation rules
user       → part request + retrieved RAG context
assistant  → verified CadQuery program

Repair records also include a failed program and real executor / validator feedback before the corrected answer.

Feature-composition training

To avoid teaching only named part templates, the dataset includes six composition generators:

composed_plate · composed_block · composed_disc · composed_l_bracket · composed_ring · composed_tray

These combine a base body with 2–4 compatible features, such as:

holes and bores;

bolt patterns;

slots;

pockets;

bosses;

chamfers;

cut-outs.

This gives the model repeated practice combining reusable CAD operations rather than seeing only one fixed construction for each object name.

Verification before training

Every accepted direct training target is checked for:

executable CadQuery;

the project's AST safety rules;

exactly one valid solid;

correct outer envelope;

watertight STL;

requested hole diameters where applicable;

feature probes for expected solid / empty regions;

consistency between dimensions in the request and the generated target.

5,860 / 5,860 direct training examples passed the verification pipeline.

RAG

RAG and fine-tuning have different jobs in Mujassam.

Fine-tuning teaches the model how to do the task

The thousands of verified text → CadQuery and repair records update the QLoRA adapter weights.

RAG supplies compact engineering context for the current request

The runtime knowledge base contains:

16 engineering construction recipes

8 CadQuery API notes

For a request, the retriever provides at most:

1 engineering recipe
+ 2 CadQuery API notes

RAG does not retrieve a finished CAD program.

The retrieved context is included in the prompt sent to the already fine-tuned model.

%%{init: {"theme":"base","themeVariables":{
  "primaryColor":"#FF6B00",
  "primaryTextColor":"#111111",
  "primaryBorderColor":"#FF6B00",
  "lineColor":"#8A8F98",
  "secondaryColor":"#202328",
  "tertiaryColor":"#F4F4F4"
}}}%%
flowchart LR
    U["Current user request"] --> R["Retriever"]
    KB["16 engineering recipes<br/>8 CadQuery API notes"] --> R
    R --> P["Request + retrieved context"]
    P --> M["Fine-tuned Qwen2.5-Coder-7B"]
    M --> C["CadQuery code"]

The user request remains the source of truth. The retrieved recipe is guidance, not a command to copy a fixed shape.

Validation and repair

After generation, Mujassam does not immediately expose the file.

The generated program goes through:

Generated code
   ↓
AST safety check
   ↓
isolated CadQuery execution
   ↓
valid solid?
   ↓
exactly one solid?
   ↓
watertight?
   ↓
overall dimensions within tolerance?
   ↓
requested holes / bores present where supported?
   ↓
PASS → export
FAIL → feedback returned to the model

Current validation scope

The pipeline is strong at checking:

whether the program runs;

one connected valid solid;

watertightness;

overall dimensions;

common requested holes / bores.

It does not yet guarantee every semantic detail of every possible CAD request. Slots, feature orientation, uncommon pockets, advanced sweeps and other complex relationships can still require visual or physical inspection.

That limitation is shown in the interface instead of being hidden.

Evaluation

We use separate sets for familiar-domain checks and genuinely unseen requests.

Final-model results

Evaluation set

Cases

Size pass

Size + requested holes

Sealed user requests

30

13/30 · 43.3%

11/30 · 36.7%

Completely held-out part types

28

10/28 · 35.7%

7/28 · 25.0%

Independent reserve

20

5/20 · 25.0%

4/20 · 20.0%

In-domain regression set

20

20/20 · 100%

20/20 · 100%

Second in-domain regression set

12

12/12 · 100%

12/12 · 100%

All numbers above are greedy first-attempt results from the frozen final model.

What the results mean

The model is very reliable on simple-to-moderate constructions represented by its learned CAD operations.

Performance drops when the request introduces geometry that is structurally unfamiliar or requires more advanced composition. On the sealed test, the main failure modes were:

generated code that did not execute;

incorrect overall size;

invalid geometry.

This generalization gap is the main technical limitation we would address next.

Physical fit testing

For the demo, we also test generated parts against real objects where possible—not only against screenshots.

Examples include:

bearing housings designed around a real bearing diameter;

mounting plates for electronics;

mechanical flanges and hubs;

Arduino mounting patterns.

The point is to show that the output is intended to become a real measured object, not only a 3D render.

Example workflow

Request

Create a rectangular 608 bearing support block with exact overall dimensions
62 x 42 x 20 mm. Cut a 22.2 mm bearing pocket 7.2 mm deep,
a concentric 12 mm through-bore, and four counterbored mounting holes.

Mujassam

request
→ retrieve relevant engineering guidance
→ generate CadQuery
→ execute
→ measure
→ validate
→ export

Output

interactive 3D preview;

.step for Onshape / CAD editing;

.stl for slicing and 3D printing;

.glb for browser viewing.

Run the project

Option 1 · Live application

Live demo: LIVE_DEMO_URL

Interface preview: https://claude.ai/artifact/PiL9DScHyTKGWyyNrriZXN

Option 2 · Colab demo

The easiest reproducible path is Mujassam_demo.ipynb.

Open the notebook in Google Colab.

Select a T4 GPU or better.

Run the cells in order.

Upload the project ZIP when requested.

Upload the trained adapter ZIP when requested.

Wait for the base model and adapter to load.

The final cell launches the application.

State the overall size explicitly in the request, for example:

Flanged bearing mount, overall 48 x 48 x 18 mm,
24 mm central bore, four 4 mm mounting holes
on a 36 mm square pattern.

The trained adapter is distributed separately from the source repository because of its size.

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

A CUDA-capable GPU is recommended for running the 7B model locally.

Repository structure

mujassam_mvp_project/
├── README.md
├── requirements.txt
├── app.py
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
│   ├── v5/
│   └── test_*.jsonl
│
├── scripts/
├── tests/
├── results/
├── docs/
│
└── Mujassam_demo.ipynb

Main modules

Module

Responsibility

app.py

interactive demo application

loop.py

generation → validation → retry orchestration

engineering_rag.py

engineering recipes and CadQuery notes

rag.py

embedding and vector retrieval

executor.py

isolated CadQuery execution

safety.py

generated-code safety filter

validate.py

geometry and dimension validation

features.py

requested hole / bore checks

monitor.py

run logging and alerts

Monitoring and responsible AI

Mujassam logs build information needed to understand system failures:

request;

model identifier;

retrieval scores;

execution status;

validation stage;

error type;

attempt count;

dimension error;

latency;

output paths.

The application also includes safeguards:

unsafe weapon / ammunition-part requests are rejected before generation;

generated Python is checked by an AST safety filter;

CadQuery runs in an isolated subprocess with a timeout;

only accepted outputs are exported;

the UI states that generated parts are not engineering-certified;

users are asked not to enter personal information because requests may be logged.

Data sources and licences

Resource

Use in Mujassam

Licence / note

Qwen/Qwen2.5-Coder-7B-Instruct

base language/code model

Apache-2.0

Project-generated procedural CAD dataset

fine-tuning

generated and verified within this project

sentence-transformers/all-MiniLM-L6-v2

RAG embeddings

see upstream model card

CadQuery

parametric CAD execution

see upstream project licence

Chroma

vector retrieval

see upstream project licence

Hugging Face Transformers / PEFT / bitsandbytes

model loading, QLoRA and 4-bit inference

see upstream licences

No external CAD dataset is used to train the final adapter.

Known limitations

Mujassam is a capstone prototype, not an engineering certification system.

Current limitations:

best performance is on simple-to-moderate mechanical geometry;

unseen topology remains harder than familiar CAD constructions;

complex lofts, sweeps, angled features and unusual feature interactions are less reliable;

prompts work best when the overall dimensions are stated directly;

feature validation is strongest for dimensions, solids, holes and bores;

a passing part should still be inspected before printing or fitting;

generated parts should not be used for safety-critical or load-critical applications without proper engineering review.

Next steps

With more development time, we would focus on:

stronger semantic validation for slots, pockets, bosses, chamfers and feature orientation;

broader verified supervision for unfamiliar topology;

persistent GPU deployment behind the final web interface;

stronger Arabic input support;

more real-world fit tests with electronics, bearings, motors and standard hardware;

better retry diversity when the first generation fails.

Team

Team member

Primary responsibility

Alreem Rashed Aldossary

Product direction, scope, user requirements, presentation and delivery coordination

Fahad Alshehri

Data generation, model training, RAG, experiment tracking and technical pipeline

Ghaida Alsalamah

Model evaluation, geometry validation, application testing, interface integration and demo preparation

AI-assisted development

AI assistants were used during the project for brainstorming, implementation support, debugging, code review, generator review, documentation and interface prototyping.

Generated training targets were not accepted because an AI wrote them. They were executed and programmatically verified before entering the training set, and the reported evaluation results come from saved project runs.

Project links





Live application

LIVE_DEMO_URL

Interface

https://claude.ai/artifact/PiL9DScHyTKGWyyNrriZXN

Demo video

DEMO_VIDEO_URL

Repository

REPOSITORY_URL

<div align="center">

Mujassam · مجسّم

Describe it · Generate it · Check it · Print it

</div>
