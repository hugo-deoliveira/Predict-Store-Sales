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



















![](/output.png)
![](/output1.png)
![](/output2.png)
![](/output3.png)
![](/output4.png)
![](/output5.png)
![](/output6.png)
![](/output7.png)
![](/output8.png)



## Teste
![](/testing%20(1).png) 
![](/testing%20(2).png)
![](/testing%20(3).png)
![](/testing%20(4).png)
![](/testing%20(5).png)
![](/testing%20(6).png)
![](/testing%20(7).png)
![](/testing%20(8).png)
![](/testing%20(9).png)

## Previsão
![](/Predictions%20(1).png) 
![](/Predictions%20(2).png)
![](/Predictions%20(3).png)
![](/Predictions%20(4).png)
![](/Predictions%20(5).png)
![](/Predictions%20(6).png)
![](/Predictions%20(7).png)
![](/Predictions%20(8).png)
![](/Predictions%20(9).png)
