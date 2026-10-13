<div align="center">

Mujassam · مجسّم

Natural language → parametric CAD → verified geometry → printable files

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
  <img src="https://img.shields.io/badge/OUTPUT-STEP_%7C_STL_%7C_GLB-6B7280?style=flat-square&labelColor=0B1F3A" alt="Output">
</p>

Tuwaiq Academy · Generative AI Application Engineering Bootcamp · October 2026

</div>

THE PROBLEM

Small custom parts can be simple in shape but still require CAD knowledge and manual modelling.

<table>
<tr>
<td align="center" width="25%"><b>⚠️ CODE</b><br><sub>generated CAD may not execute</sub></td>
<td align="center" width="25%"><b>📏 SIZE</b><br><sub>a plausible preview may still be the wrong size</sub></td>
<td align="center" width="25%"><b>🧩 GEOMETRY</b><br><sub>solids can be invalid or disconnected</sub></td>
<td align="center" width="25%"><b>⭕ FEATURES</b><br><sub>requested holes or bores may be missing</sub></td>
</tr>
</table>

Mujassam checks the generated geometry before it is exported.

THE SOLUTION

Mujassam is a generative CAD tool for students, robotics teams, fab labs, and small workshops.

<table>
<tr>
<td align="center" width="22%">
<img src="https://img.shields.io/badge/1-DESCRIBE-0B1F3A?style=for-the-badge" alt="Describe"><br>
<sub>Part description + overall size</sub>
</td>
<td align="center" width="4%"><h2>→</h2></td>
<td align="center" width="22%">
<img src="https://img.shields.io/badge/2-GENERATE-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Generate"><br>
<sub>Fine-tuned Qwen writes CadQuery</sub>
</td>
<td align="center" width="4%"><h2>→</h2></td>
<td align="center" width="22%">
<img src="https://img.shields.io/badge/3-VERIFY-0B1F3A?style=for-the-badge" alt="Verify"><br>
<sub>Execute · measure · validate</sub>
</td>
<td align="center" width="4%"><h2>→</h2></td>
<td align="center" width="22%">
<img src="https://img.shields.io/badge/4-EXPORT-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Export"><br>
<sub>STEP · STL · GLB</sub>
</td>
</tr>
</table>

<!--
ADD FINAL WEBSITE SCREENSHOTS HERE

<p align="center">
  <img src="docs/assets/home.png" width="49%" alt="Mujassam home screen">
  <img src="docs/assets/result.png" width="49%" alt="Mujassam generated result">
</p>

Optional physical-fit photo:
<p align="center">
  <img src="docs/assets/physical-fit.jpg" width="65%" alt="Printed generated part fitted to a real component">
</p>
-->

SYSTEM ARCHITECTURE

Main generation path

<table>
<tr>
<td align="center">
<img src="https://img.shields.io/badge/INPUT-Web_UI-0B1F3A?style=for-the-badge" alt="Web UI">
</td>
<td align="center"><h2>→</h2></td>
<td align="center">
<img src="https://img.shields.io/badge/CONTROL-Pipeline_Orchestrator-0B1F3A?style=for-the-badge" alt="Pipeline Orchestrator">
</td>
<td align="center"><h2>→</h2></td>
<td align="center">
<img src="https://img.shields.io/badge/GENERATE-Qwen_7B_%2B_QLoRA-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Qwen + QLoRA">
</td>
<td align="center"><h2>→</h2></td>
<td align="center">
<img src="https://img.shields.io/badge/SAFE-AST_Gate-0B1F3A?style=for-the-badge" alt="AST Safety">
</td>
</tr>
<tr>
<td></td><td></td><td></td><td></td>
<td align="center"><h2>↓</h2></td><td></td><td></td>
</tr>
<tr>
<td align="center" colspan="3">
<img src="https://img.shields.io/badge/CONTEXT-Spec_Reader_%2B_RAG-0B1F3A?style=for-the-badge" alt="Spec Reader and RAG">
<br><sub>feeds dimensions + retrieved engineering guidance into generation</sub>
</td>
<td></td>
<td align="center">
<img src="https://img.shields.io/badge/RUN-CadQuery_Executor-0B1F3A?style=for-the-badge" alt="CadQuery Executor">
</td>
<td align="center"><h2>→</h2></td>
<td align="center">
<img src="https://img.shields.io/badge/CHECK-Geometry_Validator-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="Geometry Validator">
</td>
</tr>
<tr>
<td></td><td></td><td></td><td></td><td></td><td></td>
<td align="center"><h2>↓</h2></td>
</tr>
<tr>
<td align="center" colspan="5"><sub>Rejected output → execution / measurement feedback → model retries</sub></td>
<td></td>
<td align="center">
<img src="https://img.shields.io/badge/PASS-STEP_%7C_STL_%7C_GLB-0B1F3A?style=for-the-badge" alt="Exports">
</td>
</tr>
</table>

