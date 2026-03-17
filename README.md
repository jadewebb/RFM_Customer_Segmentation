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
**RFM** (Recency, Frequency, Monetary Value) metrics were calculated and **standardized** for each of the 4338 unique customers

**Silhouette** and **Elbow** methods were used to suggest optimal K-Means cluster counts of k=4 and k=5

![K-Means Optimal Cluster Count Visualizations](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/K-Means%20Optimal%20Cluster%20Counts.png)

**Two K-Means models (k=4 and k=5)** were used to cluster the RFM data, with clusters visualized in 3D and in 2D via **t-SNE embedding**

![K-Means Clusterings - 3D](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/K-Means%20Clusterings%20-%203D.png)

![K-Means Clusterings - 2D Embeddings](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/K-Means%20Clusterings%20-%202D%20Embeddings.png)

## Segmentation Business Analysis
The **k=5** K-Means model was selected as the final model based on visual indication that k=5 preserves **meaningful subgroups** across the spectrum of customers in the low recency region

Five distinct **customer profiles** were identified, analyzed, and visualized based on RFM averages and cluster counts, to obtain actionable business insights based on customer behavior

Analysis reveals that this online retail business is relying on a **small number of big spenders**, as most customers belong to the At-Risk and Low-Value RFM clusters. This highlights the business value of taking **immediate action** to **win back** At-Risk Customers and **re-engage** Low-Value Customers, as well as retain Champion/VIP Customers, upgrade Loyal Customers, and solidify relationships with Potential Loyalists.

![RFM Business Analysis - Customer Profiles](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/RFM%20Business%20Analysis%20-%20Customer%20Profiles.png)

![RFM Business Analysis - Customer Distribution](https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/RFM%20Business%20Analysis%20-%20Customer%20Distribution.png)

<img src="https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/RFM%20Business%20Analysis%20-%20Heatmap.png" width="700">

<img src="https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/RFM%20Business%20Analysis%20-%20Radar%20Chart.png" width="580">

<img src="https://raw.githubusercontent.com/jadewebb/RFM_Customer_Segmentation/main/Visualizations/RFM%20Business%20Analysis%20-%20Bubble%20Plot.png" width="600">
