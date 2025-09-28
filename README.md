"# CapstoneProject" 

Problem Statement : Sales predictions summary for the upcoming month by product wise.

• Why this question is important Retailers can analyze the historical sales data, sales trends and consumer behavior to accurately Forecast demand. This minimizes overstock or understock situations while ensuring customers Find what they want. Better supply chain management

Link to Jupyter Notebook :
https://github.com/chandtr/CapstoneProject/blob/master/SalesPrediction.ipynb

**How to run this notebook :**

*.Clone this repository in a directory <br>
*.Run this notebook using the Jupyter Notebook application from the Python Installation


# Exploratory Data Analysis of Coupon Acceptance

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

This Jupyter Notebook is doing the following tasks along with EDA,
*. Data cleansing and outlier removals
*. Aggregating and analyzing the datat for 33 months
*. Removing the outliers by Sales Count and Item Price
*. Aggregated sales data by month wise

### Data Cleansing 
Few points for data cleansing,
*.Based on the sales data, noticed that sales data has below 0 sales values, which needs to be remvoed, so i have filtered the records with negative sales numbers<br><br>
*.Noticed that few duplicated rowes were there, which has been dropped <br><br>
*.Based on the data distribution analysis, found out that some item prices are greater than $5000, which is a outlier because most of the sales prices are
  falling under 5000. Few Gaming and Software related items have item price more than 40000, those outliers has been removed <br><br><br>
  <img width="706" height="491" alt="image" src="https://github.com/user-attachments/assets/784bcb7a-9038-4c4a-96a5-2f06a96d0cb4" /><br><br>
*.Density of the item sales count is better under 10, i have removed the outliers based on the sales count,<br><br><br>
<img width="613" height="495" alt="image" src="https://github.com/user-attachments/assets/17b566ce-6ff7-4067-9feb-14eda4c879cc" /><br><br>

*.Making sure the sales data is avaiable for all the shop_id, item_id and I am populating the default value for shop_id/item_id has missing sales data<br><br>
*.Aggregating the data for getting the monthly sales summary for all the shop_ids and item_ids<br><br>

<img width="998" height="607" alt="image" src="https://github.com/user-attachments/assets/ea537d59-5dcf-4775-83b7-1404760a5fce" />

*. Filling the sales data for missing dates, making sure sales is listed for all the sales id and item id combination for every month
*. Spliting the Traning and Testing data like first 25 months for training data and remaining for testing
*. Created the baseline model with dummy classifier
