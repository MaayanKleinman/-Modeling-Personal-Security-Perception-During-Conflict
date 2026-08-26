# Modeling Personal Security Perception Based on Public Sentiment and Casualty Data

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Machine Learning](https://img.shields.io/badge/Domain-Machine%20Learning%20%2F%20Regression-green.svg)]()
[![Dataset](https://img.shields.io/badge/Data-INSS%20%26%20IDF%20Public%20Data-orange.svg)]()

A supervised machine learning study evaluating whether public perception of personal security during wartime can be predicted using sentiment-based public survey metrics and contextual casualty data.

📄 **[Read the Full Research Report (PDF)](./Modeling_Personal_Security_Perception_Report.pdf)**

---

## 📌 Research Overview & Motivation
During prolonged national crises, public emotional resilience and perceived personal safety fluctuate continuously. Understanding the key driving factors behind these shifts is critical for sociologists, policymakers, and crisis management frameworks.

This study explores whether supervised regression models can capture and forecast changes in perceived personal security based on a combination of:
1. **Public Sentiment Indices** (National surveys).
2. **Contextual Severity Factors** (Weekly military casualty metrics).
3. **Temporal Exposure** (Duration elapsed since crisis onset).

---

## 📊 Dataset & Feature Engineering

The dataset consolidates monthly national public opinion surveys conducted by the **Institute for National Security Studies (INSS)** (Feb 2024 – Mar 2025) alongside official **IDF casualty data**:

- **Target Variable ($Y$):** The proportion of respondents reporting a "High" or "Very High" level of personal security.
- **Predictive Feature Set ($X$, 7 features per observation):**
  - **Trust in the IDF** (Proportion of positive responses)
  - **Belief in victory in Gaza**
  - **Perceived societal solidarity**
  - **Level of social concern**
  - **Optimism regarding national recovery**
  - **Weekly Military Fatalities** (Preceding each survey date)
  - **Time Elapsed** (Months since October 2023)

*All features were standardized and evaluated using a 70/30 train-test split with fixed random seeds for full reproducibility.*

---

## 🤖 Models & Methodological Framework

Given the challenges inherent to low-sample datasets ($n=14$), we implemented and contrasted two distinct regression paradigms:

1. **Ridge Regression ($L_2$ Regularization):**
   - Implemented as a regularized linear baseline to mitigate multicollinearity and prevent extreme overfitting across small sample sizes.
2. **Gaussian Process Regression (GPR):**
   - Implemented with non-linear kernels to capture complex inter-feature dynamics and quantify predictive uncertainty.

---

## 📈 Key Findings & Insights

| Model | Test MSE | Test $R^2$ | Behavior |
| :--- | :---: | :---: | :--- |
| **Ridge Regression** | **0.000593** | **-0.225** | Lower variance, more symmetric residual distribution, closer tracking of true trends. |
| **Gaussian Process Regression (GPR)** | 0.000956 | -0.973 | Overfitted to small sample size; exhibited wider and erratic error spreads. |

* **Small-Data Constraints in Supervised Learning:** Complex and highly flexible models (such as GPR or Neural Networks) suffer severe overfitting when training sample volume is constrained ($n=14$), whereas simpler regularized linear models (Ridge) deliver significantly better generalization and stability.
* **Feature Signals:** Contextual and attitudinal features carry detectable directional signals, demonstrating the feasibility of regularized regression for tracking public sentiment trends over time.

---

## 🔮 Future Directions
- Expanding sample frequency to weekly/bi-weekly intervals to support non-linear architectures (e.g., Support Vector Regression with RBF kernel, ElasticNet).
- Incorporating broader media sentiment and economic indices to enrich the feature space.

---

## 👥 Authors
- **Reut Berkowitz** & **Maayan Kleinman**
- **Department of Biomedical Engineering**, Faculty of Engineering Sciences, Ben-Gurion University of the Negev
- **Data Sources:** Institute for National Security Studies (INSS), Official IDF Casualty Records
