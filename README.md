# Clustering-Based Customer Segmentation from Online Retail Data

## Overview

This project implements advanced customer segmentation techniques using the **Online Retail Dataset** from the UCI Machine Learning Repository. By leveraging **RFM (Recency, Frequency, Monetary) analysis** and multiple clustering algorithms, we identify distinct customer segments to enable data-driven marketing strategies and business decisions.

### Objectives
- Apply RFM analysis to build comprehensive customer profiles
- Compare the effectiveness of different clustering algorithms
- Generate actionable business insights from customer segments
- Provide recommendations for targeted marketing strategies

## Clustering Methods Compared

| Algorithm | Type | Key Features |
|-----------|------|-------------|
| **K-Means** | Centroid-based | Fast, scalable, requires predefined k |
| **Hierarchical (AGNES)** | Connectivity-based | Dendrogram visualization, no predefined clusters |
| **DBSCAN** | Density-based | Handles noise/outliers, discovers arbitrary shapes |

## Dataset Information

**Source**: [UCI Machine Learning Repository - Online Retail Dataset](https://archive.ics.uci.edu/ml/datasets/online+retail)

**Description**: Transactional data from a UK-based online retailer specializing in unique all-occasion gifts.

### Data Fields
- `InvoiceNo`: Unique transaction identifier
- `StockCode`: Product code
- `Description`: Product description
- `Quantity`: Number of items purchased
- `InvoiceDate`: Transaction timestamp
- `UnitPrice`: Price per unit
- `CustomerID`: Unique customer identifier
- `Country`: Customer location

### Dataset Statistics
- **Time Period**: December 2010 - December 2011
- **Total Records**: ~541,909 transactions
- **Unique Customers**: ~4,372 customers
- **Countries**: 38+ countries (focused on UK)

## Methodology

### 1. Data Preprocessing
```python
# Key preprocessing steps
- Remove records with missing CustomerID
- Filter UK-only transactions
- Remove cancelled orders (InvoiceNo starting with 'C')
- Handle negative quantities and prices
- Remove duplicate transactions
```

### 2. RFM Feature Engineering
```python
# RFM Metrics Calculation
Recency (R)  = Days since last purchase (from analysis date)
Frequency (F) = Number of distinct invoices per customer
Monetary (M)  = Total purchase value (Σ Quantity × UnitPrice)
```

### 3. Data Standardization
- Applied StandardScaler to normalize RFM features
- Ensures equal weighting across different scales

### 4. Clustering Implementation

#### K-Means Clustering
- **Optimal Clusters**: Determined using Elbow Method
- **Initialization**: K-means++ for better convergence
- **Evaluation**: Within-cluster sum of squares (WCSS)

#### Hierarchical Clustering (AGNES)
- **Linkage Methods**: Single, Complete, Average
- **Visualization**: Dendrogram analysis
- **Cluster Selection**: Based on dendrogram structure

#### DBSCAN
- **Parameter Selection**: 
  - `eps`: Determined using k-distance plot
  - `min_samples`: Set to D+1 (where D = feature dimensions)
- **Noise Detection**: Identifies outliers and anomalies

## Evaluation Metrics

### Quantitative Measures
- **Silhouette Score**: Measures cluster cohesion and separation
- **Intra-cluster Distance**: Average distance within clusters
- **Inter-cluster Distance**: Distance between cluster centroids
- **Calinski-Harabasz Index**: Ratio of between-cluster to within-cluster dispersion

### Qualitative Assessment
- **Business Interpretability**: Meaningfulness of customer segments
- **Actionability**: Practical application for marketing strategies

## Customer Segments Identified

### Champions
- **Characteristics**: High R, F, M scores
- **Strategy**: VIP treatment, premium products, loyalty rewards

### Loyal Customers
- **Characteristics**: Medium-High F, M; Variable R
- **Strategy**: Loyalty programs, cross-selling, upselling

### Potential Loyalists
- **Characteristics**: High R, Low-Medium F, M
- **Strategy**: Engagement campaigns, personalized offers

### At-Risk Customers
- **Characteristics**: Low R, High F, M (historical value)
- **Strategy**: Win-back campaigns, reactivation discounts

### Outliers (DBSCAN)
- **Characteristics**: Unusual purchasing patterns
- **Applications**: Fraud detection, anomaly analysis

## Key Results

### Algorithm Performance Comparison
| Metric | K-Means | Hierarchical | DBSCAN |
|--------|---------|-------------|---------|
| Silhouette Score | 0.xx | 0.xx | 0.xx |
| Number of Clusters | X | X | X |
| Noise Points | 0 | 0 | XX |
| Computation Time | Fast | Medium | Fast |

## Installation & Usage

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn plotly
```

### Running the Analysis
```bash
# Clone the repository
git clone https://github.com/yourusername/customer-segmentation.git
cd customer-segmentation

# Launch Jupyter Notebook
jupyter notebook Customer_Segmentation_Analysis.ipynb
```

## Project Structure
```
├── data/
│   └── Online_Retail.xlsx          # Raw dataset
├── notebooks/
│   └── Customer_Segmentation_Analysis.ipynb
├── src/
│   ├── data_preprocessing.py
│   ├── rfm_analysis.py
│   ├── clustering_methods.py
│   └── visualization.py
├── results/
│   ├── cluster_plots/
│   ├── evaluation_metrics/
│   └── business_insights/
├── report/
│   └── Customer_Segmentation_Report.pdf
└── README.md
```

## Visualizations

The project includes comprehensive visualizations:
- **RFM Distribution Histograms**
- **Correlation Heatmaps**
- **PCA-based Cluster Plots**
- **Dendrograms** (Hierarchical Clustering)
- **K-distance Plots** (DBSCAN parameter selection)
- **Silhouette Analysis Plots**

## Business Impact

### Marketing Applications
- **Targeted Campaigns**: Segment-specific messaging
- **Resource Optimization**: Focus on high-value customers
- **Churn Prevention**: Proactive retention strategies
- **Customer Lifetime Value**: Predict future value

### Revenue Opportunities
- **Cross-selling**: Recommend complementary products
- **Upselling**: Promote premium alternatives
- **Personalization**: Customized shopping experiences
- **Pricing Strategy**: Segment-based pricing models

## Future Enhancements

### Technical Improvements
- [ ] Implement ensemble clustering methods
- [ ] Explore deep learning clustering (autoencoders)
- [ ] Real-time segmentation pipeline
- [ ] A/B testing framework for segment strategies

### Business Extensions
- [ ] Integration with CRM systems
- [ ] Recommendation engine development
- [ ] Customer journey mapping
- [ ] Multi-channel behavior analysis

## Research Paper

This project is documented in an IEEE-format research paper:
**"Comparative Analysis of Clustering Algorithms for Customer Segmentation in E-commerce"**

*Abstract*: This study presents a comprehensive comparison of clustering algorithms for customer segmentation using RFM analysis on online retail data...

## Contributing

Contributions are welcome! Please read our [Contributing Guidelines](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Eshin Menusha**  
Department of Computer Science & Engineering  
University of Moratuwa  

## References

1. Chen, D., Sain, S. L., & Guo, K. (2012). Data mining for the online retail industry: A case study of RFM model-based customer segmentation using data mining. *Journal of Database Marketing & Customer Strategy Management*, 19(3), 197-208.

2. Dua, D. and Graff, C. (2019). UCI Machine Learning Repository. Irvine, CA: University of California, School of Information and Computer Science.

3. Arthur, D., & Vassilvitskii, S. (2007). k-means++: The advantages of careful seeding. *Proceedings of the Eighteenth Annual ACM-SIAM Symposium on Discrete Algorithms*.

## Acknowledgments

- UCI Machine Learning Repository for providing the dataset
- University of Moratuwa for academic support
- The scikit-learn community for excellent documentation and tools

---
**Star this repository if you found it helpful!**
