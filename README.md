# Predicting the Functionality of Tanzanian Water Wells

## 📌 Project Overview
Access to safe water remains a major challenge in Tanzania, where many communities depend on wells. However, a significant number of these wells are **non-functional** or **in need of repair** due to poor maintenance and resource limitations.  

This project uses **Exploratory Data Analysis (EDA)** and **Machine Learning (ML)** to:
- Classify wells as **functional**, **non-functional**, or **functional but needs repair**.  
- Identify the **key drivers of well functionality**.  
- Provide **actionable insights** for government and NGOs to improve water access.  

---

## 🗂 Dataset
- **Source:** Tanzania Water Wells Dataset (70,000+ records).  
- **Target Variable:** `status_group`  
  - `functional`  
  - `non functional`  
  - `functional needs repair`  

### Key Features
- **Geospatial:** `longitude`, `latitude`, `gps_height`  
- **Infrastructure:** `construction_year`, `extraction_type_group`, `waterpoint_type_group`  
- **Governance:** `management_group`, `scheme_management`, `permit`, `public_meeting`  
- **Service Quality:** `water_quality`, `quantity_group`, `source_class`  
- **Categorical IDs:** `funder`, `installer` (cleaned into grouped forms)  

---

## 🔎 EDA Insights
- **Infrastructure Age:** Older wells are more likely to fail.  
- **Topography:** Elevation (`gps_height`) affects functionality.  
- **Governance & Compliance:**  
  - Wells with permits and structured management are more reliable.  
- **Service Quality & Quantity:** Poor `water_quality` and low `quantity_group` strongly correlate with non-functionality.  
- **Community Engagement:** Public meetings are linked to better well performance.  

📌 **Takeaway:** Failures are not random. They are associated with **age, governance, geography, and service quality**.  

---

## 🤖 Modeling
Three models were tested:  
1. **Logistic Regression** – Accuracy ~0.63 (too weak, struggles with nonlinearities).  
2. **Random Forest** – Accuracy ~0.79 (best overall accuracy).  
3. **XGBoost** – Accuracy ~0.71, but **highest recall** for the minority class (*needs repair*).  

**Interpretation:**  
- Use **Random Forest** if the goal is maximum overall accuracy.  
- Use **XGBoost** if the goal is to **catch wells needing repair** (operationally most critical).  

---

## ✅ Recommendations
1. **Governance & Repairs**
   - Prioritise wells without permits for monitoring.  
   - Strengthen community-based management systems.  

2. **Repair Prioritisation**
   - Focus on older wells, poor water quality, and insufficient water quantity.  
   - Use XGBoost predictions to rank “needs repair” wells.  

3. **Data Quality Improvements**
   - Collect reliable `construction_year`.  
   - Standardise categorical fields (e.g., `funder`, `installer`, `scheme_management`).  

4. **Community Engagement**
   - Encourage public meetings and maintain governance records.  

5. **Model-Assisted Decision Making**
   - Random Forest for general monitoring.  
   - XGBoost for proactive repair targeting.  

---

## 📊 Project Structure
├── data/                         # Data folder (optional in repo, usually in .gitignore if too large)
│   ├── raw/                      # Original raw dataset files (CSV)
│   ├── processed/                # Cleaned or transformed datasets
│
├── notebooks/                    
│   └── notebook.ipynb            # Main Jupyter Notebook with EDA, preprocessing, modeling

│
├── models/                       
│   └── tanzania_rf_model.pkl     # Example: saved Random Forest model
│   └── tanzania_xgb_model.pkl    # Example: saved XGBoost model
│
├── outputs/
│   ├── figures/                  # Plots and visualizations (EDA charts, feature importance, confusion matrix)
│   ├── reports/                  # Generated reports or exported results
│
├── requirements.txt              # Python dependencies (pandas, scikit-learn, matplotlib, etc.)
├── README.md                     # Project documentation (this file)
└── Tanzania_Water_Wells_Presentation.pptx   # Final project presentation slides

