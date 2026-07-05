# SpaceX-Launch-Prediction
# 🚀 SpaceX Falcon 9 First Stage Landing Prediction

Predicting whether the Falcon 9 first stage will land successfully, using data collected via web scraping and the SpaceX API, then cleaned, explored, visualized, and modeled with machine learning.

SpaceX advertises Falcon 9 rocket launches at a cost of **$62 million**, far cheaper than other providers, largely because SpaceX can reuse the first stage. Predicting whether the first stage will land successfully makes it possible to estimate the cost of a launch — useful information if a competing company wants to bid against SpaceX. This project builds that predictive model end-to-end: data collection, wrangling, exploratory data analysis, interactive visual analytics, and finally classification with machine learning.

This repository is a personal walkthrough of the **IBM Applied Data Science Capstone** project, organized as a series of Jupyter notebooks.

---

## 📂 Notebooks in this Project

| # | Notebook | Description |
|---|----------|-------------|
| 1 | [`jupyter-labs-webscraping.ipynb`](./jupyter-labs-webscraping__1_.ipynb) | Scrapes the Falcon 9 launch history from Wikipedia and parses the HTML tables into a Pandas DataFrame. |
| 2 | [`labs-jupyter-spacex-Data_wrangling.ipynb`](./labs-jupyter-spacex-Data_wrangling__1_.ipynb) | Cleans the raw launch data, engineers a binary `Class` landing-outcome label, and handles missing values. |
| 3 | [`edadataviz.ipynb`](./edadataviz__1_.ipynb) | Exploratory data analysis and visualization — relationships between flight number, payload, launch site, orbit type, and landing success. |
| 4 | [`lab_jupyter_launch_site_location.ipynb`](./lab_jupyter_launch_site_location__1_.ipynb) | Interactive geospatial analysis with **Folium** — maps launch sites, marks success/failure per launch, and measures proximity to coastlines, highways, and cities. |
| 5 | [`SpaceX_Machine_Learning_Prediction_Part_5.ipynb`](./SpaceX_Machine_Learning_Prediction_Part_5__1_.ipynb) | Builds and tunes classification models (Logistic Regression, SVM, Decision Tree, KNN) to predict first-stage landing success. |

> **Note:** An EDA-with-SQL notebook (`jupyter-labs-eda-sql-coursera_sqllite.ipynb`) is referenced as part of the original coursework but wasn't included in the files provided for this README — add it back into the table above if you include it in the repo.

---

## 🧭 Project Workflow

```
Data Collection  →  Data Wrangling  →  EDA & Visualization  →  Geospatial Analysis  →  Predictive Modeling
  (Webscraping        (Clean data,        (Charts, trends,        (Folium maps of         (Logistic Regression,
   + SpaceX API)       label outcomes)     correlations)           launch sites)            SVM, Tree, KNN)
```

### 1. Data Collection — Web Scraping
Requests the **List of Falcon 9 and Falcon Heavy launches** Wikipedia page, parses the HTML launch table, and extracts columns like flight number, launch site, payload, orbit, and outcome into a structured DataFrame.

### 2. Data Wrangling
- Calculates the number of launches per site
- Calculates the number/occurrence of each orbit type
- Calculates mission outcomes per orbit
- Creates the **landing outcome label** (`Class`: 1 = successful landing, 0 = failure) used as the target variable for machine learning

### 3. Exploratory Data Analysis & Visualization
Visual analysis of how landing outcomes relate to:
- Flight number vs. launch site
- Payload mass vs. launch site
- Success rate by orbit type
- Flight number vs. orbit type
- Payload mass vs. orbit type
- Yearly landing success trend

Also includes feature engineering: one-hot encoding categorical variables (orbit, launch site, landing pad, etc.) and casting numeric columns to `float64` in preparation for modeling.

**Sample visualizations:**

<p align="center">
  <img src="./images/flight-number-vs-launch-site.png" width="45%" alt="Flight Number vs Launch Site">
  <img src="./images/payload-vs-launch-site.png" width="45%" alt="Payload Mass vs Launch Site">
</p>
<p align="center">
  <img src="./images/success-rate-vs-orbit.png" width="45%" alt="Success Rate by Orbit Type">
  <img src="./images/yearly-success-trend.png" width="45%" alt="Yearly Landing Success Trend">
</p>

### 4. Interactive Visual Analytics (Folium)
Builds interactive maps marking all launch sites, color-codes launches as successful (green) or failed (red) using marker clusters, and calculates distances from launch sites to the nearest coastline, city, railway, and highway to understand siting constraints.

### 5. Machine Learning Prediction
Trains and tunes four classifiers with `GridSearchCV` to predict landing success (`Class`) from the engineered features, then compares them on held-out test accuracy.

| Model | Best CV Accuracy | Test Accuracy |
|---|---|---|
| Logistic Regression | 84.6% | 83.3% |
| Support Vector Machine | 84.8% | 83.3% |
| Decision Tree | 87.5% | 77.8% |
| K-Nearest Neighbors | 84.8% | 83.3% |

**Confusion matrix (example model):**

<p align="center">
  <img src="./images/confusion-matrix.png" width="45%" alt="Confusion Matrix">
</p>

---

## 🛠️ Tech Stack

- **Python** — Pandas, NumPy
- **Web scraping** — BeautifulSoup, Requests
- **Visualization** — Matplotlib, Seaborn, Folium (interactive maps), Plotly Dash (in the original capstone)
- **Machine Learning** — scikit-learn (Logistic Regression, SVM, Decision Tree, KNN, `GridSearchCV`, train/test split, confusion matrix)
- **Environment** — Jupyter Notebook

---

## ▶️ Getting Started

1. Clone this repository
2. Install dependencies:
   ```bash
   pip install pandas numpy beautifulsoup4 requests matplotlib seaborn folium scikit-learn
   ```
3. Run the notebooks in order (1 → 5) since later notebooks depend on the cleaned dataset produced by earlier ones.

---

## ✍️ Authors

Based on the **IBM Applied Data Science Capstone** course labs (IBM Corporation).

---

## 📄 License

This project is for educational purposes, adapted from the IBM Data Science Professional Certificate coursework.
