# Exploratory Data Analysis: Ground Water Level Trends in India (1994–2024)

This repository serves as the final analysis output for a comprehensive study on India's long-term groundwater dynamics. The project focuses on bridging the "Data Accessibility Gap" by engineering a custom extraction pipeline to transform unstructured legacy PDF reports from the **Central Ground Water Board (CGWB)** into a unified, machine-readable dataset.

## 📊 Project Overview
Groundwater is the lifeline for India’s agriculture and domestic consumption. However, a significant barrier exists in accessing historical data (1994–2024) locked within non-machine-readable PDF reports. This project utilizes a custom **Sliding Window Tokenization** algorithm (V6) to extract over 1.5 million records and perform rigorous spatiotemporal analysis.

### Key Analytical Objectives
* **Automate Data Extraction:** Develop a robust Python-based parsing algorithm capable of reading unstructured PDF tables and handling multi-line rows.
* **Temporal Trend Identification:** Analyze 30 years of history to identify statistically significant trends using the Mann-Kendall test.
* **Analyze Seasonal Dynamics:** Quantify the impact of seasonal cycles (Monsoon vs. Winter) on aquifer recharge and depletion.
* **Map Regional Disparities:** Use geospatial analysis to pinpoint specific districts suffering from critical groundwater stress.

---

## 📂 Dataset Source & Engineering
The primary data for this study was sourced from the **Ground Water Year Books** published annually by the **Central Ground Water Board (CGWB)**, Ministry of Jal Shakti, Government of India.

* **Temporal Range:** January 1994 to May 2024.
* **Data Scale:** Includes a network of approximately 15,000 to 20,000 observation wells across all Indian states.
* **The Extraction Challenge:** Standard tools failed due to "Ghost Columns" and "Floating Layouts." The final **V6 Algorithm** achieved near-perfect extraction by shifting from line-based logic to a token-stream approach.

### Parser Performance Comparison
| Algorithm Version | Logic Paradigm | Key Feature | Success Rate (Good Rows) | Outcome |
| :--- | :--- | :--- | :--- | :--- |
| **V1** | Line-Based | Simple Anchor Detection | 383,226 | Poor precision |
| **V5** | Token-Based | Naive Indexing | 223,830 | Unstable alignment |
| **V6 (Final)** | **Token + Window** | **Sliding Window Heuristic** | **383,559** | **Optimal Solution** |

---

## 📈 Key Analysis Findings

### 1. The Depletion Crisis
Statistical analysis of 817 high-quality monitoring stations reveals a distinct national bias toward depletion. Out of the stations with significant trends, **61.8% show active depletion** (rising mbgl), while only 38.2% show recharge.

### 2. The "Red Belt" (North-West Depletion)
* **Critical Areas:** A dense cluster of depletion dominates the North-Western plains (Punjab, Haryana, Northern Rajasthan).
* **Depletion Magnitude:** Stressed aquifers in this "Food Bowl" are dropping by nearly **0.88 meters per year**.
* **Connectivity Paradox:** In these zones, "Net Recharge" is nearing zero, suggesting aquifers have become hydraulically disconnected from surface rainfall.

### 3. Regional Resilience
* **Peninsular Variability:** In contrast, parts of Telangana and Coastal Andhra Pradesh show "Green Pockets" of recovery, likely correlating with state-level water restoration interventions.

---

## 🖼️ Visualizations





---

## 🛠️ Methodology & Tech Stack
* **Language:** Python
* **Extraction:** PyMuPDF (V6 Sliding Window Algorithm)
* **Cleaning:** Pandas (Z-score outlier removal and coordinate rectification)
* **Statistics:** Mann-Kendall Trend Test and Sen’s Slope Estimator
* **Geospatial:** Folium and K-Means Clustering (k=9)

---
