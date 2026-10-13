<div align="center">

<h1><strong>Mujassam · مجسّم</strong></h1>

<h3>Natural language → parametric CAD → verified geometry → printable files</h3>

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
  <img src="https://img.shields.io/badge/EXPORT-STEP_%7C_STL_%7C_GLB-6B7280?style=flat-square&labelColor=0B1F3A" alt="Exports">
</p>

<p>
  <img src="https://img.shields.io/badge/Python-0B1F3A?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Hugging_Face-FF6B00?style=flat-square&logo=huggingface&logoColor=white" alt="Hugging Face">
  <img src="https://img.shields.io/badge/GitHub-0B1F3A?style=flat-square&logo=github&logoColor=white" alt="GitHub">
</p>

**Tuwaiq Academy · Generative AI Application Engineering Bootcamp · October 2026**

</div>

---

<h1><strong>THE PROBLEM</strong></h1>

A custom mechanical part may be small, but creating it still requires CAD knowledge, precise modelling, and time.

General-purpose language models can generate CAD-like code, but a plausible preview does not guarantee a usable part.

<p align="center">
  <img src="https://img.shields.io/badge/CODE-May_not_execute-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Code may fail">
  <img src="https://img.shields.io/badge/SIZE-May_not_fit-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Wrong size">
  <img src="https://img.shields.io/badge/GEOMETRY-May_be_invalid-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Invalid geometry">
  <img src="https://img.shields.io/badge/FEATURES-May_be_missing-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Missing features">
</p>

> **Mujassam was built so generated geometry is executed, measured, and checked before it is exported.**

---

<h1><strong>THE SOLUTION</strong></h1>

**Mujassam is a generative CAD tool** for students, robotics teams, fab labs, and small workshops.

The user describes the part and gives its overall dimensions in millimetres. Mujassam retrieves compact engineering guidance, generates CadQuery, executes the program, validates the resulting solid, retries rejected outputs, and returns editable and printable files.

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
  <sub>Part description + dimensions &nbsp;&nbsp;&nbsp; Fine-tuned CadQuery generation &nbsp;&nbsp;&nbsp; Execute + measure + validate &nbsp;&nbsp;&nbsp; STEP · STL · GLB</sub>
</p>

<!-- Replace these with screenshots from the final deployed Mujassam website.

<p align="center">
  <img src="docs/assets/home.png" width="49%" alt="Mujassam input screen">
  <img src="docs/assets/result.png" width="49%" alt="Mujassam generated CAD result">
</p>

Optional physical-fit photo:
<p align="center">
  <img src="docs/assets/physical-fit.jpg" width="60%" alt="Printed generated part fitted to a real component">
</p>
-->

---

<h1><strong>SYSTEM ARCHITECTURE</strong></h1>

<p align="center">
  <img
    src="https://kroki.io/graphviz/png/eNqlVM2O2jAQvu9TWFTqpYACLT9SlUrJClAlqgKh7QH2YOJJ4q6xI8csu6167QP0ZXrvo_RJOg4hZCnSqs0FM5OZ7xvPfOMrxmNN04RMyNcrQg7_V5s4VEJpt2E0lVlKNUjTaBI0bhnX7nTRJCllbsNpd3vol4pBBqm1X_WKuMLuWztLBZeQuUqbRN28Rh6bQVZZQlNwN-oeQ8yDALeh1U4yYM2ICwEMUyMljaRb_ORpTkXhyfgXcDvdJtlSHXNpiTrDJv50MSAFuefMJG6n3cvJgMVIVtzo2Xjc9x2nGoc4VGu1z1Gd9jBP2nGyEnQDwm18gg358NZSY1VHGMfvjF96RT2Fc59wA-g6i8nxlA6TEnHGU7AtWcv36IYM22yUrsmQpRCWDAEaPOIhNVzJtVwAZVCXQNO4xF94E4tqNIe72sBbVIMooed7kN12r3WNXt0a-Gv5gsynauGdsZSDrLCcqM-iDh2iEZQ0XrAkATrMw1pOaF5bnTvAfaX715TNd6AReYTuXf3Z3tFTfyagtth4BP9IBWcXlPPvnVE7c5LOcjQjv36SYDm1x2Tq1yxeqJNu3inJsWAu47V8TqYqzs7AR73RYOQ_VXvfH3SHee2HVW29yResXDS07TpUbVRvuSVo5po7qrpqH8RoAaxa8MwniyfO4DgKS1fpGJl5QfDEY-VcvNFNBfHxFhANnyE05Pf3HyQCYBsa3v7dgMegpfPwmjKaJfiWYo60LwyXxo2oyOCkV2TNh3MefwZ3EaCo-j_zv139AQpTAxw"
    width="100%"
    alt="Mujassam system architecture"
  >
