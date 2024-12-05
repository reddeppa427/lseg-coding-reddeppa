## Project Overview

This repository contains Java code for a simple "Hello World" program. The project includes a CI/CD pipeline with the following stages:

1. **Build and Test**
2. **Snyk Security Scan**
3. **Deployment Stages**
   - Development (Dev)
   - Quality Assurance (QA)
   - Production (Prod)

## Pipeline Details

### Build and Test
- The build and test processes are executed in a single stage.

### Snyk Security Scan
- After the build is completed, the code undergoes a Snyk security scan.
- The scan has a threshold of medium or higher severity.
- Scan details are published to GitHub Security.
- We can verify third-party vulnerabilities detected by Snyk in GitHub Security.

### Deployment
- The pipeline is triggered when a Pull Request (PR) is merged into the `development`, `release`, or `main` branches.
- **Development Branch**: Deploys changes to the development environment.
- **Release Branch**: Deploys changes to the QA environment.
- **Main Branch**: Deploys changes to the production environment.

## Secrets Management
- The Snyk token is added to GitHub Secrets to secure the value from unauthorized access.

## Branch Protection Rules
- Branch protection rules are enabled for the `development`, `release`, and `main` branches.
- It is mandatory to raise a PR with at least one reviewer.
- Pipeline level approvals are enabled, restricting deployments to the production environment without approvals from development leads.

