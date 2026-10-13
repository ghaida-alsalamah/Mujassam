<div align="center">

<h1><strong>Mujassam · مجسّم</strong></h1>

<h3>Natural Language → Parametric CAD → Verified Geometry → Printable Files</h3>

<p>
  <a href="LIVE_DEMO_URL">
    <img src="https://img.shields.io/badge/LIVE_DEMO-OPEN-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Live Demo">
  </a>
  &nbsp;
  <a href="DEMO_VIDEO_URL">
    <img src="https://img.shields.io/badge/DEMO_VIDEO-WATCH-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Demo Video">
  </a>
</p>

<p>
  <img src="https://img.shields.io/badge/MODEL-Qwen2.5--Coder--7B-6B7280?style=flat-square&labelColor=0B1F3A" alt="Model">
  <img src="https://img.shields.io/badge/ADAPTATION-QLoRA_r16-6B7280?style=flat-square&labelColor=0B1F3A" alt="Adaptation">
  <img src="https://img.shields.io/badge/RAG-MiniLM_%2B_Chroma-6B7280?style=flat-square&labelColor=0B1F3A" alt="RAG">
  <img src="https://img.shields.io/badge/CAD-CadQuery-6B7280?style=flat-square&labelColor=0B1F3A" alt="CAD">
  <img src="https://img.shields.io/badge/EXPORT-STEP_%7C_STL_%7C_GLB-6B7280?style=flat-square&labelColor=0B1F3A" alt="Export">
</p>

Ghaida Alsalamah · Alreem Rashed Aldossary · Fahad Alshehri

Tuwaiq Academy · Generative AI Application Engineering Bootcamp · October 2026

</div>

<p align="center">
  <img
    src="./docs/assets/mujassam-hero.jpg"
    width="100%"
    alt="Mujassam generative CAD project"
  >
</p>

<h1><strong>THE PROBLEM</strong></h1>

A custom mechanical part may be simple in shape, but creating it still requires CAD knowledge, precise modelling, and time.

General-purpose language models can generate CAD-like code, but a plausible preview does not guarantee a usable part.

<p align="center">
  <img src="https://img.shields.io/badge/CODE-May_not_execute-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Code may fail">
  <img src="https://img.shields.io/badge/SIZE-May_not_fit-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Wrong size">
  <img src="https://img.shields.io/badge/GEOMETRY-May_be_invalid-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Invalid geometry">
  <img src="https://img.shields.io/badge/FEATURES-May_be_missing-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Missing features">
</p>

Mujassam was built so generated geometry is executed, measured, and checked before it is exported.

<h1><strong>THE SOLUTION</strong></h1>

Mujassam is a generative CAD tool for students, robotics teams, fab labs, and small workshops.

The user describes a mechanical part in plain English and provides its overall dimensions in millimetres. Mujassam retrieves relevant engineering knowledge, generates a parametric CadQuery program, executes the generated code, measures the resulting geometry, validates it, and exports the part only when the current checks pass.

<p align="center">
  <img src="https://img.shields.io/badge/01-DESCRIBE-0B1F3A?style=for-the-badge" alt="Describe">
  &nbsp;→&nbsp;
  <img src="https://img.shields.io/badge/02-GENERATE-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Generate">
  &nbsp;→&nbsp;
  <img src="https://img.shields.io/badge/03-VERIFY-0B1F3A?style=for-the-badge" alt="Verify">
  &nbsp;→&nbsp;
  <img src="https://img.shields.io/badge/04-EXPORT-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Export">
</p>

<p align="center">
  <sub>
    Description + dimensions
    &nbsp;&nbsp;&nbsp;&nbsp;
    CadQuery generation
    &nbsp;&nbsp;&nbsp;&nbsp;
    Execute + measure + validate
    &nbsp;&nbsp;&nbsp;&nbsp;
    STEP · STL · GLB
  </sub>
</p>

<h1><strong>SYSTEM ARCHITECTURE</strong></h1>

