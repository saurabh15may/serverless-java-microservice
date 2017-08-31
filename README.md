# weather-app-microservice

##### Please find the steps to build and deploy the microservice using Serverless.
###### It is assumed that nodeJS is installed and npm commands can be executed via command-line

#### Install serverless
>npm install -g serverless

#### configure AWS profile (An IAM user linked to my personal AWS account)
>serverless config credentials --provider aws --key XXXXXXXX --secret XXXXXXXXXX

#### Build the project
>mvn package

#### Deploy to AWS Lambda (Will create an API link vi API Gateway)
>serverless deploy
```sh
Serverless: Packaging service...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
..............
Serverless: Stack update finished...
Service Information
service: weather-app-microservice
stage: dev
region: us-east-1
stack: weather-app-microservice-dev
api keys:
  None
endpoints:
  GET - https://4ce8rjr0je.execute-api.us-east-1.amazonaws.com/dev/weather/city
functions:
  currentWeather: weather-app-microservice-dev-currentWeather
```
#### Test by opening the below URL on any browser
>https://4ce8rjr0je.execute-api.us-east-1.amazonaws.com/dev/weather/city?id=7839805

#### Test the created lambda function on local
>serverless invoke --function currentWeather --log {"pathParameters":{"id":"7839805"}}