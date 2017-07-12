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

jupyter notebook accern_anomaly_detection.ipynb

### Explanation

In its current version, the notebook includes functions which can be used to find anomalies in a time series based on moving variance.  
The accern_sentiment values for each row from the provided dataset are used to show how these functions can be used to find anomalies by flagging values off by more than 3 standard deviations from the moving average/mean.