Where is the generative AI?

Qwen2.5-Coder-7B + QLoRA generates the CadQuery program for every request.
Retrieval, execution, validation, monitoring, and export are deterministic support components around the model.

REQUEST WORKFLOW

<table>
<tr>
<td align="center"><b>1</b><br>Describe part<br><sub>+ overall size</sub></td>
<td align="center">→</td>
<td align="center"><b>2</b><br>Read spec<br><sub>dimensions + tolerance</sub></td>
<td align="center">→</td>
<td align="center"><b>3</b><br>Retrieve<br><sub>recipe + API notes</sub></td>
<td align="center">→</td>
<td align="center"><b>4</b><br>Generate<br><sub>CadQuery</sub></td>
</tr>
<tr>
<td align="center"><b>8</b><br>Export<br><sub>STEP · STL · GLB</sub></td>
<td align="center">←</td>
<td align="center"><b>7</b><br>Feature check<br><sub>supported holes / bores</sub></td>
<td align="center">←</td>
<td align="center"><b>6</b><br>Geometry check<br><sub>solid · watertight · size</sub></td>
<td align="center">←</td>
<td align="center"><b>5</b><br>Execute<br><sub>isolated CadQuery run</sub></td>
</tr>
</table>

<div align="center">

FAIL at any gate → feedback → regenerate

</div>

MODEL & STACK

<table>
<tr>
<th>Component</th>
<th>Choice</th>
<th>Why it is used</th>
</tr>
<tr><td><b>Base model</b></td><td><code>Qwen2.5-Coder-7B-Instruct</code></td><td>code-focused generation</td></tr>
<tr><td><b>Adaptation</b></td><td>QLoRA · r16 · α32</td><td>task-specific fine-tuning</td></tr>
<tr><td><b>Quantization</b></td><td>4-bit NF4</td><td>memory-efficient training / inference</td></tr>
<tr><td><b>Embeddings</b></td><td>all-MiniLM-L6-v2</td><td>semantic retrieval</td></tr>
<tr><td><b>Vector store</b></td><td>Chroma</td><td>RAG knowledge search</td></tr>
<tr><td><b>CAD engine</b></td><td>CadQuery</td><td>parametric solid modelling</td></tr>
<tr><td><b>Exports</b></td><td>STEP · STL · GLB</td><td>edit · print · preview</td></tr>
</table>

TRAINING DATA

<div align="center">

<img src="https://img.shields.io/badge/DESIGNED_TYPES-85-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="85 designed types">
<img src="https://img.shields.io/badge/TRAINING_TYPES-76-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="76 training types">
<img src="https://img.shields.io/badge/DIRECT_EXAMPLES-5%2C860-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="5860 direct examples">
<img src="https://img.shields.io/badge/REPAIR_EXAMPLES-963-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="963 repair examples">
<img src="https://img.shields.io/badge/TOTAL_RECORDS-6%2C823-FF6B00?style=for-the-badge&labelColor=0B1F3A" alt="6823 records">