<p align="center">
  <img
    src="https://kroki.io/graphviz/png/eNqlVM2O2jAQvu9TWFTqpYACLT9SlUrJClAlqgKh7QH2YOJJ4q6xI8csu6167QP0ZXrvo_RJOg4hZCnSqs0FM5OZ7xvPfOMrxmNN04RMyNcrQg7_V5s4VEJpt2E0lVlKNUjTaBI0bhnX7nTRJCllbsNpd3vol4pBBqm1X_WKuMLuWztLBZeQuUqbRN28Rh6bQVZZQlNwN-oeQ8yDALeh1U4yYM2ICwEMUyMljaRb_ORpTkXhyfgXcDvdJtlSHXNpiTrDJv50MSAFuefMJG6n3cvJgMVIVtzo2Xjc9x2nGoc4VGu1z1Gd9jBP2nGyEnQDwm18gg358NZSY1VHGMfvjF96RT2Fc59wA-g6i8nxlA6TEnHGU7AtWcv36IYM22yUrsmQpRCWDAEaPOIhNVzJtVwAZVCXQNO4xF94E4tqNIe72sBbVIMooed7kN12r3WNXt0a-Gv5gsynauGdsZSDrLCcqM-iDh2iEZQ0XrAkATrMw1pOaF5bnTvAfaX715TNd6AReYTuXf3Z3tFTfyagtth4BP9IBWcXlPPvnVE7c5LOcjQjv36SYDm1x2Tq1yxeqJNu3inJsWAu47V8TqYqzs7AR73RYOQ_VXvfH3SHee2HVW29yResXDS07TpUbVRvuSVo5po7qrpqH8RoAaxa8MwniyfO4DgKS1fpGJl5QfDEY-VcvNFNBfHxFhANnyE05Pf3HyQCYBsa3v7dgMegpfPwmjKaJfiWYo60LwyXxo2oyOCkV2TNh3MefwZ3EaCo-j_zv139AQpTAxw"
    width="100%"
    alt="Mujassam system architecture"
  >
</p>

<h2><strong>Where is the Generative AI?</strong></h2>

Qwen2.5-Coder-7B + QLoRA generates the CadQuery program for every request.

The final geometry is not produced by a hidden deterministic CAD compiler.

The surrounding pipeline handles:

retrieval → safety → execution → measurement → validation → repair → export

<h1><strong>REQUEST WORKFLOW</strong></h1>

<p align="center">
  <img
    src="https://kroki.io/graphviz/png/eNqllM2O0zAQx-99ilGQuGxSJS1pkVAitbCtkHoouysuDQcnniQWrh3Z7seCuPIAvAx3HoUnYdJmw6qcUC9JZjIzv_l7bA-4qAxraljC1wHA-XuTV4WW2iSeM0zZhhlUzvOBjM9cmGR150PDeOKFw1FMfqU5Wmxaexx3cZ0dt7ZtpFBoE21crT-9IU6bARtbswaTXB8pxD1KTDyjd4oj90shJXJKLbVyim3p18wIJjuPFV8wiSIftsxUQrWgKPbpEVFAg-oguKuTaBifYMgrgnWKXiwWk3kYPo8b-cCM0YdT1XA4PWcx2EiWo0y8KFPv0BZG5EiyjcvUDeg9GiYltDltU9TvEyCcR4vxrOu0cx5q4dq4i5gTKO9Bo0zdIeOwRWZ3huUSM1p9LEQpCuaEVleSip40bknOCNwjGAI02Iqard_TZBzaKzm857zK1BIVLZUjwFvGP-zQPF5U7wfyrPpf5EXUeaB9_ThTt0csdg5BqEwJqyWhODRGF2iv1VH2nEmmPjIpOBUHYghOg6HJww3UWv6zXv-vqOpJ00ytDe4FHuAl4LHR7X67f7hdw6-fcP-wal_L1fxKZSxI8yAtgpQHKQZpGaTVSTA5-k6gZELC7-8_aIc0TBjv6ZRyZms6o33hyXw6en0pt3cWWlm6RoRyScmkReJ_G_wB80Bn2A"
    width="100%"
    alt="Mujassam request workflow"
  >
</p>

