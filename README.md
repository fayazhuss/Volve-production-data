Volve Field Production Trend Analysis 🛢️
Analysis of the Volve Open Dataset (North Sea) to model daily oil production trends using reservoir-aware feature engineering and Gradient Boosting.

📌 Project Overview
This project moves beyond standard time-series forecasting by incorporating reservoir physics proxies. Instead of relying solely on historical lags (autocorrelation), the model utilizes pressure differentials and cumulative depletion markers to predict the "heartbeat" of Well 15/9-F-14.

Key Technical Highlights:
Physics-Informed Features: Developed dp_ratio (Drawdown proxy) and cum_oil (Reservoir exhaustion marker) to capture true production decline.

Model: Utilized LightGBM (LGBMRegressor) for high-efficiency training on high-variance sensor data.

Noise Reduction: Implemented custom scrubbing logic to filter injector noise and sensor outliers.

Clean Code: Written with a focus on modularity, avoiding SettingWithCopy pitfalls and tutorial-style verbosity.

🛠️ Tech Stack
Language: Python 3.x

Libraries: Pandas, NumPy, LightGBM, Matplotlib

Data Source: Equinor Volve Open Data

🚀 The Data Science Pipeline
1. Data Engineering
Used custom cleaning functions to standardize headers, parse time-series indices, and extract temporal features (Day of Year/Year) to account for seasonal operational shifts.

2. Feature Importance
Unlike basic models that rely on "what happened yesterday," this model identifies the following as top production drivers:

Cumulative Oil: Represents the natural decline and energy loss of the reservoir.

Average Choke Size: Captures operational throttling decisions.

Pressure Ratios: Proxies for the fluid dynamics between downhole and wellhead.

3. Visualization
The model successfully tracks the high-variance production spikes and the late-life tail of the well without overfitting to noise.

<img width="1091" height="528" alt="image" src="https://github.com/user-attachments/assets/b925f559-5bca-41bc-bf1a-9a78cb325d3f" />
 ![Final Trend](path/to/your/plot.png))

📂 Project Structure
Bash
├── data/                   # (Omitted from Git - Download from Kaggle/Equinor)
├── notebooks/              # Exploratory Analysis
├── src/
│   └── production_model.py # Final consolidated logic
├── requirements.txt        # Environment dependencies
└── README.md
📝 Future Work
Water Cut Analysis: Integrating BS&W (Basic Sediment and Water) to predict well drowning.

LSTM Integration: Testing Deep Learning architectures for multi-well spatial dependencies.

EUR Calculation: Automating Estimated Ultimate Recovery via Arps' Decline Curve integration.

Author: Fayaz Hussain
