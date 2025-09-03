"# CapstoneProject" 

Problem Statement : Sales predictions summary for the upcoming month by product wise.

• Why this question is important Retailers can analyze the historical sales data, sales trends and consumer behavior to accurately Forecast demand. This minimizes overstock or understock situations while ensuring customers Find what they want. Better supply chain management

Observations from the Data sales_train.csv (Sales Data) date:
1034 unique dates — suggests daily data over a period of 34 months (date_block_num).
shop_id: 60 unique shops.
item_id: 21,807 unique items.
item_price: 19,993 unique prices — some items may have fluctuating prices.
item_cnt_day: 198 unique sales counts for a day — includes both positive and negative values, possibly returns or corrections.

test.csv (Test Data) :
ID: 214,200 unique entries — this is the number of test samples for which we need to predict.
shop_id: 42 unique shops in the test set — fewer than the training set, so we may need to handle shops that appear in training but not in testing and vice versa.
item_id: 5,100 unique items in the test set — fewer items than in the training set.

This Jupyter Notebook is doing following tasks,
*. Data cleansing and outlier removals
*. Aggregating and analyzing the datat for 33 months
*. Removing the outliers by Sales Count and Item Price

<img width="998" height="607" alt="image" src="https://github.com/user-attachments/assets/ea537d59-5dcf-4775-83b7-1404760a5fce" />

*. Filling the sales data for missing dates, making sure sales is listed for all the sales id and item id combination for every month
*. Spliting the Traning and Testing data like first 25 months for training data and remaining for testing
*. Created the baseline model with dummy classifier

Link to Jupyter Notebook :
https://github.com/chandtr/CapstoneProject/blob/master/SalesPrediction.ipynb

