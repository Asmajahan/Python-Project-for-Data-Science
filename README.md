# Stock Data Extraction and Visualization

This project focuses on extracting stock data for analysis and visualization. By using financial data from popular stocks, we can analyze and compare stock trends with revenue performance to gain insights into market patterns. This project uses web scraping and Python libraries to acquire, process, and visualize stock and revenue data for two well-known companies.

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)
- [Features](#features)
- [Usage](#usage)
- [Contributions](#contributions)

## Overview
Stock data analysis is crucial for making informed decisions in finance. This project involves:
- Extracting historical stock data for selected companies.
- Web scraping revenue data.
- Visualizing stock prices alongside revenue over time.

Using libraries like `yfinance`, `requests`, and `BeautifulSoup`, we gather stock prices and revenue data, then display them with line charts to identify trends.

## Project Structure
The project includes:
- **Data Extraction**: Using `yfinance` to pull stock data.
- **Web Scraping**: Extracting quarterly revenue data for selected companies.
- **Visualization**: Generating line charts that show historical stock prices and revenues.

## Dependencies
Install the following packages:

```bash
pip install yfinance==0.1.67
mamba install bs4==4.10.0 -y
pip install pandas
pip install plotly
```

# Features
- **Data Extraction**: Gather data using the yfinance API for historical stock data.
- **Revenue Data Scraping**: Use BeautifulSoup to extract revenue data from company web sources.
- **Interactive Visualization**: Line graphs display stock and revenue data over time using Plotly.

# Usage
1. **Define Function for Visualization**: Create a function to plot stock and revenue data with dual axes.
2. **Extract Stock Data**: Use yfinance to download stock data.
3. **Scrape Revenue Data**: Use requests and BeautifulSoup to obtain quarterly revenue data.
4. **Generate Visualization**: Plot the extracted data for comparative analysis.

### Example code snippet:
```python
import yfinance as yf
import pandas as pd
import requests
from bs4 import BeautifulSoup
import plotly.graph_objects as go
from plotly.subplots import make_subplots

# Define graphing function
def make_graph(stock_data, revenue_data, stock_name):
    # Create subplots for stock price and revenue with shared x-axis
    fig = make_subplots(rows=2, cols=1, shared_xaxes=True, 
                        subplot_titles=("Historical Share Price", "Historical Revenue"), 
                        vertical_spacing=0.1)
    # Plotting stock price data
    fig.add_trace(go.Scatter(x=stock_data['Date'], y=stock_data['Close'], 
                             mode='lines', name="Stock Price"), row=1, col=1)
    # Plotting revenue data
    fig.add_trace(go.Scatter(x=revenue_data['Date'], y=revenue_data['Revenue'], 
                             mode='lines', name="Revenue"), row=2, col=1)
    # Layout settings
    fig.update_layout(title=stock_name, xaxis_rangeslider_visible=True)
    fig.show()

# ```
