Forecasting with Transformer vs SARIMA
1. Introduction
This project investigates the performance of a Transformer-based time series forecasting model compared to a SARIMA baseline. The objective is to evaluate whether deep learning architectures can outperform classical statistical models when systematic hyperparameter tuning and rigorous evaluation are applied.

2. Data Preprocessing
- Dataset description: source, size, and features.
- Cleaning and normalization steps.
- Train/validation/test split strategy.
- Sequence length and input-output windowing.

3. Hyperparameter Tuning
- Search strategy: Grid Search, Random Search, or Bayesian Optimization.
- Parameters explored:
- Learning rate: [0.0001, 0.001, 0.01]
- Epochs: [50, 100, 150]
- Batch size: [16, 32, 64]
- Dropout: [0.1, 0.3, 0.5]
- Best configuration identified and justification.
- Evidence of tuning runs documented in logs or tables.

4. Model Architectures
- SARIMA: baseline model with chosen parameters.
- Transformer: description of layers, hidden size, attention heads, and dropout.
- Rationale for architecture choices.

5. Evaluation Methodology
- Metrics used: MASE, RMSE, MAE.
- Forecast horizon analysis (short-term vs long-term).
- Statistical comparison:
- Diebold-Mariano test results.
- Confidence intervals for error metrics.
- Error distribution analysis.

6. Code Structure
project/
│── data_preprocessing.py
│── model.py
│── train.py
│── evaluate.py
│── utils.py
│── notebooks/ (exploratory analysis)
│── README.md



7. Results
- SARIMA performance: MASE = X.X
- Transformer performance: MASE = Y.Y
- Comparative analysis with discussion of why one model outperformed the other.

8. Reproducibility
- Installation instructions.
- How to run preprocessing, training, and evaluation scripts.
- Example usage:
python train.py --model transformer --epochs 100 --lr 0.001



9. Limitations and Future Work
- Limitations of dataset and model.
- Potential improvements:
- Larger datasets.
- Hybrid models.
- Advanced tuning strategies.
