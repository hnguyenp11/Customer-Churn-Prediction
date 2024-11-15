# **Customer Churn Prediction**
![image](https://github.com/user-attachments/assets/ef95244e-33fc-46cc-8b31-43d2ea37f115)


## **Project Goal**
The primary goal of this project is to identify key indicators of customer churn within a telecommunications company and develop a predictive model that can flag high-risk customers. By understanding which customers are most likely to leave, the company can implement targeted retention strategies to reduce churn, stabilize revenue, and strengthen customer loyalty.


## **Techniques Used** 
- **Data Preparation**: The dataset included 4,280 customer records. We removed irrelevant features, encoded categorical variables, standardized numerical values, and used SMOTE to address class imbalance.
- **Feature Selection**: Correlation matrix, Chi-Square Test, and Fisher Scores were applied to select impactful variables: state, international_plan, number_vmail_messages, total_day_minutes, and number_customer_service_calls.
- **Modeling**: Multiple models were tested, including Decision Tree, Logistic Regression, Random Forest, K-Nearest Neighbors, and Support Vector Machine (SVM). SVM performed best, achieving 87% accuracy and an F1-score of 0.6 for the churn class, focusing on minimizing false negatives.

## **Findings (Insights)**
- **Customer Service Calls**: Higher churn likelihood among customers with frequent service calls, indicating possible dissatisfaction with the quality of service or unresolved issues with the telecom provider. This trend suggests a need to address common service complaints or improve customer support response.
- **Total Day Minutes and Charges**: Heavy usage during the day correlates with higher churn, indicating possible dissatisfaction with high usage costs or call quality.
- **International Plan**: Nearly half of the customers with an international plan tend to churn. This suggests possible issues with the perceived value or cost of international services. There may also be limitations or hidden charges in the plan that don’t meet customer expectations, driving them to switch providers.
- **Number of voice mail messages**: Customers who use voicemail services less frequently are more likely to churn. This could indicate that these customers may feel less engaged with the telecom's offerings or do not find enough value in the voicemail feature, suggesting a potential opportunity to enhance or market this feature more effectively.
- **Regional Patterns**: Customers from New Jersey (NJ) show a higher-than-average churn rate, possibly due to regional competition, network quality issues, or unmet service expectations in that state.

## **Recommendations**
- Enhance Customer Service: Conduct a detailed analysis of frequent customer complaints and implement targeted training programs for customer service representatives to improve resolution rates.
- Usage-Based Retention Offers: Develop tiered or unlimited plans tailored for heavy daytime users, offering competitive pricing and added benefits such as free minutes after a threshold.
- Re-evaluate International Plan Offerings: Reassess the pricing and features of the international plan to improve value. Include transparent pricing and additional perks like discounted rates for frequently called countries.
- Promote Voicemail Plans: Enhance voicemail features, such as transcription to text or integration with messaging apps, and actively market these upgrades to low-usage customers.
- Targeted Regional Marketing: Investigate state-specific churn factors, such as network quality or competitive pressures, and implement localized solutions like infrastructure upgrades or promotional campaigns.


