# Online-Retail-Customer-Segmentation

![Retail customer segmentation project](https://user-images.githubusercontent.com/104018984/203330270-ac08ce23-d417-4a0e-97bf-4af8db5e8b34.jpeg)

## Problem Description: 

The main goal is to identify major customer segments like customers that are most profitable and the ones who churned out using Unsupervised ML Clustering Algorithms to prevent further loss of customer by redefining company policies. In this project, our task is to identify major customer segments on a transnational dataset which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail. The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers. The dataset provided contains information about Invoice No, Stock Code, Description, Quantity, Invoice Date, Unit Price, Customer ID and Country for each transaction.

## Data Description:

The dataset contains transactions between 01/12/2010 and 09/12/2011 with 541909 rows and 8 features.

* **InvoiceNo**: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each
transaction. If this code starts with letter 'c', it indicates a cancellation.
* **StockCode:** Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each
distinct product.
* **Description:** Product (item) name. Nominal.
* **Quantity:** The quantities of each product (item) per transaction. Numeric.
* **InvoiceDate:** Invoice Date and time. Numeric, the day and time when each transaction was
generated.
* **UnitPrice:** Unit price. Numeric, Product price per unit in sterling.
* **CustomerID:** Customer number. Nominal, a 5-digit integral number uniquely assigned to each
customer.
* **Country:** Country name. Nominal, the name of the country where each customer resides.


## Steps Involved:-

### 1. Data Preprocessing: 

Started with understanding the dataset, some basic inspection like checking columns, data statistics, missing values, duplicate values after that handling those null values, duplicates and some data cleaning. Following are the observation's in this stage: 

* The dataset has 541909 observations and 8 features/columns.

* Our dataset possess high null values in CustomerID and Description column. Around
25% missing values are there in CustomerID and 0.26% null values present in
Description column.

* Also the dataset contains a total of 5225 observations which are duplicate.

* We have to drop all null values and duplicate observations because each CustomerID
are uniquely assigned to a particular customer which means that we cannot impute it
with any other values from the dataset.

* After dealing with null and duplicate values we were left with 401604 instances/rows
and 8 features in our dataset.

### 2. Feature Engineering:

Feature engineering is a machine learning technique that leverages data to create new variables that aren't in the training set. 

In this we extracted new features named Year, Month, Day, Hour from the DateTime column named InvoiceDate.
Also we created a new feature 'TotalAmount' by multiplying Quantity and UnitPrice. 

### 3. Exploratory Data Analysis:

After feature engineering, we did some data analysis and drew some insights like- the United Kingdom has the most number of customers and the most number of purchases as compared to other countries. Also, most orders are placed between 10:00 AM to 3:00 Pm. From this, we also inferred the top customers and top products for our business.

### 4. RFM Analysis: 

After EDA we built an RFM-based model for finding segments where R is Recency(how recently a purchase happened), F is Frequency(how frequent transactions are made), and M is Monetary value(Value of all transactions for a customer). Recency, Frequency, and Monetary score for each customer are calculated. The latest data is assigned as a placeholder to calculate recent purchases. All the transactions are grouped using CustomerID and then aggregate lambda operations are performed. As a result of this operation, numbers were obtained which depict the recency, frequency, and how much a specific customer spent to date. All these are stored in a new data frame RFM.

**Perception of RFM score**:

*  If the RFM score of any customer is 111. His Recency is good, frequency is more and Monetary is more. So, he is the best customer. 

* If the RFM score of any customer is 444. His Recency is low, frequency is low and Monetary is low. So, he is the churning customer. 

* If the RFM score of any customer is 411. He purchased a long time ago but buys frequently and spends more. And so on.

* Like this, we can come up with several segments for all combinations of R, F, and M based on our use case. The lower the RFM score, the more valuable the customer is to the business. 


## Model Summary: 

* We started with binning of RFM Score and RFM Group segmentation model, then moved to more complex models.

* We moved to k-means clustering , we selected optimal number of clusters with the help of Elbow Curve and Silhouette Score and visualized the results with different number of clusters. As we know there is no assurance that k-means will lead to the global best solution. We moved forward and tried Hierarchical Clustering as well.

* We created several useful clusters of customers on the basis of different metrics and methods to categorize the customers on the basis of their beavioural attributes to define their valuability, loyality, profitability etc. for the business. Though significantly separated clusters are not visible in the plots, but the clusters obtained is fairly valid and useful as per the algorithms and the statistics extracted from the data.

## Results: 

**Cluster Summary:** 

+---------+----------------------------------------+------+---------------------------+
| Sr. No. |               Model_Name               | Data | Optimal_Number_of_cluster |
+---------+----------------------------------------+------+---------------------------+
|    1    |                K-Means                 | RFM  |             3             |
|    2    |     K-Means with silhouette_score      | RFM  |             2             |
|    3    |      K-Means with Elbow method         | RFM  |             4             |
|    4    |       Hierarchical clustering          | RFM  |             2             |
|    5    | Hierarchical clustering after Cut-off  | RFM  |             3             |
+---------+----------------------------------------+------+---------------------------+

