</p>

### **Where is the generative AI?**

**Qwen2.5-Coder-7B + QLoRA writes the CadQuery program for every request.**

There is no deterministic CAD compiler generating the final shape behind the model. Retrieval, execution, validation, repair, monitoring, and export are supporting components around generation.

---

<h1><strong>REQUEST WORKFLOW</strong></h1>

<p align="center">
  <img
    src="https://kroki.io/graphviz/png/eNqllM2O0zAQx-99ilGQuGxSJS1pkVAitbCtkHoouysuDQcnniQWrh3Z7seCuPIAvAx3HoUnYdJmw6qcUC9JZjIzv_l7bA-4qAxraljC1wHA-XuTV4WW2iSeM0zZhhlUzvOBjM9cmGR150PDeOKFw1FMfqU5Wmxaexx3cZ0dt7ZtpFBoE21crT-9IU6bARtbswaTXB8pxD1KTDyjd4oj90shJXJKLbVyim3p18wIJjuPFV8wiSIftsxUQrWgKPbpEVFAg-oguKuTaBifYMgrgnWKXiwWk3kYPo8b-cCM0YdT1XA4PWcx2EiWo0y8KFPv0BZG5EiyjcvUDeg9GiYltDltU9TvEyCcR4vxrOu0cx5q4dq4i5gTKO9Bo0zdIeOwRWZ3huUSM1p9LEQpCuaEVleSip40bknOCNwjGAI02Iqard_TZBzaKzm857zK1BIVLZUjwFvGP-zQPF5U7wfyrPpf5EXUeaB9_ThTt0csdg5BqEwJqyWhODRGF2iv1VH2nEmmPjIpOBUHYghOg6HJww3UWv6zXv-vqOpJ00ytDe4FHuAl4LHR7X67f7hdw6-fcP-wal_L1fxKZSxI8yAtgpQHKQZpGaTVSTA5-k6gZELC7-8_aIc0TBjv6ZRyZms6o33hyXw6en0pt3cWWlm6RoRyScmkReJ_G_wB80Bn2A"
    width="100%"
    alt="Mujassam request workflow"
  >
</p>

A rejected build returns its execution or measurement failure to the model. Only accepted geometry reaches export.

---

<h1><strong>MODEL & TECHNOLOGY</strong></h1>

| Component | Final choice |
|---|---|
| **Base model** | `Qwen/Qwen2.5-Coder-7B-Instruct` |
| **Adaptation** | QLoRA · rank 16 · alpha 32 · dropout 0.05 |
| **Quantization** | 4-bit NF4 + double quantization |
| **Context length** | 2,048 tokens |
| **Trainable weights** | ~40.4M · ~0.53% |
| **Embeddings** | `sentence-transformers/all-MiniLM-L6-v2` |
| **Vector store** | Chroma |
| **CAD engine** | CadQuery |
| **Output formats** | STEP · STL · GLB |

---

<h1><strong>TRAINING DATA</strong></h1>

The final adapter is trained on **project-generated procedural CAD data**.

Parameterized generators produce varied dimensions, optional features, natural-language requests, and an exact CadQuery target. The target is executed and verified before it can enter training.

### **Dataset by examples**

<div align="center">

<img src="https://img.shields.io/badge/TOTAL_SUPERVISED_RECORDS-6%2C823-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="6823 total records">

<br><br>

<img src="https://img.shields.io/badge/DIRECT_GENERATION-5%2C860-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="5860 direct examples">
<img src="https://img.shields.io/badge/REPAIR-963-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="963 repair examples">

<br><br>

<img src="https://img.shields.io/badge/OPTIMIZATION_TRAIN-6%2C687-0B1F3A?style=for-the-badge" alt="6687 training records">
<img src="https://img.shields.io/badge/LOSS_VALIDATION-136-0B1F3A?style=for-the-badge" alt="136 loss validation records">

</div>

### **Dataset by part types**

