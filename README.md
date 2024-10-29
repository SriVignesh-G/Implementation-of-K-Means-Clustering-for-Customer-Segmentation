# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start.
2. Load and explore customer data.
3. Use the Elbow Method to find the best number of clusters.
4. Perform clustering on customer data.
5. Plot clustered data to visualize customer segments.
6. End.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Sri Vignesh G
RegisterNumber: 212223040204
*/

import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans 

data=pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()

wcss=[]
for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred



data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segment")
```

## Output:
### Predicted Y:
![image](https://github.com/user-attachments/assets/c0a5a96f-5997-49a6-824a-f72080e633ef)
### Elbow Method:
![download](https://github.com/user-attachments/assets/f485979f-09d4-42fa-8736-aea51f15caf1)
### Customer Segmentation:
![image](https://github.com/user-attachments/assets/0784adde-6a55-4ef4-82bd-6c7170e6cb79)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
