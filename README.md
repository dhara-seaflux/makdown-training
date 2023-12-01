# Lambda Stream Response

![Demo of Verba](https://github.com/weaviate/Verba/blob/dev/img/verba.gif)

- [Lambda Stream Response](#lambda-stream-response)
  - [About](#about)
  - [Deployment](#deployment)
    - [Prerequisites](#prerequisites)
    - [Setup](#setup)

## About
__Lambda-OpenAI-Stream__ lets you stream OpenAI responses via an AWS Lambda Function URL. It is a simple implementation in vanilla JS. The only (optional) dependency is dotenv.

## Deployment

### Prerequisites
* General AWS knowledge needed.
* You need to have [Docker](https://docs.docker.com/engine/install/) installed locally.
* You need to have [aws-sam](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html) installed locally and configured with your AWS account.

### Setup
1. Clone the repository
   ```sh
   git clone https://github.com/maxsagt/lambda-openai-stream.git
   ```
2. Create the .env in ./src with your OpenAI API key:
    ```
    OPENAI_API_KEY=abc123
    ```
3. Install dotenv
    ```sh
    npm init
    npm install dotenv
    ```   
4. Build and test the Lambda function locally
    ```sh
    sam build
    sam local invoke -e event.json
    ```
5. Deploy to AWS. Note that your AWS user or role needs (temporary) IAM permissions for AWS CloudFormation, S3, Lambda and IAM.
    ```sh
    sam build --cached --parallel

