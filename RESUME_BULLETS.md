# Resume bullets

XYZ format: accomplished **X**, measured by **Y**, by doing **Z**. Every number is read from the repo's committed results
(`results/metrics.json` and friends) or its README; the source is noted under each project.

## fraud-detection-pipeline  (https://github.com/lukefreyman-ai/fraud-detection-pipeline)
- Built an end-to-end card-fraud detection pipeline that catches 81% of fraud dollars-at-risk (81 % recall, $5,339 of $7,729) at 27 alerts per 10,000 transactions, by engineering backward-looking velocity features on 284,807 real transactions and training LightGBM against a logistic-regression baseline on a chronological split.
- Cut expected fraud-plus-review cost 8 % versus a class-weighted logistic baseline ($3,166 vs $3,457 on the held-out window) by replacing F1/AUC threshold selection with a cost matrix (missed fraud = transaction amount, false decline = $5) optimised on validation data.
- Showed that SMOTE and class weighting did not improve decisions once thresholds were cost-tuned (1.8-2.3x more alerts for equal recall), and shipped a Streamlit review queue with per-transaction SHAP explanations and a decision log for analysts.
  *Source: results/metrics.json, results/results_table.md.*

## aml-transaction-monitoring  (https://github.com/lukefreyman-ai/aml-transaction-monitoring)
- Designed a rules-based AML transaction-monitoring engine (8 scenario rules in DuckDB SQL: structuring, rapid movement, round-dollar, dormant reactivation, geographic velocity, high-risk wires, cash intensity, velocity spike) over a 518,492-row synthetic bank dataset with 190 labelled suspicious customers across 6 injected typologies.
- Raised alert precision from 53% to 83% while keeping coverage at 190/190 suspicious customers and cutting volume from 58 to 39 alerts/month, by building a false-positive analysis that tunes each rule's threshold against an analyst capacity budget and retires rules below a precision floor (velocity-spike rule: 85% false positives, disabled).
- Delivered the operational layer: alert scoring/prioritisation (rule weight x severity + KYC risk + multi-rule bonus), templated SAR-style case summaries for the top 25 cases, and a 7-table Power BI star schema with a notebook of hit rate and FP rate by rule.
  *Source: results/metrics.json, results/rule_summary_baseline.csv, results/tuning_selection.csv.*

## model-risk-monitoring  (https://github.com/lukefreyman-ai/model-risk-monitoring)
- Built a model-validation and monitoring toolkit (PSI, CSI, KS/Gini tracking, decile calibration, champion-vs-challenger, auto-generated SR 11-7-style HTML report) around a WOE/logistic credit scorecard on 150,000 Give Me Some Credit borrowers (dev KS 0.555, Gini 0.716).
- Detected and attributed a simulated population shift - score PSI 0.17 (amber) to 0.36 (red) across five monitoring windows, traced to revolving utilisation (CSI 0.40) - while showing discrimination and calibration held (KS >= 0.52, calibration gap <= 0.5 pp), and wrote the recommendation as a cut-off review rather than a rebuild.
- Quantified a gradient-boosting challenger at +2.8 Gini points with 14 % decay under drift vs 7 % for the champion, and documented why lift alone does not justify replacing an explainable scorecard; produced a first-year-analyst validation report with findings, actions and limitations.
  *Source: results/metrics.json, results/performance.csv, results/csi.csv.*

## credit-risk-scorecard  (https://github.com/lukefreyman-ai/credit-risk-scorecard)
- Developed a bank-style credit scorecard (WOE/IV binning, logistic regression, 600 @ 50:1 odds / PDO 20 point scaling) on 150,000 borrowers that achieves test AUC 0.857 (Gini 0.713) and KS 0.557 with no train/test gap, by selecting 7 characteristics with IV > 0.02 and VIF < 1.25.
- Translated model output into a business-usable score: score bands with 54 % default rate below 500 points vs under 2 % above 600, with per-bin points that map directly to adverse-action reasons.
  *Source: scorecard.ipynb outputs.*

## medicare-claims-denial-analysis  (https://github.com/lukefreyman-ai/medicare-claims-denial-analysis)
- Identified 31,693 Medicare outpatient claims (4.1 % of 779,815) with hard NCCI code-pair violations and ~$1.22 M of line-level payment exposure, by normalising 3.77 M service lines and matching 3.56 M candidate code pairs bidirectionally against 64,711 CMS procedure-to-procedure edits.
- Showed the exposure is systemic rather than provider-driven (67.5 % of 6,293 providers affected; top 10 providers only 6.4 % of violations; one lab-panel pair = 41 %), and validated the 4.1 % rate against CMS CERT's 6.55 % FY2025 improper-payment rate; documented a withdrawn hypothesis (venipuncture pair) after checking the edit file.
  *Source: README.md findings (notebook outputs).*

## complaint-triage  (https://github.com/lukefreyman-ai/complaint-triage)
- Benchmarked Claude Haiku 4.5 as a complaint router against 1,651 real CFPB consumer complaints with regulator-assigned product labels: 76.5% accuracy on a balanced 9-category sample (majority baseline 11.1%) versus a misleading 86.5% on a random sample whose majority class was 84.2%.
- Measured, rather than assumed, a prompt change: a disambiguation rule for the top confusion pair lowered accuracy to 73.7%, and kept the negative result with confusion matrices and an urgency score for human triage.
  *Source: data/results*.csv (regenerated by src/evaluate.py).*

## kalshi-edge  (https://github.com/lukefreyman-ai/kalshi-edge)
- Built a Python CLI that scans every open Kalshi prediction market (4,453 fee-adjusted opportunities across 469 series in the latest scan), ranks near-resolution and thin-spread setups, and paper-trades them inside hard risk limits ($5/market, $50 exposure, 10 % of bankroll) with settlement against real outcomes in a SQLite ledger.
- Automated the daily scan-trade-settle-export loop with launchd and a JSON-fed dashboard (bankroll curve, win rate, $ at risk, 3D market map) - 10 paper positions tracked to date.
  *Source: paper.db, README.md.*
