# serverless-Web-API

Production style serverless REST API built with AWS CDK v2. This project introduces API Gateway in front of Lambda functions to provide a uniform REST interface backed by DynamoDB. Runtime validation is implemented using JSON Schema and AJV.

## Architecture Overview

This stack provisions:

- API Gateway REST API with a dev stage
- Lambda functions for REST endpoints
- DynamoDB movies table
- Optional DynamoDB movie cast table and index
- IAM permissions defined via CDK grants
- Optional seed data applied during stack creation

Request flow:

Client → API Gateway → Lambda → DynamoDB → JSON response

## API Endpoints

Movies:

- GET /movies  
  Returns all movies

- GET /movies/{movieId}  
  Returns a specific movie

- POST /movies  
  Creates a new movie, validated at runtime

Optional extensions:

- DELETE /movies/{movieId}  
  Deletes a movie

- GET /movies/cast with query parameters  
  Supports filtered cast queries using movieId and optional filters

## Technology Stack

- AWS CDK v2
- TypeScript
- AWS API Gateway
- AWS Lambda
- DynamoDB
- AWS SDK v3
- AJV for runtime validation
- typescript-json-schema for schema generation

## Repository Structure

- bin  
  CDK application entry point

- lib  
  Infrastructure definitions

- lambdas  
  API handlers

- shared  
  Type definitions and generated schemas

- seed  
  Initial dataset

## Installation

npm install

## Schema Generation

npm run schema

## Deployment

cdk deploy

The deployment output includes the API root URL.

## Infrastructure Teardown

cdk destroy

## Key Concepts Demonstrated

- REST resource modelling with API Gateway
- Lambda proxy integration
- Path parameters and query string handling
- Runtime payload validation
- Infrastructure as Code with AWS CDK
- Secure IAM configuration
- Clean infrastructure lifecycle management
