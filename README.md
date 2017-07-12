## ACCERN

#### _Data for this project can be found [here](https://s3.amazonaws.com/accern-data/2017-07-05.jsonl.gz)._

### Setup

You can install the required python packages using either pip or conda.

- pip  
`pip install -r requirements.txt`

- conda  
`conda env create -f environment.yml`

External unix tools used:

- jq  
`sudo apt-get install jq` (Debian)  
`sudo dnf install jq` (Fedora/RedHat)  

### Notebook

Run the jupyter notebook from the terminal using the below command:

`jupyter notebook --NotebookApp.iopub_data_rate_limit=1.0e10 accern_anomaly_detection.ipynb`

### Explanation

#### Anomaly Detection

##### Low-pass filter (Univariate)

The notebook includes functions which can be used to find anomalies in a time series based on moving variance, i.e. a **low-pass filter**.  
The accern_sentiment values for each row from the provided dataset are used to show how these functions can be used to find anomalies by flagging values off by more than 3 standard deviations from the moving average/mean.

##### K-Means clustering (Multivariate)

Using sklearn's kmeans clustering model, anomaly detection is performed on a dataframe comprised of selected variables from our dataset. The input data is preprocessed so that all the variables are numeric. This is done through binary encoding, one-hot encoding and conversion to numeric type from string type. These numeric variables are normalized so that they are centered around 0 and have a standard deviation of 1.  
This will be useful when performing anomaly detection since we will be able to define a clear threshold (2 would correspond to a data point being 2 standard deviations away from the center of cluster).


#### Anomaly visualization
The function `plot_interactive_ts()` can be used to plot a univariate time series as well as associated anomalies.  
When its parameter `rangeSlider` is set to `True`, it generates a plotly visualization with an interactive x-axis which can
be used to focus on particular time periods.  
It currently supports rolling variance method for anomaly detection. If the anomalies are required to be plotted in addition to the time series, its parameter `with_anomalies` must be set to `True` (default is `False`).

### Notes

##### Challenges
- Limited prior exposure to time-series analysis and anomaly detection methodology, and time constraint resulted in more time spent on grasping fundamentals which could have been put to use for extensive experimentation.
- Large data volume also proved to be slight impediment for experimentation.

##### Libraries considered but not used
- h2o (ref: https://dzone.com/articles/dive-deep-into-deep-learning-using-h2o-1)
- pyculiarity (ref: https://github.com/nicolasmiller/pyculiarity)
- nupic (ref: https://github.com/numenta/nupic, http://www.sciencedirect.com/science/article/pii/S0925231217309864) - *Might be promising for anomaly detection on streaming data*
- filterpy (ref: https://github.com/rlabbe/filterpy) - *Implements Kalman filtering; could have been a good approach but lack of documentation/material to support quick experimentation for anomaly detection*er   
