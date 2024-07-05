Table of Contents
1) Project Details
2) Presentation
3) Data Cleaning
4) Data Exploration


Project Overview
* Entire project  was done in python
* Used data cleaning tools with pandas and aggregated the data 
* Data explatory using pandas and
* data visualization using seaborn and matplotib

Project Goal:
* Who are the Top customers in total spending?
* What is the trend in sales revenue over time?
* What is the unit price over year vs the quantity price over year?
* Which countries have the highest total sales per country ?
* What is the average sale per country?
* Which 5 products are the best sellers in terms of quantity sold?

 1) Who are the Top customers in total spending?
    
 ![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/c4f73c7c-a963-4a98-af77-2216670c2bc7)

2) What is the trend in sales revenue over time?
   
![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/0715025c-3178-48c8-808c-4c36dd2c1c04)

3) What is the unit price over year vs the quantity price over year?
   
![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/d20774d6-f7de-4c25-871d-80a78f5ec5c0) ![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/b3708e8c-1737-4a17-b082-3aa8d51f96b8)

4) Which countries have the highest total sales per country ?
   
![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/edde4b66-d736-4db7-8066-e951f0bb012e)

5)What is the average sale per country?

![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/0ce6158e-01d1-4dca-a726-ed5d4d823cbd)

6) Which 5 products are the best sellers in terms of quantity sold?

Description

Paper Craft , Little Birdie           80995

Medium Ceramic Top Storage Jar        77916

World War 2 Gliders Asstd Designs     54319

Jumbo Bag Red Retrospot               46078

White Hanging Heart T-Light Holder    36706






DATA CLEANING

> Import all the modules required
```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
```
Once imported we glance the entire data by using to check for the overall data
```
data.info()
```
![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/f0ae3346-4f8b-4e96-b542-8779ce31399f)

In order to clean few steps are used
* Cleaning Duplicates
```
data = data.drop_duplicates()
```

* Check for Null values
```
data.isnull().sum()
```

![Screenshot 2024-07-04 103319](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/043c1ffe-acd9-497c-99a6-04f494391eb6)

* Dropping all the null values as they are insignificant to the data 
```
data = data.dropna(axis = 0, subset = 'CustomerID')

```

* Next splitting up unncessary added values or random symbols also changing the dtype to string and back to date.

```
data['InvoiceDate'] = data['InvoiceDate'].astype(str)
data['InvoiceDate'] = data['InvoiceDate'].str.split(' ').str[0]
data['InvoiceDate'] = data['InvoiceDate'].astype('datetime64[ns]')
```

```
characters_to_remove = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
for char in characters_to_remove:
  data["StockCode"] = data['StockCode'].str.replace(char, '')

print(data["StockCode"].head())
```
![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/0a3e8a05-5d89-4421-ac41-c178708ca234)


* changing most of the dtype columns
```
data['Year'] = data['Year'].astype(int)
data['Month'] = data['Month'].astype(int)
data['Day'] = data['Day'].astype(int)
data['InvoiceDate'] = data['InvoiceDate'].astype('datetime64[ns]')
```
![image](https://github.com/Srikrishnareddy00/Online_Retail_Sales_Project/assets/152496878/719fcd7d-3a9f-439c-93c7-a6b825e2c8b3)


* Dropping unwanted data and columns as the final step for a clean data
```
data.drop(columns = ['InvoiceDate'])
```

