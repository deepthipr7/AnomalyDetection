# AnomalyDetection

Anomaly detection in time series data is finding an abnormlity in the data distribution considering the seasonlaity factor of the data.

# High Level Overview of the Code and Algorithm:
First, the provided data was visualized using tableau to gain an overall understanding. The visualization and observations have been show below.

In order to detect the anomaly, the first step is to decompose the time series into its various components – trend, seasonality and residual. To do this, the Seasonal Trend Decomposition by Loess (STL) algorithm was selected. This algorithm handles seasonality very well and uses locally weighted polynomial regression to estimate trend (which is superior to using a moving average method). It is also pretty simple to implement.  The code was implemented in python using an open source library from stldecompose. 


Prior to running the algorithm, a data preprocessing step was required to estimate the data points for the 15th/16th of June (since STL requires a continuous set of data). This was estimated as the average of the values of the data (at similar times) for the 14th and 15th.

The STL algorithm was then run and the results initially analyzed using Tableau (shown below). The green line (residual) shows a sudden spike due to the anomalous data value for the 18th of June.

The residual component of the time series was analyzed to detect the anomalous timestamps. The rule applied to categorize a point as anomalous is as follows: “if there are more than 5 consecutive timestamps having values greater than three times the standard deviation of the residual, then the points are anomalous”.

Following are some possible alternatives I came across but did not get a chance to try due to limitations on time:

      Alternate Algorithms: Exponential forecasting methods such as holt-winters seasonal model and classification and regression trees
      Alternate Outlier Detection Methods: Median/Mean Absolute Deviation instead of Standard Deviation 

# Execution Instructions (in Linux)
1. The code is developed in python.
2. Download or clone the repository.
3. Go to the folder and right click open terminal.
4. Run jupyter notebook command.
5. Jupyter opens in the browser. Double-click Anomaly detection algorithm.ipynb
6. Run the code or shift+enter to get the results.
