# AI Governance Case Files

[![Tests](https://github.com/nitinparab4cloud/nus-masters-projects/actions/workflows/tests.yml/badge.svg)](https://github.com/nitinparab4cloud/nus-masters-projects/actions/workflows/tests.yml)

A four-project portfolio built to demonstrate AI governance experience for the job
search — classify an AI system's regulatory risk, technically audit a real model for
fairness, explain its individual decisions in plain language, then document the full
governance artifact set. Grew out of NUS's MSI5004 (AI Governance and Ethics) module,
with Legal-2 extending into material from a separate AI ethics course. Full plan,
weekly milestones, and progress tracker:
**[AI Governance Case Files (working plan)](https://claude.ai/code/artifact/6c79a3b0-6071-46a6-ba06-e443a4afd022)**.

| # | Project | Track | Status |
|---|---|---|---|
| 01 | [AI Act Risk Navigator](01-ai-act-risk-navigator/) | Regulatory classification | Built, tested, live |
| 02 | [Algorithmic Fairness Auditor](02-fairness-auditor/) | Technical audit | Core pipeline, metrics, and a live browser demo built; audit report + counterfactual test remaining |
| 03 | [Governance Documentation Suite](03-governance-documentation-suite/) | Documentation & process | Generator built and tested with a worked example |
| 04 | [Explainability Auditor](04-explainability-auditor/) | Technical audit — individual explanations | Built and tested, including a live browser demo |
| 05 | Governed RAG/Agent *(planned)* | GenAI & agentic governance | Design brief in progress — see Roadmap below |

## Why four, in this order

The build order (01–04, by folder number) isn't quite the narrative order — Legal-2
was added after CrossSector-2. Read as a story, the arc mirrors NIST AI RMF's own function
sequence (Govern → **Map** → **Measure** → **Manage**) and the actual order an AI
governance program works in:

1. **Classify** (CrossSector-1) — determine what regulatory tier a system falls into.
2. **Audit** (Legal-1) — test a real model for group-level fairness with the rigor a
   compliance review would demand.
3. **Explain** (Legal-2) — answer the individual-level question group metrics can't:
   why was this specific person's outcome what it was.
4. **Document** (CrossSector-2) — produce the paper trail that keeps a system governed,
   drawing on what the previous three established.

## Employer skills demonstrated

Cross-referenced against recurring requirements in recent AI Governance / AI Risk /
Responsible AI / Model Risk job postings, not just the MSI5004 syllabus. Built means
there's working, tested code behind the claim; Planned means it's scoped but not
built yet — listed here on purpose rather than left out, so the gap is visible
instead of implied away.

| Skill domain | Where it's demonstrated | Status |
|---|---|---|
| Regulatory mapping | CrossSector-1 maps a system description to EU AI Act articles/Annex III, a NIST RMF action per function, and a Singapore Model AI Governance Framework note; Legal-2 ties individual explanations to Article 86 | Built |
| AI risk assessment & control mapping | CrossSector-1's tier classification with cited article/category; CrossSector-2's probability × severity risk matrix (`generate.py::RISK_MATRIX`) | Built |
| Bias & fairness testing | Legal-1: demographic parity difference, equalized odds difference, disparate impact ratio, and subgroup selection/TPR/FPR, on the real ProPublica COMPAS dataset | Built |
| Explainability & transparency | Legal-2: closed-form SHAP-style per-case attribution with an exact local-accuracy guarantee, plus CrossSector-2's Model Card generation | Built |
| Model/AI evaluation | Legal-1's surrogate-fidelity check (agreement vs. COMPAS, vs. a majority-class baseline); Legal-2's 5 automated sanity checks (fidelity, local accuracy, monotonicity, flag consistency) | Built |
| Human oversight | CrossSector-2's Human Oversight Design doc (in/over/out-of-the-loop model, escalation path, contestability mechanism) | Built |
| Privacy & data governance | CrossSector-2's Data Governance Statement (PII flag, data governance measures) | Built |
| Audit & evidence readiness | CrossSector-2 generates a six-document evidence set (Model Card, Risk Assessment, Data Governance Statement, Human Oversight Design, Incident Response Runbook, Vendor AI Risk Questionnaire) from one spec file, reproducibly | Built |
| Third-party / vendor AI risk | CrossSector-2's Vendor AI Risk Questionnaire template | Built |
| Technical foundations | Python throughout; every live demo is a dependency-free static JS port verified against its Python source (CrossSector-1, Legal-1, Legal-2); automated tests in every project; reproducible via `requirements.txt` | Built |
| Stakeholder & policy translation | Each project's README states the plain-language "why this exists" case before the technical detail; the portfolio's own Classify → Audit → Explain → Document narrative | Built |
| AI governance operating model (intake, inventory, approval workflow, RACI) | CrossSector-1 + CrossSector-2 together cover classify → document; no stateful intake/approval-workflow application yet | Planned |
| Model risk / independent validation | Legal-1's fidelity numbers are validation-flavored; a formal builder-vs-validator report split, robustness/stress tests, and drift simulation are scoped, not built | Planned |
| Monitoring & observability (drift, degradation, control effectiveness) | Not built | Planned |
| Governance reporting (executive dashboard, risk heatmap) | Not built | Planned |
| Agentic AI governance (least privilege, policy-as-code, audit log) | Not built — this is the scope of the planned Safety-1 | Planned |
| GenAI security (prompt injection, jailbreaks, data leakage) | Not built — this is the scope of the planned Safety-1 | Planned |

## Roadmap

Three workstreams are scoped on top of the four built projects, in this order:

1. **Safety-1 — Governed RAG/Agent** *(new project)*. The one capability area
   nothing above touches: a small tool-calling agent or RAG demo with a
   prompt-injection test suite, a least-privilege tool allowlist, and a
   human-approval gate on a simulated high-risk action. Built first because its
   RAG/citation patterns get reused by workstream 3.
2. **Legal-1 + Legal-2 → Model Risk Validation Lab**. Add a model card, a
   robustness/stress test, a drift simulation, and a builder-vs-validator report
   split on top of the existing fairness and explainability work.
3. **CrossSector-2 → Regulatory Compliance & Evidence Copilot**. Add explicit NIST AI
   RMF / ISO 42001 mapping tables and a citation-grounded LLM layer that answers
   from a supplied regulatory corpus rather than free-generating — reusing
   workstream 1's RAG foundation.

## Sources

Every input across all four built projects is public: the EU AI Act's text, NIST's
published RMF, the ProPublica COMPAS dataset, and an open-weight Hugging Face model.
Each project's own README lists its specific sources.

## Layout

Each project folder is self-contained (its own `README.md`, `requirements.txt`, and
`LICENSE`) and can be run independently — `cd` into a folder and follow its README.
They're kept together here, under `msi5004-ai-governance-portfolio/`, because they
form one continuous narrative and share this top-level plan and progress tracker.
