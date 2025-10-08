# Demand Forecasting

# Problem Statement :
Sales predictions summary for the upcoming month by product wise.

# Why :
• Why this question is important Retailers can analyze the historical sales data, sales trends and consumer behavior to accurately Forecast demand. This minimizes overstock or understock situations while ensuring customers Find what they want. Better supply chain management

# Business Objective :
To support data-driven sales planning, we evaluated multiple machine learning models to predict monthly sales by product. The goal is to identify the most accurate and generalizable model that can reliably forecast next month's sales across multiple products.

Link to Jupyter Notebook :
https://github.com/chandtr/CapstoneProject/blob/master/SalesPrediction.ipynb

**How to run this notebook :**

*.Clone this repository in a directory <br>
*.Run this notebook using the Jupyter Notebook application from the Python Installation


# Exploratory Data Analysis of Sale Predictions

The Dataset used for this analysis contains 2 years of Sales data for a Retail store, which includes multiples and stores and multiple products.
Here is the details about the source data,
Observations from the Data sales_train.csv (Sales Data) date:
2935849 : total number sales records
1034 unique dates — suggests daily data over a period of 34 months (date_block_num).
shop_id: 60 unique shops.
item_id: 21,807 unique items.
item_price: 19,993 unique prices — some items may have fluctuating prices.
item_cnt_day: 198 unique sales counts for a day — includes both positive and negative values, possibly returns or corrections.

test.csv (Test Data) :
ID: 214,200 unique entries — this is the number of test samples for which we need to predict.
shop_id: 42 unique shops in the test set — fewer than the training set, so we may need to handle shops that appear in training but not in testing and vice versa.
item_id: 5,100 unique items in the test set — fewer items than in the training set.

This Jupyter Notebook is doing the following tasks along with EDA,<br>
*. Data cleansing and outlier removals<br>
*. Aggregating and analyzing the datat for 33 months<br>
*. Removing the outliers by Sales Count and Item Price<br>
*. Aggregated sales data by month wise<br>

### Data Cleansing 
Few points for data cleansing,<br>
*.Based on the sales data, noticed that sales data has below 0 sales values, which needs to be remvoed, so i have filtered the records with negative sales numbers<br><br>
*.Noticed that few duplicated rows were there, which has been dropped <br><br>
*.Based on the data distribution analysis, found out that some item prices are greater than $5000, which is a outlier because most of the sales prices are
  falling under 5000. Few Gaming and Software related items have item price more than 40000, those outliers has been removed <br><br><br>
  
  <img width="805" height="484" alt="image" src="https://github.com/user-attachments/assets/27b04fad-a2d9-4db7-9a02-9a00fc266b37" /><br>

  <img width="526" height="443" alt="image" src="https://github.com/user-attachments/assets/1773d60d-2da5-424c-ac19-705a9408bc34" /> <br>

  <img width="547" height="449" alt="image" src="https://github.com/user-attachments/assets/246dcae6-30ff-45ec-a882-75c8281faaac" /> <br>


  <img width="706" height="491" alt="image" src="https://github.com/user-attachments/assets/784bcb7a-9038-4c4a-96a5-2f06a96d0cb4" /><br><br>
*.Density of the item sales count is better under 10, i have removed the outliers based on the sales count,<br><br><br>
<img width="808" height="505" alt="image" src="https://github.com/user-attachments/assets/66f7bb58-6e84-442e-9bfe-0622a467c45a" /><br>
<img width="499" height="433" alt="image" src="https://github.com/user-attachments/assets/fa9a5f40-fe18-4993-8086-d6b2133a4271" /><br>
<img width="613" height="495" alt="image" src="https://github.com/user-attachments/assets/17b566ce-6ff7-4067-9feb-14eda4c879cc" /><br>
<img width="793" height="513" alt="image" src="https://github.com/user-attachments/assets/171bdef4-411d-4b99-95b8-d4a130c4edba" /><br>

*.Making sure the sales data is avaiable for all the shop_id, item_id and I am populating the default value for shop_id/item_id has missing sales data<br><br>
*.Aggregating the data for getting the monthly sales summary for all the shop_ids and item_ids<br><br>

<img width="809" height="489" alt="image" src="https://github.com/user-attachments/assets/9e084a17-e121-4556-a699-b4fd2d3a8629" />

