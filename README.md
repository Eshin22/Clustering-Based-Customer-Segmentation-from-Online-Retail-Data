🛒 Clustering-Based Customer Segmentation from Online Retail Data
📌 Overview

This project focuses on customer segmentation using the Online Retail Dataset (UCI Repository)
.
We apply RFM (Recency, Frequency, Monetary) analysis to build customer profiles and explore different clustering algorithms to group customers into meaningful segments.

The study compares:

K-Means Clustering

Hierarchical Clustering (AGNES)

DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

The goal is to identify customer groups such as Champions, Loyal Customers, Potential Loyalists, and At-Risk Customers to enable better marketing and business strategies.

📂 Dataset

Source: UCI Machine Learning Repository

Data: Transactions from a UK-based online retailer

Fields: InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country

⚙️ Data Preparation & Feature Engineering

Data Cleaning

Remove missing CustomerID records

Filter only United Kingdom transactions

Remove cancelled invoices (InvoiceNo starting with "C")

RFM Features

Recency: Days since last purchase

Frequency: Number of distinct invoices

Monetary: Total purchase value (Quantity × UnitPrice)

Feature Scaling

Standardize RFM data before clustering

Visualization

Histograms, scatter plots, PCA-based cluster plots

🔍 Clustering Methods
1️⃣ K-Means

Used Elbow Method to find optimal clusters

Interpreted centroids as customer segments

2️⃣ Hierarchical Clustering (AGNES)

Tested Single, Complete, and Average Linkage

Visualized dendrograms for cluster selection

3️⃣ DBSCAN

Used k-distance plot to select eps

Set min_samples = D+1 rule

Identified noise/outliers

📊 Evaluation Metrics

Silhouette Score (cluster cohesion & separation)

Intra-cluster vs Inter-cluster distances

Interpretability of customer segments

💡 Business Insights

Champions → Retention strategies, premium offers

Loyal Customers → Loyalty programs, cross-sell opportunities

Potential Loyalists → Engagement campaigns to convert them

At Risk → Reactivation campaigns, win-back discounts

Outliers (DBSCAN) → Fraud detection or anomalies

📑 Deliverables

Well-commented Python code (Jupyter Notebook)

Report (IEEE Format, max 4 pages)

Visualizations of clusters and evaluation results

🚀 Future Work

Explore ensemble clustering or deep clustering approaches

Test on larger e-commerce datasets

Integrate with real-world recommendation systems

👨‍💻 Author

Eshin Menusha
Department of Computer Science & Engineering
University of Moratuwa
