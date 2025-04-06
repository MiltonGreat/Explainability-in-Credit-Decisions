# Credit Risk Model Bias Audit with SHAP & LIME

![screenshot-localhost_8888-2025 04 03-13_05_34](https://github.com/user-attachments/assets/0e837e6f-bb5a-42e4-a914-796ab6cc18f4)

### Project Overview

This project audits a credit risk prediction model for potential biases using SHAP (SHapley Additive exPlanations) and LIME (Local Interpretable Model-agnostic Explanations). The goal is to ensure fairness and transparency in automated credit decisions by identifying features that disproportionately impact protected groups (e.g., gender, education, marital status).

### Dataset

**Features**:
- Financial (e.g., AMT_INCOME_TOTAL, AMT_CREDIT)
- Demographic (e.g., CODE_GENDER, NAME_EDUCATION_TYPE)
- External credit scores (e.g., EXT_SOURCE_3)
- Target: TARGET (1 = default, 0 = non-default)

### Methodology

1. Bias Detection
- SHAP: Quantifies global feature importance and bias via:
- Summary plots
- Dependency plots for protected attributes
- Kolmogorov-Smirnov tests for distributional differences
- LIME: Explains individual predictions to identify localized bias.

2. Fairness Metrics
- Disparate Impact Ratio: Approval rate gaps between groups.
- Statistical Parity: Difference in positive prediction rates.

3. Mitigation Strategies
- Preprocessing (remove proxy features)
- Model adjustments (reweighting, fairness constraints)
- Post-processing (threshold optimization)

### Key Findings

**Model Performance**:
- Recall = 62% (good at catching defaults)
- Precision = 17% (high false positives)
- ROC AUC = 0.745 (moderate discrimination power)

**Bias Indicators**:
- EXT_SOURCE_3 overly influenced rejections.
- ORGANIZATION_TYPE correlated with socioeconomic status.
- Gender (CODE_GENDER) had minimal direct impact but indirect effects via proxies.

**Fairness Violations**:
- Disparate impact ratio < 0.8 for some education levels.

### Recommendations

1. Immediate Actions:
- Increase decision thresholds to reduce false positives.
- Remove proxy features (e.g., zip codes).

2. Long-Term Solutions:
- Implement fairlearn for fairness-aware modeling.
- Deploy ongoing bias monitoring with SHAP/LIME.

3. Compliance:
- Document audit results for regulatory reviews (e.g., EU AI Act).

### Conclusion

This project demonstrated how explainability tools can uncover hidden biases in credit models, even when protected attributes are not directly influential. While the model achieves its primary goal (identifying defaults), its fairness-cost trade-off requires refinement.

### Source

[Home Credit Default Risk Dataset from Kaggle](https://www.kaggle.com/datasets/anggundwilestari/home-credit)


