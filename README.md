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

##### Anomaly Detection
In its current version, the notebook includes functions which can be used to find anomalies in a time series based on moving variance.  
The accern_sentiment values for each row from the provided dataset are used to show how these functions can be used to find anomalies by flagging values off by more than 3 standard deviations from the moving average/mean.

##### Anomaly visualization
The function `plot_interactive_ts()` can be used to plot a univariate time series as well as associated anomalies.  
When its parameter `rangeSlider` is set to `True`, it generates a plotly visualization with an interactive x-axis which can
be used to focus on particular time periods.  
It currently supports rolling variance method for anomaly detection. If the anomalies are required to be plotted in addition to the time series, its parameter `with_anomalies` must be set to `True` (default is `False`).
