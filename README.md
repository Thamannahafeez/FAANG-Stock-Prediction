# FAANG Stock Forecasting \& Spike News Analysis

This project leverages Python to analyse, forecast, and explain major price movements ("spikes") for key technology stocks, often referred to as the "FAANG" group, plus NVIDIA. The workflow encompasses data acquisition, price prediction, spike detection, and automated news headline retrieval, enabling the interpretation of market movements.

## Features

- **Stock Data Retrieval**: Download historical daily stock prices for Meta, Amazon, Netflix, Google, and NVIDIA using `yfinance`.
- **Forecasting with Prophet**: Predicts stock closing prices for up to 2 years into the future on selected target dates.
- **Spike Detection**: Identifies significant daily price changes (by default >5%).
- **Automated News Scraping**: Uses SerpAPI to fetch major news headlines related to each price spike—enabling quick fundamental insight.
- **CSV Outputs**: Saves raw data, spike events, and news links to separate CSV files for further analysis.


## Project Structure

```
/
├── FAANG.ipynb           # Jupyter notebook with all code & analysis
├── Meta.csv              # Stock price history for Meta (generated)
├── Amazon.csv            # Stock price history for Amazon (generated)
├── Netflix.csv           # Stock price history for Netflix (generated)
├── Google.csv            # Stock price history for Google (generated)
├── NVIDIA.csv            # Stock price history for NVIDIA (generated)
├── spike_<name>.csv      # Price spike events for each stock (generated)
└── faang_spike_news.csv  # News headlines for spike days (generated)
```


## Workflow Overview

1. **Setup \& Import**
    - Loads all necessary packages: `yfinance`, `Prophet`, `pandas`, SerpAPI, etc.
2. **Data Download**
    - Downloads and stores up to 5+ years of daily price data for each company.
3. **Stock Forecasting**
    - Runs Prophet forecasts for each stock and prints target-date predictions.
4. **Spike Detection**
    - Flags daily price changes above a set threshold (default 5%) for recent (last-year) data.
5. **News Headline Retrieval**
    - For each spike, queries Google News (via SerpAPI) for relevant headlines and saves results.

## Requirements

- Python 3.8+
- [yfinance](https://pypi.org/project/yfinance/)
- [Prophet](https://facebook.github.io/prophet/)
- [pandas](https://pandas.pydata.org/)
- [datetime](https://docs.python.org/3/library/datetime.html)
- [dateutil](https://dateutil.readthedocs.io/en/stable/)
- [serpapi](https://pypi.org/project/google-search-results/)

Install using pip:

```bash
pip install yfinance prophet pandas python-dateutil google-search-results
```


## Usage

1. **Clone the repo \& enter the directory:**

```
git clone <your-github-repo-url>
cd <repo-folder>
```

2. **Open the Jupyter notebook:**

```
jupyter notebook FAANG.ipynb
```

3. **Edit API Keys (if needed):**
    - Set your [SerpAPI](https://serpapi.com/) key in `SERPAPI_KEY`.
4. **Run through each cell:**
    - The workflow is automatically handled from setup to saving results.

## 🔎 Outputs

- **Stock CSVs:** Daily prices for each ticker.
- **Spike CSVs:** All spikes (up or down) >5% for each company, last year.
- **News CSV:** Headlines relevant to each spike (in `faang_spike_news.csv`).

Sample forecast output for 2025-2027 (Meta):

```
2025-08-31: $724.67
2025-12-31: $761.17
2026-08-31: $895.27
...
```

Sample spike notification:

```
⚠️ on 2025-04-09 (spike: 14.76%)...
```


## ⚠️ Important Notes

- **Financial Disclaimer:** This code is for educational analysis only. Stock predictions are not investment advice.
- **API Limits:** Too many rapid SerpAPI requests can hit rate limits—see [SerpAPI docs](https://serpapi.com/) for terms.
- **Data Delays:** yfinance and news APIs may slightly lag real-time markets.