If a build fails execution or validation, the failure information is returned to the model for another generation attempt.

Only an accepted result reaches export.

<h1><strong>MODEL & TECHNOLOGY</strong></h1>

Component

Final Choice

Base Model

Qwen/Qwen2.5-Coder-7B-Instruct

Adaptation

QLoRA

LoRA Configuration

rank 16 · alpha 32 · dropout 0.05

Quantization

4-bit NF4 + double quantization

Context Length

2,048 tokens

Trainable Parameters

~40.4M · ~0.53%

Embeddings

sentence-transformers/all-MiniLM-L6-v2

Vector Database

Chroma

CAD Engine

CadQuery

Exports

STEP · STL · GLB

<h1><strong>TRAINING DATA</strong></h1>

The final adapter is trained on project-generated procedural CAD data.

Parameterized generators create varied dimensions, optional features, natural-language requests, and an exact CadQuery target. The target is executed and verified before it can enter training.

<h2><strong>Dataset by Examples</strong></h2>

<div align="center">

<img src="https://img.shields.io/badge/TOTAL_SUPERVISED_RECORDS-6%2C823-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="6823 total records">

<br><br>

<img src="https://img.shields.io/badge/DIRECT_GENERATION-5%2C860-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="5860 direct examples">
&nbsp;
<img src="https://img.shields.io/badge/REPAIR_EXAMPLES-963-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="963 repair examples">

<br><br>

<img src="https://img.shields.io/badge/OPTIMIZATION_TRAIN-6%2C687-0B1F3A?style=for-the-badge" alt="6687 training records">
&nbsp;
<img src="https://img.shields.io/badge/LOSS_VALIDATION-136-0B1F3A?style=for-the-badge" alt="136 validation records">

</div>

<h2><strong>Dataset by Part Types</strong></h2>

<p align="center">
  <img src="https://img.shields.io/badge/DESIGNED_TYPES-85-FF6B00?style=flat-square&labelColor=0B1F3A" alt="85 designed types">
  <img src="https://img.shields.io/badge/TRAINING_TYPES-76-6B7280?style=flat-square&labelColor=0B1F3A" alt="76 training types">
  <img src="https://img.shields.io/badge/VALIDATION_ONLY_TYPES-2-6B7280?style=flat-square&labelColor=0B1F3A" alt="2 validation types">
  <img src="https://img.shields.io/badge/HELD_OUT_TYPES-7-6B7280?style=flat-square&labelColor=0B1F3A" alt="7 held out types">
</p>

<h2><strong>Separate Validation & Test Sets</strong></h2>

42 generated validation cases

30 in-distribution

12 from the 2 validation-only part types

28 held-out part-type cases

7 unseen part types

4 requests per type

30 sealed user requests

20 independent reserve requests

20 in-domain regression requests

12 second in-domain regression requests

<h2><strong>Verification Before Training</strong></h2>

<p align="center">
  <img src="https://img.shields.io/badge/EXECUTION-PASS-0B1F3A?style=flat-square" alt="Execution">
  <img src="https://img.shields.io/badge/ONE_SOLID-PASS-0B1F3A?style=flat-square" alt="One solid">
  <img src="https://img.shields.io/badge/ENVELOPE-PASS-0B1F3A?style=flat-square" alt="Envelope">
  <img src="https://img.shields.io/badge/WATERTIGHT-PASS-0B1F3A?style=flat-square" alt="Watertight">
  <img src="https://img.shields.io/badge/FEATURE_PROBES-PASS-0B1F3A?style=flat-square" alt="Feature probes">
</p>

5,860 / 5,860 direct-generation targets passed the verification pipeline.

<h1><strong>FEATURE COMPOSITION</strong></h1>

The dataset does not only repeat complete named parts.

Six composition generators teach the model to combine 2–4 compatible CAD operations:

composed_plate · composed_block · composed_disc · composed_l_bracket · composed_ring · composed_tray

Examples:

base plate
+ mounting holes
+ pocket
+ chamfer

disc
+ centre bore
+ bolt circle
+ raised boss

L-bracket
+ adjustment slots
+ upright holes

