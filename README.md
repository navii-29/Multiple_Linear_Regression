# Multiple_Linear_Regression

# Algerian Forest Fires – EDA and Preprocessing

This notebook focuses on exploratory data analysis (EDA) and preprocessing of the original Algerian Forest Fires dataset before model training.[file:2]

## Project Overview

- Goal: Clean, understand, and prepare the raw Algerian Forest Fires data for downstream modeling.[file:2]  
- Scope: Load the raw CSV, inspect structure, handle missing and inconsistent values, engineer features, and export a clean dataset.[file:2]

## Dataset Description

The notebook loads `Algerian_Fire.csv` with `header=1` to skip descriptive rows at the top of the file.[file:2]  

The dataset contains daily records with:[file:2]

- **Date components**: day, month (June to September), year (2012)  
- **Weather observations**:  
  - `Temp`: noon temperature in Celsius (approx. 22–42)  
  - `RH`: relative humidity in percent (approx. 21–90)  
  - `Ws`: wind speed in km/h (approx. 6–29)  
  - `Rain`: total daily rainfall in mm (approx. 0–16.8)[file:2]
- **FWI system components**:  
  - `FFMC` – Fine Fuel Moisture Code  
  - `DMC` – Duff Moisture Code  
  - `DC` – Drought Code  
  - `ISI` – Initial Spread Index  
  - `BUI` – Buildup Index  
  - `FWI` – Fire Weather Index[file:2]
- **Target variable**: `Classes` with two categories, “fire” and “not fire”.[file:2]  
- **Region information**: Rows belonging to two different regions in Algeria, with a region indicator added during cleaning.[file:2]

## Workflow

The main steps covered in the notebook are:[file:2]

1. **Import libraries and load data**  
   Uses `pandas`, `numpy`, `seaborn`, and `matplotlib`, then reads `Algerian_Fire.csv`.[file:2]

2. **Initial inspection**  
   - Displays head and tail of the dataframe.  
   - Checks dtypes, missing values, and any non‑data header rows present in the middle of the file.[file:2]  
   - Identifies the row that marks the start of the second region’s data and handles it appropriately.[file:2]

3. **Data cleaning**  
   - Removes or fixes non‑numeric strings (e.g., region titles or malformed numeric entries).  
   - Converts columns like `day`, `month`, `year`, and numeric FWI variables to proper numeric types.[file:2]  
   - Encodes the `Classes` column to numeric form and adds a `Region` column to distinguish the two regions.[file:2]

4. **Exploratory data analysis**  
   - Descriptive statistics for meteorological and FWI variables.  
   - Visualizations: histograms, boxplots, and pairplots to study distributions and potential outliers.[file:2]  
   - Correlation matrix and heatmap to examine relationships among temperature, humidity, FWI components, and the fire class.[file:2]

5. **Exporting cleaned data**  
   After cleaning and EDA, the notebook saves a processed file (e.g., `algerian_fire_cleaned.csv`) that is used later for modeling.[file:1][file:2]

## How to Run

1. Place `Algerian_Fire.csv` in the same directory as the notebook.[file:2]  
2. Create and activate a Python environment:

# Algerian Forest Fire – Model Training

This notebook trains machine learning models to predict the occurrence of forest fires in Algeria using cleaned fire weather data derived from the original Algerian Forest Fires dataset.[file:1]

## Project Overview

- Goal: Build a supervised learning model that predicts whether a day is classified as “fire” or “not fire”.[file:1]
- Input: Meteorological and fire weather indices such as temperature, relative humidity, wind speed, rainfall, and FWI components.[file:1]
- Output: Binary class label indicating fire risk for a given day.[file:1]

## Dataset

The notebook uses `algerian_fire_cleaned.csv`, a preprocessed version of the Algerian Forest Fires dataset.[file:1]

Key features include:[file:1]  

- Date components: `day`, `month`, `year`  
- Weather variables: `Temperature`, `RH` (relative humidity), `Ws` (wind speed), `Rain`  
- FWI components: `FFMC`, `DMC`, `DC`, `ISI`, `BUI`, `FWI`  
- Targets: `Classes` (fire / not fire), `Region` (encoded region id)[file:1]

## Workflow

The notebook roughly follows these steps:[file:1]

1. **Import libraries**  
   Uses `pandas`, `numpy`, `seaborn`, and `matplotlib` for data handling and visualization.[file:1]

2. **Load data**  
   Reads the cleaned dataset with:  
   `data = pd.read_csv("algerian_fire_cleaned.csv")`.[file:1]

3. **Exploratory data analysis**  
   - Head, info and descriptive statistics.  
   - Distribution plots and pairwise correlations between meteorological variables and FWI components.[file:1]  
   - Heatmaps to inspect correlation strength between features and the target class.[file:1]

4. **Data preprocessing**  
   - Handling of any remaining missing values or inconsistencies (if present in the cleaned file).  
   - Encoding categorical variables such as `Classes` and `Region` into numeric form.[file:1]  
   - Feature scaling or normalization where required (e.g., for distance‑based models).[file:1]

5. **Model training**  
   - Splits the dataset into training and test sets.  
   - Trains one or more classification models (e.g., logistic regression, tree‑based models, or ensemble methods) on the engineered features.[file:1]  
   - Tunes hyperparameters and evaluates performance using metrics such as accuracy, precision, recall, F1‑score, and confusion matrix.[file:1]

6. **Evaluation and insights**  
   - Visualizes performance metrics and confusion matrices to understand model behavior on fire vs. not‑fire days.[file:1]  
   - Analyzes feature importance or coefficients to understand which variables most influence fire occurrence (e.g., `FFMC`, `ISI`, `FWI`, temperature, and humidity).[[file:1]]

## How to Run

1. Place `algerian_fire_cleaned.csv` in the same directory as the notebook.[file:1]  
2. Create and activate a Python environment (example with `conda`):



