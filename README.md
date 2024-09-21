## NVDA Price Prediction using Random Forest Classifier

This project uses Yahoo Finance data to analyze and predict the movement of NVIDIA (NVDA) stock prices. Starting with a basic machine learning model using a Random Forest Classifier, we then enhance the model by introducing new predictors such as rolling averages and trends to move from a beginner to intermediate level.

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
[![jupyter](https://img.shields.io/badge/Jupyter-Lab-F37626.svg?style=flat&logo=Jupyter)](https://jupyterlab.readthedocs.io/en/stable)

## Table of Contents
Introduction
Dataset
Requirements
Installation
Beginner Version
Intermediate Version 
Contributing
License

### Introduction
The goal of this project is to predict whether NVDA price will rise or fall on the next trading day based on historical data. The project uses a machine learning model called Random Forest Classifier to make these predictions.

The main tasks included:

Training the model on historical stock price data.
Backtesting the model to evaluate performance.
Improving the model by adding rolling averages and trends as predictors.
Evaluating precision, i.e., how often the model correctly predicts upward stock movements.

### Dataset
The dataset used for this project contains stock price data such as:

Open
High
Low
Close
Volume
Target (The movement direction: 0 for down, 1 for up)
Additionally, new features like rolling averages and trends were created based on the raw data to improve the model’s predictive power.

### Requirements
The project requires the following Python libraries:

pandas
numpy
matplotlib
scikit-learn

### You can install all the dependencies by running:

pip install -r requirements.txt

### Installation
Clone this repository:

bash
Copy code
git clone https://github.com/your-username/stock-prediction-random-forest.git
cd stock-prediction-random-forest

Install the dependencies:

bash
Copy code
pip install -r requirements.txt
Place your stock price data in the appropriate format (e.g., a CSV file with the relevant columns) into the directory.

### Beginner Version:
Basic Data Extraction: Using the yfinance package to pull NVDA stock data from Yahoo Finance.
Initial Predictions: Creating a basic stock price prediction model using Random Forest Classifier based on simple stock attributes like Close, Open, High, Low, and Volume.
Target Generation: Introducing a simple prediction logic for predicting if the next day's stock price will be higher or lower.

### Intermediate Version:
Advanced Predictors: Added new rolling averages and trend-based predictors over different horizons (2, 5, 60, 250, 1000 days).
Improved Model: Adjusted the RandomForestClassifier to better handle complex features and used probability predictions to adjust model thresholds dynamically.
Backtesting: Implemented a more advanced backtesting framework to simulate the model over historical data and measure its effectiveness.
Model Evaluation: The precision of the model was recalculated with new predictors, achieving a better understanding of upward movement predictions.

### Contributing
Feel free to contribute to this project. Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

### Fork the project.
Create your feature branch (git checkout -b feature/your-feature-name).
Commit your changes (git commit -m 'Add your feature').
Push to the branch (git push origin feature/your-feature-name).
Open a pull request.

### License
This project is licensed under the MIT License - see the LICENSE file for details.
