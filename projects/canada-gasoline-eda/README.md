# Canadian Gasoline Prices: Exploratory Data Analysis

This project explores historical monthly average retail fuel prices reported by Statistics Canada. The notebook inspects the source data, prepares dates and geographic labels, answers filtering and grouping questions, and visualizes price trends across the represented markets.

## Scope and interpretation

The source file covers January 1979 through October 2021. Prices are reported in cents per litre. Geographic records represent selected Canadian city and metropolitan markets. The province and territory map summarizes those represented city-market observations; it is not a complete set of official province-wide or national averages. Ottawa–Gatineau is a cross-border market and is excluded from the province-level grouping.

## Data sources

- [Statistics Canada table 18-10-0001-01](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=1810000101)
- [CSV file used by the notebook](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-ML0232EN-SkillsNetwork/asset/18100001.csv)
- [Province and territory GeoJSON used for the map](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-ML0232EN-SkillsNetwork/asset/canada_provinces.geojson)

The notebook's data-acquisition cell downloads the CSV into `data/18100001.csv` and loads it with pandas. Running that cell again replaces the local file with a fresh download. The project Git ignore rules exclude the downloaded CSV. The geographic visualization downloads its GeoJSON when its cell runs.

## Set up the environment

Run these commands in a VS Code terminal from this project directory:

```bash
cd ~/Documents/ml-journey/projects/canada-gasoline-eda
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install pandas requests matplotlib plotly ipykernel
```

The virtual environment is local to this project and is excluded from Git. Pandas handles the data, Requests downloads the source files, Matplotlib creates a static chart, and Plotly creates interactive charts and the map. The notebook also uses Python's built-in `datetime`, `json`, and `pathlib` modules, which do not need to be installed separately.

## Open and run the notebook

1. Open the `ml-journey` folder in VS Code.
2. Open `projects/canada-gasoline-eda/notebooks/gasoline_eda.ipynb`.
3. Select the Python interpreter at `projects/canada-gasoline-eda/.venv/bin/python` as the notebook kernel.
4. Run the cells from top to bottom. The first data-acquisition cell downloads the CSV into this project's `data/` directory.

If VS Code does not list the environment, activate `.venv` in the terminal and install `ipykernel` with the command above, then reopen the kernel selector.

## Notebook sections

- Dataset dimensions, columns, data types, and missing-value counts
- Date and geographic-label preparation
- Filtering and grouped summaries
- Annual and monthly price visualizations
- A map of represented city-market prices by province or territory

## Project structure

```text
canada-gasoline-eda/
├── data/
│   └── 18100001.csv             # downloaded locally; excluded from Git
├── notebooks/
│   └── gasoline_eda.ipynb
├── .gitignore
└── README.md
```

The notebook is the main project deliverable. The dataset and virtual environment are not committed; the notebook retrieves the source CSV when its acquisition cell is run.
