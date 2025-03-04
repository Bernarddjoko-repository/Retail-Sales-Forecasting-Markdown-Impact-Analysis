![Sales Prediction](https://github.com/user-attachments/assets/1b4312a8-4f57-4ed5-b9b1-8107142b4a42)

# 📌 Retail Sales Forecasting & Markdown Impact Analysis
🔹 Predicting Sales & Understanding Markdown Effects for Better Retail Decisions
## 📌 Introduction
Retail businesses rely on historical sales data to make key decisions about inventory, promotions, and markdowns.<br> However, sales forecasting is challenging due to seasonal variations, economic factors, and unpredictable consumer behavior.<br>

This project tackles these challenges by using machine learning and time-series forecasting to:<br>
✅ Predict department-wide sales for the upcoming year.<br>
✅ Model the impact of markdowns on holiday weeks to optimize promotions.<br>
✅ Improve revenue strategies by analyzing the effects of holidays and economic factors.<br>

## 📌 Dataset Overview
The dataset consists of three main sources:<br>

1️⃣ Stores Dataset → Contains store type and size for 45 stores.<br>
2️⃣ Features Dataset → Includes weekly economic data (CPI, Unemployment, Fuel Price), markdowns, and holiday indicators.<br>
3️⃣ Sales Dataset → Historical weekly sales data for each department in each store from 2010-02-05 to 2012-11-01.<br>

### Key Business Holidays included:<br>
📌 Super Bowl<br>
📌 Labor Day<br>
📌 Thanksgiving<br>
📌 Christmas<br>

📌 Holiday weeks are given 5x weight in model evaluation since they significantly impact business revenue.<br>

### 📌 Business Problem
Why is this project important?<br>

📌 Retailers need accurate demand forecasting to avoid overstocking or understocking products.<br>
📌 Markdowns (discounts) impact sales, but how much? We need a model that predicts their effect.<br>
📌 Holidays have a major impact on sales, but there is limited historical data.<br>

### ❓ Business Questions to Answer
1️⃣ How can we accurately predict next year's sales?<br>
2️⃣ How do markdowns affect sales, especially during holidays?<br>
3️⃣ What strategies can we use to improve markdown efficiency and optimize inventory?<br>

## 📌 Step-by-Step Approach

1️⃣ Data Preparation<br>
✅ Handled missing values:<br>
   🔹 Filled missing markdowns with 0 (assuming no markdown).<br>
   🔹 Used rolling mean for missing CPI and Unemployment data to smooth fluctuations.<br>

✅ Handled outliers:<br>
   🔹Winsorization (limiting extreme values) for robust models.<br>

✅ Merged all datasets into one feature-rich dataset for analysis.<br>

2️⃣ Feature Engineering<br>
We created several new features to improve model performance:<br>

✅ Time-based Features:<br>
Year, Month, Week, Day of the Week, IsWeekend to capture seasonality.<br>

✅ Lag Features:<br>
Lag_1, Rolling_4, Rolling_12, Lag_52 to track sales trends over time.<br>

✅ Holiday Features:<br>
Super Bowl, Thanksgiving, Christmas, Labor Day indicators.<br>

✅ Total Markdown Impact:<br>
   🔹Summed markdown values across different promotions.<br>
   🔹Created a feature to measure markdowns during holiday weeks.<br>

3️⃣ Feature Selection & Scaling<br>
📌 Used Random Forest Feature Importance to remove low-impact variables.<br>
📌 Dropped highly correlated features to avoid redundancy.<br>
📌 Applied StandardScaler to normalize numerical features.<br>

4️⃣ Time-Based Train-Test Split<br>
Since this is a time-series problem, we cannot use random splitting.<br>
✅ Training Data: 2010 - 2011<br>
✅ Testing Data: 2012<br>
This ensures real-world predictive performance by simulating how a business would forecast future sales.<br>

5️⃣ Model Training
We trained multiple models to compare performance:<br>

✅ Machine Learning Models<br>
📌 Random Forest Regressor<br>
📌 XGBoost Regressor<br>

🔹 Techniques Used:<br>
✅ Log Transformation to normalize skewed sales data.<br>
✅ Weighted Loss (Holiday weeks get 5x importance).<br>

✅ Time-Series Models<br>
📌 SARIMA (Seasonal ARIMA for long-term forecasting).<br>
📌 Exponential Smoothing (Captures seasonal sales trends).<br>

## 📌 Challenges & Solutions
1️⃣ Limited Holiday Data <br>
🔹 Issue: Holidays only occur once a year, making it difficult for models to learn patterns.<br>
🔹 Solution: Used weighted loss function to prioritize holiday weeks during training.<br>

2️⃣ Extreme Outliers in Sales Data<br>
🔹 Issue: Some departments had unusually high or low sales, which skewed model predictions.<br>
🔹 Solution: Applied Winsorization and Log Transformation to reduce the impact of outliers.<br>

3️⃣ Time-Based Dependencies<br>
🔹 Issue: Random train-test splits would lead to data leakage and unrealistic results.<br>
🔹 Solution: Used a time-based split (training on 2010-2011, testing on 2012).<br>

4️⃣ Slow SARIMA Training<br>
🔹 Issue: SARIMA took a long time to train on large datasets.<br>
🔹 Solution: Ran initial tests on smaller samples and optimized hyperparameters.<br>

## 📌 Results
📌 XGBoost performed best for overall sales forecasting.<br>
📌 Weighted Loss significantly improved holiday week predictions.<br>
📌 SARIMA was slow but useful for capturing long-term seasonality.<br>

## 📌 Future Work
🔹 Deep Learning Models → Implement LSTMs or Transformers for advanced sequential learning.<br>
🔹 A/B Testing for Markdown Strategies → Experiment with markdown levels to optimize revenue.<br>
🔹 Automated Model Retraining → Set up a pipeline to update predictions as new data arrives.<br>

## 📌 Installation & How to Run
bash
Copy
Edit
#### Clone the Repository  
git clone https://github.com/your-github-username/Retail-Sales-Forecasting.git  
cd Retail-Sales-Forecasting  

#### Install Dependencies  
pip install -r requirements.txt  

#### Run Data Preparation & Feature Engineering  
python data_preprocessing.py  

#### Train Machine Learning Models  
python train_models.py  

#### Train Time-Series Models  
python train_time_series.py  

#### Evaluate Model Performance  
python evaluate_models.py  

#### Visualize Results  
python visualize_results.py  

## 📌 Key Takeaways
✅ Real-world business impact: Improves retail sales forecasting & markdown optimization.<br>
✅ Advanced Machine Learning & Time-Series Forecasting applied.<br>
✅ Tackles challenges like seasonal demand shifts & sparse holiday data.<br>
✅ Scalable to real-world applications like demand forecasting & pricing optimization.<br>

## 📌 Why This Project is Important:
✔ Real Business Application → Helps retailers reduce losses and maximize profit.<br>
✔ Advanced Data Science Techniques → Machine Learning + Time-Series + Feature Engineering.<br>
✔ Proves Forecasting & Analytical Skills → Essential for roles in Retail Analytics, Demand Forecasting, and Predictive Modeling.<br>
