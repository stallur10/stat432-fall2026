---
name: lda-qda-report
description: Guides an agent through a cross-validated LDA/QDA classification analysis and a one-page report. Use only when the user explicitly invokes it by name and supplies the dataset, response, and predictors.
disable-model-invocation: true
---

# LDA/QDA analysis report

## Behavior
Run only on explicit request. Use only the dataset, response, and predictors the user supplies; do not guess or add variables. Every classifier must be based on LDA, QDA, or a combination of them. Never use test data for any choice.

## Protocol
1. Set one random seed and report it. Apply the user's coding of categorical predictors. Check dimensions, missing values, and class counts.
2. Reserve a stratified test set (about 30%) before fitting any model. Do not touch it until step 6.
3. On the training data, create one set of stratified K-fold labels (K = 10; use 5 if the smallest class has fewer than 30 training cases). Use the same folds for every candidate.
4. Candidates, all with empirical class priors unless told otherwise:
   - ordinary LDA and ordinary QDA (required baselines);
   - probability blends w * P_QDA + (1 - w) * P_LDA over a small grid of w in (0, 1);
   - optional: PCA embedding with d components (standardize first), followed by LDA or QDA, over a grid of d up to the number of predictors.
   Drop any candidate that cannot be fitted (for example, a singular covariance matrix) and say so.
5. Cross-validate. Inside each fold, estimate all preprocessing (centering, scaling, PCA) from that fold's training part only and apply it to the validation part. Record the misclassification rate in each fold, then its mean and standard error across folds. Select the lowest mean error; if a simpler candidate (fewer parameters) is within one standard error of the best, choose the simpler one.
6. Refit the selected model and its preprocessing on all training data. Evaluate once on the test set: misclassification rate, a 95% binomial interval, and the confusion matrix with observed classes in rows.
7. Never change the model after seeing test results. Revise this skill only from training and cross-validation results.

## Report: at most one printed page
Concise, plain language, in this order:
- Title and one sentence on the data (observations, predictors, class balance, seed).
- Methods: candidate models and the cross-validation procedure, including what is estimated within each fold.
- One figure: cross-validated error (mean with standard-error bars) against each candidate's tuning setting, with the selected model marked. Label axes in words and keep fonts readable.
- One table: candidate, setting, cross-validated error, standard error.
- Numerical results: selected model and settings, cross-validated error, test error with interval, confusion matrix.
- Findings and limitations in 3 to 5 sentences. Cover the LDA/QDA covariance assumptions, sample size, that differences within one standard error are not evidence of a better model, and that one test split gives a noisy estimate.
Check that the finished report fits one printed page and trim if it does not.
