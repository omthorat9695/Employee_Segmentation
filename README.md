# Employee Workforce Segmentation

Segmenting employees into workforce groups using **K-Means**, **Hierarchical Clustering** and **PCA**, then analysing retention risk, department-level segments and performance groups.

## Project Overview

This project groups employees by their HR characteristics (tenure, income, satisfaction, overtime, promotion history and more) to find patterns in who is at risk of leaving. Attrition is **not** used to build the clusters. It is only used afterwards to check which segments are high-risk.

## Deliverables

| Deliverable | File |
|---|---|
| Colab notebook (full code) | `Employee_Workforce_Segmentation.ipynb` |
| Employee Segmentation Report | `Employee_Segmentation_Report.docx` |
| PCA Summary | `pca_summary.csv`, `pca_loadings.csv` |
| Workforce Analytics Dashboard | `workforce_dashboard.png` |
| Segment summary and segmented employees | `segment_summary.csv`, `employees_segmented.csv` |

## Methodology

1. **Feature engineering:** OverTime encoded 0/1, BusinessTravel as an ordinal, MonthlyIncome log-transformed, all features standardised.
2. **PCA:** keeps enough components to explain at least 80% of variance (22 features reduced to 11 components).
3. **K-Means:** k chosen using silhouette score, inertia (elbow) and Davies-Bouldin index.
4. **Hierarchical clustering:** Ward linkage with a dendrogram, compared with K-Means using silhouette score and Adjusted Rand Index.
5. **Segment profiling:** each segment is named automatically from its most distinctive features.
6. **Analysis:**
   - High-risk employee clusters (with a chi-square test)
   - Department-level workforce segments
   - Performance groups
   - Retention-risk groups, using a risk index built without the attrition label and validated with ROC-AUC

## Dataset

By default the notebook runs on a **synthetic HR dataset** (1,470 employees, with columns in the style of the IBM HR Analytics Employee Attrition dataset), so it works immediately. Results from that data illustrate the method and are not real workforce findings.

To use real data, download the IBM HR Analytics Employee Attrition dataset from Kaggle and set `DATA_SOURCE = "upload"` in Section 1 of the notebook.

## How to Run

1. Open `Employee_Workforce_Segmentation.ipynb` in [Google Colab](https://colab.research.google.com/).
2. Click **Runtime ▸ Run all**.
3. (Optional) Set `DATA_SOURCE = "upload"` and upload your own CSV when prompted.
4. All outputs are saved to the `outputs/` folder and downloaded as a zip. This includes an HTML version of the report.

## Tech Stack

Python, pandas, NumPy, scikit-learn, SciPy, Matplotlib, Seaborn (Plotly optional for the interactive plot)

## Limitations

- Clusters are descriptive, not causal.
- Segment results should be used at group level and not for individual employment decisions.
- Re-run the analysis periodically as the workforce changes.

## Author

Shivani Navgire