<p align="center">
  <img src="https://img.shields.io/badge/DESIGNED_TYPES-85-FF6B00?style=flat-square&labelColor=0B1F3A" alt="85 designed types">
  <img src="https://img.shields.io/badge/TRAINING_TYPES-76-6B7280?style=flat-square&labelColor=0B1F3A" alt="76 training types">
  <img src="https://img.shields.io/badge/VALIDATION_ONLY_TYPES-2-6B7280?style=flat-square&labelColor=0B1F3A" alt="2 validation types">
  <img src="https://img.shields.io/badge/HELD_OUT_TYPES-7-6B7280?style=flat-square&labelColor=0B1F3A" alt="7 held out types">
</p>

### **Separate validation and test data**

- **42 generated validation cases**
  - 30 in-distribution cases
  - 12 cases from the 2 validation-only part types
- **58-case model-selection suite**
  - the 42 validation cases above
  - plus 16 existing development prompts
- **28 held-out part-type test cases**
  - 7 part types never used in training
  - 4 requests per type
- **30 sealed user requests**
- **20 independent reserve requests**
- **20 in-domain regression requests**
- **12 second in-domain regression requests**

### **Verification before training**

<p align="center">
  <img src="https://img.shields.io/badge/EXECUTION-PASS-0B1F3A?style=flat-square" alt="Execution">
  <img src="https://img.shields.io/badge/ONE_SOLID-PASS-0B1F3A?style=flat-square" alt="One solid">
  <img src="https://img.shields.io/badge/ENVELOPE-PASS-0B1F3A?style=flat-square" alt="Envelope">
  <img src="https://img.shields.io/badge/WATERTIGHT-PASS-0B1F3A?style=flat-square" alt="Watertight">
  <img src="https://img.shields.io/badge/FEATURE_PROBES-PASS-0B1F3A?style=flat-square" alt="Feature probes">
</p>

**5,860 / 5,860 direct-generation targets passed the verification pipeline.**

---

<h1><strong>FEATURE COMPOSITION</strong></h1>

The dataset does not only repeat complete named parts.

Six composition generators teach the model to combine **2–4 compatible CAD operations**:

`composed_plate` · `composed_block` · `composed_disc` · `composed_l_bracket` · `composed_ring` · `composed_tray`

Examples of what gets combined:

```text
base plate + mounting holes + pocket + chamfer

disc + centre bore + bolt circle + raised boss

L-bracket + adjustment slots + upright holes

ring + radial hole + split + chamfer
```

This gives the model repeated practice with reusable geometry operations rather than only fixed object templates.

---

<h1><strong>FINE-TUNING vs RAG</strong></h1>

<p align="center">
  <img
    src="https://kroki.io/graphviz/png/eNqtVE1v2zAMvedXENlxdhCnc9LBcIAkaIoBHbD22hSDYjG2MFlSabtpN_R37b5fNvqjThsM2KG5yCZN8ZnvPWkgVUrCZXAJvwYA7fvtNk2sthQPSxKmcILQlEMPOPghFcVXNx44IePheDQJOW-sxAJdHZ-FXV0XTzksnFYGi9hSmdm7iGHqDXBbZMJhvLWPXFI-aYyHZCsjUXo7pTVK3rqzpjQi508LUkJ3mUL9xDgIPMgFpcrUOEHo8RJwgUOzV7LM4mD0qQFDmTJYN9CH9Xq6HI9f1008EER233Qdj2Zhs6uoti0Zia6KEuk7U6FMQxKAFlvU8XDNY_llZZRJ4c9v0CjIoIQt7iwhSHTaPuU1ddHxILC0WnbpdppJBC-_OF4G67MFf309StQAS7jtsEPvfDqGByS1Uyg3hnXBpAR8FLnTWNRMMYlHLVv6uuQ-UyVy6qjmrkWiHunz9AwInVC0MSdrn_Tt1yjKitBPbO5soUplzQlxdI9zfWVvFiCkcKzmUd_eFK_6HsCOqrrO0p_rCKhZk3rl7PO_jEMifWubm8VlbRfCkhQ-sGHYLoAiyTh1X2FxQr_QQcZgCmj4tCBbxqQbw3ZR7gQMC6d6jHNYCXldIT1tzOLbFz7n5SmsyET1EF-VUVdf4SOsMrK5OIGQxBrWEFE9SvfaaXnfw64qqi9BqAqkmrtWp7fgF-HF7GL5P_DpcjY578Bd3_8SDZJoze94MPf-5vnhiHX3VH1PXO_RTEahv-IrmPzZ8p3q2OMJaowXE7xbnPuDHPXTn7su2zy1P8-bQbvY-XMbDZ4HfwFJTRy9"
    width="100%"
    alt="Fine tuning versus RAG"
  >
