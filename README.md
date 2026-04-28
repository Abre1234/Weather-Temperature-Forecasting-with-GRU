# 🌦️ Weather Temperature Forecasting with GRU

## 📌 Overview
This project builds a **GRU (Gated Recurrent Unit)** model to forecast weekly average temperatures using time series data from ~318 weather stations across the United States. GRU is chosen because it performs better than LSTM on small datasets by reducing overfitting while capturing temporal patterns effectively.

---

## 🚀 Why GRU Instead of LSTM?

| Model        | Parameters | Good for Small Data | Overfitting Risk |
|--------------|-----------|--------------------|------------------|
| Vanilla RNN  | Low       | Yes                | High             |
| GRU          | Medium    | Yes                | Low              |
| LSTM         | High      | No                 | High             |

GRU is the optimal balance between performance and simplicity for this dataset.

---

## ⚠️ Key Improvement
Instead of aggregating all stations into a single time series (which caused poor learning and flat predictions), each station is treated as an independent time series. This increases data size to ~15,000 sequences and allows the model to learn real weather patterns.

---

## 📊 Dataset
- Period: 2016–2017 (weekly data)  
- Stations: ~318  
- Records: 16,743  
- Target: Average Temperature (°F)

---

## 🧠 Pipeline
Data loading → cleaning → EDA → per-station sequence creation → train/test split → GRU model → training → evaluation → visualization

---

## 🔧 Model Architecture
Input (4 time steps) → GRU(64) → Dropout(0.3) → GRU(32) → Dropout(0.2) → Dense(1)

- Loss: MSE  
- Optimizer: Adam  
- Metric: MAE  

---

## ⚙️ Training Setup
- Window size: 4 weeks  
- Train/Test split: 80/20 (time-based)  
- Batch size: 32  
- EarlyStopping + ReduceLROnPlateau used for stability and preventing overfitting  

---

## 📈 Results
- MAE: 4.83 °F  
- RMSE: 6.36 °F  
- MAPE: 11.71%  

The model shows strong generalization with stable predictions across stations.

---

## 📉 Key Insights
- Predictions closely follow real trends  
- Residuals are centered around zero (low bias)  
- No major overfitting observed  
- Model successfully captures seasonal temperature patterns  

---

## 🧪 Techniques Used
Time series forecasting, sliding window approach, per-station scaling, GRU deep learning, dropout regularization, learning rate scheduling

---

## 🛠️ Tech Stack
Python, NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn, TensorFlow/Keras

---

## 💡 Key Takeaway
Proper data preparation (per-station sequences) is more important than model complexity. It transformed the model from a constant predictor into a strong forecasting system.

---

## 👤 Author
Abraraw Ayal  
GitHub: https://github.com/Abre1234  
