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
.
├── IndianAgriculturalProductivityAnalysis.ipynb     # Main analysis notebook
├── DataAnalysisReport.pdf                           # Final submitted lab report
├── README.md                                        # Project documentation
