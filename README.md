## NVDA Price Prediction using Random Forest Classifier

This project demonstrates how to use a Random Forest Classifier to predict stock price movements. It applies various predictors such as closing price, volume, open/high/low prices, and introduces rolling averages and trends over different time horizons to enhance model performance.

## Table of Contents
Introduction
Dataset
Requirements
Installation
Usage
Model Details
Results
Contributing
License

### Introduction
The goal of this project is to predict whether a stock price will rise or fall on the next trading day based on historical data. The project uses a machine learning model called Random Forest Classifier to make these predictions.

The main tasks included:

Training the model on historical stock price data.
Backtesting the model to evaluate performance.
Improving the model by adding rolling averages and trends as predictors.
Evaluating precision, i.e., how often the model correctly predicts upward stock movements.

### Dataset
The dataset used for this project contains stock price data such as:Open
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

### Usage
Train the Model:

You can train the model using the provided code by defining the training and test sets, then fitting the model.

Example:

python
Copy code
model = RandomForestClassifier(n_estimators=100, min_samples_split=100, random_state=1)
model.fit(train[predictors], train["Target"])
Make Predictions:

After training the model, you can use it to make predictions on the test set:

python
Copy code
predictions = model.predict(test[predictors])
Backtesting:

To evaluate the model’s performance over different test periods, use the backtesting function:

python
Copy code
predictions = backtest(nvda, model, predictors)
Plot Results:

You can visualize the comparison between actual and predicted values by plotting:

python
Copy code
combined.plot()

### Model Details
The model used is a Random Forest Classifier:

n_estimators: The number of decision trees used in the model (default is 100).
min_samples_split: The minimum number of samples required to split a node in the decision tree (default is 50).
The model predicts whether the stock price will rise (1) or fall (0).
We also introduced rolling averages and trend indicators to enhance the model’s feature set. These features are computed for different time horizons (2, 5, 60, 250, 1000 days).

Example of adding rolling averages and trends:

python
Copy code
horizons = [2, 5, 60, 250, 1000]

for horizon in horizons:
    rolling_averages = nvda.rolling(horizon).mean()
    ratio_column = f"Close Ratio_{horizon}"
    nvda[ratio_column] = nvda["Close"] / rolling_averages["Close"]
    
    trend_column = f"Trend_{horizon}"
    nvda[trend_column] = nvda.shift(1).rolling(horizon).sum()["Target"]

### Results
After backtesting, we evaluate the model’s performance using precision—which is the ratio of correct positive predictions to the total number of positive predictions.

Precision score example after model training:

python
Copy code
precision_score(test["Target"], predictions)
Example Precision Scores:
Initial Precision: 0.7
After Backtesting: 0.511
After Adding New Predictors: 0.577
You can adjust the model and predictors to further improve precision or other metrics like recall and accuracy.

### Contributing
Feel free to contribute to this project. Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

### Fork the project.
Create your feature branch (git checkout -b feature/your-feature-name).
Commit your changes (git commit -m 'Add your feature').
Push to the branch (git push origin feature/your-feature-name).
Open a pull request.

### License
This project is licensed under the MIT License - see the LICENSE file for details.
