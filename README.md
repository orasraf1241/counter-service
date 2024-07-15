# CI/CD Pipeline for Building and Pushing Python Image to AWS ECR

This repository contains the CI/CD pipeline configuration for building a Docker image of the counter-service application, pushing it to Amazon Elastic Container Registry (ECR), and triggering a Continuous Deployment (CD) pipeline.

## Prerequisites

Before setting up the pipeline, ensure you have the following:

- AWS CLI installed and configured.
- GitHub repository set up with required secrets and variables.

## Create ECR Repository

First, create an ECR repository using the following command:

```
aws ecr create-repository  \
    --repository-name orasraf/devops-exam-repo \
    --region eu-east-1 \
    --tags '[{"Key":"Environment","Value":"Test"},{"Key":"Project","Value":"CheckPoint"},{"Key":"Team","Value":"DevOps"}]'
```
## Pipeline Overview

The pipeline performs the following steps:
1. **Checkout**: Fetches the code from the repository.
2. **Configure AWS Credentials**: Sets up AWS credentials for accessing ECR.
3. **Login to Amazon ECR**: Authenticates Docker with ECR.
4. **Automatic Tagging of Releases**: Increments the Git tag for the release.
5. **Build, Tag, and Push Docker Image**: Builds the Docker image, tags it, and pushes it to ECR.
6. **Print Docker Image URL**: Outputs the URL of the pushed Docker image.
7. **Trigger CD Pipeline**: Initiates the deployment pipeline using a repository dispatch event.



# Environment Variables and Secrets
* Secrets:

* * AWS_ACCESS_KEY_ID:      Your AWS access key ID.
* * AWS_SECRET_ACCESS_KEY:  Your AWS secret access key.
* * PAT_GITHUB_TOKEN:       Your GitHub personal access token.

* Variables:

* * AWS_REGION: The AWS region where your ECR repository is located.
* * ECR_REPOSITORY: The name of your ECR repository.
* * VERSION_INCREMENT: The version increment type (major, minor, or patch).
* * CD_GIT_REPO: The name of your CD repo that will be triggered from this pipeline.

To configure the workflow, you'll need to set the above secrets and variables in your GitHub repository.