# real_state_funds_VS_SELIC
# Correlation matrix between a real state fund vs Brazil Interest rate SELIC

# First we have to import our library

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import pandas_datareader.data as web
import seaborn as sns

# Upload the csv file 

asset = pd.read_csv('HGLG11.SA_PRED.csv', encoding = "latin-1")


asset.head()

# We have to drop any null value that may appear 

asset = asset.dropna()
asset

# Let's define our variable 

asset.columns = ["Date", "Close", "Interest Rate - SELIC"]
asset

# We then plot the graph with both variables Close, which is the closing price of the last trading day VS The last SELIC rate given by the central bank.

sns.set()
asset.plot(subplots=True, figsize=(22,8))

# By looking at the graph we can tell a negative correlation. When Interest rate goes up, the real state fund (HGLG) goes down and vice-versa. This phenomena can be explained by the cost of opportunity. But this is something to be discussed in another opportunity. 

# Let's now plot the matrix 

sns.heatmap(asset.corr(), annot=True)

# The result shows a negative correlation of -.83, which means that when Interest rate goes up, fund's price goes down. 
