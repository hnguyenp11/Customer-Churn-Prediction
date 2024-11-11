# **Customer Churn Prediction**

## **I. Business Understanding**
Customer churn represents one of the most pressing challenges for businesses, particularly in highly competitive industries like telecommunications. When customers leave, it disrupts revenue and inflates acquisition costs, as acquiring a new customer is often more expensive than retaining an existing one. Reducing churn not only stabilizes revenue but also provides a strategic advantage in customer loyalty, helping the company build a dependable customer base.

To effectively address this challenge, I will analyze data on customer behavior, service usage, and engagement patterns with a telecommunications provider. The goal is to develop a predictive model that can identify potential churners before they leave, allowing the company to implement proactive strategies to retain these customers. By understanding key churn drivers, the business can take informed actions—whether through personalized offers, improved customer service, or other retention strategies—to maintain and grow its revenue base.

## **II. Data Preparation**
The dataset comprises 4,280 customer records, each containing details about geographic and service-related aspects that provide a comprehensive view of customer behavior and engagement with the telecommunications provider. Geographic details include the customer’s state and area code, offering some insight into demographics. Account-specific details, such as tenure with the provider and subscription to plans like international or voicemail, help characterize customer profiles. Usage metrics detail call duration, number of calls, and charges for day, evening, and night periods, as well as for domestic and international calls. These details enable a granular look into customer activity levels and preferences. Additionally, the dataset includes customer service interaction data and an indication of whether the customer eventually churned.

**Key dataset columns**
- state: Two-letter code of the US state of customer residence
- account_length: Number of months with the current telco provider
- area_code: Three-digit area code of the customer
- international_plan: Whether the customer has an international plan
- voice_mail_plan: Whether the customer has a voicemail plan
- total_day_minutes, total_day_calls, total_day_charge: Metrics for day calls
- total_eve_minutes, total_eve_calls, total_eve_charge: Metrics for evening calls
- total_night_minutes, total_night_calls, total_night_charge: Metrics for night calls
- total_intl_minutes, total_intl_calls, total_intl_charge: Metrics for international calls
- number_customer_service_calls: Number of calls to customer service
- churn: Target variable indicating customer churn

## **III. Exploratory Data Analysis**
### **1. Univariate Analysis**
Among the 4,280 customers, 598 (14.07%) have churned. This churn rate is low but still significant, as each lost customer translates into lost revenue and increased acquisition costs. The largest concentration of customers is found in West Virginia (WV), particularly within area code 415. Moreover, most churn customers in this telecom company do not have an international or voicemail plan. This provides a demographic profile to understand how location might play a role in service preferences and churn tendencies.

### **2. Bivariate Analysis**
#### ***Numerical Features - Churn***
- **Number of Voicemail Messages**: Customers who stay tend to use voicemail more frequently than those who leave, with most departing customers using few or no voicemail messages. This suggests that voicemail usage may correlate with engagement and satisfaction levels. However, there are still churned customers with high voicemail usage, indicating that engagement alone might not prevent churn.
- **Total Day Minutes**: Departing customers tend to have longer day call durations than those who stay. This could suggest a potential issue with call quality or customer satisfaction during longer calls.
- **Total Day Charge**: Departing customers incur higher day call charges than those who stay, as they tend to have longer day call durations.
- **Total International Calls**: Departing customers generally make fewer international calls, although there are outliers who make a high number of calls.
- **Number of Customer Service Calls**: Departing customers make significantly more customer service calls, with a longer upper whisker on the boxplot, indicating some customers make many calls. This factor appears strongly related to the likelihood of leaving.

#### ***Categorical Features - Churn***
- **State**: States like NJ and CA show higher-than-average churn rates. Analyzing these regions could reveal region-specific issues or competition that influences customer loyalty.
- **International Plan**: Almost half of customers with an international plan end up churning. This trend indicates a potential disconnect between customer expectations and service value in this plan.
- **Voicemail Plan**: Customers without a voicemail plan show a higher churn rate (16.44%) than those with one (7.37%). Offering voicemail plans could potentially improve retention by adding a valued service feature.

## **IV. Feature Selection**
To identify the most impactful variables for my predictive model, I used the following methods:
- Correlation Matrix: identified and removed features with high correlation to prevent multicollinearity, which could distort model accuracy.
- Chi-Square Test: Applied to categorical features to identify variables most associated with churn.
- Fisher Scores: Used for numerical variables to rank features by their ability to differentiate between churned and non-churned customers and then I selected those that most effectively contribute to classification.
Based on these methods, I selected 5 variables (3 numerical and 2 categorical) for models: state, international_plan, number_vmail_messages, total_day_minutes, number_customer_service_calls

## **V. Model & Evaluation**
### **1. Data Preprocessing**
After removing irrelevant features, I transformed the categorical variables with dummy encoding and standardized the numerical variables to ensure consistency across the dataset. I then split the data into an 80-20 ratio for training and testing. To address the imbalance in churn, I applied the Synthetic Minority Over-sampling Technique (SMOTE), which helped create a more balanced dataset by adding synthetic examples of positive churn cases. This approach ensured the model was trained effectively with sufficient churn examples, improving its ability to recognize patterns that distinguish customers likely to churn.

### **2. Modeling & Evaluation**
I trained multiple models—Decision Tree, Logistic Regression, Random Forest, K-Nearest Neighbors, and Support Vector Machine (SVM)—on the training dataset. The SVM model emerged as the top performer, achieving over 87% accuracy on the testing set and an F1-score of 0.6 for the churn class. I chose SVM as it minimizes false negatives, allowing the company to proactively target potential churners with retention strategies.

Using permutation importance, I identified the top features for churn prediction:
- **Total Day Minutes**: Indicates a correlation between heavy usage and churn risk.
- **Number of Customer Service Calls**: Frequent calls could reflect unresolved issues or dissatisfaction.
- **Voice Mail Plan**: Customers with a voicemail plan have a lower churn rate, highlighting this as a potential retention lever.
- **International Plan (Yes)**: Customers having an international plan tend to churn more, suggesting possible dissatisfaction with plan pricing or value.
- **State (NJ)**: Certain states exhibit higher churn, signaling potential competition or service issues in these regions.
  
## **VI. Deployment**
Once trained and validated, I used this the model to predict for another dataset, which can help the company to flag high-risk customers. 




