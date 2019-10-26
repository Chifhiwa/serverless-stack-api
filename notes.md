# AWS Serverless Framework - Notes-app

## CONFIGURING AWS ENVIRONMENT

1. Configure an S3 Bucket
   1. Create a new S# Bucket
   2. Edit CORS Configuration

2. Create a User Pool
   1. Create a new user pool
   2. Enable users to register using their email address
   3. User Pool Details:
      1. Pool ID:  **us-east-1_BNnJkY7h3**
      2. Pool ARN:  **arn:aws:cognito-idp:us-east-1:770328975346:userpool/us-east-1_BNnJkY7h3**

3. Create an App Clients
   1. Disable Generate client secret: Does not woerk with Javascript SDK
   2. Enable sign-in API for server-based authentication: Required for managing users through the AWS CLI
   3. App Client Details:
      1. App Client ID: **7ctfk7dqhpu0rm6lm95he6854e**

4. Create Cognito Test user through the AWS CLI
   1. User Details:
    aws cognito-idp sign-up \
    --region us-east-1 \
    --client-id 7ctfk7dqhpu0rm6lm95he6854e \
    --username tshifhiwa47@gmail.com \
    --password Passw0rd!

   2. User ID: a6f95620-33e0-491e-bc9c-756dee9dc585
   3. Account verification details:
   aws cognito-idp admin-confirm-sign-up \
    --region us-east-1 \
    --user-pool-id us-east-1_BNnJkY7h3\
    --username tshifhiwa47@gmail.com

5. Install Serverless Framework: npm install serverless -g
6. Instal Nodejs Serverless Starter: serverless install --url https://github.com/AnomalyInnovations/serverless-nodejs-starter --name notes-app-api
7. Install node packages:
   1. npm install
   2. npm install aws-sdk --save-dev
   3. npm install uuid --save
8. Webpack allows us to generate optimised packages for our Lambda Functions by only including the code that is used in out functions.
9. Customise serverless.yml file
10. Create a githum repository: https://github.com/Chifhiwa/serverless-stack-api.git
11. 