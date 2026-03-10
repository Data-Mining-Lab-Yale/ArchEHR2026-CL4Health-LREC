# Subtask 4: Evidence Alignment

**Part of [ArchEHR2026-CL4Health](../README.md)** — see the root README for overview, team, citation, and links to other subtasks.

Pipeline for **Subtask 4**: map each clinician answer sentence to the note sentence IDs that directly support it. Evaluation: micro F1 over (answer_id, evidence_id) pairs.

## Leaderboard (Codabench)

**Top 5** — 3rd out of 141 submissions.

## Pipeline overview

The system uses a **system** message plus interleaved **user**/**assistant** few-shot (up to 20 dev cases, leave-one-out). The prompt includes the patient question, clinician question, full note (numbered sentences), all answer sentences (numbered), and the full clinician answer paragraph without citations for context. The model returns a JSON array of `{answer_id, evidence_id: [ids]}`. Ensemble (o3, GPT-5.2, GPT-5.1, optional DeepSeek-R1) with self-consistency voting; links are kept when vote count ≥ θ. The threshold θ is swept on dev and written to `best_vote_threshold.txt`. Optional embedding recall adds high-similarity (answer, note) pairs after voting.

**Reported results:** Best dev **88.81** micro F1 (ensemble + rescue heuristics). Test **80.41** micro F1.


---

## Layout

Place this code as the **task4** directory or ensure data lives under `v1.5/v1.5/` relative to the script:

```
task4_release/
├── pipeline_subtask4_alignment.py
├── score_submission.py
├── submission/
├── requirements.txt
├── README.md
└── v1.5/v1.5/         
```

**Run from the directory containing the pipeline** (or set working directory accordingly):

```bash
pip install -r requirements.txt
python pipeline_subtask4_alignment.py dev
```

Output: `submission/submission_dev.json`. For full test (21–167): `python pipeline_subtask4_alignment.py test-all`.

---

## Environment variables

Set in a `.env` file in the parent directory (or same directory as the script). Required: `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_KEY`. Optional: `TASK4_ENSEMBLE_DEPLOYMENTS` (default `o3,gpt-5.2,gpt-5.1,deepseek-r1`), `TASK4_FEW_SHOT_N` (default 10), `TASK4_VOTE_THRESHOLD` (0 = use dev sweep), `TASK4_EMBEDDING_RECALL` (1/0), `AZURE_DEEPSEEK_R1_*` for DeepSeek-R1.

---

## Scoring

To compute micro/macro precision, recall, and F1 against a dev key:

```bash
python score_submission.py --submission submission/submission_dev.json [--key path/to/archehr-qa_key.json] [--out scores.json]
```

---

