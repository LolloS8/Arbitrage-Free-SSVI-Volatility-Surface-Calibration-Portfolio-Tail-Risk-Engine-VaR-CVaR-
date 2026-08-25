###-- SECTION 1: OPTION DATA INGESTION & IMPLEMENTED VOLATILITY PREPROCESSING (SPY OPTIONS) -- ###
# Objective: Download complete option chains across multiple expiration dates for SPY (S&P 500 ETF).
# Filter out illiquid quotes, construct log-moneyness k = ln(K / F_T) (log moneyness centers the data at zero and remains stable across different T), time-to-maturity T, 
# and toatl implied variance w(k, T) to prepare the raw dataset for SSVI (Surface Stochastic Volatility Inspired)
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
import yfinance as yf
from datetime import datetime 
import warnings 
warnings.filterwarnings('ignore')

# 1. Data Downloading: SPY Option Chains across Expirations 
ticker_symbol = "SPY"
print(f"\nDownloading Underlying Market Data and Option Chains for {ticker_symbol}")
