---
name: svm-analysis
description: Plan, tune, evaluate, and report a support vector machine (SVM) analysis with a one-page justification. Invoke explicitly only.
disable-model-invocation: true
---

# SVM Analysis Workflow

Follow these steps in order. Keep all reasoning general; never assume a particular dataset, variable names, or results.

1. Suitability check
   * Confirm the outcome is categorical (classification) or numeric (SVR), and state which.
   * Check sample size, number of predictors, class balance, missing values, and outliers.
   * Note whether predictors are numeric or need encoding; SVMs need scaling, so standardize predictors using training data only.
   * State clearly if SVM is a poor fit (e.g., very large n, mostly noise features, severe imbalance) and what you do about it.
2. Kernel selection
   * Consider linear, radial basis (RBF), and optionally polynomial kernels.
   * Justify each with data-based evidence (separation in exploratory plots, dimensionality relative to n, expected nonlinearity).
   * Prefer the simplest kernel that performs comparably.
3. Tuning
   * Name the parameters per kernel: cost C (all), gamma (RBF/polynomial), degree (polynomial), epsilon (SVR).
   * Tune with a grid on a log scale, refined once around the best region if the optimum sits at an edge.
   * Tune inside cross-validation only; never use the test set for tuning.
4. Evaluation
   * Use repeated or stratified k-fold cross-validation (or nested CV when comparing tuned kernels) to select the final model.
   * Choose a metric matching the goal (accuracy, AUC, F1, or RMSE) and justify it, especially under imbalance.
   * Apply the one-standard-error rule or a tie-break toward simplicity when models are close.
   * If a holdout set exists, use it once, after selection, for an unbiased estimate.
5. Required exhibits (compact)
   * One figure: tuning performance across parameter values for each kernel, with error bars or bands and the chosen setting marked.
   * One table: for each kernel, the best parameters, CV metric with uncertainty, and number of support vectors.
6. Interpretation and key numbers
   * Report the final kernel, tuned parameters, CV metric (with spread), holdout metric if available, and the support vector count or fraction.
   * Interpret: a high support vector fraction suggests overlap or complexity; large gamma suggests overfitting risk; compare against a simple baseline.
   * Mention limitations and any sensitivity to scaling or class imbalance.
7. Page budget
   * The written report must fit one printed page at 11-point font, including the figure and table.
   * Prioritize: (a) suitability verdict, (b) kernel and tuning rationale, (c) the figure and table, (d) final model with key numbers, (e) one-sentence caveat.
   * Cut background, code, and exploratory detail that does not support the final model choice.
