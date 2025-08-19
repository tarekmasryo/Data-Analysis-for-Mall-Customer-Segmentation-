# 🛍️ Mall Customer Segmentation Analysis

## 📌 Project Overview
This project segments **mall customers** into distinct behavioral groups using **clustering algorithms**.  
By understanding demographics and spending patterns, businesses can design **tailored marketing strategies**, boost **engagement**, and improve **customer loyalty**.  

We identified **6 main customer segments**, each with unique characteristics and actionable opportunities.  

---

## 📊 Dataset
- **Size**: 200 customers  
- **Features**:  
  - `Gender`  
  - `Age`  
  - `Annual Income (k$)`  
  - `Spending Score (1–100)`  

---

## 🔧 Methodology
1. **Data Cleaning & Preparation**  
   - Removed duplicates  
   - Encoded gender  
   - Renamed features  

2. **Exploratory Data Analysis (EDA)**  
   - Gender distribution  
   - Correlation matrix & boxplots  
   - Histograms & pairplots  

3. **Feature Scaling & PCA**  
   - StandardScaler applied  
   - PCA used for visualization (2D explained variance >90%)  

4. **Clustering Algorithms**  
   - **KMeans** (best_k determined via Elbow + Silhouette)  
   - **DBSCAN** (to detect outliers)  

5. **Evaluation Metrics**  
   - **Silhouette Score**  
   - **Davies-Bouldin Score**  

6. **Visualization**  
   - PCA scatter plots  
   - Radar charts for cluster profiles  
   - Heatmaps & bar plots  
   - Pairplots (original + PCA axes)  

---

## 📈 Results & Insights
- **Best number of clusters (KMeans): 6**  
- **Evaluation**:  
  - Silhouette Score: ~0.43  
  - Davies-Bouldin Score: ~0.83  
- **Cluster Personas**:

| Cluster | Avg Age | Avg Income | Avg Spending | % Male | Count | Persona / Strategy |
|---------|---------|------------|--------------|--------|-------|---------------------|
| 0 | 56.3 | 54.3 | 49.1 | 42.2% | 45 | Senior steady spenders – loyalty |
| 1 | 32.7 | 86.5 | 82.1 | 46.2% | 39 | Young VIPs – luxury offers |
| 2 | 25.6 | 26.5 | 76.2 | 44.0% | 25 | Budget youth – student deals |
| 3 | 26.1 | 59.4 | 44.4 | 40.0% | 40 | Cautious earners – incentives |
| 4 | 44.0 | 90.1 | 17.9 | 53.3% | 30 | Affluent savers – premium upgrades |
| 5 | 45.5 | 26.3 | 19.4 | 38.1% | 21 | Disengaged adults – reactivation |

---

## 💡 Business Recommendations
- 🎯 **Targeted campaigns** for each cluster (luxury offers for VIPs, discounts for disengaged).  
- 🏆 **Loyalty programs** for senior steady spenders.  
- 📢 **Student promotions** for budget youth.  
- 📬 **Reactivation campaigns** for dormant customers.  
- 📊 **Continuous monitoring**: update clusters as customer behavior evolves.  

---

## ⚠️ Limitations
- Dataset is small (200 customers).  
- Limited features (no purchase frequency, categories, or history).  
- Results need validation on larger, real-world data.  

---
