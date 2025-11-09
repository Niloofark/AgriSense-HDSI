# 🌾 HDSI AgriSense: Spatiotemporal Trends in U.S. Agriculture

### Harvard Data Science Initiative (HDSI) Datathon 2024 — Agriculture Track

## 📘 Overview
**AgriSense** explores the evolving demographics and economic patterns of U.S. agriculture from 1997–2022 using data-driven insights.  
The project investigates **spatiotemporal trends in farmer age**, **gender distribution**, and **economic productivity** across counties and states to uncover key patterns shaping the agricultural workforce.

Using data from the **USDA Census of Agriculture**, this notebook performs comprehensive cleaning, transformation, and visualization workflows powered by **Python, Pandas, Plotly, and Seaborn**.

---

## 🚀 Key Objectives
1. **Demographic Evolution:**  
   Examine how the average age of farm **principals** and **producers** has changed over time at the county, state, and national levels.
2. **Regional Deviations:**  
   Identify which states or counties show statistically significant deviations from national age trends.
3. **Gender Composition:**  
   Analyze gender distribution trends among operators and producers.
4. **Economic Impact:**  
   Quantify agricultural productivity and examine correlations between farmer age and total sales.
5. **Aging Dynamics:**  
   Detect regions with accelerating or stabilizing aging trends within the agricultural population.

---

## 📊 Dataset Summary
Data was sourced from Google Cloud Storage (GCS) bucket `hdsi-agri-prompt-data` containing 14,974 files (types: `.tif`, `.csv`, `.dbf`, `.xlsx`).  
Primary files used:
- `prompt2_demos_landtotals_county.csv` — County-level demographics  
- `prompt2_prompt3_sales.csv` — County-level sales and production  
- `state_level_2002_2007_2012_2017_2022.xlsx` — State-level agricultural sales by age and income bracket  

---

## 🧹 Data Cleaning and Preparation
- **Null Handling:** Filled missing age values using county-level means and interpolation.  
- **Type Conversion:** Converted non-numeric fields to numeric (with coercion).  
- **Feature Engineering:**  
  - `Combined_Average_Age` = mean of operator and producer ages  
  - `AGE_CHANGE_RATE` = temporal change in average age per county  
  - `Total_Farm_Production_Value` = weighted estimate using median sales brackets  

---

## 📈 Analysis Highlights
### 1. Spatiotemporal Trends
- National average farmer age increased from **54.2 years (1997)** to **56.4 years (2022)**.
- Top 5 oldest states: **Texas, New Mexico, Mississippi, Hawaii, Arizona**.
- 60.4% of U.S. counties exhibit **accelerating aging** among farm operators.

### 2. Statistical Testing
- Conducted **t-tests** comparing state vs national age trends.  
  Example: Texas showed a **significant deviation (p < 1e-9)**, confirming a unique aging pattern.

### 3. Regional Deviation Mapping
- Positive deviation (>1.5 years): Arizona, Hawaii, Mississippi, New Mexico, Texas.  
- Stabilized regions (< -1.5 years): Alaska, Pennsylvania, Vermont, Wisconsin.

### 4. Gender Distribution
| Year | Female Producers | Male Producers |
|------|------------------|----------------|
| 1997 | 1.0M             | 3.8M           |
| 2022 | 3.8M             | 3.7M           |

Female representation in agriculture **tripled** from 1997–2022.

### 5. Economic Insights
- Highest farm sales: **Texas ($477B)**, **Missouri ($215B)**, **Iowa ($185B)**.  
- Lowest sales: **Alaska, Rhode Island, Delaware, Nevada, New Hampshire**.  
- Positive correlation between age and production observed in middle-age groups (45–64 years).

---

## 🧠 Methodology
1. **Data Extraction** from GCS using `google-cloud-storage`.  
2. **Cleaning & Preprocessing** using `pandas`, `numpy`, and `re`.  
3. **Visualization** with `matplotlib`, `seaborn`, and `plotly`.  
4. **Statistical Analysis** via `scipy.stats.ttest_ind` for hypothesis testing.  
5. **Classification of Regions** (Accelerating vs Stabilizing) using age change thresholds.

---

## 🖼️ Visualizations
Key plots generated:
- Line plots of age trends by state and national averages.  
- Heatmaps showing rate of change in farmer age by state.  
- Combined gender distribution over census years.  
- Comparative bar plots for top/bottom sales regions.

---

## 🧩 Dependencies
```bash
pip install pandas numpy matplotlib seaborn plotly scipy google-cloud-storage gcsfs

