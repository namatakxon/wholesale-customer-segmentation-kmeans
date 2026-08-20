# Wholesale Customer Segmentation (K-Means Clustering)

Unsupervised clustering analysis segmenting wholesale customers by spending behavior 
across product categories, with actionable marketing recommendations per segment.

## Dataset

[Wholesale Customers Data](https://archive.ics.uci.edu/ml/datasets/wholesale+customers) 
— UCI Machine Learning Repository (22 KB, CSV)

Spending data across 6 categories: Fresh, Milk, Grocery, Frozen, Detergents_Paper, 
and Delicassen, plus customer Channel (HoReCa vs. Retail) and Region.

## Approach

1. **Data preparation**
   - Dropped `Channel` and `Region` columns to focus purely on spending behavior
   - Standardized all spending features using `StandardScaler`

2. **Determining optimal cluster count**
   - Elbow method (WCSS) across K=1–10
   - Silhouette score across K=2–10
   - Selected K=4 based on these diagnostics

3. **Clustering**
   - Applied K-means (`k-means++` init, K=4) to segment customers
   - Visualized clusters via Seaborn pairplot
   - Compared average spending per category across clusters with bar charts

## Key findings

- **Fresh products** are a universal driver across most clusters
- Two large segments (0 and 2) represent general grocery customers (~70% of the base)
- Two specialized segments stand out: Cluster 1 (fresh-focused, likely HoReCa) and 
  Cluster 3 (frozen-focused)
- **Detergents/Paper** spending is concentrated almost entirely in one cluster (2), 
  suggesting professional/institutional buyers

## Recommendations by segment

| Cluster | Profile | Suggested strategy |
|---|---|---|
| 0 | Household basket (dairy + grocery + fresh) | Bundled discounts |
| 1 | HoReCa Fresh | Morning delivery, premium fresh offers |
| 2 | Business package (detergents + grocery) | B2B bundle offers |
| 3 | Ready-to-use (frozen + fresh) | Frozen + fresh collections |

Additionally, high-spend clusters (2, 3 — ~70% of budget share) are recommended for 
premium discounts, dedicated account managers, and free delivery, while low-spend 
clusters (0, 1) are better suited to quantity-based promotions (e.g. buy-2-get-1) and 
bulk packaging.

## Tools

Python, pandas, scikit-learn (KMeans, StandardScaler, silhouette_score), Matplotlib, Seaborn
