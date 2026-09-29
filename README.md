# AI-Assisted Research & Knowledge Verification Architectures

## Project Information
- **Student Name:** Abhishek Nikam
- **Topic:** AI-Assisted Research & Knowledge Verification Architectures (Topic 5 Assessment)
- **Repository:** `prompt-engineering-researcher`
- **Domain Focus:** Cloud Container Orchestration (Kubernetes vs. Docker Swarm vs. AWS Fargate)

---

## Project Objectives

1. **Eliminate LLM Hallucinations:** Implement the multi-step **Chain of Verification (CoVe)** framework to systematically audit and correct factual inaccuracies, inflated limits, and phantom pricing in AI-generated technical reports.
2. **Apply Structured Architectural Prompting:** Leverage the **ERA Framework** (`[EXPECTATION]`, `[ROLE]`, `[ACTION]`) and Generated Knowledge prompting to ground outputs in official cloud documentation before comparative reasoning.
3. **Execute Rigorous Multi-Dimensional Synthesis:** Produce an audited technology comparison report, a multi-attribute decision matrix, an assumption bias audit, and an executive recommendation tailored for high-velocity startups.

---

## Deliverables & Repository Structure

```
prompt-engineering-researcher/
├── README.md                 # Project overview, Loom video walkthrough, and reproduction guide
├── research_report.md        # Fact sheet, CoVe audit trail, final corrected report, and assumption audit
├── comparison_matrix.md      # Multi-dimensional comparison table and dimension breakdown
├── executive_summary.md      # 150-word board-level synthesis and startup recommendation
├── prompt_documentation.md   # Complete prompt templates (ERA, CoVe 3-step cycle, Assumption Audit)
└── baseline_draft.txt        # Unverified baseline draft highlighting hallucinations caught by CoVe
```

### Deliverable Manifest

| File | Purpose |
|---|---|
| [`research_report.md`](research_report.md) | Exhaustive research report containing the baseline factual specification sheet, the complete 3-step Chain of Verification audit trail (4 questions and documented answers), the finalized report, and an assumption bias analysis. |
| [`comparison_matrix.md`](comparison_matrix.md) | Comprehensive Markdown comparison table evaluating Kubernetes, Docker Swarm, and AWS Fargate across Scalability, Setup Complexity, Operational Overhead, and Cost Model. |
| [`executive_summary.md`](executive_summary.md) | High-impact 150-word executive brief synthesizing core trade-offs and recommending AWS Fargate for fast-growing startups prioritizing developer velocity. |
| [`prompt_documentation.md`](prompt_documentation.md) | Production prompt templates documenting the Generated Knowledge prompt, ERA parameters, all 3 CoVe cycle prompts, and the Assumption Audit prompt. |
| [`baseline_draft.txt`](baseline_draft.txt) | Raw unverified baseline draft retained as reference to demonstrate the specific hallucinations identified and resolved through CoVe. |

---

## Public Loom Walkthrough Video

Watch the complete project walkthrough and live CoVe verification demonstration here:  
**[Watch the Public Loom Video](YOUR_PUBLIC_LOOM_URL)**

### Structured Video Agenda (3–4 Minutes)
- **0:00–0:45 (Introduction & Core Philosophy):** Introduction by Abhishek Nikam, overview of the container orchestration research challenge, and explanation of why Chain of Verification (CoVe) is vital for preventing AI technical hallucinations.
- **0:45–2:00 (Prompt Documentation & Framework Walkthrough):** Display [`prompt_documentation.md`](prompt_documentation.md) on screen. Walk through the ERA framework parameters (`[EXPECTATION]`, `[ROLE]`, `[ACTION]`) and explain the 3-step CoVe cycle (question formulation → factual verification → draft correction).
- **2:00–3:15 (Live ChatGPT Demo — CoVe Question Answering):** In a live ChatGPT window, paste the CoVe Question Answering Prompt and show ChatGPT auditing the 4 specific technical claims (correcting K8s limits to 5,000 nodes, confirming Docker Swarm active status, removing phantom Fargate fees, and verifying privileged container restrictions).
- **3:15–3:45 (Comparison Matrix & Closing Remarks):** Review the finalized [`comparison_matrix.md`](comparison_matrix.md) and [`executive_summary.md`](executive_summary.md), summarizing the strategic recommendation of AWS Fargate for lean startups.

---

## Summary of the Chain of Verification (CoVe) Audit

| Audit Area | Baseline Draft Claim (Hallucination) | Verified Documentation Reality | Correction Applied |
|---|---|---|---|
| **Kubernetes Scalability** | Up to 15,000 nodes natively supported. | Official Kubernetes.io limits support up to **5,000 nodes** and **150,000 pods**. | Corrected node ceiling from 15,000 to 5,000. |
| **Docker Swarm Status** | Completely deprecated and prohibited from production. | Active, open-source, and maintained within Docker Engine (Moby). | Retracted false deprecation claim; clarified lightweight production role. |
| **AWS Fargate Pricing** | Mandatory $50/month cluster fee plus hourly charges. | **Zero base fee and zero cluster management fees**; pure pay-per-second utility compute. | Eradicated phantom $50 fee; accurately documented per-second resource billing. |
| **Fargate Security Constraints**| Supports running root privileged containers natively. | Privileged containers (`--privileged`) are **strictly prohibited** in Fargate microVMs. | Added critical security constraint regarding root privileges and kernel isolation. |

---

## How to Reproduce the Research Pipeline

1. Open [`prompt_documentation.md`](prompt_documentation.md).
2. Execute **Template 1** in ChatGPT ([chatgpt.com](https://chatgpt.com)) to generate the raw factual background sheet.
3. Pipe the fact sheet into **Template 2 (ERA Baseline Prompt)** to generate the initial comparative draft.
4. Execute **Template 3 (CoVe Step 1)** to extract 4 factual audit questions from the draft.
5. Execute **Template 4 (CoVe Step 2)** in a separate clean thread to answer the questions strictly from official documentation.
6. Run **Template 5 (CoVe Step 3)** combining the draft and verified answers to produce the final hallucination-free report.
7. Execute **Templates 6, 7, and 8** to generate the assumption audit, comparison matrix, and executive summary.
