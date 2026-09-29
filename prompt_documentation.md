# Prompt Engineering Documentation: Research & Verification Architecture

This document preserves the exact prompt templates and architectural patterns utilized to conduct the technical research, baseline drafting, and Chain-of-Verification (CoVe) audit cycle.

---

## 1. Generated Knowledge Prompt (Background Fact Compilation)

- **Purpose:** Compile unvarnished, factual technical specifications, official limits, and cost structures from official documentation before attempting comparisons or subjective evaluations.
- **Cognitive Strategy:** Decouple knowledge retrieval from reasoning to minimize bias.

### Prompt Template
```markdown
Generate a factual summary detailing the core architecture, scalability limits, setup complexity, and cost structures of the following three technologies: Kubernetes, Docker Swarm, and AWS Fargate. 

Focus on raw specifications, documentation facts, and industry statistics. Do not write a comparison or recommendations yet. Keep your focus on compiling background knowledge.
```

---

## 2. ERA Baseline Report Prompt (Expectation, Role, Action)

- **Purpose:** Establish the architectural persona, declare structural boundaries, and constrain model reasoning strictly to the compiled background facts.
- **Framework:** ERA Framework ([EXPECTATION], [ROLE], [ACTION]).

### Prompt Template
```markdown
[EXPECTATION]: 
I expect a detailed comparison report comparing Kubernetes, Docker Swarm, and AWS Fargate. Structure the response with H2 headers for: Introduction, Tech Overviews, Detailed Comparison, and Final Verdict. Do not write summary tables yet.

[ROLE]: 
Act as a Lead Systems Architect specializing in cloud-native infrastructure and container orchestration.

[ACTION]: 
Write the comparison report based on the following background facts:
=== BACKGROUND FACTS ===
[PASTE BACKGROUND FACT SHEET HERE]
```

---

## 3. Chain of Verification (CoVe) Prompts

Chain of Verification (CoVe) is a multi-step hallucination prevention protocol that audits a draft by generating targeted factual questions, independently answering them against verified sources, and revising the draft.

```
┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│   CoVe Step 1    │ ──► │   CoVe Step 2    │ ──► │   CoVe Step 3    │
│ Question Form.   │     │ Fact Verification│     │ Draft Correction │
└──────────────────┘     └──────────────────┘     └──────────────────┘
```

### CoVe Step 1: Question Formulation Prompt
```markdown
Read the baseline draft comparison below. Formulate a list of exactly four specific verification questions that can be answered with absolute facts to audit the claims, numbers, and limitations stated in the text (e.g., check version limits, specific scalability numbers, or operational dependencies).

[BASELINE DRAFT]:
[PASTE BASELINE DRAFT HERE]
```

### CoVe Step 2: Question Answering Prompt (Fact Verification)
```markdown
Answer each of the following verification questions one-by-one. Rely strictly on verified developer documentation facts:

[PASTE THE 4 VERIFICATION QUESTIONS HERE]
```

### CoVe Step 3: Report Correction Prompt
```markdown
Review the original baseline draft. Rewrite the report incorporating the verified corrections below. Ensure the final report is fully accurate and resolved.

[BASELINE DRAFT]:
[PASTE BASELINE DRAFT HERE]

[VERIFIED CORRECTIONS]:
[PASTE THE 4 VERIFIED ANSWERS HERE]
```

---

## 4. Assumption Audit Prompt

- **Purpose:** Analyze the finalized text for implicit cognitive biases, flawed mental models, or unstated commercial assumptions.

### Prompt Template
```markdown
Analyze the finalized technology comparison below. Identify and list 3 hidden assumptions the writer makes regarding the technologies (e.g., assuming high capital expense always correlates with higher quality, or assuming simplicity is always better for small teams). Detail if these assumptions introduce bias.

[FINALIZED REPORT]:
[PASTE THE CORRECTED REPORT FROM COVE STEP 3]
```

---

## 5. Comparison Matrix Generation Prompt

- **Purpose:** Synthesize multi-dimensional technical data into a structured Markdown comparison table.

### Prompt Template
```markdown
Create a markdown table comparing Kubernetes, Docker Swarm, and AWS Fargate across these columns: 
- Technology
- Scalability (High/Med/Low)
- Setup Complexity (High/Med/Low)
- Operational Overhead (High/Med/Low)
- Cost Model (e.g., Pay-per-node, Pay-per-use, Free)

Ensure all ratings are derived directly from the verified facts established in the research report.
```

---

## 6. Executive Summary Prompt (Startup Recommendation)

- **Purpose:** Distill high-density technical findings into a concise, board-level executive synthesis with an actionable recommendation.

### Prompt Template
```markdown
Write a 150-word executive summary synthesizing the comparison findings. Recommend the best technology for a fast-growing startup prioritizing speed over infrastructure scaling.
```
