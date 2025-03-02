# CryptoClustering
CryptoClustering

## Instructions

In this challenge, you'll use your knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

## Prepare the Data

+ Use the StandardScaler() module from scikit-learn to normalize the data from the CSV file.
+ Create a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.
  +The first ten rows of the scaled DataFrame should appear as follows:

<img width="1166" alt="Screenshot 2025-03-01 at 8 24 08 p m" src="https://github.com/user-attachments/assets/6c28981e-ae1d-48c0-a40c-29b9a263b512" />

The 1st plot corresponding to the Dataframe should look like this:

![bokeh_plot](https://github.com/user-attachments/assets/7b3c06b3-16ad-4763-b328-b908625f19c3)


## Find the Best Value for k Using the Scaled DataFrame  

Use the elbow method to find the best value for k using the following steps:

+ Create a list with the number of k values from 1 to 11.
+ Create an empty list to store the inertia values.
+ Create a for loop to compute the inertia with each possible value of k.
+ Create a dictionary with the data to plot the elbow curve.
+ Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

This first elbow plot should look like this:

![bokeh_plot-2](https://github.com/user-attachments/assets/4fc81705-65ab-485e-a55f-3924d020d291)

+ Answer the following question in your notebook: What is the best value for k
+ 
As we can see in the plot the best value for k is 4.


## Cluster Cryptocurrencies with K-means Using the Scaled DataFrame

Use the following steps to cluster the cryptocurrencies for the best value for k on the scaled DataFrame:

+ Initialize the K-means model with the best value for k.
+ Fit the K-means model using the scaled DataFrame.
+ Predict the clusters to group the cryptocurrencies using the scaled DataFrame.
+ Create a copy of the scaled DataFrame and add a new column with the predicted clusters.
+ Create a scatter plot using hvPlot as follows:
  + Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
  + Color the graph points with the labels found using K-means.
  + Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

The 1st scatter plot should look like this:

![bokeh_plot-3](https://github.com/user-attachments/assets/b43cc305-ed96-4305-844e-90074c10b710)

## Optimize Clusters with Principal Component Analysis

+ Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.
+ Retrieve the explained variance to determine how much information can be attributed to each principal component and then answer the following question in your notebook:
  + What is the total explained variance of the three principal components?

If we sum the different variances from the PCA : 0.3719856 + 0.34700813 + 0.17603793 = 0.89503166 This means that these 3 principal components capture 89.5% approximmately from the original dataset.



















