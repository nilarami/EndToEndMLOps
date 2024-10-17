# EndToEndMLOps

from dagshub import get_repo_bucket_client
# Get a boto3.client object
s3 = get_repo_bucket_client("nilarami/EndToEndMLOps")

# Upload file
s3.upload_file(
    Bucket="EndToEndMLOps",  # name of the repo
    Filename="local.csv",  # local path of file to upload
    Key="remote.csv",  # remote path where to upload the file
)
# Download file
s3.download_file(
    Bucket="EndToEndMLOps",  # name of the repo
    Key="remote.csv",  #  remote path from where to download the file
    Filename="local.csv",  # local path where to download the file
)

Connection credentials
Bucket Name:
EndToEndMLOps 
Endpoint URL:
https://dagshub.com/api/v1/repo-buckets/s3/nilarami 
Public Key ID and Secret Access Key:
4a35381fc9b99cb46fae315644e62b787d885ad3
Region:
us-east-1 

https://dagshub.com/nilarami/EndToEndMLOps.mlflow


import dagshub
dagshub.init(repo_owner='nilarami', repo_name='EndToEndMLOps', mlflow=True)

import mlflow
with mlflow.start_run():
  mlflow.log_param('parameter name', 'value')
  mlflow.log_metric('metric name', 1)


### dagshub
[dagshub](https://dagshub.com/)

MLFLOW_TRACKING_URI=https://dagshub.com/nilarami/EndToEndMLOps.mlflow \
MLFLOW_TRACKING_USERNAME=nilarami \
MLFLOW_TRACKING_PASSWORD=4a35381fc9b99cb46fae315644e62b787d885ad3 \
python script.py

Run this to export as env variables:

```bash

export MLFLOW_TRACKING_URI=https://dagshub.com/nilarami/EndToEndMLOps.mlflow

export MLFLOW_TRACKING_USERNAME=nilarami 

export MLFLOW_TRACKING_PASSWORD=4a35381fc9b99cb46fae315644e62b787d885ad3

```
