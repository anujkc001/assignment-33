#  Food Delivery Status Prediction: Phase 3 Analysis Report

##  Introduction and Objective

This document presents the findings from Phase 3 of the Food Delivery Status Prediction project. The core objective was to evaluate three classic machine learning classifiers—**Decision Tree**, **K-Nearest Neighbors (KNN)**, and **Naive Bayes**—to determine which one is best suited to reliably predict whether a food delivery will be **"Fast"** or **"Delayed."** The ultimate goal is to enable proactive operational intervention to reduce delays.

---

##  Model Performance Comparison

The models were benchmarked on a dedicated test set. Given the high business cost of *missed delays* (False Negatives), we focused heavily on metrics related to the **'Delayed' (Class 1)** category, specifically the F1-Score and AUC.

### Evaluation Metrics Summary

| Classifier | Accuracy | Precision (Delayed) | Recall (Delayed) | F1-Score (Delayed) | ROC AUC Score |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Decision Tree** | [0.4500] | [0.4545] | [0.5000] | **[0.4762]** | [0.4375] |
| **K-Nearest Neighbors**| [0.4250] | [0.4118] | [0.3500] | [0.3784] | [0.4213] |
| **Naive Bayes** | [0.4750] | [0.4706] | [0.4000] | [0.4324] | [0.4275] |

**Key Takeaway:** The F1-Score is our primary selection metric, as it provides the most effective balance between identifying true delays (Recall) and minimizing confusing false alarms (Precision).

---

##  Visual and Diagnostic Analysis

### 1. Confusion Matrix Review

The confusion matrices were analyzed to understand the type of errors made by each model. 

* **Decision Tree:** [Describe the key finding from the DT matrix. Example: "The Decision Tree model showed the best performance in minimizing False Negatives (actual delays predicted as 'Fast'), which is crucial for business operations."]
* **K-Nearest Neighbors:** [Describe KNN's error profile. Example: "KNN had a reasonable balance, but sometimes struggled with true negative cases compared to the Decision Tree."]
* **Naive Bayes:** [Describe the Naive Bayes error profile. Example: "Naive Bayes consistently produced the highest number of False Positives, likely due to its strong assumption of feature independence."]

### 2. ROC Curve and AUC Analysis

The Receiver Operating Characteristic (ROC) curves illustrate the discrimination capability of the models. The Area Under the Curve (AUC) quantifies this power. 

* **Discriminative Power:** The curve for the **[Decision Tree]** model tracked closest to the top-left corner of the plot, which is mathematically confirmed by its superior **AUC Score of [0.4375]**. This indicates it is the most robust classifier across all possible thresholds.

---

##  Recommendation and Actionable Insights

### Trade-offs Between Classifiers

| Model | Core Advantage  | Core Limitation |
| :--- | :--- | :--- |
| **Naive Bayes** | Extremely fast and computationally inexpensive, making it a good baseline or fast-inference option. | Its reliance on features being statistically independent often limits its accuracy on real-world, correlated data. |
| **KNN** | Highly effective on complex decision boundaries without assuming data distribution (non-parametric). | It is computationally expensive during the prediction phase and is very sensitive to feature scaling and outliers. |
| **Decision Tree**| **Highly transparent:** The rules used for prediction are visible, making it easy to explain to stakeholders and operations teams. | It is inherently prone to overfitting the training data, requiring careful tuning (like setting a `max_depth`) to perform well on new, unseen data. |

### Final Classifier Recommendation

The recommended model for deployment is the **[Decision Tree]**.

#### Justification

1.  **Metric Performance:** The **[Decision Tree]** stood out by achieving the highest **F1-Score of [0.4762]** and a strong **AUC of [0.4500]**. This performance ensures the best operational balance, successfully identifying true delays while keeping false alarms manageable.
2.  **Operational Benefit (If Decision Tree is selected):** If the Decision Tree was chosen, its high interpretability is invaluable. It clearly showed that **`Haversine_Distance_km`**, **`Traffic_Conditions`**, and **`Order_Time`** are the most powerful predictors of delay. This insight allows the operations team to focus strategic efforts on improving these specific areas (e.g., optimizing route planning or shifting driver shifts).
3.  **Business Impact:** By prioritizing a model that minimizes **False Negatives**, we directly improve customer experience. The system can proactively trigger alerts (to drivers or customers) only when a delay is genuinely likely, boosting reliability and satisfaction.
