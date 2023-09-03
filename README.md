# RFM-Customer-Segmentation
This is a transnational data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail. The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers. 
<br>Dataset source: http://archive.ics.uci.edu/dataset/352/online+retail
<br>
Feature Information:
<br>
**InvoiceNo**: Invoice number. *Nominal*, a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter 'c', it indicates a cancellation. 
<br>
**StockCode**: Product (item) code. *Nominal*, a 5-digit integral number uniquely assigned to each distinct product.
<br>
**Description**: Product (item) name. *Nominal*. 
<br>
**Quantity**: The quantities of each product (item) per transaction. *Numeric*.
<br>
**InvoiceDate**: Invoice Date and time. *Numeric*, the day and time when each transaction was generated.
<br>
**UnitPrice**: Unit price. *Numeric*, Product price per unit in sterling.
<br>
**CustomerID**: Customer number. *Nominal*, a 5-digit integral number uniquely assigned to each customer.
<br>
**Country**: Country name. *Nominal*, the name of the country where each customer resides.
<br>
<br>

**RFM**: Recency, Frequency and Monetary
To prepare the data for RFM analysis, conduct exploratory data analysis (EDA) and data visualization to observe data structure and missing values. Perform descriptive analysis to understand feature relationships, clear noise, and address missing values in the dataset, making it ready for RFM analysis. Analyze distribution of Orders, Customers, and Countries before RFM analysis to inform sales policies and resource utilization.
<br>
Focus on UK transactions for RFM Analysis, Customer Segmentation, and K-Means Clustering due to its highest sales revenue and customer count. Use RFM Analysis, a customer segmentation technique based on past purchasing behavior, to develop targeted approaches for better customer understanding, trend observation, and increased retention and sales. Calculate Recency, Frequency, and Monetary values for UK transactions to create an RFM table.
<br>
In the Customer Segmentation section, create an RFM Segmentation Table to categorize customers based on their RFM values (e.g., "Big Spenders," "Lost Customer").
<br>
Compare manual customer segmentation with K-Means, DBSCAN, and Gaussian Mixture Clustering algorithm results to evaluate its effectiveness in customer clustering. Preprocess data for K-Means Clustering, including examining feature correlations, distributions, and normalizing the data. Determine the optimal number of clusters using the Elbow method and Silhouette Analysis. Visualize cluster distribution using a scatter plot and interpret results using boxplots.
<br>
# Project Structures
-Data Cleaning & Feature Engineering
<br>
-Exploratory Data Analysis
<br>
-RFM Analysis
<br>
-Customer Segmentation
<br>
-Applying K-Means Clustering
<br>
-Applying DBSCAN Clustering
<br>
-Applying Gaussian Mixture Clustering
<br>

**CONCLUSION**
<br>
***K_Means Clustering Outcomes***
</br>

Clustering is an unsupervised machine learning technique used to uncover underlying groups within data. One common approach for this is the K-means clustering algorithm, which is frequently employed to identify distinct segments within a customer dataset.

Our dataset is large so Hierarchical clustering is not well suited for analysis.

During the process of building a KMeans model, it's essential to specify the number of clusters beforehand. To determine the most appropriate number of clusters, various methods like silhouette analysis and the elbow method can be utilized. These techniques aid in selecting the optimal number of clusters that best represents the inherent structure of the data.
</br>

