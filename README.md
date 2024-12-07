# Li-ion Battery Aging Analysis

This project analyzes the aging behavior of Li-ion batteries through repeated charge/discharge cycles and impedance measurements. The dataset contains data from electrochemical impedance spectroscopy (EIS) frequency sweeps (0.1Hz to 5kHz) conducted on Li-ion batteries at various temperatures. This analysis tracks how key battery parameters evolve over time and identifies insights into battery aging and degradation.

## Project Overview

The dataset consists of various operational profiles of Li-ion batteries (charge, discharge, and impedance), with measurements taken during different stages of battery life. The main goal of this analysis is to visualize how specific battery parameters change as the battery cell undergoes aging through repeated charge/discharge cycles.

### Key Parameters:
- **Battery Impedance**: The resistance encountered by the current when passing through the battery.
- **Re**: Estimated Electrolyte Resistance (Ohms)
- **Rct**: Estimated Charge Transfer Resistance (Ohms)
- **Capacity**: The charge capacity of the battery at each cycle.
- **Ambient Temperature**: The temperature at which the battery was tested.

## Project Steps

1. **Data Cleaning**: 
   - The dataset was cleaned to handle missing values and unnecessary columns.
   - Missing values in critical columns (Re, Rct, Capacity) were filled with median or mean values respectively.
   - Unnecessary columns were either removed or replaced with default values (1 for missing values).

2. **Data Analysis**:
   - Data exploration and feature inspection were performed to ensure the integrity of the dataset.
   - Key metrics such as battery impedance, Re, and Rct were plotted to visualize how these parameters change over time and with repeated cycles.

3. **Plotting and Visualization**:
   - The dataset was plotted using Plotly to visualize the aging effect on the battery parameters.
   - The plots include line charts showing how **Re**, **Rct**, and **Capacity** change with the cycle number.

## Prerequisites

- **Python 3.x**
- **Libraries**:
    - Pandas
    - Plotly
    - NumPy

## Installation

You can install the required libraries using pip:

```bash
pip install pandas plotly numpy
```

## Usage

1. Clone or download the repository.
2. Place your cleaned dataset in the correct directory (`metadata.csv`).
3. Run the Python script to load, clean, and analyze the dataset.

### Example Script:
```python
import pandas as pd
import plotly.express as px

# Load the dataset
df = pd.read_csv('path/to/your/cleaned_dataset.csv')

# Data Preprocessing
df['Re'].fillna(df['Re'].median(), inplace=True)
df['Rct'].fillna(df['Rct'].median(), inplace=True)
df['Capacity'].fillna(df['Capacity'].mean(), inplace=True)

# Plot the Battery Parameters
fig = px.line(df, x='cycle_number', y='Re', title='Electrolyte Resistance Over Time')
fig.show()

fig = px.line(df, x='cycle_number', y='Rct', title='Charge Transfer Resistance Over Time')
fig.show()

fig = px.line(df, x='cycle_number', y='Capacity', title='Capacity Over Time')
fig.show()
```

## Results

The generated plots show the following trends:
- **Electrolyte Resistance (Re)** and **Charge Transfer Resistance (Rct)** increase as the battery ages due to internal degradation.
- **Capacity** typically decreases with aging, indicating a loss of battery life over time.

## Contribution

If you'd like to contribute, feel free to submit a pull request. You can suggest improvements to the analysis or add new features like other plots, data preprocessing methods, or statistical analysis.

## License

This project is open-source and available under the MIT License.
