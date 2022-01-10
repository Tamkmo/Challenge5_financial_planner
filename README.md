#Financial Planner

This project entails building a tool to help credit union members evaluate their financial health. Specifically, the tools will help credit union members to be able to do two things. First, they would be able to assess their monthly budgets. Second, they would be able to forecast a reasonably effective retirement plan based on their current holdings of cryptocurrencies, stocks, and bonds. 

Tool#1 - A financial planner for emergencies. The members will be able to use this tool to visualize their current savings. The members can then determine if they have enough reserves for an emergency fund.

Tool#2 - A financial planner for retirement. This tool will forecast the performance of their retirement portfolio in 30 years. 

Technologies

The project is built using jupyter notebook using Python 3.7 framework and its libraries. Jupyter notebook working under the Anaconda framework is the key dependency here, whether Windows or Mac OS. These tools will make an Alpaca API call via the Alpaca SDK to get historical price data for use in Monte Carlo simulations. 

Installation Guide

Ensure following Python libraries are installed using --pip command through the terminal. 
import os
import requests
import json
import pandas as pd
from dotenv import load_dotenv
import alpaca_trade_api as tradeapi
from MCForecastTools import MCSimulation
%matplotlib inline

Usage

The analysis is divided into following sections

Emergency Fund Evaluation
# Evaluate the possibility of creating an emergency fund with 3 conditions:
if total_portfolio > emergency_fund_value:
    print(f"Congratulations you have enough money to supplement emergency funds")

elif total_portfolio == emergency_fund_value:
    print(f"Congratulations you have reached an important financial goal to supplement emergency funds")
        
else:
    print(f"You are: {emergency_fund_value-total_portfolio}$ short to reach your financial goal")


Retirement Fund Returns in 30 yrs and 10 yrs
# Configure the Monte Carlo simulation to forecast 30 years cumulative returns
# The weights should be split 40% to AGG and 60% to SPY.
# Run 500 samples.
thirty_year_simulation = MCSimulation(
portfolio_data = portfolio_prices_mc_df,
weights=[0.40,0.60],
num_simulation=500,
num_trading_days=252*30)
