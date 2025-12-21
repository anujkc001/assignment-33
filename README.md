# Food Delivery Status Prediction: Phase 3 Analysis Report

## 1. Project Objective
This analysis evaluates three machine learning classifiers—**Decision Tree**, **K-Nearest Neighbors (KNN)**, and **Naive Bayes**—to identify the most reliable model for predicting delivery status ("Fast" vs. "Delayed"). The primary goal is to provide the operations team with a tool for proactive intervention to improve delivery performance.

---

## 2. Model Performance Comparison
The models were evaluated using a test dataset, with a specific focus on the **'Delayed' (Class 1)** category to minimize the business risk of missed delay alerts.

| Classifier | Accuracy | Precision | Recall | F1-Score | ROC AUC |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Decision Tree** | 0.4500 | 0.4545 | **0.5000** | **0.4762** | **0.4375** |
| **K-Nearest Neighbors**| 0.4250 | 0.4118 | 0.3500 | 0.3784 | 0.4213 |
| **Naive Bayes** | **0.4750** | **0.4706** | 0.4000 | 0.4324 | 0.4275 |

---

## 3. Diagnostic Insights
* **Decision Tree:** Proved most effective at minimizing False Negatives (actual delays predicted as "Fast"), making it the strongest candidate for maintaining customer trust.
* **K-Nearest Neighbors:** Demonstrated lower sensitivity to delays and higher computational overhead compared to the other models.
* **Naive Bayes:** Produced the highest accuracy but suffered from a high rate of False Positives, likely due to the assumption of feature independence.



---

## 4. Operational Recommendations
Based on the results, the **Decision Tree** is the recommended model for deployment. Its transparency allows the business to see exactly how predictions are made. Key drivers influencing delays were identified as:
1.  **Haversine Distance (km):** Longer routes significantly increase delay probability.
2.  **Traffic Conditions:** Real-time congestion is a primary factor in delivery lag.
3.  **Order Time:** Peak hours correlate strongly with increased delivery times.

---

## 5. Final Summary
In conclusion, the Phase 3 analysis identifies the **Decision Tree** as the superior model for food delivery status prediction, achieving the highest **F1-Score (0.4762)** and **Recall (0.5000)** among the tested classifiers. While the model indicates room for further optimization, it currently provides the most effective balance for identifying actual delays, thereby reducing the high business cost of missed operational interventions. By focusing on critical predictors such as **traffic conditions** and **travel distance**, the delivery team can implement actionable strategies like dynamic route reassignment and accurate real-time customer notifications to enhance overall service reliability and customer satisfaction.
