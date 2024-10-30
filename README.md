# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement.
2. Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().
3. Import KMeans and use for loop to cluster the data and Predict the cluster and plot data graphs.
4. Print the outputs and end the program


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: ARAVIND G
RegisterNumber:  212223240011
*/
```
```
import pandas as pd 
import matplotlib.pyplot as plt
d=pd.read_csv("Mall_Customers.csv")
```
## DATA SET:
```
d.head()
```
![Screenshot 2024-10-30 111728](https://github.com/user-attachments/assets/468c59d0-fd0c-4012-b179-034f8c6feec3)

## DATA INFO:
```
d.info()
```
![Screenshot 2024-10-30 111956](https://github.com/user-attachments/assets/930a5110-16d8-4066-9e03-c7e94a7b4622)
```
d.isnull().sum()
```
![Screenshot 2024-10-30 112055](https://github.com/user-attachments/assets/cb132af9-90c0-402c-adbb-1ab0855b75df)
## Elbow method graph (wcss vs each iteration):
```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    Kmeans=KMeans (n_clusters = i, init ="k-means++")
    Kmeans.fit(d.iloc[:,3:])
    wcss.append(Kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Metthod")
km=KMeans(n_clusters=5)
km.fit(d.iloc[:,3:])
y_pred = km.predict(d.iloc[:,3:])
y_pred
```
![Screenshot 2024-10-30 112353](https://github.com/user-attachments/assets/d906c6e8-bbac-46e9-9f8e-fec9ed0eec0e)
## Cluster represnting customer segments-graph:
```
d["clusters"]=y_pred
df0=d[d["clusters"]==0]
df1=d[d["clusters"]==1]
df2=d[d["clusters"]==2]
df3=d[d["clusters"]==3]
df4=d[d["clusters"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="clusters0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="clusters1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="clusters2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="clusters3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="black",label="clusters4")
plt.legend()
plt.title("Customer Segments")
```
![Screenshot 2024-10-30 112457](https://github.com/user-attachments/assets/f3f26dcf-72ca-4940-b6d3-7ca0c17d3cb7)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
