# Linear Regression Final Assessment Notebook Template Spec

Create one `.ipynb` notebook for the assigned dataset.

The notebook must be a student-facing final assessment template, not a solved notebook.

Requirements:

- Use Markdown cells for all instructions.
- Code cells must be empty.
- Do not use `TODO`.
- Do not include executed outputs.
- Every code cell must have `execution_count: null` and `outputs: []`.
- Keep the notebook concise and simple.
- Focus only on Linear Regression.
- Do not include Decision Tree, GridSearchCV, hyperparameter tuning, or long residual analysis.
- Use Indonesian language.
- Keep dataset-specific target and notes visible in the introduction.

Recommended notebook cells:

1. Markdown: title, dataset name, recommended target, problem type, and model.
2. Markdown: assessment objective and short rules.
3. Markdown: student identity section.
4. Markdown: dataset description section.
5. Empty code cell.
6. Markdown: import required libraries.
7. Empty code cell.
8. Markdown: load dataset.
9. Empty code cell.
10. Markdown: data understanding: shape, head, info, describe.
11. Empty code cell.
12. Markdown: short EDA: missing values, duplicates, target distribution, 1-2 relevant visualizations.
13. Empty code cell.
14. Markdown: data preparation: handle missing values, remove/keep duplicate with explanation, encode categorical columns, select usable features.
15. Empty code cell.
16. Markdown: split feature and target.
17. Empty code cell.
18. Markdown: train-test split.
19. Empty code cell.
20. Markdown: feature scaling. Fit scaler on train only, transform train and test.
21. Empty code cell.
22. Markdown: train Linear Regression model.
23. Empty code cell.
24. Markdown: evaluate with MAE, RMSE, and R2 Score.
25. Empty code cell.
26. Markdown: simple coefficient interpretation.
27. Empty code cell.
28. Markdown: final conclusion questions.

Final conclusion prompts:

- Dataset ini berisi data tentang apa?
- Kolom apa yang dijadikan target dan kenapa?
- Bagaimana performa model berdasarkan MAE, RMSE, dan R2?
- Fitur apa yang terlihat berpengaruh terhadap prediksi?
- Apa keterbatasan analisis atau model yang dibuat?
