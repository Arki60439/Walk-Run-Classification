# Walk-Run-Classification
Creating a Predictive model to predict whether a person is running or walking based on given variables from the perspective of a smartwatch.
## Introduction
The Walk/Run dataset presents several practical challenges ranging from non-predictive identifier columns to an inherently non-linear classification boundary invisible to linear models. This report documents each challenge encountered during the project, the technique selected to address it, and the full reasoning behind every decision.
## Dataset Attributes
| Attribute | Value |
| --- | --- |
|Total rows|88,588|
Total columns	11
Numeric features	7 (used in modeling)
Categorical/ID features	3 (date, time, username — dropped)
Target	activity — binary (0=Walk, 1=Run)
Class balance	49.9% Walk / 50.1% Run — perfectly balanced
Missing values	0 — dataset is complete
Participants	1 (viktor) — single-participant study
Wrist sensors	2 (left=0, right=1)
