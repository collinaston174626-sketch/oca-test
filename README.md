# OCA — Oxford Capacity Analysis (OCA-IP)

A fully self-contained, single-page implementation of the **Oxford Capacity Analysis (OCA-IP)** — a 200-question self-report personality inventory that builds a 10-trait profile, computes reliability metrics, and generates a PDF report. The entire app runs offline in the browser; no server, build step, or dependencies.

> ⚠️ **About the test.** The OCA was created in the 1950s and is administered by the Church of Scientology as a recruitment tool. It is **not a scientifically validated psychometric instrument** and has no affiliation with the University of Oxford. This repository is a technical reimplementation of the published OCA-IP questionnaire for study/educational purposes only — it is not a diagnostic or clinical tool.

## What the test measures

Each of the 200 questions is answered **Yes / Maybe / No**. Answers are weighted by a scoring matrix and accumulated into 10 personality traits (A–J):

| Scale | Positive pole | Negative pole |
|-------|---------------|---------------|
| A | Stable | Unstable |
| B | Happy | Depressed |
| C | Composed | Nervous |
| D | Certain | Uncertain |
| E | Active | Inactive |
| F | Assertive | Inhibited |
| G | Responsible | Irresponsible |
| H | Correct Estimation | Critical |
| I | Appreciative | Lack of Accord |
| J | Communicative | Withdrawn |

## How it works

1. **Respondent metadata** — name/pseudonym, age, sex, date, and an optional note are collected. Sex is required because it selects the correct normative table.
2. **Scoring** — each answer contributes a weighted value (plus / maybe / minus) to its trait, producing a raw score per trait (A–J).
3. **Normative lookup** — raw scores are converted to a standard index (0–100) using the official OCA-IP percentile tables, which differ by demographic group: women 18+, men 18+, boys 14–18, girls 14–18.
4. **Profile zones** — each trait is classified into one of four zones: *Desirable*, *Acceptable*, *State of attention*, or *Unacceptable*.
5. **Reliability checks** — the page computes three validity indicators:
   - **Consistency index** — 12 paired "check-questions" flag contradictory answers (< 70% → questionable, < 50% → invalid).
   - **Maybe-answer count** — ≥ 35 "Maybe" answers lowers reliability due to indecisiveness.
   - **Random-answering detection** — if the profile matches the random-answer matrix on ≥ 9 of 10 traits, it is flagged invalid.
   - Overall status is reported as **Valid / Questionable / Invalid**.

## Features

- **Fully offline** — runs entirely client-side; answers and results are stored only in the browser (`localStorage`) with autosave and resume.
- **Multilingual** — Russian, English, and Romanian interfaces.
- **Question matrix** — a grid modal to jump to any question and review answered/skipped/current items.
- **Keyboard support** — `1`/`2`/`3` to answer Yes/Maybe/No, arrow keys to navigate.
- **Visual profile** — a canvas profile chart plus a summary table (raw score, standard index, zone).
- **Exports** — downloadable PDF report, JSON, and CSV.
- **Responsive & print-friendly** — works on mobile and desktop.

## Usage

Open `index.html` directly in any modern browser. No installation, server, or build tools are required.

## License & exclusive rights

© 2026. **All Rights Reserved.**

All exclusive rights to this product belong to the copyright holder. Any use, copying, modification, distribution, sublicensing, sale, or embedding of the code into other products — whether in source or compiled form — is strictly prohibited without the prior written consent of the author.

For the full terms, see the [LICENSE](./LICENSE) file.
