# Luke Freyman - risk & fraud analytics portfolio

M.S. FinTech candidate targeting Summer 2027 analyst internships in Corporate Risk, Fraud, Model Risk and Data/BI.
Seven runnable projects - every number in every README is produced by the code in that repo.
GitHub: https://github.com/lukefreyman-ai · LinkedIn: https://linkedin.com/in/luke-freyman-a22ab7249

| project | one line | headline numbers | stack |
|---|---|---|---|
| [fraud-detection-pipeline](https://github.com/lukefreyman-ai/fraud-detection-pipeline) | Card-fraud model with cost-tuned thresholds, velocity features, SHAP and an analyst review app | 81% recall at 27 alerts/10k txns; PR-AUC 0.79; cost $3,166 vs $3,457 baseline | Python, LightGBM, scikit-learn, SHAP, Streamlit |
| [aml-transaction-monitoring](https://github.com/lukefreyman-ai/aml-transaction-monitoring) | Rules-based AML monitoring engine on labelled synthetic data with FP analysis and threshold tuning | 518,492 txns, 8 SQL rules; precision 53% -> 83% at 39 alerts/month | Python, DuckDB SQL, Power BI star schema |
| [model-risk-monitoring](https://github.com/lukefreyman-ai/model-risk-monitoring) | SR 11-7-style validation & monitoring toolkit around a credit scorecard | PSI 0.36 red / CSI util 0.40 detected; KS 0.52 held; HTML + analyst report | Python, statsmodels, scikit-learn, Jinja2 |
| [credit-risk-scorecard](https://github.com/lukefreyman-ai/credit-risk-scorecard) | WOE/IV logistic scorecard on Give Me Some Credit | AUC 0.857, Gini 0.713, KS 0.557; 600 @ 50:1, PDO 20 | Python, pandas, statsmodels |
| [medicare-claims-denial-analysis](https://github.com/lukefreyman-ai/medicare-claims-denial-analysis) | NCCI edit engine over 780k Medicare outpatient claims | 4.1 % of claims violate hard edits; ~$1.22 M exposure; 41 % from one code pair | Python, pandas, CMS DE-SynPUF + NCCI |
| [complaint-triage](https://github.com/lukefreyman-ai/complaint-triage) | LLM complaint classifier benchmarked on CFPB-labelled complaints | 76.5% on a balanced 9-class set (baseline 11%); negative prompt result kept | Python, Anthropic API (Haiku 4.5), Streamlit |
| [kalshi-edge](https://github.com/lukefreyman-ai/kalshi-edge) | Prediction-market scanner + paper ledger with risk limits and a dashboard | 4,453 opportunities/scan; fee-adjusted; $5/$50/10 % limits | Python, SQLite, Three.js dashboard |

## What ties them together

- **Decisions, not just metrics.** Thresholds are chosen from a cost matrix (fraud), an analyst budget (AML) or a
  RAG policy (model risk) - and each README says what the number means for the team that has to act on it.
- **Honest evaluation.** Chronological splits, majority-class baselines, withdrawn hypotheses and negative results are
  reported, not hidden. Limitations sections are written to be said out loud in an interview.
- **Reproducible from a clean clone.** `make setup && make run` (or `python run.py`) regenerates every result; each
  repo has tests, type hints and docstrings; results files are committed so the README numbers are traceable.

## Suggested resume header line

*Risk & fraud analytics: fraud modelling (LightGBM/SHAP), AML transaction monitoring (SQL rules, FP tuning), model
validation (PSI/CSI/KS, SR 11-7 reporting), credit scorecards (WOE/IV), claims payment integrity, LLM evaluation.*

## Interview prep

Each repo contains an `INTERVIEW_GUIDE.md` (what it does in three sentences, why each decision, what I'd change,
five likely questions with honest answers, numbers to know) and this folder holds `RESUME_BULLETS.md`.
