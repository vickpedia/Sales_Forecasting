Sales-Forecasting-Datascience-Project

This data science project focuses on forecasting weekly product sales using historical time-series data. It involves data cleaning, exploratory analysis, time-series modeling with Prophet, accuracy validation over past months, and future forecasting for upcoming months.

.

🧩 Problem Statement
You are provided with a dataset that contains weekly sales quantities (quantity) of products identified by multiple attributes such as:

weekend_date – the week-ending date (timestamp).

SerialNum – unique product ID.

channel, brand, category, sub_category – product features.

Objective:
Explore and understand historical sales trends.

Build and validate time-series forecasting models.

Forecast weekly sales for Sep–Nov 2024.

Report model performance on Jun–Aug 2024 using a custom accuracy metric.

.

🛠️ Solution Approach
1. 📊 Exploratory Data Analysis (EDA)
Performed in EDA_Sales_Forecasting.ipynb:

Converted weekend_date to datetime format.

Checked for null values, duplicate records, and consistent weekly frequency.

Grouped data by SerialNum and visualized weekly sales trends using line plots.

Identified:

Seasonal peaks in some products.

Products with occasional missing or flat (zero) sales.

Weekly seasonality patterns.

2. 🤖 Forecasting Model (Prophet)
Executed in Modeling_Sales_Forecasting.ipynb:

Data Preparation:
Sorted data chronologically for each SerialNum.

Split data into:

Training: All data before June 1, 2024

Validation: All data between June 1 – August 31, 2024

Model:
Trained one Facebook Prophet model per product.

Enabled both weekly and yearly seasonality.

Used make_future_dataframe() to forecast 13 future weeks (Sept–Nov).

Saved each model object as .pkl using joblib.

3. 📈 Validation & Monthly Accuracy
Used the custom metric provided:

mathematica
Copy
Edit
Monthly Accuracy = 1 - (Sum of absolute errors / Sum of actuals)
Steps:

Compared Prophet forecasts (yhat) vs actual sales (y) on validation set (Jun–Aug).

Grouped by month and calculated monthly accuracy per product.

Accuracy values were stored in a structured format.

📌 Observations
All products showed clear weekly trends in quantity sold.

Some SerialNums had holiday-like spikes indicating yearly patterns.

Validation accuracy differed slightly per product, depending on variability and consistency.

📍 Findings
Prophet models performed consistently well across most products.

Validation accuracy:

June: ~90%

July: ~88%

August: ~91%

Future forecast for September–November followed smooth trend lines based on historic seasonality.

💡 Insights
Individual modeling per SerialNum allowed higher control and more tailored forecasting.

Prophet's strength in handling seasonality made it a great fit for weekly retail demand.

Sales trends can be updated periodically with rolling model retraining for improved accuracy.

