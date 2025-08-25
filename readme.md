# Creating Diabetes Risk Profiles with Unsupervised Machine Learning

## 📄 Project Goal

This project aims to move beyond simple prediction and deeply understand the characteristics of the population at risk for diabetes. Using the "CDC Diabetes Health Indicators" dataset, this analysis employs a full data science workflow—from Exploratory Data Analysis (EDA) to unsupervised clustering—to identify and define distinct "risk profiles".

The final deliverable is not a model, but a **strategically enriched dataset**, ready for visualization and exploration in a Business Intelligence tool like Tableau. The core research question is: *Is it possible to identify risk profiles that combine health, socio-economic, and behavioral factors, and how are these profiles associated with diabetes?*

## ✨ Analysis Showcase & Methodology

This project is a case study in how insights from EDA directly inform data preprocessing and feature engineering decisions.

*   **Insight-Driven EDA:**
    *   **The Signal in the "Outliers":** The initial analysis of variables like `MentHlth` and `PhysHlth` revealed highly skewed distributions. The boxplots showed that the "outliers" were not data errors, but represented the minority of the population suffering from chronic health issues—**this was the signal, not the noise**.
    *   **Correlation vs. Relationship:** The analysis proved that a low Pearson correlation doesn't mean "no relationship". While `MentHlth` had a weak linear correlation with diabetes, visualizations showed a clear difference in the *distribution* of mental health days between diabetic and non-diabetic groups.
    *   **Data Integrity:** The dataset was confirmed to be of high quality, with no missing values and no problematic multicollinearity, making it ideal for robust analysis.

*   **Advanced Feature Engineering:**
    To capture complex behaviors and risks, two powerful synthetic indices were created:
    1.  **`healthy_habits_score`:** An aggregate score combining `PhysActivity`, `Fruits`, and `Veggies` consumption.
    2.  **`cardio_risk_index`:** A composite index created from the scaled values of `HighBP`, `HighChol`, and `BMI` to quantify cardiovascular risk.

*   **Robust Preprocessing & Clustering:**
    *   **`RobustScaler`:** Given the presence of significant outliers (which were identified as a key signal), `RobustScaler` was chosen over `StandardScaler` to scale the data, as it is less sensitive to extreme values.
    *   **K-Means Clustering:** The Elbow Method was used on the final engineered features to determine that **k=3** was the optimal number of clusters, providing the best balance between detail and interpretability.

## 🏆 Final Deliverable: A Tableau-Ready Clustered Dataset

The primary output of this project is the `cdc_diabetes_health_indicators_clustered.csv` file. This dataset contains all 253,680 original records enriched with:
*   The two engineered indices (`healthy_habits_score`, `cardio_risk_index`).
*   A `cluster` label (0, 1, or 2) for each individual, segmenting the population into three distinct profiles.
*   A [visualization at Tableau Public](https://public.tableau.com/views/Perfilesderiesgoparaladiabetesfinal/Caracterizacindeperfiles?:language=es-ES&:sid&:redirect=auth&:display_count=n&:origin=viz_share_link) 

### Strategic Plan for Tableau Visualization

This enriched dataset is designed to power an interactive dashboard in Tableau to answer key business questions. The plan includes:

1.  **Dashboard 1: Cluster Profile Characterization:**
    *   **Objective:** Understand what defines each of the 3 clusters.
    *   **Visuals:** Comparative bar charts for the new indices, and breakdown tables showing averages for other key variables (`MentHlth`, `GenHlth`, `Age`, `Income`) per cluster. This will allow for assigning intuitive labels like "Healthy and Active," "High Cardiovascular Risk," etc.

2.  **Dashboard 2: Diabetes Analysis by Profile:**
    *   **Objective:** Analyze how diabetes prevalence varies across the newly defined profiles.
    *   **Visuals:** Bar charts showing diabetes proportion per cluster, and interactive scatter plots mapping individuals based on the two indices, colored by their cluster. This will visually demonstrate the separation of risk profiles.

## 💻 Technologies Used

*   **Language:** Python 3
*   **Libraries:**
    *   Pandas (Data Manipulation)
    *   Matplotlib & Seaborn (Data Visualization)
    *   Scikit-learn (`RobustScaler`, `KMeans`)
    *   Jupyter Notebook (Development Environment)

## 🚀 Getting Started

To explore the analysis:
1.  Clone the repository.
2.  Install the required Python libraries: `pandas`, `scikit-learn`, `matplotlib`, `seaborn`, `ucimlrepo`.
3.  Open the `Jupyter Notebook` file and run the cells sequentially to reproduce the entire workflow from EDA to the final clustered CSV export.

## 👤 Author

**[Tu Nombre]**

*   **LinkedIn:** [Tu Perfil de LinkedIn]
*   **GitHub:** @Kamaranis