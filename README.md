# P&L Exception Dashboard

Python-based middle-office workflow for a simulated spot FX trading book. This project calculates expected daily P&L, compares it to reported P&L, classifies material variances, and produces dashboard outputs for exception review. The repo currently contains four notebooks, a `data` folder, a `reports` folder, and a `requirements.txt` file. :contentReference[oaicite:0]{index=0}

## Project Overview

This project simulates a middle-office analyst supporting a small FX trading book. It uses daily prices, trades, fees, and positions to:

- calculate expected daily P&L
- compare expected vs reported P&L
- detect material exceptions
- classify likely root causes
- generate dashboard outputs for review

## Scope

- Asset class: Spot FX
- Instruments: EURUSD, GBPUSD, AUDUSD
- Time horizon: 45 business days
- Exception types:
  - missing trade
  - duplicate booking
  - stale price
  - wrong position
  - incorrect fee

## Repository Structure

- `01_data_build.ipynb` – builds the clean input datasets
- `02_pnl_engine.ipynb` – calculates expected daily P&L
- `03_exception_logic.ipynb` – compares expected vs reported P&L and classifies breaks
- `04_dashboard.ipynb` – creates dashboard tables and charts
- `data/` – input and output files
- `reports/` – methodology, investigation notes, and summary materials :contentReference[oaicite:1]{index=1}

## Tools Used

- Python
- pandas
- numpy
- matplotlib

## Key Outputs

- expected P&L engine
- reported vs expected variance analysis
- rule-based exception classification
- dashboard summaries and charts
- investigation notes
- methodology and controls documentation

## How to Run

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
2. Run the notebooks in order:
    01_data_build.ipynb
    02_pnl_engine.ipynb
    03_exception_logic.ipynb
    04_dashboard.ipynb

## Purpose

This project was built to demonstrate skills relevant to trading middle-office and operations roles, including daily P&L explain, exception handling, control-focused reporting, and Python-based data workflows.
