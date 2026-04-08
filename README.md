# time-series-anomaly-attribution

---

##  Overview

This project implements an end-to-end pipeline for analyzing **multivariate time series data without labels**. The system decomposes each variable into structural components, detects anomalies, and—most importantly—**attributes each anomaly to its underlying cause**.

Unlike traditional anomaly detection approaches, this project focuses on **explainability**, ensuring that anomalies are not just flagged but also interpreted.

---

##  Objective

* Decompose each time series into:

  * Trend
  * Seasonal
  * Residual components
* Detect anomalies using both statistical and machine learning methods
* **Attribute anomalies to structural causes:**

  * Trend Break
  * Seasonal Deviation
  * Irregular Spike
* Analyze relationships between variables using cross-correlation
* Study temporal distribution of anomalies

---

##  Approach

### 1. Data Preparation

* Synthetic multivariate dataset generated with:

  * 2+ years of daily data
  * 3 variables: CPU Usage, Memory Usage, Network Traffic
* Injected anomalies:

  * Trend shifts
  * Seasonal disruptions
  * Random spikes

---

### 2. Preprocessing

* Applied **StandardScaler** to normalize data
* Ensures consistency across variables

---

### 3. STL Decomposition

* Used STL (Seasonal-Trend decomposition) to split data into:

  * Trend
  * Seasonal
  * Residual

* Calculated variance contribution:

  * Trend %
  * Seasonal %
  * Residual %

* Flagged variables where:

  * Residual variance > 50% → Structurally unpredictable

---

### 4. Anomaly Detection

Performed on residual component:

* Rolling Z-score
* Isolation Forest

Compared using:

* **Cohen’s Kappa Score** to measure agreement

---

### 5. Anomaly Attribution

Each anomaly is classified into:

* **Trend Break**

  * Detected using change point detection (PELT)

* **Seasonal Deviation**

  * Occurs when expected seasonal pattern is violated

* **Irregular Spike**

  * Random anomaly not explained by structure

---

### 6. Cross-Correlation Analysis

* Performed on residuals
* Identifies:

  * Leading indicators
  * Lag relationships between variables

---

### 7. Anomaly Timeline Analysis

* Analyzed anomaly occurrences over time
* Determined whether anomalies are:

  * Uniformly distributed
  * Clustered in specific periods

---

##  Deliverables

The project produces the following outputs:

1. **Jupyter Notebook**

   * Clean, step-by-step implementation

2. **Decomposition Summary Table**

   * Variance breakdown per variable

3. **Anomaly Attribution Log**

   * Timestamp, variable, anomaly type, explanation

4. **Cross-Correlation Report**

   * Leading indicator relationships

5. **Findings Summary**

   * Key insights and conclusions

---

##  Tech Stack

* Python
* Pandas, NumPy
* Matplotlib, Seaborn
* Scikit-learn
* Statsmodels (STL)
* Ruptures (PELT Algorithm)
* Jupyter Notebook

---

##  Setup Instructions

### 1. Clone Repository

```bash
git clone <repository-link>
cd <project-folder>
```

---

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

---

### 3. Run Notebook

```bash
jupyter notebook
```

Open:

```
analysis.ipynb
```

Run all cells sequentially.

---

##  Expected Outputs

* Time series decomposition plots
* Anomaly detection visualizations
* Variance summary table
* Cross-correlation heatmaps
* Anomaly timeline graphs

---

##  Key Insights

* CPU and Memory show strong trend-driven behavior
* Network Traffic exhibits high volatility
* Memory acts as a leading indicator for CPU and Network
* Anomalies are primarily caused by trend shifts
* Temporal clustering of anomalies observed

---

##  Notes

* The dataset used is synthetic for demonstration purposes
* The approach is generalizable to real-world datasets
* Code is structured for clarity and reproducibility

---

##  Submission

Kindly ensure submission within the given timeline. The solution is structured, documented, and ready for evaluation.

---

##  Conclusion

This project demonstrates that:

> **Effective anomaly detection requires both identification and interpretation.**

By combining decomposition, detection, and attribution, the system provides meaningful insights into time series behavior.

---
