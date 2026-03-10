# Subtask 2: Evidence Identification

**Part of [ArchEHR2026-CL4Health](../README.md)** — see the root README for overview, team, citation, and links to other subtasks.

Pipeline for **Subtask 2**: identify evidence (e.g. sentences) supporting fact-sheet answers from the EHR.

- **Input:** Patient question, clinician question, EHR context.
- **Output:** Identified evidence (e.g. sentence IDs or spans).

## Leaderboard (Codabench)

**Top 5** — 4th out of 106 submissions. [Leaderboard](https://www.codabench.org/competitions/13526/#/results-tab).

| Metric | Score |
|--------|-------|
| **Overall (Strict Micro F1)** | **61.9** |
| Strict Micro Precision | 52.3 |
| Strict Micro Recall | 75.7 |
| Lenient Micro Precision | 68.0 |
| Lenient Micro Recall | 75.7 |
| Lenient Micro F1 | 71.6 |
| Strict Macro Precision | 56.7 |
| Strict Macro Recall | 75.5 |
| Strict Macro F1 | 61.1 |
| Lenient Macro Precision | 73.8 |
| Lenient Macro Recall | 75.5 |
| Lenient Macro F1 | 70.4 |

## Setup

1. **Clone and install**
   ```bash
   pip install -r requirements.txt
   ```
2. Add API keys or config as needed (e.g. `.env`).

## Data

Dev/test data are not included (access via [PhysioNet](https://physionet.org/) per the [ArchEHR-QA 2026](https://archehr-qa.github.io/) instructions). Place your data in the paths expected by the scripts or adjust paths in the code.

## License

MIT License. See [LICENSE](LICENSE). Dataset terms apply via PhysioNet per ArchEHR-QA 2026.
