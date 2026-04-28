🌦️ Weather Temperature Forecasting with GRU
📌 Overview
This project builds a GRU (Gated Recurrent Unit) deep learning model to forecast weekly average temperatures using time series data from ~318 weather stations across the United States.

The model is designed specifically for short time series data, where GRU outperforms more complex architectures like LSTM.

🚀 Why GRU Instead of LSTM?
Model	Parameters	Good for Small Data	Vanishing Gradient
Vanilla RNN	Fewest	✅ Yes	❌ Yes (problem)
GRU	Medium	✅ Yes	✅ No
LSTM	Most	❌ Overfits	✅ No
👉 Key Insight:
LSTM has ~4× more parameters than a simple RNN and tends to overfit on small datasets.
GRU provides the best balance between performance and complexity.

⚠️ Key Problem & Fix
❌ Previous Approach (Wrong)
Aggregated all stations → single time series (53 points)

Result → only ~7 test samples

Model output → flat line (mean prediction)

✅ Improved Approach (Correct)
Treat each station as an independent time series

Generated ~15,000 sequences

👉 Result: Model learns real temporal patterns

📊 Dataset
📅 Time range: 2016 – 2017 (weekly data)

🛰️ Stations: ~318

📦 Total records: 16,743

🎯 Target: Average Temperature (°F)

🧠 Project Pipeline
Import libraries & set seed

Load and inspect dataset

Data cleaning

Exploratory Data Analysis (EDA)

Build per-station sequences

Train/Test split (chronological)

Build GRU model

Train with callbacks

Evaluate performance

Visualize predictions & residuals

🔧 Model Architecture
Input (4 time steps)
   ↓
GRU (64 units, return_sequences=True)
   ↓
Dropout (0.3)
   ↓
GRU (32 units)
   ↓
Dropout (0.2)
   ↓
Dense (1 output)
Loss: Mean Squared Error (MSE)

Optimizer: Adam

Metric: Mean Absolute Error (MAE)

⚙️ Training Strategy
Window size: 4 weeks → predict next week

Train/Test split: 80% / 20%

Batch size: 32

Callbacks:
⏹️ EarlyStopping (patience=15)

📉 ReduceLROnPlateau

📈 Results
Metric	Value
MAE	4.83 °F
RMSE	6.36 °F
MAPE	11.71%
👉 The model achieves accurate and stable predictions across different stations.

📉 Evaluation Insights
✅ Good Signs
Training & validation loss converge

Residuals centered around zero

No major overfitting

📊 Visualizations
Predicted vs Actual (scatter plot)

Time-series comparison

Residual distribution

🧪 Key Techniques Used
Time Series Forecasting

Sliding Window Approach

Per-group (station-wise) scaling

Deep Learning (GRU)

Regularization (Dropout)

Learning Rate Scheduling

🛠️ Tech Stack
Python 🐍

NumPy, Pandas

Matplotlib, Seaborn

Scikit-learn

TensorFlow / Keras

📂 Project Structure
├── data/
│   └── weather.csv
├── notebook/
│   └── gru_temperature_forecasting.ipynb
├── README.md
▶️ How to Run
# Clone repo
git clone https://github.com/your-username/weather-gru-forecasting.git

# Install dependencies
pip install -r requirements.txt

# Run notebook
jupyter notebook
💡 Future Improvements
Add more features (humidity, pressure)

Try attention-based models

Multi-step forecasting

Station embedding instead of independent scaling

Deploy as a web app

📌 Key Takeaway
Data preparation matters more than model complexity.
Switching from aggregated data to per-station sequences transformed a useless model into a powerful predictor.

👤 Author
Abraraw Ayal

🎓 Data Science Student

🔗 GitHub: https://github.com/Abre1234

⭐ If you like this project
Give it a ⭐ on GitHub and share it!