This gives the model repeated practice with reusable geometry operations instead of only fixed object templates.

<h1><strong>FINE-TUNING vs RAG</strong></h1>

<p align="center">
  <img
    src="https://kroki.io/graphviz/png/eNqtVE1v2zAMvedXENlxdhCnc9LBcIAkaIoBHbD22hSDYjG2MFlSabtpN_R37b5fNvqjThsM2KG5yCZN8ZnvPWkgVUrCZXAJvwYA7fvtNk2sthQPSxKmcILQlEMPOPghFcVXNx44IePheDQJOW-sxAJdHZ-FXV0XTzksnFYGi9hSmdm7iGHqDXBbZMJhvLWPXFI-aYyHZCsjUXo7pTVK3rqzpjQi508LUkJ3mUL9xDgIPMgFpcrUOEHo8RJwgUOzV7LM4mD0qQFDmTJYN9CH9Xq6HI9f1008EER233Qdj2Zhs6uoti0Zia6KEuk7U6FMQxKAFlvU8XDNY_llZZRJ4c9v0CjIoIQt7iwhSHTaPuU1ddHxILC0WnbpdppJBC-_OF4G67MFf309StQAS7jtsEPvfDqGByS1Uyg3hnXBpAR8FLnTWNRMMYlHLVv6uuQ-UyVy6qjmrkWiHunz9AwInVC0MSdrn_Tt1yjKitBPbO5soUplzQlxdI9zfWVvFiCkcKzmUd_eFK_6HsCOqrrO0p_rCKhZk3rl7PO_jEMifWubm8VlbRfCkhQ-sGHYLoAiyTh1X2FxQr_QQcZgCmj4tCBbxqQbw3ZR7gQMC6d6jHNYCXldIT1tzOLbFz7n5SmsyET1EF-VUVdf4SOsMrK5OIGQxBrWEFE9SvfaaXnfw64qqi9BqAqkmrtWp7fgF-HF7GL5P_DpcjY578Bd3_8SDZJoze94MPf-5vnhiHX3VH1PXO_RTEahv-IrmPzZ8p3q2OMJaowXE7xbnPuDHPXTn7su2zy1P8-bQbvY-XMbDZ4HfwFJTRy9"
    width="100%"
    alt="Fine tuning versus RAG"
  >
</p>

Fine-Tuning

QLoRA learns from:

5,860 verified generation examples

963 repair examples

feature-composition examples

Fine-tuning changes the adapter weights and teaches the model how to generate and repair CadQuery.

RAG

The runtime knowledge base contains:

16 engineering construction recipes

8 CadQuery API notes

MiniLM embeddings

Chroma retrieval

For each request, Mujassam retrieves at most:

1 engineering recipe + 2 API notes

RAG supplies context to the fine-tuned model. It does not retrieve the finished CAD program.

<h1><strong>REPRESENTATIVE OUTPUTS</strong></h1>

These examples are taken directly from actual Mujassam-generated CAD outputs.

<p align="center">
  <img
    src="./docs/assets/mujassam-outputs.png"
    width="100%"
    alt="Representative Mujassam CAD outputs"
  >
</p>

<p align="center">
  <img src="https://img.shields.io/badge/FLANGED_BEARING_MOUNT-PASS-FF6B00?style=flat-square&labelColor=0B1F3A" alt="Flanged bearing mount">
  <img src="https://img.shields.io/badge/U--SHAPED_SENSOR_BRACKET-PASS-FF6B00?style=flat-square&labelColor=0B1F3A" alt="U-shaped sensor bracket">
  <img src="https://img.shields.io/badge/SPLIT_SHAFT_COLLAR-PASS-FF6B00?style=flat-square&labelColor=0B1F3A" alt="Split shaft collar">
</p>

The project also generated additional parts such as flanges, pulleys, fan guards, mounting plates, and curved tube geometry during testing.

<h1><strong>BEFORE vs AFTER FINE-TUNING</strong></h1>

To measure the effect of model adaptation, the untouched Qwen2.5-Coder-7B-Instruct baseline was compared against the final Mujassam QLoRA-adapted model on the exact same locked regression requests.