</div>

Dataset split

<table>
<tr>
<td align="center" width="33%">
<h2>76</h2>
<b>Training types</b><br>
<sub>used to update the QLoRA adapter</sub>
</td>
<td align="center" width="33%">
<h2>2</h2>
<b>Validation-only types</b><br>
<sub>used for model selection</sub>
</td>
<td align="center" width="33%">
<h2>7</h2>
<b>Held-out types</b><br>
<sub>never included in training</sub>
</td>
</tr>
</table>

How a training example is created

<table>
<tr>
<td align="center"><b>Part generator</b></td>
<td align="center">→</td>
<td align="center"><b>Valid dimensions + features</b></td>
<td align="center">→</td>
<td align="center"><b>Request + target CadQuery</b></td>
<td align="center">→</td>
<td align="center"><b>Execute + verify</b></td>
<td align="center">→</td>
<td align="center"><b>Training record</b></td>
</tr>
</table>

Verification before training

<table>
<tr>
<td>✓ CadQuery executes</td>
<td>✓ AST safety rules</td>
<td>✓ one valid solid</td>
</tr>
<tr>
<td>✓ correct envelope</td>
<td>✓ watertight STL</td>
<td>✓ requested hole checks where applicable</td>
</tr>
</table>

5,860 / 5,860 direct targets passed the verification pipeline.

FEATURE COMPOSITION

Instead of only training complete named parts, six generators combine 2–4 reusable CAD features.

<table>
<tr>
<th>Generator</th>
<th>Typical combinations</th>
</tr>
<tr><td><code>composed_plate</code></td><td>holes · bolt pattern · pocket · chamfer</td></tr>
<tr><td><code>composed_block</code></td><td>bore · slot · cut-out · mounting holes</td></tr>
<tr><td><code>composed_disc</code></td><td>center bore · polar holes · boss</td></tr>
<tr><td><code>composed_l_bracket</code></td><td>base slots · upright holes · chamfer</td></tr>
<tr><td><code>composed_ring</code></td><td>bore · radial holes · split / cut</td></tr>
<tr><td><code>composed_tray</code></td><td>walls · compartments · mounting features</td></tr>
</table>

FINE-TUNING vs RAG

<table>
<tr>
<th width="50%">QLoRA · learned before deployment</th>
<th width="50%">RAG · retrieved on every request</th>
</tr>
<tr>
<td valign="top">
<b>5,860</b> verified direct examples<br>
<b>963</b> repair examples<br>
<b>6</b> feature-composition generators<br><br>
<b>Purpose:</b> teach text → CadQuery and repair behaviour
</td>
<td valign="top">
<b>16</b> engineering construction recipes<br>
<b>8</b> CadQuery API notes<br>
<b>≤1 recipe + ≤2 notes</b> per request<br><br>
<b>Purpose:</b> provide compact engineering context
</td>
</tr>
<tr>
<td align="center">changes the adapter weights</td>
<td align="center">does not change the model weights</td>
</tr>
</table>

<div align="center">

Current request + retrieved context → fine-tuned Qwen → generated CadQuery

</div>

EVALUATION

Final frozen-model comparison

