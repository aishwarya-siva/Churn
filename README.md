# Customer Retention Analysis Project
### Overview:
  This project is a comprehensive analysis of customer retention for a telecom company with a dataset of 7,043 customers, where 26.5% (1,869) have churned. The goal was to build a predictive model to identify at-risk customers and create interactive dashboards to visualize key retention metrics and trends. The project leverages Python for data processing and machine learning, with dashboards designed to provide actionable insights for business decision-making.

### Project Structure:
Churn.ipynb: A Jupyter Notebook containing the full workflow, including data import, preprocessing, exploratory data analysis (EDA), model training, evaluation, and export.
Dashboards: Four detailed visualizations (Overview, Demographics, Services, Model Evaluation) provided as images to showcase data insights.
predictions.csv: A CSV file storing actual vs. predicted churn values for the test dataset.
churn_prediction_pipeline.pkl: A serialized machine learning pipeline saved using joblib for future predictions.

### Detailed Project Content:
#### 1. Data Import and Initial Exploration:
- Imported the Telco-Customer-Churn.csv dataset using pandas, which contains 21 columns including customerID, gender, SeniorCitizen, tenure, Churn, and financial metrics like MonthlyCharges and TotalCharges.
- Checked the dataset shape (7,043 rows, 20 columns after preprocessing) and confirmed no null values, ensuring data integrity.

#### 2. Data Preprocessing:
- Identified and corrected the TotalCharges column, initially stored as an object, by converting it to float and filling missing values with the median.
- Removed the customerID column as it does not contribute to churn prediction, reducing the dataset to 20 relevant features.
- Prepared categorical (object) and numerical (int64, float64) columns for further processing using LabelEncoder and StandardScaler.

#### 3. Exploratory Data Analysis (EDA):
- Analyzed feature distributions and churn patterns using visualizations:
- Plotted a bar chart of the top 15 important features using Logistic Regression coefficients, highlighting tenure (1.51) as the most significant predictor.
- Generated pie charts and bar graphs (reflected in dashboards) to explore relationships between churn and factors like contract type, phone service, dependents, senior citizen status, and payment methods.
- Noted key insights, such as 62% churn rate at tenure 1 and 88% of churned customers being month-to-month subscribers.

#### 4. Model Development:
- Split the data into training and test sets (80-20 split) using train_test_split.
- Addressed class imbalance (imbalanced churn data) with SMOTE (Synthetic Minority Oversampling Technique).
- Trained and compared multiple models: Logistic Regression (selected for its interpretability and performance).
- Used GridSearchCV for hyperparameter tuning and cross_val_score for robust evaluation.

#### 5. Model Evaluation: 
- Evaluated the Logistic Regression model on the test set, achieving: ROC-AUC: 0.86 (strong discriminative power), Recall: 0.83 (high sensitivity to churn cases), Accuracy: 0.76, Precision: 0.53, F1 Score: 0.64.
- Generated a confusion matrix showing 310 true positives, 756 true negatives, 280 false positives, and 63 false negatives, with a misclassification rate of 24.34%.
- Visualized performance metrics (ROC-AUC, Recall, etc.) and feature importance in the dashboard.

#### 6. Output and Export:
- Saved predictions (actual vs. predicted churn) to predictions.csv for further analysis.
- Created a pipeline combining preprocessing, SMOTE, and Logistic Regression, then exported it as churn_prediction_pipeline.pkl using joblib for deployment.

#### 7. Dashboard Creation: 
- Developed four dashboards using PowerBI.
      1. Overview: Displays total customers (7,043), churned customers (1,869), churn rate (26.5%), total revenue ($16.06M), and breakdowns by contract and phone service.
      2. Demographics: Shows pie charts for dependents, partners, senior citizens, and gender, revealing lower churn among senior citizens and those with partners.
      3. Services: Includes stacked charts for OnlineSecurity, TechSupport, InternetService, and PaymentMethod, noting higher churn with electronic checks and fiber optic connections.
      4. Model Evaluation: Presents model metrics, confusion matrix, and feature importance, emphasizing tenure’s role in retention.

### Results and Insights:
- The model successfully identifies at-risk customers with a low false negative rate (63), enhancing retention planning.
- Key retention drivers include longer tenure and avoiding electronic check payments, while month-to-month contracts and short tenures increase churn risk.
- The dashboards provide a user-friendly interface for stakeholders to explore data and act on insights.