Both conditions used the same RAG context, system prompt, CadQuery executor, validator, feature checks, greedy decoding, and one generation attempt. The only model difference was QLoRA OFF vs QLoRA ON.

<h2><strong>Overall-Size Pass</strong></h2>

Evaluation Set

Base Qwen2.5-Coder-7B

Mujassam Fine-Tuned

In-Domain Regression

7/20 · 35.0%

20/20 · 100.0%

Second In-Domain Regression

1/12 · 8.3%

12/12 · 100.0%

<h2><strong>Size + Requested Holes</strong></h2>

Evaluation Set

Base Qwen2.5-Coder-7B

Mujassam Fine-Tuned

In-Domain Regression

2/20 · 10.0%

20/20 · 100.0%

Second In-Domain Regression

0/12 · 0.0%

12/12 · 100.0%

<p align="center">
  <img src="https://img.shields.io/badge/BASELINE_SIZE-35.0%25-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Baseline size pass 35 percent">
  <img src="https://img.shields.io/badge/FINE--TUNED_SIZE-100%25-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Fine tuned size pass 100 percent">
</p>

The paired comparison shows that QLoRA adaptation substantially improved reliable generation on the learned CAD operation distribution.

<h1><strong>EVALUATION</strong></h1>

<h2><strong>Final Frozen-Model Results</strong></h2>

Evaluation Set

Cases

Overall-Size Pass

Size + Requested Holes

In-Domain Regression

20

20/20 · 100%

20/20 · 100%

Second In-Domain Regression

12

12/12 · 100%

12/12 · 100%

Sealed User Test

30

13/30 · 43.3%

11/30 · 36.7%

Held-Out Part Types

28

10/28 · 35.7%

7/28 · 25.0%

Independent Reserve

20

5/20 · 25.0%

4/20 · 20.0%

<h2><strong>Sealed Test by Difficulty</strong></h2>

<p align="center">
  <img src="https://img.shields.io/badge/TIER_1_%C2%B7_1--2_FEATURES-60.0%25-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Tier 1">
  <img src="https://img.shields.io/badge/TIER_2_%C2%B7_3--4_FEATURES-33.3%25-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Tier 2">
  <img src="https://img.shields.io/badge/TIER_3_%C2%B7_COMPLEX_GEOMETRY-37.5%25-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Tier 3">
</p>

<h2><strong>Main Sealed-Test Failure Modes</strong></h2>

<p align="center">
  <img src="https://img.shields.io/badge/CODE_ERRORS-9-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="9 code errors">
  <img src="https://img.shields.io/badge/WRONG_SIZE-5-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="5 wrong size">
  <img src="https://img.shields.io/badge/INVALID_GEOMETRY-3-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="3 invalid geometry">
</p>

The model performs strongly on familiar CAD operations.

The main remaining challenge is generalization to unfamiliar geometry and more complex feature relationships.

<h1><strong>VALIDATION</strong></h1>

<h2><strong>Automatically Checked</strong></h2>

<p align="center">
  <img src="https://img.shields.io/badge/AST_SAFETY-CHECKED-0B1F3A?style=flat-square" alt="AST safety">
  <img src="https://img.shields.io/badge/EXECUTION-CHECKED-0B1F3A?style=flat-square" alt="Execution">
  <img src="https://img.shields.io/badge/ONE_SOLID-CHECKED-0B1F3A?style=flat-square" alt="One solid">
  <img src="https://img.shields.io/badge/WATERTIGHT-CHECKED-0B1F3A?style=flat-square" alt="Watertight">
  <img src="https://img.shields.io/badge/OVERALL_SIZE-CHECKED-0B1F3A?style=flat-square" alt="Overall size">
  <img src="https://img.shields.io/badge/HOLES_%2F_BORES-CHECKED_WHERE_SUPPORTED-0B1F3A?style=flat-square" alt="Holes">
</p>

<h2><strong>Still Requires Human Review</strong></h2>

Advanced sweeps and lofts · unusual slots · subtle feature orientation · structural suitability · final physical fit

