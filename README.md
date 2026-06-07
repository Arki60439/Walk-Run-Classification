# Walk-Run-Classification
Creating a Predictive model to predict whether a person is running or walking based on given variables from the perspective of a smartwatch.
## Introduction
The Walk/Run dataset presents several practical challenges ranging from non-predictive identifier columns to an inherently non-linear classification boundary invisible to linear models. This report documents each challenge encountered during the project, the technique selected to address it, and the full reasoning behind every decision.
## Dataset Attributes
| Attribute | Value |
| --- | --- |
|Total rows|88,588|
|Total columns|11|
|Numeric features|7 (used in modeling)|
|Categorical/ID features|3 (date, time, username — dropped)|
|Target|activity — binary (0=Walk, 1=Run)|
|Class balance|49.9% Walk / 50.1% Run — perfectly balanced|
|Missing values|0 — dataset is complete|
|Participants|1 (viktor) — single-participant study|
|Wrist sensors|2 (left=0, right=1)|
## Challenges
|#|Challenge Category|Technique|Outcome|
|---|---|---|---|
|1|	date, time, username carry no signal|	Data Leakage|	Drop before modeling|	Zero leakage; no memorisation|
|2|	Different feature magnitude scales|	Preprocessing|	StandardScaler on all features|	Correct distance/regularization calc|
|3|	Non-linear decision boundary|	Model Selection|Tree + kernel models selected	|Accuracy 99%+ vs 86% for linear|
|4|	Single participant only|	Data Limitation	|Documented as generalisation caveat|	Honest scope statement in report|
|5|	Logistic Regression only 86.4% acc|	Model Failure|	Retained as baseline comparator|	Confirms non-linearity of problem|
|6|	KNN vs Random Forest near-identical|Model Selection|	RF selected (AUC + feature import.)|	RF chosen for AUC + interpretability|
|7|	SVM slow on 70K samples|	Performance|	RBF kernel; probability=True|	Correct AUC-ROC; acceptable speed|
## Lessons Learnt
•	Always drop identifier columns (date, time, user IDs) before modeling — they cause memorization, not learning. <br>
•	Apply StandardScaler before any distance-sensitive model (KNN, SVM) or regularized linear model — unscaled features produce misleading results. <br>
•	Use the correlation heatmap as a quick linearity check before selecting model families — weak correlations signal non-linear boundaries. <br>
•	When two models have near-identical accuracy, use AUC-ROC, inference speed, and interpretability as tiebreakers. <br>
•	Document single-participant datasets as a generalisation caveat — a 99% accuracy claim only holds for the measured individual without multi-participant validation. <br>
•	Retaining failing baselines (Logistic Regression) in the comparison table adds scientific value — it quantifies how much non-linearity costs, and proves the stronger models are genuinely better, not just lucky. <br>
