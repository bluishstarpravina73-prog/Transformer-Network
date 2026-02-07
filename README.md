Advanced Time Series Forecasting using Attention-Based Transformer Networks
1. Introduction

Time series forecasting is critical in domains such as finance, economics, energy demand prediction, and transportation. Traditional statistical models like ARIMA and SARIMA rely on assumptions of linearity and stationarity. However, real-world time series often exhibit complex, non-linear, and long-range temporal dependencies.

This project implements an attention-based Transformer Encoder model for multi-step time series forecasting and compares its performance with a classical SARIMA baseline.

2. Objective

The objectives of this project are:

To implement a Transformer encoder adapted for time series forecasting.

To incorporate positional encoding to preserve temporal order.

To perform multi-step forecasting.

To compare model performance against a strong statistical baseline (SARIMA).

To evaluate results using RMSE, MAE, and MASE metrics.

3. Dataset Description

The project uses the AirPassengers dataset, which contains monthly airline passenger counts from 1949 to 1960.

Dataset Characteristics:

Strong seasonality (12-month cycle)

Upward trend

Non-stationary behavior

Increasing variance over time

These properties make it suitable for testing deep learning models capable of capturing long-range dependencies.

4. Data Preprocessing
4.1 Train-Test Split

80% training data

20% testing data

Overlapping window used to preserve historical context

4.2 Scaling

StandardScaler was applied to normalize the data before training.
Inverse transformation was applied after prediction to compute real-scale metrics.

4.3 Sequence Creation

Sliding window approach was used:

Sequence Length (Input window): 12 months

Forecast Horizon (Output window): 6 months

Each training sample consists of:

12 past months → predict next 6 months

5. Model Architecture
5.1 Transformer Encoder Components

Input Projection Layer

Maps 1-dimensional time series input to 64-dimensional feature space.

Positional Encoding

Sinusoidal encoding is added to retain temporal order.

Essential because Transformers lack recurrence.

Multi-Head Self-Attention

4 attention heads

Captures long-range dependencies

Learns seasonal patterns automatically

Feedforward Network

Extracts nonlinear temporal features

Final Linear Layer

Outputs 6-step forecast

6. Hyperparameters
Parameter	Value
Sequence Length	12
Forecast Horizon	6
d_model	64
Attention Heads	4
Encoder Layers	2
Dropout	0.1
Learning Rate	0.001
Epochs	120
Optimizer	Adam
Loss Function	MSE
7. Baseline Model

A SARIMA (1,1,1)(1,1,1,12) model was implemented as a statistical benchmark.

SARIMA:

Handles seasonality explicitly

Requires differencing

Assumes linear relationships

8. Evaluation Metrics

The models were evaluated using:

8.1 RMSE (Root Mean Squared Error)

Measures prediction error magnitude. Sensitive to large errors.

8.2 MAE (Mean Absolute Error)

Average absolute difference between prediction and actual values.

8.3 MASE (Mean Absolute Scaled Error)

Scale-independent metric:

𝑀
𝐴
𝑆
𝐸
=
𝑀
𝐴
𝐸
𝑀
𝑒
𝑎
𝑛
 
𝐴
𝑏
𝑠
𝑜
𝑙
𝑢
𝑡
𝑒
 
𝑁
𝑎
𝑖
𝑣
𝑒
 
𝐸
𝑟
𝑟
𝑜
𝑟
MASE=
Mean Absolute Naive Error
MAE
	​


MASE < 1 indicates performance better than naive forecasting.

9. Results Summary
Transformer Model

Successfully captured seasonality

Learned trend progression

Provided stable multi-step forecasts

SARIMA Model

Strong baseline performance

Effective for linear seasonal patterns

Limited in modeling nonlinear temporal dependencies

10. Comparative Analysis
Aspect	Transformer	SARIMA
Long-range dependency	Excellent	Limited
Nonlinearity handling	Strong	Weak
Interpretability	Moderate	High
Multi-step forecasting	Natural	Manual
Feature learning	Automatic	Manual
Key Insight:

The Transformer leverages self-attention to dynamically weight past observations, making it highly effective for complex time series with long-term dependencies.

11. Conclusion

This project demonstrates that attention-based Transformer architectures can be successfully adapted for time series forecasting. Compared to SARIMA:

Transformer better captures nonlinear temporal dependencies.

Positional encoding preserves sequence order.

Self-attention allows flexible long-range learning.

Performance is competitive or superior in multi-step forecasting.

Transformers represent a powerful alternative to traditional statistical methods, especially for complex and non-stationary time series data.

12. Future Improvements

Hyperparameter tuning using grid search

Multivariate time series forecasting

Attention weight visualization

Early stopping & learning rate scheduling

Larger datasets (M4 Competition, financial markets)

Probabilistic forecasting