<img width="998" height="607" alt="image" src="https://github.com/user-attachments/assets/ea537d59-5dcf-4775-83b7-1404760a5fce" /><br><br>

*.Monthly summary for the top 10 highest sale items,
<img width="1200" height="2000" alt="newplot" src="https://github.com/user-attachments/assets/58cb855d-6c32-41f3-a16b-e46702c9a640" />

# Top 10 Item by Total Sales :
<img width="568" height="313" alt="image" src="https://github.com/user-attachments/assets/d4aad420-9540-410b-a877-34a8144392ea" />

# Top 10 Shops by Total Sales :
<img width="355" height="304" alt="image" src="https://github.com/user-attachments/assets/45b937bf-aba8-4d32-bbd1-fb5d533719b9" />


*. Filling the sales data for missing dates, making sure sales is listed for all the sales id and item id combination for every month <br> <br>
*. Spliting the Traning and Testing data like first 25 months for training data and remaining for testing<br> <br>
*. Created the baseline model with dummy classifier<br><br><br><br>

# Model Training and Cross validation <br><br>

I have trained the following models for predicting the sales,<br><br>
1.Linear Regression<br>
2.XGB Regressor<br>
3.Random Forest<br>
4.LightGBM Timeseries<br><br>

Training and Testing accuracy score is better for Random Forest model and LigthGBM timeseries model,<br><br>
both got around 82% accuracy for Training datasets,<br><br>
                72% accuracy for the Testing datasets.<br><br><br>
                
Training the dataset with RandomForest took long time to process, close to an hour for that training.<br><br>
                
Here is the accuracy score for these different models <br><br>
<img width="390" height="94" alt="image" src="https://github.com/user-attachments/assets/1d33285a-2091-4051-b478-700b4433c3a5" /> <br><br><br>

# Sample Predictions :

Trained the Timeseries model using LGBM and validated the predicted data with the testing dataset here, <br><br>
<img width="1342" height="373" alt="image" src="https://github.com/user-attachments/assets/15c7fc88-d73b-48dc-95a9-63b5ed670ccd" /> <br><br>

# Technical Insights<br><br>

## Linear Regression :<br>
Very limited capacity to capture non-linear relationships.<br>
Serves as a benchmark, but unsuitable for production.<br>
## Random Forest:<br>
Best performance on testing data.<br>
Ensemble method reduces bias but still shows moderate variance.<br>
## XGBoost:<br>
Strong performance and generalization.<br>
Built-in regularization helps prevent overfitting.<br>
May be the most stable choice for deployment if consistency is a priority.<br>
## LightGBM:<br>
Similar to XGBoost but faster.<br>
Slightly more overfitting; <br>
Suitable for large-scale data or faster iteration cycles.<br>

# Technical next steps:
Hyperparameter Tuning	Optimize model parameters using GridSearchCV <br>
Feature Engineering	Explore additional transformations or interaction terms<br>
Residual Analysis	Visual checks for pattern in errors <br>
Model Packaging	Wrap in pipeline with preprocessing for deployment<br>
Monitoring Plan	Define metrics and thresholds for model drift detection<br>

# Deliverables :
Python scripts and notebooks for all models<br>
Model performance logs and comparison tables<br>
Sample sales forecasts for next month (by product)<br>

# Summary

We tested four different models to find the most accurate and reliable one for our prediction task. After comparing their results, the Random Forest and XGBoost models showed the best performance.

Random Forest had the highest overall accuracy.

XGBoost was slightly less accurate but more stable (less prone to overfitting).

Linear Regression was too simple and did not perform well.

LightGBM performed well but overfit slightly more than the others.

📌 Recommended Model:
Random Forest (or XGBoost, depending on whether stability or raw accuracy is prioritized).<br><br><br>

<img width="748" height="214" alt="image" src="https://github.com/user-attachments/assets/b94cf003-a9f4-4d28-bf3f-22e5e9ef8556" />


# Summary & Business Impact :

Sales can now be forecasted by product with >70% accuracy<br>
Supports better demand planning and inventory decisions<br>
Helps align sales, supply chain, and marketing strategies<br>
Scalable and automatable solution ready for integration

<br><br>
# Next Steps :

Model Tuning – We will fine-tune the top models to improve performance even more.

Validation – We'll test the final model on new data to make sure it performs well.

Deployment – Once validated, the model can be integrated into our systems (e.g., dashboards, decision tools).

