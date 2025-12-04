# 🌾 Indian Agricultural Productivity Analysis  
### A Complete Data Analytics & Machine Learning Pipeline (1997–2020)

**Author:** Bijayeeni Halder  
**Roll No:** 2470106  
**Course:** Data Analytics Lab (MC5191)  

---

## 📌 Project Overview  

This project analyzes agricultural crop production data across multiple Indian states from **1997 to 2020**.  
The goal is to build a **data-driven predictive model** that can estimate crop production using climate factors, fertilizer/pesticide usage, and cultivated land area.

The workflow includes:

- Data collection  
- Dataset profiling using **ydata-profiling**  
- Exploratory Data Analysis (EDA)  
- Data preprocessing  
- Feature scaling experiments  
- Dimensionality reduction using PCA  
- Model training and evaluation  
- Performance comparison  
- Final model selection  

---

## 📂 Dataset  

- **Source:** https://www.kaggle.com/datasets/akshatgupta7/crop-yield-in-indian-states-dataset  
- **Target variable:** `Production` (metric tons)  

### Features  

- `Crop` – Name of the crop  
- `Crop_Year` – Year of cultivation (1997–2020)  
- `Season` – Cropping season (Kharif, Rabi, Whole Year, etc.)  
- `State` – Indian state  
- `Area` – Total cultivated area (hectares)  
- `Production` – Crop production (metric tons)  
- `Annual_Rainfall` – Annual rainfall received (mm)  
- `Fertilizer` – Total fertilizer used (kg)  
- `Pesticide` – Total pesticide used (kg)  
- `Yield` – Production per hectare  

---

## 🧭 Project Structure

```text

├── IndianAgriculturalProductivityAnalysis.ipynb     # Main analysis notebook
├── DataAnalysisReport.pdf                           # Final submitted lab report
├── README.md                                        # Project documentation
```

---

## 📊 Exploratory Data Analysis (EDA)

### ✔ Missing Values  
- Checked using `df.isnull().sum()`
- The dataset contains **zero missing values** → No imputation required

### ✔ Skewness Analysis  
Several numerical variables show **heavy right-skew**, which is common in real-world agricultural datasets due to unequal production among states.

| Feature       | Skewness |
|---------------|----------|
| Pesticide     | 25.63    |
| Area          | 21.85    |
| Production    | 19.29    |
| Fertilizer    | 13.41    |
| Yield         | 12.78    |

### ✔ Correlation Study  
- Production positively correlates with **Area, Fertilizer, Rainfall, and Yield**
- A heatmap was generated to visualize relationships among co-related features

---

## 🛠️ Data Preprocessing  

Preprocessing steps applied to the dataset:

- Removed duplicate records using `df.drop_duplicates()`
- Checked and validated numeric datatypes
- Label encoded `Crop`, `Season`, and `State` using `LabelEncoder`
- Handled outliers through IQR (Interquartile Range) filtering on continuous variables

No missing values were observed; hence **no imputation was required**.

---

## 🔧 Feature Scaling  

Multiple scalers were tested to observe the effect on models:

- `MinMaxScaler`
- `StandardScaler`
- `RobustScaler`
- `Normalizer`
- `QuantileTransformer` (uniform and normal)
- `PowerTransformer (Yeo-Johnson)`
- `np.log1p()` (log transform)

### 📝 Observation  
Tree-based models such as **Random Forest** and **XGBoost** are **invariant to scaling**.  
However, scaling **significantly improves** the performance of KNN and distance-based models.

---

## 🔻 PCA: Dimensionality Reduction  

- Applied after Standard Scaling using `PCA(n_components=0.95)`
- Reduced original features into **7 principal components**
- Retained **~99.28% variance**

### 📌 Effect on XGBoost Performance  

| Model        | R²     | RMSE    | MAE    |
|--------------|--------|---------|--------|
| XGB Original | 0.9590 | 1405.23 | 479.03 |
| XGB PCA      | 0.9346 | 1775.42 | 733.97 |

🔹 PCA reduced dimensionality but **slightly dropped prediction accuracy**, proving tree models work best on original features.

---

## 🤖 Machine Learning Models  

The following supervised regression models were trained and evaluated:

1. **RandomForestRegressor**
2. **XGBRegressor**
3. **AdaBoostRegressor**
4. **KNeighborsRegressor**  
   - Tested with and without StandardScaler (scaling improved results)

### 📏 Evaluation Metrics Used  
- **R²** – Coefficient of Determination  
- **RMSE** – Root Mean Squared Error  
- **MAE** – Mean Absolute Error  

---

## 📈 Model Performance Summary  

| Model                 | R²    | RMSE   | MAE    |
|-----------------------|-------|--------|--------|
| Random Forest         | 0.960 | 1437   | 434    |
| **XGBoost (Best)**    | **0.959** | **1405** | **479** |
| AdaBoost              | 0.720 | 3659   | 3077   |
| K-Nearest Neighbors   | 0.340 | 5641   | 2632   |

📌 **XGBoost performed the best overall**, balancing accuracy and error metrics effectively.

---

## 🏆 Final Conclusion  

XGBoost trained on the **original feature space** achieved the best accuracy, with **R² = 0.959** and **RMSE ≈ 1405**.  
Although PCA reduced dimensionality and preserved ~99.28% variance, the PCA-compressed data slightly decreased XGBoost’s performance.  

📍 Therefore, **tree-based models work best with original, non-compressed features** in a tabular dataset like this.  

This project successfully demonstrates a complete machine learning pipeline for crop production prediction, from data collection and profiling to model evaluation and final selection.

---

## 🔁 Reproducibility  

### 🔧 Install Requirements  

```bash
pip install pandas numpy scikit-learn xgboost ydata-profiling seaborn matplotlib
```

### ▶️ Run the Project

```bash
git clone https://github.com/beBijayeeni/Indian-Agricultural-Productivity-Analysis.git
cd Indian-Agricultural-Productivity-Analysis
```
- Open the notebook in Google Colab or Jupyter Notebook
- Run the cells step-by-step from top to bottom

---

### 📬 Contact 

💡 Interested in collaborating or providing feedback? Reach out!

- **Name:** Bijayeeni Halder  
- **Email:** *bijayeenihalder@gmail.com*  
- **LinkedIn:** *https://www.linkedin.com/in/bijayeeni-halder-0b1037289*  

⭐ If you found this project useful, don't forget to star the repository!
