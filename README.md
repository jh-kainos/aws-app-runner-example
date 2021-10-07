[![Build, Tag and Push Docker image to ECR](https://github.com/jh-kainos/aws-app-runner-example/actions/workflows/DockerTagAndPush.yml/badge.svg)](https://github.com/jh-kainos/aws-app-runner-example/actions/workflows/DockerTagAndPush.yml)
# aws-app-runner-example

This is a basic example of how to deploy a container image to an AWS App Runner service. The API is located in the `express-ts-api` folder and was generated with `npx express-generator-typescript`.

The Express API is containerised and deployed using the included GitHub action.

## Prerequisities

1. node
2. npm
3. AWS API credentials and an IAM role to assume (there is an IAM policy included but it has not been extensively tested and assumes the use of default CF parameter values and requires you to replace `${AWSRegion}` and `${AWSAccountId}` with your desired deployment region and AWS account ID)

## Setup

1. Install node modules with `npm`

```
cd express-ts-api
npm install
```

2. Create an Elastic Container Repository in AWS (manually create or deploy included `ecr.yml`)
3. If using GitHub Actions to build the image and deploy the stack:
   1. Configure GitHub Secrets:
      1. `AWS_ACCESS_KEY`: AWS API Access Key
      2. `AWS_ECR_REPO`: URI of image repository created in step 2
      3. `AWS_REGION`: AWS Region to deploy AWS App Runner in
      4. `AWS_ROLE_TO_ASSUME`: An IAM Role to assume for stack deployment
      5. `AWS_SECRET_KEY`: AWS API Secret Key

## Run Express API locally

Run the following:

```
npm build
npm run start:dev
```