# RFM Customer Segmentation

RFM customer segmentation using K-Means clustering 

## Dataset
Online Retail Transaction Dataset from the UC Irvine Machine Learning Repository https://archive.ics.uci.edu/dataset/352/online+retail

- 541909 transaction samples occurring between 01/12/2010 and 09/12/2011 for a UK-based online retailer
  
   - 3 IDs: 
      - InvoiceNo: unique transaction ID
      - StockCode: unique product ID
      - CustomerID: unique customer ID
       
   - 5 Features:
      - Description: product description
      - Quantity: product quantity per transaction
      - InvoiceDate: date and time of transaction
      - UnitPrice: product price per unit
      - Country: country where customer resides

## Cleaning
Dataset was loaded, inspected, and cleaned down to 392688 transaction samples

- Null: drop rows that contain a null value
     
- Duplicates: drop duplicate rows
     
- Format: convert InvoiceDate datatype to DateTime
     
- Impossible Values: drop rows that contain impossible Quantity or UnitPrice values
     
- Feature Extraction: create new Total feature (total spent on product per transaction)
     
- Outliers: clip outliers at the 0.95 quantile to achieve <2 skewness for Quantity, UnitPrice, and Total
        - Feature histograms were used to visualize skewness while determining clip threshold

## K-Means RFM Customer Segmentation
RFM (Recency, Frequency, Monetary Value) metrics were calculated and standardized for each of the 4338 unique customers

Silhouette and Elbow methods were used to suggest optimal K-Means cluster counts of k=4 and k=5

![K-Means Optimal Cluster Count Visualizations](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/K-Means%20Optimal%20Cluster%20Counts.png)

2 K-Means models (k=4 and k=5) were used to cluster the RFM data, with clusters visualized in 3D and in 2D via t-SNE embedding

![K-Means Clusterings - 3D](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/K-Means%20Clusterings%20-%203D.png)

![K-Means Clusterings - 2D Embeddings](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/K-Means%20Clusterings%20-%202D%20Embeddings.png)






