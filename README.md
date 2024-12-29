## MLFLOW on AWS

### MLFLOW on AWS Setup

1. Login to AWS console
2. Create IAM with AdministratorAccess\*
3. Export the credentials in your AWS CLI by runing "aws configure"
4. Create S3 bucket
5. Create an EC2 Instance (Ubuntu) and add security groups Port 5000

Run the command on EC2 Instance created

```bash
sudo apt update
sudo apt install python3-pip
sudo apt install pipenv
sudo apt install virtualenv
mkdir mlflow
cd mlflow
pipenv install mlflow
pipenv install awscli
pipenv install boto3

pipenv shell

## Then set aws credentials
aws configure


## Finally
mlflow server -h 0.0.0.0 --default-artifact-root s3://trackingmlflow

## Open Public IPV4 DNS to the port 5000

## Set uri in your local terminal and in your code
export MLFLOW_TRACKING_URI=http://ec2-3-86-106-120.compute-1.amazonaws.com:5000/
or
os.environ["MLFLOW_TRACKING_URI"]="http://ec2-3-86-106-120.compute-1.amazonaws.com:5000/"
```
