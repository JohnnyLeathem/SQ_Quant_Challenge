# Credit Spread Prediction and ETF Allocation Strategy

This project uses machine learning to predict US credit spreads based on macroeconomic indicators and market volatility. It implements a regime-switching trading strategy that dynamically allocates ETFs based on forecasted credit market risk.

## Overview

- **Goal:** Forecast weekly credit spread movements using macroeconomic data (Treasury yields, VIX) with Random Forest and XGBoost models.
- **Outputs:** 
  - Predicted credit spreads
  - Market regime classification ("Low Risk" / "High Risk")
  - Dynamic ETF allocation signals based on regimes and credit spread direction
- **Data:** Weekly US Treasury yields (short-term and long-term), VIX index, historical credit spreads.
- **Models:** Linear Regression, Random Forest, XGBoost (best performance).
- **Strategy:** Rotate ETFs weekly between growth and defensive based on predicted regime.

## Features

- Lagged and rolling window features to capture temporal dynamics.
- Feature importance analysis for interpretability.
- Regime classification combining VIX and predicted credit spreads.
- Tactical spread direction signals (widening/tightening) for trade timing.
- Visualization of feature importance and model performance.

## Setup Instructions

1. Clone this repo.
   
2. Intall dependencies (recommended: use a virtual environment):
  ```bash
  pip install -r requirements.txt
  ```

3. Prepare your dataset files and place in the root - one file needed, with the following structure:

|            | T-Bill_13W_Yield   | 10Y_Treasury_Yield | VIX   | Credit_Spread |
|------------|--------------------|--------------------|-------|---------------|
| 01/01/2018 | 1.23               | 3.45               | 17.5  | 120           |
| 02/01/2018 | 1.25               | 3.50               | 18.0  | 123           |
| 03/01/2018 | 1.28               | 3.55               | 16.8  | 119           |
| 04/01/2018 | 1.30               | 3.60               | 17.2  | 122           |
| 05/01/2018 | 1.35               | 3.62               | 16.5  | 121           |

4. Since the project's main code is in a **Jupyter Notebook** (.ipynb) format, it is not directly executable via the command line using python script_name.py.

Instead, to run the notebook:
  - Open it in Jupyter Notebook or JupyterLab.
  - Execute cells interactively in the notebook interface.

To run the code via command line:
  - Convert the notebook to a Python script using:
    ```
    jupyter nbconvert --to script your_notebook.ipynb
    ```
  - This generates your_notebook.py, which you can then run with:
    ```
    python your_notebook.py
    ```
  - Alternatively, copy essential code into a .py file (e.g., main.py) and run it with:
    ```
    python main.py
    ```

## File Structure

📦 SQ_Quant_Challenge/
├── SQIG_Code.ipynb              # Main Jupyter notebook containing the full analysis, modeling, and results
├── SQIG_data.csv                # Primary dataset with macroeconomic indicators, VIX, and credit spreads
├── SQIG Final Report Summary - PDF.pdf  # Concise report summarising approach, results, and insights
├── requirements.txt             # List of Python package dependencies required to run the notebook

## Usage

- Modify the data input paths in the code if needed.
- Tune model hyperparameters for XGBoost in the main notebook (optional).
- Adjust choice of ETFs in main trading strategy (optional).

## Results

- XGBoost achieved ~99% directional accuracy on credit spread prediction.

- Long-term Treasury yields were the most important features.

- The ETF allocation strategy dynamically switched between growth and defensive ETFs according to model regimes.

- Weekly trading signals indicated spread widening or tightening, aiding tactical decisions.

## Future Improvements

- Incorporate additional macro features (inflation surprises, employment data).

- Enhance regime classification with more nuanced states.

## License