**[Elbow Method](https://www.statology.org/elbow-method-in-python/)**</br>
One of the most common ways to choose a value for K is known as the elbow method, which involves creating a plot with the number of clusters on the x-axis and the total within sum of squares on the y-axis and then identifying where an “elbow” or bend appears in the plot.</br>

The point on the x-axis where the “elbow” occurs tells us the optimal number of clusters to use in the k-means clustering algorithm.
![image](https://github.com/senadnmzky/RFM-Customer-Segmentation/assets/56525534/688eb1a9-61cb-4c07-8023-dce20cff8cd3)

As we analyze the graph depicting the sum of squared errors for various values of K, it's evident that the error tends to decrease with the increasing number of clusters. However, upon closer examination, when K reaches around 4 or 5, the rate of error reduction becomes notably steeper. This implies that by adding more clusters, the reduction in error becomes marginal compared to the increment in cluster count.</br>

Each cluster in this context corresponds to a distinct customer segment. Implementing tailored policies for each of these segments requires additional resources and planning. As the number of clusters rises, the organization incurs extra costs to devise and execute individualized strategies for each segment.</br>

Hence, while it's tempting to consider a higher number of clusters to capture finer details in customer behavior, this can lead to diminishing returns in terms of error reduction and increased operational complexity. Striking a balance is crucial, and in this case, opting for K=4 appears reasonable. This choice offers a good compromise between reducing errors through segmentation and managing the practicality of implementing policies for the distinct customer groups.</br>

[Silhouette Coefficient](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_silhouette_analysis.html)</br>
The overall silhouette score for a clustering can be computed by taking the average silhouette coefficient across all data points. This score provides insight into how well the data is clustered and whether the chosen number of clusters is appropriate. Higher silhouette scores indicate better-defined clusters.</br>
![image](https://github.com/senadnmzky/RFM-Customer-Segmentation/assets/56525534/e4e07573-3050-4e07-a2dd-2fb50e05d339)


**Outcomes by Elbow method and Silhoutte score**</br>

Based on the results obtained, selecting the ***highest silhouette score*** suggests that there could be ***two*** distinct clusters. On the other hand, choosing the ***lowest elbow squared error*** indicates that there might be around ***ten*** clusters. </br>

As a result, in order to determine the most suitable number of clusters based on graphics, it is necessary to carefully consider the outcomes, and it appears that opting for a solution with ***four different cluster groups*** could be a ***balanced approach***. </br>

**K=4 have optimal score. Let's visualize these clusters.** </br>


| | **Recency** |**Frequency**|**Monetary**|
|:--------:|:--------:|:--------:|:--------:|
|**Cluster**| | ||
|0|6|203|3823|
|1|70|66|1137|
|2|144|10|226|
|3|13|30|480|
</br>
</br>


|**Cluster Number**| **RFM Decoding Customer Value** |**Type of Customer**|
|:--------:|:--------:|:--------:|
|0|Bought most recently but low frequency and monetary|New Customers|
|1|Last bought while ago and less frequent and spend the most|Risky Customers|
|2|Bought most recently and most often, and spend the most|Best Customers|
|3|Bought long time ago and least frequency and monetary|Churned Customer|
</br>
</br>
</br>

***DBSCAN (Density-Based Spatial Clustering of Applications with Noise) Clustering Outcomes***
</br>

K-Means and Hierarchical Clustering struggle with creating clusters of complex shapes and adapting to varying densities. In contrast, DBSCAN excels by grouping densely packed data points into clusters and effectively identifying clusters in large spatial datasets based on local density.
The most exciting feature of DBSCAN clustering is that it is robust to outliers.
</br>
| | **Recency** |**Frequency**|**Monetary**|
|:--------:|:--------:|:--------:|:--------:|
|**Cluster**| | | |
|-1|61|396|21853|
|0|91|82|1420|
|1|245|1|203|
</br>
</br>

|**Cluster Number**| **RFM Decoding Customer Value** |**Type of Customer**|
|:--------:|:--------:|:--------:|
|(-1)|Bought most recently and most often, and spend the most|Best Customers|
|0|Last bought while ago and less frequent and spend the most|Risky Customers|
|1|Bought long time ago and least frequency and monetary|Churned Customer|
</br>
</br>

***Gaussian Mixture Model(GMM) Outcomes***
</br>

Gaussian Mixture Models is a statistical model that represents data as a combination of multiple Gaussian distributions. It assumes that the data is generated from a mix of these distributions, each characterized by its own average, spread, and weight. GMMs are used for tasks like clustering and data modeling. They assign probabilities to data points belonging to each Gaussian component and find the best parameters through the Expectation-Maximization (EM) algorithm. This makes GMMs valuable for understanding complex datasets with hidden patterns or clusters.
</br>

| | **Recency** |**Frequency**|**Monetary**|
|:--------:|:--------:|:--------:|:--------:|
|**Cluster**| | | |
|0|8|260|8141|
|1|185|24|926|
|2|34|91|701|
|3|111|64|1240|
</br>
</br>

|**Cluster Number**| **RFM Decoding Customer Value** |**Type of Customer**|
|:--------:|:--------:|:--------:|
|0|Bought most recently and most often, and spend the most|Best Customers|
|1|Bought long time ago and least frequency and monetary|Churned Customer|
|2|Bought most recently but low frequency and monetary|New Customers|
|3|Last bought while ago and less frequent and spend the most|Risky Customers|
