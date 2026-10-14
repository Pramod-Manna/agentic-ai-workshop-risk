# Complete the Grounding: Risks, incidents and problems

IEEE-CIS Amrita — Agentic AI + Knowledge Grounding Workshop · Dataset **RISK**

## Problem statement

141 records in 12 categories. A technology organisation's service-management and risk log: incidents, problem investigations, the risk register, changes, vendors, alerts and audits. Four pairs of categories deliberately share vocabulary. Most records stand alone; some carry an identifier or a code.

Build an agent that distinguishes a recorded connection from a plausible story. Similar language alone does not show that two records describe the same event. Your task is to decide which identifiers can safely connect records and explain the resulting answers.

## Choose one notebook

| Notebook | Graph storage | Additional setup |
| --- | --- | --- |
| [starter_RISK_no_neo4j.ipynb](starter_RISK_no_neo4j.ipynb) | Supplied Python lookup tables | LLM API key |
| [starter_RISK.ipynb](starter_RISK.ipynb) | Neo4j | LLM API key and Neo4j connection |

Both versions have the same dataset, public questions and participant tasks. Complete and submit **one** version. The records and public questions are embedded in the notebook; no separate data download is required. Follow [SETUP.md](SETUP.md) to begin in Google Colab.

## What you are given

The notebooks include embeddings and retrieval, baseline RAG, graph construction, grounded answering, and a starter registry containing the **Incident ID** pattern. The graph/table implementation is supplied.

## Your tasks

1. Configure your LLM provider in section 1 and run the starter.
2. Explore the records in sections 2 and 5. Identify strings that consistently name one entity or event (**Kind 1**) and descriptive fields reused across unrelated events (**Kind 2**).
3. Extend `PATTERNS` in section 6. Each entry needs `name`, `regex`, `kind`, `example` and `why`. Put one capture group around the identifier.
4. Explain the candidates you chose not to link on in `REJECTED_CANDIDATES`.
5. Re-run section 7 after registry edits, then run the section 9 public pack: **P1–P8** and **PP1–PP3**.
6. Complete `OUTCOMES` in section 10 for all 11 questions: `baseline_fabricated`, `grounded_correct` and a specific explanation. Read the actual answers; a graph PASS alone does not verify the LLM's wording.
7. Fill `REMAINING_FAILURE` with one specific remaining limitation.

Preserve `DATASET_ID`, the records, public questions and submission-summary format. Improve the registry rather than hardcoding answers to individual questions. Keep credentials in Colab Secrets, never in submitted cells.

## Submission

Restart the runtime and run all cells. Confirm `validate_registry()` reports no problems. Submit your completed notebook with outputs, all 11 outcomes and the remaining-failure note. Be ready to show your registry, cite record IDs and explain a result during the Day 2 checkpoint.
