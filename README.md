# EndToEndMLOps
<img width="1247" alt="Screenshot 2024-10-17 at 10 11 32 PM" src="https://github.com/user-attachments/assets/d8565286-bd54-43b2-9785-7f795fe3edf4">
<img width="547" alt="Screenshot 2024-10-17 at 10 12 15 PM" src="https://github.com/user-attachments/assets/1aa7752c-9513-4d3e-bf6b-855158bb700e">



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

# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

	#with specific access

	1. EC2 access : It is virtual machine

	2. ECR: Elastic Container registry to save your docker image in aws


	#Description: About the deployment

	1. Build docker image of the source code

	2. Push your docker image to ECR

	3. Launch Your EC2 

	4. Pull Your image from ECR in EC2

	5. Lauch your docker image in EC2

	#Policy:

	1. AmazonEC2ContainerRegistryFullAccess

	2. AmazonEC2FullAccess

## 3. Create ECR repo to store/save docker image
    - Save the URI: 249189165717.dkr.ecr.us-east-1.amazonaws.com/mlproj

## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
Check if docker is working -> docker --version

# 6. Configure EC2 as self-hosted runner:
## this is connecting github runner with ec2 instance, CI/CD 
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

    AWS_ACCESS_KEY_ID=

    AWS_SECRET_ACCESS_KEY=

    AWS_REGION = us-east-1

    AWS_ECR_LOGIN_URI = demo>>  249189165717.dkr.ecr.us-east-1.amazonaws.com

    ECR_REPOSITORY_NAME = simple-app




## About MLflow 
MLflow

 - Its Production Grade
 - Trace all of your expriements
 - Logging & tagging your model


