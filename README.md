# Global Air Quality Dashboard

A compact interactive dashboard exploring global air quality measurements from OpenAQ.

## Overview
This repository contains a Dash-based interactive dashboard (in `DAV Project FINAL.ipynb`) that visualises air pollutant measurements (PM2.5, PM10, NO2, SO2, O3, CO) from the provided `openaq.csv` dataset. The dashboard allows filtering by pollutant, date range, and interacting with geographic visualisations to update the rest of the charts.

## Data
- `openaq.csv` — Observational air quality measurements used for visualisations and analysis.
- `world_data.csv` — Country/region lookup dataset used to resolve continents/regions for the sunburst and filtering.

## Features
- Interactive world map of monitoring stations (scatter markers sized/colored by pollutant value)
- Sunburst chart showing continent → country → pollutant (or continent → country for single pollutant)
- Time series plot (per-pollutant or multiple pollutants when `All` is selected)
- Top-10 country bar chart (by average pollutant value)
- Metric cards showing mean, median and max values for the current selection
- Date range picker and pollutant dropdown filter

## Cleaning & Preprocessing Summary
Key steps applied in the notebook:
- Converted `Last Updated` to timezone-aware datetime and created a `Date` column
- Split `Coordinates` into `Latitude` and `Longitude` and coerced to numeric values
- Filled missing `City` values with `Unknown`
- Removed sentinel values like `-9999` and `9999`; removed negative or NaN pollutant readings
- Resolved country → continent mapping using `world_data.csv` with fallbacks (pycountry, fuzzy matching, special-case mappings)