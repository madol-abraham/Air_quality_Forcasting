# Air Quality Forecasting
![Project Banner](https://yourdomain.com/path-to-banner-image.png)

# project overview
Air pollution has become a pressing concern globally due to its adverse impact on human health, climate change and the environment. In Beijing, the effects of high PM2.5 levels are deep, affecting millions of residents. This task aims to predict the PM2.5 concentrations using a Time series forecasting technique based on the historical  air quality data provided for this project. I chose to use the Long Short-Term Memory (LSTM) algorithm. I decided to navigate a learning path on how deep learning can assist in forecasting air pollution levels and see better ways to contribute to public health strategies and policies that drive informed decisions.


## 📂 Project Structure

├── dataset/                   # Dataset files
├── notebooks/              # Jupyter Notebooks for data exploration and modeling               
├── submission files/                # Evaluation metrics and model outputs
├── README.md               # Project documentation


## 🌍 Problem Statement

Air pollution, particularly PM2.5, poses severe health and environmental risks. This project aims to predict PM2.5 concentrations in Beijing using historical air quality and meteorological data.

## 🔍 Approach

1. **Exploratory Data Analysis (EDA)**: Visualized distributions, trends, and missing values.
2. **Feature Engineering**:
   - Extracted cyclical time features (hour, month, season).
   - Engineered meteorological features like `temp_dew_diff = TEMP - DEWP`.
   - Computed rolling averages (6-hour, 24-hour) for trend analysis.
3. **Preprocessing**:
   - Handled missing values in `pm2.5`.
   - Standardized features using `StandardScaler`.
   - Scaled target (`PM2.5`) with `MinMaxScaler`.
4. **Modeling**:
   - Built and tuned Bidirectional LSTM models.
   - Regularized with Dropout and L2.
   - Added Batch Normalization and Gradient Clipping.
5. **Evaluation**:
   - Metrics: RMSE, MAE, R².
   - Visualization: Predicted vs Actual, Loss Curves.

## 📊 Results

| Metric   | Value  |
|----------|---------|
| RMSE     | 75.75   |
| MAE      | 50.69   |
| R² Score | 0.50    |

## 📈 Experiment Table

| Experiment | Layers (units) | LR     | Batch Size | Dropout | Other      | Loss | Epochs | RMSE (Test) | Notes                                   |
|------------|----------------|--------|------------|---------|------------|------|--------|--------------|-----------------------------------------|
| 1          | 64             | 0.1    | 32         | -       | Adam, mse  | mse  | -      | 57.2         | High LR caused unstable convergence.     |
| 2          | 64,32          | 0.001  | 64         | 0.2     | relu, mae  | mae  | 50     | 61.5         | Lower LR stabilized training.           |
| 3          | 128,64,32      | 0.001  | 64         | 0.1,0.4 | Adam, mse  | mse  | 100    | 75.75        | Larger batch size increases variance.    |
| 4          | 256,64         | 0.001  | -          | 0.3,0.1 | EarlyStop  | me   | 50     | 56.7         | Smaller batch improved convergence.      |
| 5          | 128,64         | 0.0005 | 32         | -       | tanh, mae  | mae  | 25     | 56.9         | Lower LR marginal gain.                  |

## 🚀 How to Reproduce

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/madol-abraham/Air_quality_Forecasting.git
   cd Air_quality_Forecasting

Install Dependencies:
pip install -r requirements.txt
Prepare Data:
Ensure train.csv is in the dataset/ folder.
Run the Notebook :
Open notebooks/Air_quality_prediction.ipynb for interactive exploration.
 #Future Work
Incorporate external factors e.g., traffic, industrial activities.

Explore attention mechanisms for feature importance.

Experiment with hybrid models 
