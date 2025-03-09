# Mental Health AI Assistant - README

## Introduction

This project is a generative AI-powered Mental Health Assistant built using Amazon Bedrock, Amazon DynamoDB, Amazon Kendra, Amazon Lex, and LangChain. It is designed to provide intelligent, context-aware responses to users seeking mental health resources, general knowledge, and personalized assistance. The system utilizes Retrieval-Augmented Generation (RAG) to enhance its ability to provide accurate and relevant responses by leveraging Amazon Kendra's indexing capabilities and a LangChain Conversational Agent.

## Architecture Overview

The solution architecture consists of three primary components:

1. **Check-In System:**

   - Users can check in with a demo username and password (`123456`) for testing.
   - Future improvement: Integration with Amazon Cognito for secure user authentication before accessing Lex.

2. **Mental Health AI Assistant:**

   - Amazon Lex chatbot for natural language interaction with two main options:
     1. **Emergency Helpline Assistance**: Provides users with access to an emergency support chat offering general support and important helpline information.
     2. **General Mental Health Support**: Allows users to engage in conversations with "Alex" for personalized support.
   - AWS Lambda functions for business logic and API calls.
   - Amazon Bedrock-powered LLM (Claude 3 Sonnet) for generative AI responses.
   - Amazon Kendra for authoritative search and document retrieval.
   - Amazon DynamoDB for chat history storage and session persistence.

3. **Metrics and Monitoring:**

   - Future improvement: Integration with AWS CloudWatch to enhance observability and performance monitoring.

## Technologies Used
- **Version Control:** Git
- **Infrastructure as Code:** AWS CloudFormation
- **Cloud Services:** AWS Lambda, Amazon Lex, Amazon Bedrock, Amazon Kendra, Amazon DynamoDB
- **Security:** HTTPS, IAM Roles, Amazon Cognito (future improvement)

## Deployment Guide

### Prerequisites

- Install AWS CLI
- Set up an AWS account with necessary IAM permissions
- Fork and clone the repository

### Steps

1. **Clone the Repository**
   ```sh
   git clone <YOUR-FORKED-REPOSITORY-URL>
   cd generative-ai-mental-health-assistant
   ```
2. **Set Up AWS CLI**
   ```sh
   aws configure
   ```
3. **Navigate to the Deployment Directory**
   ```sh
   cd shell
   ```
4. **Set Up Environment Variables**
   ```sh
   export AMPLIFY_REPOSITORY=<YOUR-FORKED-REPOSITORY-URL> # Forked repository URL from Pre-Deployment (Exclude '.git' from repository URL)
   export GITHUB_PAT=<YOUR-GITHUB-PAT> # GitHub PAT copied from Pre-Deployment
   export STACK_NAME=<YOUR-STACK-NAME> # Stack name must be lower case for S3 bucket naming convention
   export KENDRA_WEBCRAWLER_URL=<YOUR-WEBSITE-ROOT-DOMAIN> # Public or internal HTTPS website for Kendra to index via Web Crawler (e.g., https://www.investopedia.com/) - Please see https://docs.aws.amazon.com/kendra/latest/dg/data-source-web-crawler.html
   export AWS_REGION=<YOUR-STACK-REGION> # Stack deployment region
   ```
5. **Run Deployment Script**
   ```sh
   ./create-stack.sh
   ```

## Testing and Validation

- Access the deployed Lex chatbot via the Amplify-hosted website.
- Verify that the chatbot can respond to mental health queries using Amazon Bedrock and Kendra.
- Confirm conversation history is stored in DynamoDB.
- Run logs and monitoring checks via CloudWatch (future improvement).

## Cleanup

To avoid incurring unnecessary AWS costs, execute the following command:

```sh
aws cloudformation delete-stack --stack-name <YOUR-STACK-NAME>
```

## Future Improvements

1. **Authentication Security**:
   - Replace the demo login system with Amazon Cognito for secure user authentication before accessing Lex.
2. **Observability Enhancements**:
   - Implement AWS CloudWatch to track chatbot interactions, latency, and error rates.
3. **Performance Optimization**:
   - Improve caching strategies to reduce API calls and enhance response speed.
4. **Expanded Data Sources**:
   - Integrate additional mental health data sources for a richer knowledge base.

## Conclusion

This project serves as a foundation for creating AI-powered mental health assistants using AWS services and LangChain. With the recommended improvements, this system can be further enhanced for security, scalability, and performance. If you have any questions or need support, please reach out through GitHub Issues or AWS Developer Forums.

