# Cryptocurrencies
Module 18: Unsupervised Machine Learning and Cryptocurrencies
## Overview
The aim is to create an analysis for the cryptocurrency market. Create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this an investment portfolio for cryptocurrencies. The data needs to be processed to fit the machine learning models. Since there is no known output we have decided to use unsupervised learning. To group the cryptocurrencies, we decided on a clustering algorithm. Lastly we will use data visualizations to share our findings.
## Deliverable 1: Preprocessing the Data for PCA
The dataset in csv format is read in to crypto_df dataframe with the 'Unnamed Column: 0' column as the index. 

<img width="560" alt="Screenshot 2021-12-30 at 19 20 26" src="https://user-images.githubusercontent.com/87828174/147796053-23f90a5c-3139-4ca7-9df1-0a7f29068b08.png">

The following preprocessing is done on the dataframe:

- All cryptocurrencies that are not being traded are removed
- The IsTrading column is dropped
- All the rows that have at least one null value are removed
- All the rows that do not have coins being mined are removed
- The CoinName column is dropped

The final crypto_df dataframe looks like this.

<img width="427" alt="Screenshot 2021-12-30 at 19 31 40" src="https://user-images.githubusercontent.com/87828174/147796380-d372f9cb-46dc-4d6f-ad9d-3517ca02e414.png">

Additionally, a new DataFrame is created that stores all cryptocurrency names from the CoinName column and retains the index from the crypto_df DataFrame. The get_dummies() method is used to create variables for the text features, which are then stored in a new DataFrame, X. 

<img width="1102" alt="Screenshot 2021-12-30 at 19 20 58" src="https://user-images.githubusercontent.com/87828174/147796062-ceb3c75d-5071-4af5-abec-8a8ea17a136f.png">

The features from the X DataFrame are standardized using the StandardScaler fit_transform() function.

## Deliverable 2: Reducing Data Dimensions Using PCA
The PCA algorithm reduces the dimensions of the X DataFrame down to three principal components. The pcs_df DataFrame is created and has the following three columns, PC 1, PC 2, and PC 3, and has the index from the crypto_df DataFrame.

<img width="264" alt="Screenshot 2021-12-30 at 19 21 06" src="https://user-images.githubusercontent.com/87828174/147796068-64cee54a-1855-4ab4-a156-52db510dd908.png">

## Deliverable 3: Clustering Cryptocurrencies Using K-means
The K-means algorithm is used to cluster the cryptocurrencies using the PCA data, where the following steps have been completed:

- An elbow curve is created using hvPlot to find the best value for K

<img width="728" alt="Screenshot 2021-12-30 at 17 39 03" src="https://user-images.githubusercontent.com/87828174/147796127-f7420bbe-8cc4-45bd-a1da-e046a6593c4c.png">

- Using K = 4, predictions are made on the K clusters of the cryptocurrencies’ data
- A new DataFrame is created called clustered_df with the same index as the crypto_df DataFrame and has the following columns: Algorithm, ProofType, TotalCoinsMined, TotalCoinSupply, PC 1, PC 2, PC 3, CoinName, and Class. Class contains the predictions from the K-Model.

<img width="831" alt="Screenshot 2021-12-30 at 19 24 30" src="https://user-images.githubusercontent.com/87828174/147796158-b622d277-2626-405d-9e69-50e2a1ec7545.png">

## Deliverable 4: Visualizing Cryptocurrencies Results

- The clusters are plotted using a 3D scatter plot, and each data point shows the CoinName and Algorithm on hover

<img width="955" alt="Screenshot 2021-12-30 at 17 39 37" src="https://user-images.githubusercontent.com/87828174/147796179-f1240cc1-ba37-4966-afeb-c23a0086a32c.png">

- A table with tradable cryptocurrencies is created using the hvplot.table() function

<img width="647" alt="Screenshot 2021-12-30 at 17 39 46" src="https://user-images.githubusercontent.com/87828174/147796192-7ae08cf3-d930-412a-974c-a7165f79f87b.png">

- The total number of tradable cryptocurrencies is printed which is 532

<img width="318" alt="Screenshot 2021-12-30 at 19 27 29" src="https://user-images.githubusercontent.com/87828174/147796259-2b9323e9-4a3a-467b-a938-adf68ac8ae06.png">

- A DataFrame is created that contains the clustered_df DataFrame index, the scaled data, and the CoinName and Class columns

<img width="435" alt="Screenshot 2021-12-30 at 19 26 31" src="https://user-images.githubusercontent.com/87828174/147796237-e074f3f1-482a-410d-856c-ee509b5b115e.png">

- A hvplot scatter plot is created where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it shows the CoinName when you hover over the data point

<img width="735" alt="Screenshot 2021-12-30 at 17 39 57" src="https://user-images.githubusercontent.com/87828174/147796274-b05f6524-d54b-419c-8d9d-af684611bdad.png">