<table>
<tr>
<th>Evaluation set</th>
<th>Cases</th>
<th>Overall-size pass</th>
<th>Size + requested holes</th>
</tr>
<tr>
<td><b>In-domain regression</b></td>
<td align="center">20</td>
<td align="center"><img src="https://img.shields.io/badge/20%2F20-100%25-FF6B00?style=flat-square&labelColor=0B1F3A" alt="100%"></td>
<td align="center"><img src="https://img.shields.io/badge/20%2F20-100%25-FF6B00?style=flat-square&labelColor=0B1F3A" alt="100%"></td>
</tr>
<tr>
<td><b>Second in-domain regression</b></td>
<td align="center">12</td>
<td align="center"><img src="https://img.shields.io/badge/12%2F12-100%25-FF6B00?style=flat-square&labelColor=0B1F3A" alt="100%"></td>
<td align="center"><img src="https://img.shields.io/badge/12%2F12-100%25-FF6B00?style=flat-square&labelColor=0B1F3A" alt="100%"></td>
</tr>
<tr>
<td><b>Sealed user test</b></td>
<td align="center">30</td>
<td align="center"><img src="https://img.shields.io/badge/13%2F30-43.3%25-6B7280?style=flat-square&labelColor=0B1F3A" alt="43.3%"></td>
<td align="center"><img src="https://img.shields.io/badge/11%2F30-36.7%25-6B7280?style=flat-square&labelColor=0B1F3A" alt="36.7%"></td>
</tr>
<tr>
<td><b>Held-out part types</b></td>
<td align="center">28</td>
<td align="center"><img src="https://img.shields.io/badge/10%2F28-35.7%25-6B7280?style=flat-square&labelColor=0B1F3A" alt="35.7%"></td>
<td align="center"><img src="https://img.shields.io/badge/7%2F28-25.0%25-6B7280?style=flat-square&labelColor=0B1F3A" alt="25%"></td>
</tr>
<tr>
<td><b>Independent reserve</b></td>
<td align="center">20</td>
<td align="center"><img src="https://img.shields.io/badge/5%2F20-25.0%25-6B7280?style=flat-square&labelColor=0B1F3A" alt="25%"></td>
<td align="center"><img src="https://img.shields.io/badge/4%2F20-20.0%25-6B7280?style=flat-square&labelColor=0B1F3A" alt="20%"></td>
</tr>
</table>

Sealed test by difficulty

<table>
<tr>
<th>Difficulty</th>
<th>Cases</th>
<th>Passed</th>
<th>Pass rate</th>
</tr>
<tr><td><b>Tier 1</b> · 1–2 features</td><td align="center">10</td><td align="center">6</td><td align="center"><b>60.0%</b></td></tr>
<tr><td><b>Tier 2</b> · 3–4 features</td><td align="center">12</td><td align="center">4</td><td align="center"><b>33.3%</b></td></tr>
<tr><td><b>Tier 3</b> · curved / angled / patterned</td><td align="center">8</td><td align="center">3</td><td align="center"><b>37.5%</b></td></tr>
</table>

Main failure modes on the sealed test

<table>
<tr>
<td align="center" width="33%"><h2>9</h2><b>Code errors</b></td>
<td align="center" width="33%"><h2>5</h2><b>Wrong size</b></td>
<td align="center" width="33%"><h2>3</h2><b>Invalid geometry</b></td>
</tr>
</table>

The results show strong performance on familiar CAD operations and a clear generalization gap on genuinely unfamiliar geometry.

VALIDATION & SAFETY

<table>
<tr>
<th>Automatically checked</th>
<th>Still requires human review</th>
</tr>
<tr>
<td>✓ generated-code safety</td>
<td>uncommon slot geometry</td>
</tr>
<tr>
<td>✓ isolated execution + timeout</td>
<td>advanced sweeps / lofts</td>
</tr>
<tr>
<td>✓ exactly one valid solid</td>
<td>subtle feature orientation</td>
</tr>
<tr>
<td>✓ watertightness</td>
<td>every pocket / chamfer relationship</td>
</tr>
<tr>
<td>✓ overall dimensions</td>
<td>structural suitability</td>
</tr>
<tr>
<td>✓ supported holes / bores</td>
<td>real-world mechanical fit</td>
</tr>
</table>

Mujassam is a capstone prototype, not an engineering-certification system.

DEMO