</p>

### **Fine-tuning**

Changes the QLoRA adapter weights using:

- **5,860 verified direct-generation records**
- **963 repair records**
- feature-composition supervision

It teaches the model **how to turn a request into CadQuery and how to respond to failures**.

### **RAG**

Runs on the current request using:

- **16 engineering construction recipes**
- **8 CadQuery API notes**
- MiniLM embeddings
- Chroma retrieval

At runtime Mujassam retrieves **up to 1 engineering recipe + 2 API notes**.

RAG provides guidance. It does **not** retrieve the finished CAD program.

---

<h1><strong>EVALUATION</strong></h1>

### **Final frozen-model results**

| Evaluation set | Cases | Overall-size pass | Size + requested holes |
|---|---:|---:|---:|
| **In-domain regression** | 20 | **20/20 · 100%** | **20/20 · 100%** |
| **Second in-domain regression** | 12 | **12/12 · 100%** | **12/12 · 100%** |
| **Sealed user test** | 30 | **13/30 · 43.3%** | **11/30 · 36.7%** |
| **Held-out part types** | 28 | **10/28 · 35.7%** | **7/28 · 25.0%** |
| **Independent reserve** | 20 | **5/20 · 25.0%** | **4/20 · 20.0%** |

### **Sealed user test by difficulty**

<p align="center">
  <img src="https://img.shields.io/badge/TIER_1_%C2%B7_1--2_FEATURES-60.0%25-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Tier 1 60%">
  <img src="https://img.shields.io/badge/TIER_2_%C2%B7_3--4_FEATURES-33.3%25-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Tier 2 33.3%">
  <img src="https://img.shields.io/badge/TIER_3_%C2%B7_COMPLEX_GEOMETRY-37.5%25-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="Tier 3 37.5%">
</p>

### **Main sealed-test failure modes**

<p align="center">
  <img src="https://img.shields.io/badge/CODE_ERRORS-9-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="9 code errors">
  <img src="https://img.shields.io/badge/WRONG_SIZE-5-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="5 wrong size">
  <img src="https://img.shields.io/badge/INVALID_GEOMETRY-3-6B7280?style=for-the-badge&labelColor=0B1F3A" alt="3 invalid geometry">
</p>

### **Generated-part grids**

<p align="center">
  <img src="./results/v5/grid_v5_user_u01_u30.png" width="49%" alt="Sealed user test generated parts">
  <img src="./results/v5/grid_v5_heldout_types.png" width="49%" alt="Held-out part-type generated parts">
</p>

The results show strong performance on learned CAD operations and a clear generalization gap on unfamiliar topology. We report both rather than showing only familiar examples.

---

<h1><strong>VALIDATION</strong></h1>

### **Automatically checked**

<p align="center">
  <img src="https://img.shields.io/badge/AST_SAFETY-CHECKED-0B1F3A?style=flat-square" alt="AST safety">
  <img src="https://img.shields.io/badge/EXECUTION-CHECKED-0B1F3A?style=flat-square" alt="Execution">
  <img src="https://img.shields.io/badge/ONE_SOLID-CHECKED-0B1F3A?style=flat-square" alt="One solid">
  <img src="https://img.shields.io/badge/WATERTIGHT-CHECKED-0B1F3A?style=flat-square" alt="Watertight">
  <img src="https://img.shields.io/badge/OVERALL_SIZE-CHECKED-0B1F3A?style=flat-square" alt="Overall size">
  <img src="https://img.shields.io/badge/HOLES_%2F_BORES-CHECKED_WHERE_SUPPORTED-0B1F3A?style=flat-square" alt="Holes">
</p>

### **Still requires human review**

Advanced sweeps and lofts · unusual slots · subtle feature orientation · every pocket/chamfer relationship · structural suitability · real-world fit.

> **Mujassam is a capstone prototype, not an engineering-certification system.**

---

<h1><strong>LIVE DEMO</strong></h1>

