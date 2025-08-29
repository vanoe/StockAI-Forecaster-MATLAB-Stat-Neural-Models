# 📈 AI Stock Price Predictor

**Predict stock prices accurately using fast statistical models combined with AI-refined neural networks.**  
Built in **MATLAB**, this tool gives both quick short-term forecasts and deeper AI-based insights. Ideal for investors, trading teams, and robo-advisors looking for **smarter decisions, real-time signals, and risk analysis**.

---

## 🛠️ Scheme

<img src="./img/img-1.png" alt="Scheme" />

---

## ⚙️ Technical Description

This AI-powered stock predictor combines **fast forecasting** with **deep learning** to give investors and analysts more accurate and explainable market insights.

- **Baseline Model:** Quick short-term forecasts for intraday or daily decisions.
- **AI-Refined Neural Network:** Adaptive MLP that grows automatically to learn complex market patterns.
- **Explainable Predictions:** Highlights which features matter most.

It uses historical price data, technical indicators, and macroeconomic factors to forecast future movements while adapting to changing market regimes.

---

## 🧩 Examples

<table>
    <tbody>
        <tr>
            <td>
                <img src="./img/img-2.png" alt="img" />
            </td>
            <td>
                <img src="./img/img-3.png" alt="img" />
            </td>
        </tr>
        <tr>
            <td>
                <img src="./img/img-4.png" alt="img" />
            </td>
            <td>
                <img src="./img/img-5.png" alt="img" />
            </td>
        </tr>
        <tr>
            <td>
                <img src="./img/img-6.png" alt="img" />
            </td>
            <td>
                <img src="./img/img-7.png" alt="img" />
            </td>
        </tr>
    </tbody>
</table>

<img src="./img/img-8.webp" alt="img" />

<img src="./img/img-9.webp" alt="img" />

<video src=" " controls preload>
    Your browser does not support the video tag.
</video>

## 📖 Full Description

<details>
  <summary>📖 Click to expand the Description</summary>

## Overview
This **AI-powered stock price predictor** combines **fast forecasting** with **deep learning** to deliver accurate and explainable market insights.

Built in **MATLAB**, the tool features two models:
- ⚡ **Baseline Forecast (Quick-Cycle Model):** For fast short-term predictions.
- 🤖 **AI-Refined Forecast (Constructive MLP):** An adaptive neural network that grows dynamically to capture complex market patterns.

The system ingests historical price data, technical indicators, and macroeconomic factors to predict future movements while adapting to **changing market regimes**.

**Key benefits:**
- Prevents overfitting by adding neurons **only when validation improves**.
- Uses **second-order optimization** for faster, more reliable training.
- Provides **explainability** by highlighting the most important features driving predictions.
- Offers **real-time APIs** for trading, robo-advisors, and risk management.

---

### Problem
Stock price prediction is challenging due to:
- **Non-stationary, noisy data** with regime shifts.
- Traditional models (ARIMA, GARCH, etc.) capturing only limited patterns.
- Off-the-shelf AI models often being **black-boxes**, prone to overfitting, and ignoring intraday context.

**Market needs:**  
✅ A robust, **explainable engine** that:
- Learns changing regimes automatically.
- Ingests price/volume data plus macro factors.
- Delivers both fast baseline forecasts and **deeper AI insights**.

---

### Solution & Approach
Two complementary forecasting pipelines inside MATLAB:

1. **Baseline Forecast (Quick-Cycle)**
    - Lightweight regression/ARIMA variant.
    - Delivers instant, low-latency predictions for short-term decisions.
    - Serves as a benchmark for AI improvements.

2. **AI-Refined Forecast (Constructive MLP)**
    - Grows hidden neurons sequentially until validation error no longer improves.
    - Trained with **Hessian-based Levenberg-Marquardt optimizer** for stability.
    - Captures nonlinear dependencies and **market regime shifts** automatically.

Both pipelines share:
- Common feature engineering.
- Rolling-window validation.
- Standardized error tracking for fair A/B testing.

---

### Key Achievements
- 📉 **7–12% lower RMSE** vs tuned ARIMA on S&P 500 back-tests.
- ⚡ **<120ms latency** for baseline, **<350ms** for AI model (CPU).
- 🧠 **Constructive MLP** prevents overfitting via adaptive growth.
- 🔍 **Explainability built-in:** Hessian sensitivity analysis surfaces top 15 features per prediction.

---

### Process

#### 1. Data Collection & Preprocessing
- **Inputs:**
    - OHLCV stock data (daily/intraday).
    - Technical indicators (RSI, MACD, ATR, Bollinger Bands, MAs).
    - Optional macro factors (rates, CPI, Fed funds, VIX).

- **Steps:**
    - Timestamp alignment & forward-fill.
    - Outlier removal.
    - Log returns & normalization.
    - Lagged rolling features (1, 3, 5, 10 days).
    - Time-aware train/validation/test splits.

---

#### 2. Feature Engineering
- **Domain Features:** RSI, MACD, ATR, EMA/SMA crossovers, volatility clusters.
- **Macro Factors:** Fed rate changes, inflation shocks, VIX spikes.
- **Interaction Terms:** Nonlinear feature combinations.

---

#### 3. Baseline Forecasting
- Lightweight regression or ARIMA-style learner.
- Provides **instant predictions** and acts as benchmark.

---

#### 4. Constructive MLP Growth
- Start with 1 hidden neuron.
- Add neurons **only if ΔValidation Error < -0.2%**.
- Activation: ReLU/Tanh.
- Weight Init: He/Xavier.

---

#### 5. Optimization & Training
- **Second-Order LM Optimizer** (Hessian-based).
- **Mini-batching + MATLAB Parfor** for acceleration.
- **Early stopping + dropout + weight decay** for generalization.

---

#### 6. Validation & Testing
- **Walk-forward CV** simulating live trading.
- **Hyperparameter tuning** inside rolling windows.
- Metrics: RMSE, MAE, Directional Accuracy.

---

#### 7. Explainability
- Hessian sensitivity → highlights top 10–15 features.
- Visualization → detect **regime shifts** and market anomalies.

---

#### 8. Deployment
- Exported to **C++ libraries** for production.
- REST APIs:
    - `/forecast/current` → baseline model.
    - `/forecast/refined` → AI-refined model.
- **Monitoring:** Canary releases + auto-retrain if drift detected.
- **Scalable:** Parallel pipelines for multiple securities.

---

### Technologies Used
- MATLAB R2024a + Neural Network Toolbox
- Constructive MLP (cascade-correlation style growth)
- Levenberg-Marquardt + Hessian optimization
- MATLAB Datastore + Parfor for parallel preprocessing

---

### End Use Cases
- **Trading desks:** real-time signals.
- **Robo-advisors:** blend baseline + AI outlooks.
- **Risk teams:** stress testing & scenario analysis.
- **Retail brokers:** client-facing AI widgets.
- **Academia/R&D:** benchmarks for constructive neural nets.

---

### References
- Box et al. (2015). *Time Series Analysis: Forecasting and Control.* Wiley.
- Engle, R. F. (1982). *ARCH Models.* Econometrica.
- Bishop, C. M. (2006). *Pattern Recognition & Machine Learning.* Springer.
- Fahlman & Lebiere (1990). *Cascade-Correlation Learning Architecture.* NIPS.
- Hagan et al. (2014). *Neural Network Design (2nd ed.).*
- Levenberg, K. (1944). *Least-Squares Optimization.* QAM.
- MATLAB Docs (2024). *Neural Network Toolbox.* MathWorks.
- Zhang et al. (1998). *Forecasting with Artificial Neural Networks.* IJF.

</details>