# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import libraries
2.Read the given CSV file
3.Import KMeans and use for loop to cluster the data.
4.Predict the cluster and plot data graphs.
5.Print the outputs and end the program

## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: HARSHITHA V
RegisterNumber: 212223230074
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv(r"C:\Users\admin\Downloads\Mall_Customers.csv")

data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i,init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
  
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
print("Y Predicted : \n",y_pred)

data['cluster'] = y_pred
df0 = data[data['cluster'] == 0]
df1 = data[data['cluster'] == 1]
df2 = data[data['cluster'] == 2]
df3 = data[data['cluster'] == 3]
df4 = data[data['cluster'] == 4]


plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c='red', label="Cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c='black', label="Cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c='blue', label="Cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c='green', label="Cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c='magenta', label="Cluster 4")
plt.legend()
plt.title("Customer Segments")
```
## Output:

![image](https://github.com/user-attachments/assets/52a695de-ed19-4824-8f13-dd5d6a082155)
![image](https://github.com/user-attachments/assets/d91e0f83-0279-491c-88a7-1cf82e1ef88e)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
