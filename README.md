<div align="center">

# VESPERA<span style="color:#2563EB">.</span>
### Deterministic Symbolic Document Question Answering & Rule-Based Inference Engine

[![Zero NLP](https://img.shields.io/badge/NLP-Zero%20%2F%20None-18181B?style=for-the-badge)](https://github.com/Ahadcf)
[![Zero RAG](https://img.shields.io/badge/RAG-Zero%20%2F%20None-2563EB?style=for-the-badge)](https://github.com/Ahadcf)
[![Inference](https://img.shields.io/badge/Logic-Modus%20Ponens-D4FF33?style=for-the-badge&labelColor=18181B)](https://github.com/Ahadcf)
[![Single File](https://img.shields.io/badge/Architecture-Zero--Dependency%20HTML5-10B981?style=for-the-badge)](https://github.com/Ahadcf)

*A transparent, verifiable document intelligence agent built strictly on classical symbolic AI principles—combining sentential knowledge representation, deterministic lexical indexing, and forward-chaining `IF–THEN` logical deduction.*

</div>

---

## Overview

Modern Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG) pipelines rely on opaque neural weights and probabilistic token prediction that can introduce hallucinations and obscure how answers are derived.

**VESPERA.** takes a deterministic, explainable approach to Document Question Answering:
- **Zero NLP / Zero RAG:** No neural embeddings, vector databases, external stemmers, or pre-trained language models.
- **100% Document-Grounded:** Every response is traced directly to extracted document facts (`F1…Fn`) or derived via explicit conditional production rules (`R1…Rm`).
- **Interactive 3D Editorial Workspace:** Combines a Swiss-inspired editorial UI and autonomous 3D frosted-glass folder visualization (Three.js) with a streamlined three-stage Q&A workflow.

---

## Core AI Architecture & Pipeline

VESPERA executes a four-stage symbolic processing pipeline directly in the browser:

```text
┌──────────────────────┐     ┌──────────────────────────┐     ┌──────────────────────────┐     ┌──────────────────────────┐
│  01. INGESTION       │ ──▶ │  02. KNOWLEDGE BASE      │ ──▶ │  03. QUERY ANALYSIS      │ ──▶ │  04. INFERENCE & OUTPUT  │
│  • .TXT / .PDF /     │     │  • Sentence Segmentation │     │  • Alphanumeric Tokens   │     │  • Contradiction Guard   │
│    .DOCX Extraction  │     │  • Atomic Facts (F1..Fn) │     │  • Stopword Filtering    │     │  • Modus Ponens (P→Q)    │
│  • Whitespace Norm.  │     │  • IF–THEN Rules (R1..Rm)│     │  • Intent Classification │     │  • Keyword Overlap Rank  │
└──────────────────────┘     └──────────────────────────┘     └──────────────────────────┘     └──────────────────────────┘
```

### 1. Multi-Format Document Ingestion
- **Plain Text (`.txt`):** Native browser stream decoding.
- **PDF Documents (`.pdf`):** Deterministic page-by-page text extraction via `PDF.js`.
- **Word Documents (`.docx`):** XML text extraction via `Mammoth.js`.

### 2. Symbolic Knowledge Base Construction
Extracted text is normalized and segmented along punctuation boundaries (`. ! ?`). Each sentence is classified into:
- **Production Rules (`R1…Rm`):** Statements matching `IF <antecedent> THEN <consequent>` are decomposed into structured condition keywords $T(P)$ and conclusion clauses $Q$.
- **Atomic Facts (`F1…Fn`):** Declarative statements are indexed with stopword-filtered alphanumeric tokens while preserving domain symbols (e.g., `A*`, `FIFO`, `LIFO`).

### 3. Question Processing & Overlap Scoring
Queries are tokenized, stripped of deterministic stopwords, and categorized into *Conditional / Inference*, *Verification*, or *Factual / Definition* queries. Candidate facts are scored by normalized keyword overlap:

$$\text{OverlapScore}(q, F_i) = \frac{|T(q) \cap T(F_i)|}{|T(q)|}$$

### 4. Modus Ponens Deduction & Contradiction Guardrails
- **Forward-Chaining Inference:** When a query satisfies at least **60%** of a rule's antecedent keywords (with $\ge 2$ matched terms), **Modus Ponens** ($P, P \rightarrow Q \vdash Q$) fires to derive the conclusion.
- **Predicate Contradiction Check:** Mutually exclusive predicate pairs (e.g., `labelled` vs. `unlabelled`, `supervised` vs. `unsupervised`, `complete` vs. `incomplete`) block invalid rule activation and alert the user.
- **Zero-Hallucination Scope Check:** Queries falling below the minimum evidence threshold (`0.35`) are cleanly rejected as unsupported by the document.

---

## Quick Start

Because VESPERA is engineered as a self-contained single-page web application (`index.html`), no build step or backend server is required:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Ahadcf/vespera.git
   cd vespera
   ```
2. **Launch the application:**
   - Open `index.html` directly in any modern browser (Chrome, Edge, Safari, Firefox), **or**
   - Serve locally with Python or VS Code Live Server:
     ```bash
     python3 -m http.server 8080
     ```
3. **Test with the built-in corpus:**
   - Click **`Try Demo`** in the navbar (or **`✨ Load sample document to try`** in Stage 01) to load the sample AI knowledge base and test rule deduction, direct retrieval, contradiction detection, and out-of-scope rejection.

---

## Verification & Test Scenarios

| Test ID | Scenario | Sample Query | Expected Symbolic Behavior |
| :--- | :--- | :--- | :--- |
| **TC-01** | **Modus Ponens Deduction** | *"What happens if a machine learning model is trained using labelled data?"* | Fires Rule `R1` and deduces *"it is called a supervised learning model."* |
| **TC-02** | **Direct Fact Retrieval** | *"How does Breadth-First Search explore nodes?"* | Retrieves Fact `F4` (*FIFO queue*) with keyword overlap percentage. |
| **TC-03** | **Contradiction Detection** | *"If a model is trained using unlabelled data, is it a supervised learning model?"* | Flags `labelled vs. unlabelled` conflict and cites Rule `R2`. |
| **TC-04** | **Out-of-Scope Rejection** | *"What is the boiling point of liquid nitrogen?"* | Rejects query with *"Insufficient supporting information"* (0% hallucination). |

---

## Project Structure

```text
vespera/
├── index.html                        # Complete self-contained VESPERA web app (UI, 3D WebGL, Symbolic Engine)
├── Vespera_AID201A_IEEE_Report.docx  # IEEE-formatted academic report (Ramaiah University of Applied Sciences)
└── README.md                         # Project documentation
```

---

## Academic Context

Developed for **AID201A: Artificial Intelligence (Assignment 1)** at the **Faculty of Engineering and Technology, Ramaiah University of Applied Sciences (RUAS), Bengaluru**, demonstrating classical symbolic AI knowledge representation, search, and logical inference without NLP or RAG frameworks.

---

<div align="center">

**Engineered & Architected by [AHAD](https://github.com/Ahadcf)**

</div>