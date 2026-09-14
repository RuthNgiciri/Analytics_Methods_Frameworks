# NovaBank: Predictive Retention at Scale

Analytics Methods & Frameworks Project (Quantic MSBA) — a predictive framework for prioritizing proactive customer retention outreach.

## Overview

NovaBank's retention team currently reacts to churn instead of preventing it. This project builds a model to score customers by their likelihood of responding positively to proactive outreach, then translates that score into a capacity-constrained targeting rule — who to contact, how confident to be, and what the cost/fairness trade-offs are.

**Note on the data:** the provided dataset is a bank marketing-response file, not a literal churn log. `y = 1` (accepted an offer) is used as a documented proxy for "retainable / responsive to outreach" — this assumption is stated explicitly in the notebook rather than presented as verified churn history.

## Project Structure

```
Analytics_Methods_Frameworks/
├── data/           DataSet.csv (raw input data)
├── notebooks/      Analytics_Methods_Frameworks_Project.ipynb (main analysis)
├── outputs/        exported charts/figures
├── models/         (reserved for saved model artifacts)
├── docs/           executive memo, slide appendix
├── requirements.txt
└── README.md
```

## Setup & Reproduction

```bash
# from the project root
python -m venv .venv
.venv\Scripts\activate        # Windows
# source .venv/bin/activate   # Mac/Linux

pip install -r requirements.txt
```

Open `notebooks/Analytics_Methods_Frameworks_Project.ipynb` in VS Code (or Jupyter), select the `.venv` kernel, and **Run All**. The notebook runs top to bottom with no manual steps, using `data/DataSet.csv` as input.

## Methods

- **Baseline model:** Logistic Regression (class-balanced)
- **Improved model:** Gradient Boosting Classifier
- Call `duration` is excluded from all models as a leakage feature (only known after contact, not before)
- Decision threshold chosen via cost-based analysis under a retention-team capacity constraint
- Includes a fairness check across age/job segments and a macro-scenario sensitivity test

## Deliverables

- **Executive memo:** `docs/NovaBank_Executive_Memo.docx`
- **Slide appendix:** `docs/NovaBank_Slide_Appendix.pptx`
- **Notebook (this repo):** `notebooks/Analytics_Methods_Frameworks_Project.ipynb`

## AI Usage

This project was developed with assistance from Claude (Anthropic) as a coding/analysis copilot. A full breakdown of what AI contributed at each stage is documented in the closing section of the notebook and the final slide of the appendix.
