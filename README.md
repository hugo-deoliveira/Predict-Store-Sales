# Store Sales Prediction

## Code and resources used
**Python version**: 3.8  
**Packages**: matplotlib, numpy, pandas, scipy, seaborn, shap, sklearn, xgboost  
**Dataset**: https://www.kaggle.com/c/store-sales-time-series-forecasting

## A first look at the dataset and data cleaning
This dataset is part of a Kaggle Competition where the user must be able to predict sales based on a forecast dataset.  
The dataset is composed of 7 files, only 1 is the dataset to be used to predict future data (16/08 ~ 31/08), all others are information about sales, transactions, gas price, holidays and stores. So the first task is to merge all the data into a single file. After that, those are the informations that we have to train our model:
* Date
* Store number
* Product family
* Store sales
* Products on promotion
* Holidays (It's easy to think we have an addition of sales in a holiday. People buy more to commemorate, to chill with family or friends...)
* Holidays transferred (Some holidays are transferred to another day, making the actual day of the holiday less important, probably less  impact on sales.)
* City
* State
* Type (There are 5 types of stores)
* Cluster (The stores are grouped in different clusters)
* City holidays
* City holidays transferred
* State holidays
* State holiday transferred
* Daily oil price
* Transactions by store  

After some analysis is possible to discover some numbers:
|  | Total |
| --- | --- |
| Stores | 54 |
| States | 16 |
| City | 22 |
| Product family| 33 |  

In the chart below, we can see the daily sale of all stores, it is possible to notice that sales have increased since 2013, where it has, on average, more than 200 thousand sold, and in 2017 it is most of the time above 400 thousand:
![](/output.png)

And when we look at the annual sales, we can confirm that sales are increasing:
![](/output1.png)

As we have 54 stores, I selected 10 stores to see the average sales for the year. In all the stores observed, it is easy to see the increase in sales:
![](/output3.png)

![](/output4.png)
Above we have the graph that indicates the daily average of products on sale. Until 2014 we do not have any product on sale, in 2014 the average is between 40 and 30 products, in 2017 the daily average is already around 60 products. In the dataset that we will use to forecast sales, the average is above 118 products, this is shown in the graph below, the straight line indicates that the number of products on sale will be fixed.
![](/output5.png)
Looking at the average of products on sale from those 10 selected stores, in all stores the number of promotions increased over the years:
![](/output6.png)

## Regression
Tried linear regression and XGBoost on this dataset. Using linear regression I got 1,932 in RMSE and 0.41 in R², using XGBoost I got 0.280 in RMSE and R² of 0.98. Therefore, the model used to forecast sales will be XGBoost.  
Analyzing the main impact on the model is easy to understand the power of promotion on sales, even more so than on holidays, as stores often try out multiple promotions before the holidays to increase sales. It would be a good exercise to try A/B test on holidays using some group of stores with promotions and another without, to test how holidays alone could increase sales. What we can get here is how promotions impact sales.
![](/output7.png)
![](/output8.png)


## Testing
As we saw in the section above, the model that used XGBoost gave us a prediction with an R² of 0.98, which means that our model is able to describe 98% of the variations in sales, a good model. The next 9 charts have predictions for different product families using the same dataset used in model training. Predictions are the red line on each graph. It appears to be a good forecasting model.
![](/testing%20(1).png) 
![](/testing%20(2).png)
![](/testing%20(3).png)
![](/testing%20(4).png)
![](/testing%20(5).png)
![](/testing%20(6).png)
![](/testing%20(7).png)
![](/testing%20(8).png)
![](/testing%20(9).png)

## Forecasting
Now we take the model and enter the data intended to be used in the forecast, that dataset with almost twice products on promotion. The result can be seen below, all sales grow:
![](/Predictions%20(1).png) 
![](/Predictions%20(2).png)
![](/Predictions%20(3).png)
![](/Predictions%20(4).png)
![](/Predictions%20(5).png)
![](/Predictions%20(6).png)
![](/Predictions%20(7).png)
![](/Predictions%20(8).png)
![](/Predictions%20(9).png)
This is explained by the impact of promotions on sales results. With such a significant increase in the number of promotions, an increase in sales is expected. The question that must be asked is what is the impact of these promotions on the stores' financial results. If more promotions were not sufficiently compensated by the increase in sales, the store would profit less, this model has no price or cost, more important than the sale is the result.

## Conclusion
The model looks good for predicting sales, but a more interesting task would be to maximize profit. The current model could lead a company to make promotions to increase sales aiming profit, which could be a huge mistake as revenue would be negatively impacted (increase but increase less), but costs will keep increasing.
However, this would still be an option if this were a strategy to make it more attractive to the consumer, even so it would be recommended to study the impact on operating profit, as it would not be a smart idea to become the most beloved chain of stores but with an irrecoverable loss and went bankrupt and closed next month.

