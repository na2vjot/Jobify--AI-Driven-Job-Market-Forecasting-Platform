# Jobify — AI-Driven Job Market Forecasting Platform

> **Published Research:** [AI-Driven Predictive Analytics for Identifying Emerging Trends in Quality-Oriented Employment](https://journals.mriindia.com/index.php/ijeecs/article/view/231)  
> *International Journal of Electrical, Electronics and Computer Systems (IJEECS), Vol. 14, Issue 1, pp. 56–62 | DOI: 10.65521/ijeecs.v14i1.231*

Jobify is an end-to-end job market analytics platform built as a Third Year Engineering project. It scrapes live job postings from Naukri.com, applies SARIMA-based time-series forecasting to predict hiring trends across 40 job roles in four industries, and surfaces insights through an interactive Tableau dashboard and a PHP/MySQL web frontend.

---

## Table of Contents
- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Methodology](#methodology)
- [Model Performance](#model-performance)
- [Dashboard](#dashboard)
- [Frontend](#frontend)
- [How to Run](#how-to-run)
- [Dataset](#dataset)
- [Research Paper](#research-paper)

---

## Overview

The labour market is evolving rapidly across technology, finance, healthcare, and manufacturing. Jobify addresses the challenge of forecasting where hiring demand is headed — giving job seekers, employers, and policymakers data-driven guidance.

**Key capabilities:**
- Scrapes and processes job postings data from Naukri.com
- Forecasts job demand for 40 roles (10 per industry) over a 3-year horizon using SARIMA
- Identifies top in-demand skills and location-based hiring heatmaps per role
- Visualizes salary distributions, seasonal hiring patterns, and trend trajectories in Tableau
- Web frontend (PHP + MySQL, hosted on AWS RDS) for browsing insights by industry

---

## Tech Stack

| Layer | Tools |
|---|---|
| Data Collection | Python, BeautifulSoup (web scraping) |
| Data Processing | Python, Pandas, NumPy |
| Forecasting Model | SARIMA (statsmodels) |
| Visualization | Tableau |
| Frontend | PHP, HTML/CSS, JavaScript |
| Database | MySQL (AWS RDS) |
| Notebooks | Jupyter |

---

## Project Structure

```
jobify/
├── web-scraping.ipynb                  # Naukri.com scraper
├── preprocessing.ipynb                 # Data cleaning & EDA
├── sarima-model.ipynb                  # SARIMA model training & forecasting
├── model_evaluation_metrics.csv        # MAE, MSE, RMSE, R² per job role
│
├── raw sample data/
│   ├── data analyst.csv
│   └── cyber analyst.csv
│
├── clean data/
│   ├── clean_analyst.csv
│   └── clean_cyber.csv
│
├── job_role_data/                      # Per-role output files
│   ├── Cyber Security Analyst_predictions.csv
│   ├── Cyber Security Analyst_top_skills.csv
│   └── Cyber Security Analyst_location_heatmap.csv
│
├── Cyber Security Analyst_future_job_forecast.csv   # 3-year forecast (2025–2027)
│
└── frontend/
    ├── index.php                       # Landing page
    ├── login.php / signup.php
    ├── db.php                          # AWS RDS connection
    ├── technology.html
    ├── finance.html
    ├── healthcare.html
    ├── manufacturing.html
    ├── styles.css
    └── javascript.js
```

---

## Methodology

1. **Web Scraping** — Collected historical job postings for 40 roles across 4 industries from Naukri.com using BeautifulSoup.
2. **Preprocessing** — Cleaned raw data: removed duplicates, standardised job titles, parsed dates, extracted skill keywords.
3. **Modelling** — Applied **SARIMA** (Seasonal ARIMA) to capture both long-term trends and seasonal hiring cycles. SARIMA was chosen over XGBoost and LSTM because it explicitly models temporal autocorrelation and seasonality — critical for monthly job posting data.
4. **Forecasting** — Generated 36-month forecasts (2025–2027) per job role, along with top-skills frequency and location-based demand heatmaps.
5. **Visualisation** — Published an interactive Tableau dashboard with filters for industry, role, skills, salary, and geography.
6. **Frontend** — Built a PHP web app connected to AWS RDS, allowing users to browse industry-specific insights.

---

## Model Performance

Sample metrics for **Cyber Security Analyst**:

| Metric | Value |
|---|---|
| MAE | 200.58 |
| MSE | 49,628.39 |
| RMSE | 222.77 |
| R² | **0.7914** |

---

## Dashboard

<!-- Add your Tableau Public link below -->
> 📊 **Tableau Dashboard:** https://public.tableau.com/app/profile/navjot.singh.shron/viz/cybersecurity_17405068312400/Dashboard1

The dashboard covers:
- Job count trends and 3-year forecasts per role
- Top skills by frequency
- Hiring heatmaps by location
- Salary distribution across roles and industries
- Seasonal hiring patterns

---

## Frontend

The web app is built in PHP and connects to a MySQL database hosted on AWS RDS. Users can browse job insights segmented by industry — Technology, Finance, Healthcare, and Manufacturing.

> The frontend uses environment variables for DB credentials (`RDS_HOSTNAME`, `RDS_USERNAME`, etc.) — do not hardcode credentials.

---

## How to Run

### Notebooks (Scraping → Preprocessing → Modelling)

```bash
pip install pandas numpy statsmodels matplotlib seaborn beautifulsoup4 requests jupyter
jupyter notebook
```

Run in order:
1. `web-scraping.ipynb`
2. `preprocessing.ipynb`
3. `sarima-model.ipynb`

### Frontend (Local)

Requires PHP + MySQL. Set the following environment variables before running:

```bash
export RDS_HOSTNAME=your_host
export RDS_USERNAME=your_user
export RDS_PASSWORD=your_password
export RDS_DB_NAME=your_db
```

Then serve with:
```bash
php -S localhost:8000 -t frontend/
```

---

## Dataset

Raw and cleaned sample data is included for **Data Analyst** and **Cyber Security Analyst** roles. Full dataset for all 40 roles was scraped from [Naukri.com](https://www.naukri.com/).

---

## Research Paper

This project was published in the **International Journal of Electrical, Electronics and Computer Systems (IJEECS)**:

> *AI-Driven Predictive Analytics for Identifying Emerging Trends in Quality-Oriented Employment*  
> IJEECS, Vol. 14, Issue 1, pp. 56–62, April 2025  
> DOI: [10.65521/ijeecs.v14i1.231](https://doi.org/10.65521/ijeecs.v14i1.231)  
> [Read the paper →](https://journals.mriindia.com/index.php/ijeecs/article/view/231)

---

## Authors

Built as a Third Year B.E. Computer Engineering project at Mumbai University.