<table>
<tr>
<td align="center" width="50%">
<h3>LIVE APPLICATION</h3>
<a href="LIVE_DEMO_URL"><b>Open Mujassam →</b></a>
</td>
<td align="center" width="50%">
<h3>DEMO VIDEO</h3>
<a href="DEMO_VIDEO_URL"><b>Watch the demo →</b></a>
</td>
</tr>
</table>

TEAM

<table>
<tr>
<td align="center" width="33%"><h2>👤</h2><b>[Team Member 1]</b></td>
<td align="center" width="33%"><h2>👤</h2><b>[Team Member 2]</b></td>
<td align="center" width="33%"><h2>👤</h2><b>[Team Member 3]</b></td>
</tr>
</table>

<details>
<summary><b>▶ Run the project</b></summary>

Colab demo

Open Mujassam_demo.ipynb.

Select a T4 GPU or better.

Run the cells in order.

Upload Mujassam_QWEN7B_V5_project.zip.

Upload mujassam_v5_A_7B_r16_adapter.zip.

Wait for the base model + adapter to load.

Launch the application from the final cell.

Example request:

Flanged bearing mount, overall 48 x 48 x 18 mm,
24 mm central bore, four 4 mm mounting holes
on a 36 mm square pattern.

Local setup

git clone https://github.com/ghaida-alsalamah/Mujassam.git
cd Mujassam
python -m venv .venv

Windows:

.venv\Scripts\activate

macOS / Linux:

source .venv/bin/activate

Then:

pip install -r requirements.txt

A CUDA-capable GPU is recommended for local 7B inference.

</details>

<details>
<summary><b>▶ Repository structure</b></summary>

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

</details>

<details>
<summary><b>▶ Data sources & licences</b></summary>

<table>
<tr><th>Resource</th><th>Role</th><th>Licence / note</th></tr>
<tr><td>Qwen2.5-Coder-7B-Instruct</td><td>base code model</td><td>Apache-2.0</td></tr>
<tr><td>Project-generated procedural CAD data</td><td>fine-tuning supervision</td><td>generated and verified in this project</td></tr>
<tr><td>all-MiniLM-L6-v2</td><td>RAG embeddings</td><td>Apache-2.0</td></tr>
<tr><td>CadQuery</td><td>CAD execution</td><td>Apache-2.0</td></tr>
<tr><td>Chroma</td><td>vector retrieval</td><td>Apache-2.0</td></tr>
<tr><td>Transformers · PEFT · bitsandbytes</td><td>model loading / QLoRA</td><td>upstream licences</td></tr>
</table>

No external CAD dataset is used to train the final adapter.

</details>

<details>
<summary><b>▶ Monitoring, risks & next steps</b></summary>

Monitoring

Each build records:

request · model · retrieval scores · pass/fail · rejected gate · error type · attempts · dimension error · latency

Responsible use

unambiguous weapon / ammunition requests are rejected before generation;

generated Python passes an AST safety filter;

execution runs in an isolated process with a timeout;

failed parts are not exported;

users are warned that generated parts are not engineering-certified;

users are asked not to enter personal information because requests may be logged.

What we learned

Worked well

Main limitation

Next step

verified procedural data

unfamiliar topology

broader verified geometry coverage

code-focused QLoRA

incomplete semantic checking

stronger feature validators

compact engineering RAG

repeated repair failures

more diverse repair strategies

execution-based validation

English-first input

stronger Arabic support

physical-fit testing

temporary compute

persistent GPU deployment

</details>

<details>
<summary><b>▶ AI-assisted development disclosure</b></summary>

AI tools were used during development for implementation support, debugging, code review, generator review, documentation, and interface prototyping.

The team directed the work, ran training and evaluation, and reviewed the outputs. Training targets were executed and programmatically verified before inclusion in the fine-tuning set.

</details>

<div align="center">

Mujassam · مجسّم

Describe it · Generate it · Check it · Print it

Repository: https://github.com/ghaida-alsalamah/Mujassam

</div>
