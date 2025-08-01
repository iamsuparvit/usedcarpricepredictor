# 🚗 Used Car Price Predictor (RodKaidee Dataset)

This project provides a regression-based machine learning model for predicting the prices of second-hand cars using data scraped from RodKaidee, one of Thailand’s popular car marketplaces.

### 🔍 Project Overview

The goal is to estimate the resale price of a used car based on multiple input features such as brand, model, engine size, year, mileage, and more. The model was trained using real-world listings and evaluated for performance using regression metrics.

---

### 🧠 Model Architecture

The predictor is a fully-connected feedforward neural network built using PyTorch, consisting of:

* **Input Layer**: 138 features (including one-hot encoded categorical data + scaled numeric values)
* **Hidden Layers**:

  * Linear(138 → 128) → BatchNorm → ReLU → Dropout(0.2)
  * Linear(128 → 64) → BatchNorm → ReLU → Dropout(0.2)
  * Linear(64 → 32) → ReLU
* **Output Layer**: Linear(32 → 1)

---

### 🧪 Model Performance

* **R² Score**: 0.924

  > Indicates the model explains \~92.4% of the variance in car prices.
* **Mean Squared Error (MSE)**: 0.00136

  > Very low MSE after output rescaling, indicating precise predictions.

---

### 🧰 Tools and Dependencies

* **Libraries**: PyTorch, pandas, NumPy, joblib, scikit-learn, Gradio
* **Encoders/Scalers**:

  * One-Hot Encoding for categorical variables
  * StandardScaler for `Year`, `Mileage`, and `Price`

---

### 🎮 Interactive Interface

A Gradio UI is included for demo purposes, where users can:

* Select car features from dropdown menus
* Receive predicted price instantly
* Try with pre-filled example cases

Example features include:

* Brand, Model, Engine Size
* Segment, Province, Color
* Year, Mileage

---

### 🧾 How It Works

1. Input features are collected via Gradio.
2. Categorical data is one-hot encoded.
3. Numerical features are scaled using pre-fitted scalers.
4. The model predicts the scaled price.
5. The output is then inverse-transformed to return the actual THB value.

---

### 📌 Example Prediction

```python
predict_car_price(
    brand='Honda',
    model='Civic',
    engine=1.8,
    segment='C-Segment',
    province='กรุงเทพมหานคร',
    color='Silver',
    year=2006,
    mileage=232433.0
)
# Output: 242086 THB
```

---

### 🚀 Launch the App

To run the application:

```bash
python app.py
```

Or launch the Gradio interface as shown in the script.

---
