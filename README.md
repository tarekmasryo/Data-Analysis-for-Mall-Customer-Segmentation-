# 🛍️ Mall Customer Segmentation — KMeans, PCA & DBSCAN

## 📌 Project Overview
This project segments **mall customers** into distinct behavioral groups using **unsupervised learning**.  
By understanding demographics and spending patterns, we design **targeted marketing strategies**, boost **engagement**, and improve **loyalty**.

We identify **six customer segments** and turn them into **actionable personas** with clear playbooks.

---

## 📊 Dataset
- **Size:** 200 customers  
- **Features:** `Gender`, `Age`, `Annual Income (k$)`, `Spending Score (1–100)`

---

## 🔧 Methodology (Upgraded)
1) **Data Cleaning & Prep**  
   - Drop duplicates, rename columns, encode `Gender` (Male=1, Female=0).  
   - Create **`Spend_Income_Ratio` = Spending Score / (Annual Income + ε)**.

2) **Scaling & Dimensionality Reduction**  
   - `StandardScaler` for modeling features.  
   - **PCA (2D)** for visual separation (explained variance typically **~90–95%**).

3) **k-Selection (Enhanced)**  
   - Evaluate **k=2…10** using:  
     - **Elbow (Inertia)**  
     - **Silhouette** (cohesion/separation)  
     - **Calinski–Harabasz (CH)**  
   - Choose **best_k** where Silhouette peaks and CH is high (usually **k=6** on this dataset).

4) **Clustering Algorithms (Comparison)**  
   - **KMeans** (primary)  
   - **Agglomerative Clustering** (baseline)  
   - **Gaussian Mixture (GMM)** (soft clusters)

5) **Outlier Detection**  
   - **DBSCAN** with k-distance heuristic (ε ≈ 90th percentile) to flag unusual shoppers.

6) **Evaluation & Visualization**  
   - Metrics: **Silhouette**, **Davies–Bouldin (DB)**, **Calinski–Harabasz (CH)**.  
   - Visuals: PCA scatter, Income×Spending with **centroids**, heatmaps, radar charts, pairplots, DBSCAN k-distance.

7) **Persona Generation (Auto)**  
   - Rules driven by **Income** & **Spending** (and optionally **Age**) to avoid manual label mix-ups.  
   - Export **persona table** for the CRM.

---

## 🧠 Features Used
- Core: `Age`, `Annual Income`, `Spending Score`  
- Engineered: **`Spend_Income_Ratio`**

---

## 📈 Results & Insights (typical with `random_state=42`)
- **Best k (KMeans):** **6**  
- **Quality:** Silhouette **≈ 0.43–0.50**, DB **≈ 0.8–0.9**, CH **peaks ~140** at k=6.  
- **Model comparison:** KMeans usually tops Silhouette; Agglomerative slightly lower; GMM comparable but softer boundaries.  
- **PCA (2D):** explains **~90–95%** of variance → clusters are clearly separable in 2D.  
- **Outliers (DBSCAN):** small set of shoppers flagged (potential VIPs or at-risk).  
- **Drivers:** `Spending Score` and `Annual Income` dominate; `Spend_Income_Ratio` isolates **budget enthusiasts**.

---

## 🧩 Cluster Personas (Auto-Generated)
> Names are assigned **programmatically** from cluster means (no manual mismatch if labels change).

| Persona | Traits (typical) | Strategy |
|---|---|---|
| **VIP Big Spenders** | High income • High spend | Exclusive bundles, early access, VIP events |
| **Affluent Savers** | High income • Low spend | Premium upsell, concierge nudges |
| **Budget Enthusiasts** | Low income • High spend | Student deals, entry-level products |
| **Balanced Shoppers** | Mid income • Mid spend | Value bundles, loyalty perks |
| **Senior Steady Spenders** | Older • Moderate spend | Classic products, comfort & loyalty |
| **Disengaged Adults** | Low income • Low spend | Win-back flows, limited-time offers |

> The exact **cluster → persona** mapping is produced by the code based on the cluster averages.

---

## 🗺️ Visual Gallery
- **Elbow + Silhouette + CH** (k-selection)  
- **PCA scatter** with cluster coloring  
- **Income × Spending** with **centroids**  
- **Heatmap** of cluster means (Age, Income, Spending)  
- **Radar charts** for quick cluster fingerprints  
- **Pairplots** (original & with PCA axes)  
- **DBSCAN k-distance** & outlier summary

---

## 💡 Business Recommendations
- Design **tailored campaigns** per persona (VIP exclusives, student offers, win-back discounts).  
- Launch **loyalty** for steady spenders; **premium upsell** for affluent savers.  
- Use targeted **SMS/Email/Push** for low-activity and price-sensitive groups.  
- Track **segment migration** monthly; intervene before high-value customers churn.  
- Store **cluster IDs** to power **personalized onsite content** and **ad audiences**.

---

## ⚠️ Limitations
- Small sample (200 rows) and limited features (no RFM, categories, or purchase history).  
- KMeans is sensitive to scaling/initialization; DBSCAN depends on ε/min_samples.  
- Validate on a larger, real-world dataset before production.

---

## 🔭 Future Work
- Enrich with **RFM**, product mix, channels, and geo.  
- Test **hierarchical/GMM/spectral** and **stability** (e.g., bootstrapped ARI).  
- Tie segments to **KPIs** (conversion, AOV, retention, CAC/LTV) with A/B tests.  
- Build **CLV** & **churn** models; align incentives by lifetime value and risk.  
- Operationalize: nightly scoring, **feature store**, and **drift monitoring**.

---

## 🧪 Repro Notes
- Typical run uses: `random_state=42`, features = `[Age, Annual Income, Spending Score, Spend_Income_Ratio]`.  
- **k-selection:** pick the k where **Silhouette** peaks and **CH** is high; visually confirm separation on **PCA**.  
- **Personas** are generated from the profile table **each run** (no hard-coded cluster numbers).

---

## 📎 Deliverables
- Notebook with: EDA, k-selection plot, algorithm comparison, PCA plots, centroids plot, persona table.  
- Exportable tables: **`profile`**, **`persona_df`**, and outlier list from **DBSCAN**.

---

**TL;DR**: Clear **six-segment** structure, clean visuals, and **auto-generated personas** that translate directly into **marketing playbooks**.