<div align="center">

### **[Open Mujassam →](LIVE_DEMO_URL)**

### **[Watch the demo video →](DEMO_VIDEO_URL)**

</div>

---

<h1><strong>TEAM</strong></h1>

<p align="center">
  <img src="https://ui-avatars.com/api/?name=Fahad+Alshehri&background=0B1F3A&color=FFFFFF&size=128&bold=true" width="90" alt="Fahad Alshehri">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://ui-avatars.com/api/?name=Ghaida+Alsalamah&background=FF6B00&color=FFFFFF&size=128&bold=true" width="90" alt="Ghaida Alsalamah">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://ui-avatars.com/api/?name=Alreem+Rashed+Aldossary&background=0B1F3A&color=FFFFFF&size=128&bold=true" width="90" alt="Alreem Rashed Aldossary">
</p>

<p align="center">
  <strong>Fahad Alshehri</strong>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <strong>Ghaida Alsalamah</strong>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <strong>Alreem Rashed Aldossary</strong>
</p>

---

<details>
<summary><h2><strong>RUN THE PROJECT</strong></h2></summary>

### Colab

1. Open `Mujassam_demo.ipynb`.
2. Select a **T4 GPU or better**.
3. Run the cells in order.
4. Upload the project ZIP when requested.
5. Upload the trained adapter ZIP when requested.
6. Wait for Qwen2.5-Coder-7B + the QLoRA adapter to load.
7. Launch the application.

Example:

```text
Flanged bearing mount, overall 48 x 48 x 18 mm,
24 mm central bore, four 4 mm mounting holes
on a 36 mm square pattern.
```

### Local setup

```bash
git clone https://github.com/ghaida-alsalamah/Mujassam.git
cd Mujassam

python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

macOS / Linux:

```bash
source .venv/bin/activate
```

Then:

```bash
pip install -r requirements.txt
```

A CUDA-capable GPU is recommended for local 7B inference.

</details>

---

<details>
<summary><h2><strong>REPOSITORY STRUCTURE</strong></h2></summary>

```text
Mujassam/
├── README.md
├── requirements.txt
├── app.py
├── Mujassam_demo.ipynb
├── mujassam/        # generation, RAG, execution, validation, monitoring
├── data/            # training and evaluation data
├── scripts/         # data preparation and release utilities
├── tests/           # validator and pipeline tests
├── results/         # saved evaluation evidence and result grids
└── docs/            # run guides and project documentation
```

</details>

---

<details>
<summary><h2><strong>DATA SOURCES & LICENCES</strong></h2></summary>

- **Qwen2.5-Coder-7B-Instruct** — base code model · Apache-2.0
- **Project-generated procedural CAD data** — final fine-tuning supervision
- **all-MiniLM-L6-v2** — RAG embeddings · Apache-2.0
- **CadQuery** — parametric CAD execution · Apache-2.0
- **Chroma** — vector retrieval · Apache-2.0
- **Transformers / PEFT / bitsandbytes** — model loading, QLoRA, quantized inference · upstream licences

**No third-party CAD dataset is used to train the final adapter.**

</details>

---

<details>
<summary><h2><strong>MONITORING & RESPONSIBLE USE</strong></h2></summary>

Each build records:

`request · model · retrieval scores · pass/fail · rejected gate · error type · attempts · dimension error · latency`

Safeguards include:

- generated Python is checked by an AST safety filter;
- CadQuery runs in an isolated process with a timeout;
- rejected parts are not exported;
- unambiguous weapon / ammunition requests are refused before generation;
- users are warned that generated parts are not engineering-certified;
- users are asked not to submit personal information because requests may be logged.

</details>

---

<details>
<summary><h2><strong>LESSONS & NEXT STEPS</strong></h2></summary>

**What worked**

Verified procedural training data, code-focused QLoRA, compact engineering RAG, and execution-based validation.

**Main limitation**

Performance drops when a request requires genuinely unfamiliar topology or feature relationships.

**Next**

Stronger semantic feature validation · broader verified geometry coverage · persistent GPU deployment · stronger Arabic input support · more physical fit tests.

</details>


---

<div align="center">

<h1><strong>Mujassam · مجسّم</strong></h1>

**Describe it · Generate it · Check it · Print it**

<br>

**Repository:** https://github.com/ghaida-alsalamah/Mujassam

</div>
