# U.S. Recession Prediction with Temporal Machine Learning

This repository contains the full implementation for our project on forecasting U.S. economic recessions using macro-financial indicators and temporal machine learning models. We benchmark classical, ensemble, and deep sequence models—including ARIMAX, logistic regression, LightGBM, BiLSTM, and logistic regression + random forest + Synthetic Minority Oversampling Technique stacked ensembles—to predict NBER-defined recessions up to three months ahead.

## Project Overview

Recessions are difficult to forecast in real time due to nonlinear macro-financial dynamics and regime shifts. Our approach leverages a structured set of monthly indicators (e.g., yield spreads, credit spreads, labor market metrics, volatility measures) and evaluates how temporal models compare in terms of accuracy, timing, and consistency. We introduce two custom metrics—Timing Score and Coverage Score—to assess not just whether models predict recessions, but whether they do so early and consistently.

## Repository Structure

```
├── main.ipynb                      # Main notebook: trains all models and reproduces results
├── requirements.txt                # Python environment dependencies
├── Results/                        # Saved figures and output plots from experiments
├── Trials/                         # Archived notebooks and previous experiment iterations
├── README.md                       
└── .gitignore
```

## Setup Instructions

1. Clone the repository:
   git clone https://github.com/DavidA00/Recession_Prediction.git
   cd Recession_Prediction

2. (Recommended) Create and activate a virtual environment
   python3 -m venv venv
   source venv/bin/activate

3. Install required dependencies
   pip install -r requirements.txt

4. Register the environment as a Jupyter kernel
   python -m ipykernel install --user --name=venv --display-name "Python (Recession_Prediction)"

5. Launch Jupyter Notebook (or JupyterLab if installed)
   jupyter notebook
   OR
   jupyter lab


## Running the Project

All code and results are contained in main.ipynb. Open and run the notebook from top to bottom:

'''
jupyter notebook main.ipynb
'''

This will:
- Load and preprocess the macro-financial dataset
- Train all models (ARIMAX, BiLSTM, LightGBM, ensemble, etc.)
- Evaluate performance using both standard and custom metrics
- Generate all figures and save them

## Models and Evaluation

The models evaluated include:
- Logistic Regression with autoregressive terms
- LightGBM with SMOTE oversampling
- Stacked Ensemble: Random Forest + Logistic Regression
- Stacked Ensemble: Random Forest + Logistic Regression + SMOTE
- ARIMAX and ARIMAX + PCA
- BiLSTM and BiLSTM + PCA

We report standard metrics (ROC AUC, F1, Precision, Recall, Average Precision), along with two custom temporal metrics:
- Timing Score: rewards early and penalizes late recession warnings
- Coverage Score: measures how consistently a model flags the full duration of true recessions

## Reproducibility

You need to request an API key from the FRED website to access the macro-financial dataset. You may do so here: https://fred.stlouisfed.org/docs/api/api_key.html. 
Once you have the key, replace the placeholder in main.ipynb with your actual key. 


## Citation

If you use this code or results, please cite this repository:  
https://github.com/DavidA00/Recession_Prediction
