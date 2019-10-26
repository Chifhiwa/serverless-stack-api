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
9. Confgure the backend create function
   1.  Lamnbda Function: Create a create.js function
   2.  Configure Endpoint:
       1.  Create environment variable for DynamoDB table
       2.  Create IAM roles for Lambda Function
       3.  Create a function
           1.  name of the function
           2.  the configuration of the event to trigget the function (http for API gateway - post, path, etc. )

      4. Test the Function:
         1. create folder called mocks
         2. create a json document with the expected input for the API
         3. execute serverless invoke local --function create --path mocks/create-event.json

10. Create a Stripe Account:
    1.  Stripe details:
        1.  Publishable Key: **pk_test_xtxVANpylkOsDOzH7xFVoiJO00P9l6JEQG**
        2.  Secret key: **sk_test_Lxk6kqZjwYHwqngWFlZKelD900KyCEkPaY**

11. Billing API is created and added. Business Logic code is contained in a library file, and is not necesarily embaded into the code and is not a seperate lambda function. It is a library