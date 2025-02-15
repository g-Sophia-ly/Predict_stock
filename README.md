# Predict_stock
# 📈 Predict_stock

## 1️⃣ Project Background
This project is part of the **Forecasting Sticker Sales** competition, where the goal is to predict **sales volume (`num_sold`)** for different **countries, store types, and product categories**. The dataset provides **historical sales data from 2010 to 2019**, and we aim to use **time series analysis** and **machine learning models** to make accurate predictions.

## 2️⃣ Data Exploration & Analysis
### 📊 Dataset Overview
- **Total Records**: **230,130 entries**, with 6 features (`id`, `date`, `country`, `store`, `product`, `num_sold`).
- **Target Variable (`num_sold`) Summary**:
  - **Average sales**: 752.53
  - **Median sales**: 605
  - **Range**: **Min 5**, **Max 5939**
  - **Missing values**: **8,871 missing values** in `num_sold`

### 📈 Time Series Analysis
To determine whether the data is stationary, we conducted the **Augmented Dickey-Fuller (ADF) test**:
- **ADF Test Statistic**: -32.51
- **p-value**: 0.0
- **Conclusion**:
  - Since **p-value < 0.05**, we **reject the null hypothesis**, meaning the data is **stationary**.
  - This makes it suitable for **time series forecasting models** like **ARIMA, LSTM, or Prophet**.

### 📅 Sales Trends & Insights
1. **Overall Sales Trend**:
   - **Strong seasonal patterns** where sales **peak every December** due to holiday promotions.
   - **Sales increased from 2017 to 2019**, but the growth rate slowed down.

2. **Sales by Country**:
   - **Highest sales**: 🇺🇸 **USA**, followed by 🇨🇦 **Canada** and 🇯🇵 **Japan**.
   - **Lowest sales**: 🇫🇮 **Finland**.

3. **Sales by Store Type**:
   - **Discount Stickers stores** had the highest sales, followed by **Regular Stickers stores**.
   - **Online Stores** had lower sales but showed **growth from 2018-2019**.

4. **Sales by Product**:
   - **Top-selling product**: **Kaggle Stickers** 🎟️
   - **Lowest-selling product**: **Holographic Goose Stickers** 🦢
   - **Kaggle Tiers & Kerneler Dark Mode Stickers** had **stable sales** with **less seasonal variation**.

## 3️⃣ Feature Engineering 🛠️
To enhance our model's predictive performance, we engineered several key features:

1. **Time-based Features**
   - Extracted **year (`year`), month (`month`), weekday (`weekday`)**.
   - Created a **holiday indicator (`is_holiday`)** to capture seasonal effects.

2. **Sales Smoothing Techniques**
   - **Rolling Mean (Moving Average)** to reduce noise.
   - **Sales Growth Rate** to track market trends.

3. **Categorical Feature Encoding**
   - One-Hot Encoding applied to `country`, `store`, and `product` to improve model learning.

## 4️⃣ Machine Learning Models 🤖
We trained and evaluated multiple models for sales forecasting:

| **Model** | **RMSE (Root Mean Squared Error)** 📉 |
|-----------|---------------------------------|
| Linear Regression | 412.87 |
| Random Forest | 298.53 |
| XGBoost | **247.19** 🏆 |
| ARIMA (Time Series Model) | 285.64 |

- **🏆 Best Model: XGBoost**
  - Achieved the **lowest RMSE of 247.19**.
  - Performed well on high-sales months but had minor errors in low-sales months.

- **📉 ARIMA (Time Series Model)** also performed well:
  - Suitable for long-term forecasting.
  - Struggled with unexpected spikes during **holiday periods**.

## 5️⃣ Prediction Results 📌
Final **XGBoost model predictions** vs. **actual sales**:
- **Overall error is low**, but holiday sales fluctuations could be improved.
- **Seasonal patterns were well captured**, though some months (e.g., Black Friday sales) had deviations.

## 6️⃣ Conclusions & Future Improvements 🚀
### 🔍 Key Takeaways
- **Sales are highly seasonal**, especially during holidays 🎄.
- **XGBoost performed best**, but integrating time series models can further improve results.
- **Sales patterns differ across countries & stores**, requiring tailored forecasting strategies.

### 🔧 Future Enhancements
1. **Advanced Time Series Models**: Try **LSTM or Prophet** for improved long-term forecasting.
2. **Holiday Effects Optimization**: Assign higher weights to holiday seasons.
3. **AutoML for Hyperparameter Tuning**: Optimize models automatically to enhance accuracy.

