# wids-datathoners
ml for adhd prediction among women

# Overview
Neuropsychiatric disorders that occur in development, like anxiety, depression, autism, and attention deficit hyperactivity disorder, or ADHD, often differ in how and to what extent they affect males and females. ADHD occurs in about 11% of adolescents, with around 14% of boys and 8% of girls having a diagnosis. There is some evidence that girls with ADHD can often go undiagnosed, as they tend to have more inattentive symptoms which are harder to detect. Girls with ADHD who are undiagnosed will continue suffering with symptoms that burden their mental health and capacity to function.

# Execution Process

1. Initial Data Exploration
- **Data Profiling**: 
  - Inspect the dataset for missing values, outliers, and distribution of target variables (ADHD_Outcome and Sex_F).
  - Look for potential imbalances in the dataset, especially in female ADHD cases, since they are weighted higher in evaluation.
- **Visualize Correlations**: 
  - Create heatmaps or pair plots to understand correlations between features and targets.

2. Data Preprocessing
- **Missing Value Handling**: Use appropriate imputation techniques (mean/mode for continuous variables, categorical encoding for socio-demographic variables).
- **Scaling and Normalization**: Standardize numerical features, especially brain imaging data, to improve model performance.
- **Dimensionality Reduction**: If brain imaging data has high dimensionality, consider techniques like PCA or autoencoders.

3. Feature Engineering
- Combine socio-demographic features with brain imaging data.
- Generate interaction terms if they seem relevant.
- Explore domain knowledge for meaningful feature combinations (e.g., specific brain regions linked to ADHD).

4. Model Development
- Start with simple models like Logistic Regression or Random Forest for baseline performance.
- Progress to more complex models like:
  - **Gradient Boosting Models**: XGBoost, LightGBM, or CatBoost.
  - **Neural Networks**: A multi-task learning approach using shared layers for both outcomes.
- Use **stratified k-fold cross-validation** to ensure balanced representation of target classes during training.
- Apply **class weighting** or **oversampling** techniques for underrepresented female ADHD cases.

5. Evaluation and Optimization
- Use the weighted **F1 Score** as the primary metric.
- Focus on improving recall for female ADHD cases, as precision and recall are equally critical.
- Hyperparameter tuning can be done using GridSearchCV or Optuna.
  
6. Model Explainability
- Use SHAP or LIME to explain feature importance.
- Investigate which features contribute most to ADHD diagnosis and whether they differ by sex.

7. Submission Preparation
- Ensure predictions are in the required format: `participant_id, ADHD_Outcome, Sex_F`.
- Generate probability scores for each prediction to meet the requirement of real-valued outputs.
- Test submission files with small batches before full submission.

8. Iteration and Reporting
- Continuously iterate based on leaderboard feedback.
- Keep a shared log of experiments and model versions to track improvements.
- Document key findings to support your final model choice.

9. Final Presentation
Since this competition is also about uncovering gender inequities, prepare a final report or presentation detailing:
- Insights about gender differences in ADHD diagnosis.
- The models and techniques used.
- Key learnings and next steps.