Mujassam is a capstone prototype, not an engineering-certification system.

<h1><strong>LIVE DEMO</strong></h1>

<div align="center">

Open Mujassam →

Watch the Demo Video →

</div>

<h1><strong>TEAM</strong></h1>

<p align="center">
  <img src="https://ui-avatars.com/api/?name=Ghaida+Alsalamah&background=0B1F3A&color=FFFFFF&size=128&bold=true" width="90" alt="Ghaida Alsalamah">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://ui-avatars.com/api/?name=Alreem+Rashed+Aldossary&background=0B1F3A&color=FFFFFF&size=128&bold=true" width="90" alt="Alreem Rashed Aldossary">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://ui-avatars.com/api/?name=Fahad+Alshehri&background=0B1F3A&color=FFFFFF&size=128&bold=true" width="90" alt="Fahad Alshehri">
</p>

<p align="center">
  <strong>Ghaida Alsalamah</strong>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <strong>Alreem Aldossary</strong>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <strong>Fahad Alshehri</strong>
</p>

<details>
<summary><h2><strong>RUN THE PROJECT</strong></h2></summary>

Colab

Open Mujassam_demo.ipynb.

Select a T4 GPU or better.

Run the cells in order.

Upload the project ZIP when requested.

Upload the trained QLoRA adapter ZIP when requested.

Wait for the model and adapter to load.

Launch the application.

Example:

Flanged bearing mount, overall 48 x 48 x 18 mm,
24 mm central bore, four 4 mm mounting holes
on a 36 mm square pattern.

Local Setup

git clone https://github.com/ghaida-alsalamah/Mujassam.git
cd Mujassam

python -m venv .venv

Windows:

.venv\Scripts\activate

macOS / Linux:

source .venv/bin/activate

Install dependencies:

pip install -r requirements.txt

A CUDA-capable GPU is recommended for local 7B inference.

</details>

<details>
<summary><h2><strong>REPOSITORY STRUCTURE</strong></h2></summary>

Mujassam/
├── README.md
├── requirements.txt
├── app.py
├── Mujassam_demo.ipynb
├── mujassam/
├── data/
├── scripts/
├── tests/
├── results/
└── docs/
    └── assets/
        ├── mujassam-hero.jpg
        └── mujassam-outputs.png

</details>

<details>
<summary><h2><strong>DATA SOURCES & LICENCES</strong></h2></summary>

Resource

Role

Qwen2.5-Coder-7B-Instruct

base code model · Apache-2.0

Project-generated procedural CAD data

fine-tuning supervision

all-MiniLM-L6-v2

RAG embeddings

Chroma

vector retrieval

CadQuery

parametric CAD execution

Transformers · PEFT · bitsandbytes

model loading, QLoRA, quantized inference

No external CAD dataset is used to train the final adapter.

</details>

<details>
<summary><h2><strong>MONITORING & RESPONSIBLE USE</strong></h2></summary>

Each build records:

request · model · retrieval scores · pass/fail · rejected gate · error type · attempts · dimension error · latency

Safeguards include:

generated Python passes an AST safety filter;

CadQuery runs in an isolated subprocess with a timeout;

rejected outputs are not exported;

unambiguous weapon and ammunition-part requests are rejected before generation;

users are warned that generated parts are not engineering-certified;

users are asked not to enter personal information because requests may be logged.

</details>

<details>
<summary><h2><strong>LESSONS & NEXT STEPS</strong></h2></summary>

What Worked

Verified procedural training data · code-focused QLoRA · compact engineering RAG · execution-based validation

Main Limitation

Generalization drops when a request requires genuinely unfamiliar topology or feature relationships.

Next Steps

Stronger semantic validation · broader geometry coverage · persistent GPU deployment · Arabic input support · more real-world fit testing

</details>

<div align="center">

<h1><strong>Mujassam · مجسّم</strong></h1>

Describe It · Generate It · Check It · Print It

<br><br>

Ghaida Alsalamah · Alreem Aldossary · Fahad Alshehri

<br><br>

Repository: https://github.com/ghaida-alsalamah/Mujassam

</div>
