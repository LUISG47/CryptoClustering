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

<img width="737" alt="Screenshot 2025-03-01 at 8 46 18 p m" src="https://github.com/user-attachments/assets/2e325bf4-8c77-434e-97e2-8fa4e9f2aa13" />




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

<img width="746" alt="Screenshot 2025-03-01 at 8 47 01 p m" src="https://github.com/user-attachments/assets/80d64695-19dd-48a9-8bcb-e67f60ef2efa" />


## Optimize Clusters with Principal Component Analysis

+ Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.
+ Retrieve the explained variance to determine how much information can be attributed to each principal component and then answer the following question in your notebook:
  + What is the total explained variance of the three principal components?

If we sum the different variances from the PCA : 0.3719856 + 0.34700813 + 0.17603793 = 0.89503166 **This means that these 3 principal components capture 89.5% approximmately from the original dataset**

+ Create a new DataFrame with the scaled PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame
  + The first five rows of the scaled PCA DataFrame should appear as follows:
 
<img width="349" alt="Screenshot 2025-03-01 at 8 49 15 p m" src="https://github.com/user-attachments/assets/8779198a-2e0d-49a5-9e47-0588675af575" />

## Find the Best Value for k Using the PCA DataFrame

Use the elbow method on the scaled PCA DataFrame to find the best value for k using the following steps:

+ Create a list with the number of k-values from 1 to 11.
+ Create an empty list to store the inertia values.
+ Create a for loop to compute the inertia with each possible value of k.
+ Create a dictionary with the data to plot the Elbow curve.
+ Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.
+ Answer the following question in your notebook:
  + What is the best value for k when using the scaled PCA DataFrame?
  + Does it differ from the best k value found using the original scaled DataFrame?

The resulting graph should look as follows:

<img width="741" alt="Screenshot 2025-03-01 at 8 54 47 p m" src="https://github.com/user-attachments/assets/c9dc2f55-ebbc-4507-befd-44c540b6d927" />

As we can see for this plot the best number of clusters is also 4, so it doesn't differ from the best k value using the original scaled DF

## Cluster Cryptocurrencies with K-means Using the PCA DataFrame

Use the following steps to cluster the cryptocurrencies for the best value for k on the PCA DataFrame:

+ Initialize the K-means model with the best value for k.
+ Fit the K-means model using the scaled PCA DataFrame.
+ Predict the clusters to group the cryptocurrencies using the scaled PCA DataFrame.
+ Create a copy of the scaled PCA DataFrame and add a new column to store the predicted clusters.
+ Create a scatter plot using hvPlot as follows:
  + Set the x-axis as "PC1" and the y-axis as "PC2"
  + Color the graph points with the labels found using K-means.
  + Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.
 
The resulting plot should look like this:

<img width="723" alt="Screenshot 2025-03-01 at 8 57 39 p m" src="https://github.com/user-attachments/assets/4c5f67ee-886f-479f-8dd2-7e46ceb5cc3a" />


Answer the following question:
+ What is the impact of using fewer features to cluster the data using K-Means?

To answer this question we will use composite graphs to watch the difference:


<img width="850" alt="Screenshot 2025-03-01 at 8 59 06 p m" src="https://github.com/user-attachments/assets/b1a4645e-e4c3-4eb4-bd8f-a682a92eb430" />

![bokeh_plot-8](https://github.com/user-attachments/assets/6a5c49c6-35ce-4b67-8a83-859b6db31c4a)


### CONCLUSION

As we can see in the graph, reducing the information with PCA results in having more compact information and more organized groups. The scatter in the graph with PCA is less noisy than the clusters with the original scaled data. This is due to PCA's goal of capturing the most variance in the data with fewer features. As a result, we get a display with less noise when the groups are more condensed.



