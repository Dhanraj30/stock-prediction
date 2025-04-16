# Microsoft Stock Forecasting with LSTMs

This project implements a Long Short-Term Memory (LSTM) model to forecast Microsoft stock prices using historical data. The dataset is sourced from Yahoo Finance and processed to train, validate, and test the LSTM model.

## Project Overview

The notebook walks through the following steps:
1. **Data Loading**: Load historical stock price data from a CSV file.
2. **Data Preprocessing**: Format the data, convert dates, and create windowed datasets for time series forecasting.
3. **Model Training**: Train an LSTM model to predict stock prices based on historical data.
4. **Evaluation**: Evaluate the model's performance on training, validation, and test datasets.
5. **Visualization**: Plot predictions and observations for better understanding.

## Dataset

- **Source**: [Yahoo Finance](https://finance.yahoo.com/quote/MSFT/history/)
- **Columns Used**: `Date` and `Close`
- **Preprocessing**: Dates are converted to `datetime` objects, and the data is indexed by date.

## Model Architecture

The LSTM model is implemented using TensorFlow/Keras with the following layers:
- Input layer: `(3, 1)` shape
- LSTM layer: 64 units
- Dense layers: Two layers with 32 units each and ReLU activation
- Output layer: 1 unit

![](https://github.com/Dhanraj30/stock-prediction/blob/main/diagram-export-4-11-2025-12_41_22-PM.png)

```
+-----------------------+
|   Data Collection     |
|-----------------------|
| - Download MSFT.csv   |
|   (Historical Stock   |
|    Prices)            |
+-----------------------+
           |
           v
+-----------------------+
| Data Preprocessing    |
|-----------------------|
| - Load CSV into       |
|   Pandas DataFrame    |
| - Select 'Date' and   |
|   'Close' columns     |
| - Convert 'Date' to   |
|   datetime format     |
| - Set 'Date' as index |
+-----------------------+
           |
           v
+-----------------------+
| Data Visualization    |
|-----------------------|
| - Plot stock prices   |
|   over time           |
+-----------------------+
           |
           v
+-----------------------+
| Sliding Window        |
|-----------------------|
| - Create sliding      |
|   windows of size n   |
| - Generate features   |
|   (X) and targets (Y) |
+-----------------------+
           |
           v
+-----------------------+
| Train-Test Split      |
|-----------------------|
| - Split data into     |
|   training,           |
|   validation, and     |
|   testing sets        |
+-----------------------+
           |
           v
+-----------------------+
| Model Architecture    |
|-----------------------|
| - Input Layer (3, 1)  |
| - LSTM Layer (64)     |
| - Dense Layer (32)    |
| - Dense Layer (32)    |
| - Output Layer (1)    |
+-----------------------+
           |
           v
+-----------------------+
| Model Training        |
|-----------------------|
| - Compile model with  |
|   MSE loss and Adam   |
|   optimizer           |
| - Train for 100       |
|   epochs              |
+-----------------------+
           |
           v
+-----------------------+
| Model Evaluation      |
|-----------------------|
| - Predict on training,|
|   validation, and     |
|   testing sets        |
| - Plot predictions    |
|   vs actual values    |
+-----------------------+
           |
           v
+-----------------------+
| Recursive Predictions |
|-----------------------|
| - Use model output as |
|   input for future    |
|   predictions         |
| - Plot recursive      |
|   predictions         |
+-----------------------+

```

## How to Run

1. **Setup Environment**:
   ```bash
   # Create and activate a virtual environment
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate

   # Install dependencies
   pip install -r requirements.txt
