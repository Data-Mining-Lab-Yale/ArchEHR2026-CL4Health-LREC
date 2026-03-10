# ArchEHR-QA 2026 — Data Mining Lab @ Yale

**Official submission repository** for the [ArchEHR-QA 2026](https://archehr-qa.github.io/) shared task (CL4Health @ LREC-COLING 2026). We participated in all four subtasks and placed in the **top 5** on **3 out of 4** official leaderboards. Only THREE teams achieved top 5 on three subtasks; no team placed in the top 5 on all four subtasks.

---

## Team

| | |
|---|---|
| **Lab** | [Data Mining Lab @ Yale](https://github.com/Data-Mining-Lab-Yale) |
| **Participants** | [Elyas Irankhah](https://github.com/Elyasirankhah), Samah Fodeh |
| **Competition** | [CL4Health @ LREC 2026](https://archehr-qa.github.io/) — ArchEHR-QA (patient-authored questions over EHR) |

---

## Subtasks & Results

| Subtask | Task | Place | Main metric | Folder |
|--------|------|-------|-------------|--------|
| **1** | Question interpretation (patient → clinician question, ≤15 words) | **Top 5** (5th / 84) | Overall 27.1 (ROUGELsum, BERTScore, AlignScore, MEDCON) | [ArchEHR-QA-2026-Subtask1-main](ArchEHR-QA-2026-Subtask1-main) |
| **2** | Evidence identification (sentences supporting fact-sheet answers) | **Top 5** (4th / 106) | Strict Micro F1 **61.9** | [ArchEHR-QA-2026-Subtask2-main](ArchEHR-QA-2026-Subtask2-main) |
| **3** | Answer generation (≤75 words, grounded in note) | **Top 5** | Dev 34.01 (BLEU, ROUGE, SARI, BERTScore); Test 30.95 | [ArchEHR-QA-2026-Subtask3-main](ArchEHR-QA-2026-Subtask3-main) |
| **4** | Evidence alignment (answer sentence → note sentence IDs) | **Top 5** (3rd / 141) | Micro F1 **80.41** (test) | [ArchEHR-QA-2026-Subtask4-main](ArchEHR-QA-2026-Subtask4-main) |

Leaderboards: [Subtask 1](https://www.codabench.org/competitions/12865/#/results-tab) · [Subtask 2](https://www.codabench.org/competitions/13526/#/results-tab).

---

## Repository structure

```
ArchEHR2026-CL4Health/
├── README.md                          ← you are here
├── .gitignore
├── ArchEHR-QA-2026-Subtask1-main/     # Question interpretation
│   ├── pipeline.py
│   ├── run_leaderboard_submission.py
│   ├── build_codabench_subtask1_submission.py
│   └── requirements.txt
├── ArchEHR-QA-2026-Subtask2-main/     # Evidence identification
│   ├── pipeline_subtask2_evidence.py
│   └── requirements.txt
├── ArchEHR-QA-2026-Subtask3-main/     # Answer generation
│   ├── pipeline_subtask3_answer.py
│   ├── run_approaches.py
│   ├── score_minimal.py
│   └── requirements.txt
└── ArchEHR-QA-2026-Subtask4-main/     # Evidence alignment
    ├── pipeline_subtask4_alignment.py
    ├── score_submission.py
    └── requirements.txt
```

Each subtask folder has its own **README**, **requirements**, and (where present) **LICENSE**. Use the instructions in the subfolder READMEs to run or reproduce that subtask.

---

## Quick start

1. **Clone**
   ```bash
   git clone https://github.com/Data-Mining-Lab-Yale/ArchEHR2026-CL4Health.git
   cd ArchEHR2026-CL4Health
   ```

2. **Data**  
   Dev/test data are **not** included. Obtain them via [PhysioNet](https://physionet.org/) per [ArchEHR-QA 2026](https://archehr-qa.github.io/) instructions. Place XML/JSON in the paths expected by each pipeline (see subtask READMEs).

3. **Environment**  
   - **Subtask 1:** `.env` with `OPENAI_API_KEY`, `ANTHROPIC_API_KEY` (in Subtask1 folder or repo root).  
   - **Subtasks 2–4:** `.env` with `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_KEY`; optional deployment and task-specific variables (see each subtask README).  
   Do **not** commit `.env`.

4. **Run a subtask**  
   From the repo root, install and run as described in that subtask’s README, for example:
   ```bash
   pip install -r ArchEHR-QA-2026-Subtask1-main/requirements.txt
   cd ArchEHR-QA-2026-Subtask1-main && python pipeline.py
   ```

---

## Citation

If you use this repository or build on our ArchEHR-QA 2026 submission, please cite our paper:

**Elyas Irankhah, Samah Fodeh.** *Yale-DM-Lab at ArchEHR-QA 2026: Deterministic Grounding and Multi-Pass Evidence Alignment for EHR Question Answering.* CL4Health @ LREC-COLING 2026.

**BibTeX:**

```bibtex
@inproceedings{irankhah-fodeh-2026-yale-dm-lab-archehr,
  title     = {Yale-DM-Lab at ArchEHR-QA 2026: Deterministic Grounding and Multi-Pass Evidence Alignment for EHR Question Answering},
  author    = {Irankhah, Elyas and Fodeh, Samah},
  booktitle = {Proceedings of the Workshop on Computational Linguistics for Health (CL4Health) at LREC-COLING 2026},
  year      = {2026},
  address   = {Yale University, Department of Emergency Medicine, New Haven, CT, USA},
  url       = {https://github.com/Data-Mining-Lab-Yale/ArchEHR2026-CL4Health}
}
```

---

## License

Individual subtask folders may contain a **LICENSE** file (e.g. MIT). Dataset use is governed by PhysioNet and ArchEHR-QA 2026 terms.

---

## References

- **ArchEHR-QA 2026:** [archehr-qa.github.io](https://archehr-qa.github.io/)
- **CL4Health @ LREC-COLING 2026**
- **Data:** [PhysioNet](https://physionet.org/) (subject to their access and DUA)

