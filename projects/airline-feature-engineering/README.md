# Airline Feature Engineering

A beginner-friendly notebook for exploring and engineering features from airline ticket data. This is a separate project inside the `ml-journey` repository and uses its own Python virtual environment.

## Dataset

The notebook uses the airline fares workbook from March–June 2019: [airlines_data.xlsx](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-ML0232EN-SkillsNetwork/asset/airlines_data.xlsx). The notebook downloads the workbook into `data/airlines_data.xlsx` when it is missing. It does not overwrite an existing local copy. The raw workbook is excluded from Git, so each person running the notebook will get a local copy on the first run.

## Environment

From this project directory, create and activate its environment, then install dependencies:

```bash
cd ~/Documents/ml-journey/projects/airline-feature-engineering
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

In VS Code, open `notebooks/feature_engineering.ipynb` and select the `.venv` Python interpreter as its kernel. Run the cells from top to bottom. The acquisition cell creates the `data/` directory if needed and downloads the workbook only when a local copy is missing.

## Notebook progress

- `notebooks/feature_engineering.ipynb` — covers the full workflow so far:
  1. Setup, dataset inspection, and missing-value handling
  2. Feature transformation (label merging, one-hot encoding, stop-count encoding)
  3. Date and time features (duration in minutes, departure/arrival parts, time-of-day groups, calendar fields)
  4. Feature selection with a correlation heatmap and correlations with `Price`
  5. Feature extraction with PCA (explained variance, 95% variance target, 16 components)
