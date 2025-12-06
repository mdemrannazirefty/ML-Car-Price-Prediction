# Car Price Prediction

This project predicts car prices using **linear regression** and **ridge regression** on the **Car Features and MSRP** dataset.  
The goal is to build a simple but solid model that can estimate a car's price based on its specs and engineered features. Includes data cleaning, feature engineering, model tuning, and a fully implemented linear regression + ridge regularization model built from scratch.
The project explores numeric and categorical features, adds engineered variables like car age, applies one-hot encoding, and evaluates performance on train/validation/test splits.
Final model achieves a 0.44 RMSE on unseen test data and provides stable, interpretable predictions.

---

## Project Files

- **CAR PRICE PREDICTION.pdf** – full project report  
  (Google Drive link: https://drive.google.com/file/d/1q3zxaJxjHT1I2y85I1_QJLXwrh-d9Au3/view?usp=drive_link)
- `CarPricePrediction.ipynb` – complete notebook with preprocessing, modeling, and evaluation  
- `data/data.csv` – dataset used in the project  
- `requirements.txt` – Python dependencies  
- `.gitignore` – excludes environment and cache files  

---

## Dataset

- **Name:** Car Features and MSRP  
- **Source:** Kaggle  
- **Link:** https://www.kaggle.com/datasets/CooperUnion/cardataset  

The dataset contains 11,914 cars with attributes like make, model, year, engine specs, fuel type, transmission, driven wheels, body style, fuel economy, and the target variable **MSRP**.

---

## Methodology (Short Summary)

### **1. Data Cleaning & EDA**
- Converted column names to snake_case  
- Normalized string fields  
- Handled missing values (engine horsepower, cylinders, doors)

### **2. Train/Val/Test Split**
- Random split: **60% train**, **20% validation**, **20% test**  
- Transformed target variable using `log1p` for better stability

### **3. Baseline Model**
Linear regression on numeric features only:
- `engine_hp`, `engine_cylinders`, `highway_mpg`, `city_mpg`, `popularity`  
Baseline RMSE ≈ **0.76**

### **4. Feature Engineering**
Added:
- **Age** = `2017 - year`  
- One-hot encodings for `number_of_doors`, `make`, `model`,  
  `engine_fuel_type`, `transmission_type`, `driven_wheels`,  
  `market_category`, `vehicle_size`, `vehicle_style`

Final feature matrix: **52 features**

### **5. Ridge Regression**
Implemented ridge regression manually:

\[
w = (X^T X + rI)^{-1} X^T y
\]

Tuned `r` across `[0, 1e-5, 1e-4, 1e-3, 0.01, 0.1, 1, 10]`.

---

## Results

- **Best r:** `0.01`  
- **Validation RMSE:** ~ **0.456**  
- **Test RMSE:** ~ **0.442**  

The model generalizes well: test error closely matches validation error.  
Predictions are stable and reasonable for most vehicles.

---

## Example Prediction

For one test-set car:

- **Actual price:** ~ \$2,000  
- **Predicted price:** ~ \$3,062  

A bar chart comparison is included in the PDF report.

---

## How to Run

```bash
# Clone the repo
git clone https://github.com/mdemrannazirefty/car-price-prediction.git
cd car-price-prediction

# Install dependencies
pip install -r requirements.txt

# Open notebook
jupyter notebook CarPricePrediction.ipynb
```

Contact

Md. Emran Nazir Efty
📧 Email: mdemrannazirefty@gmail.com

💻 GitHub: https://github.com/mdemrannazirefty

🔗 LinkedIn: https://www.linkedin.com/in/mdemrannazirefty

