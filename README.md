# tomcat-sample-webapp
This is sample web app file which can be packaged into war file and deployed on tomcat.
Github Multi-Branching Pipelines assignment

Objective: Create a pipeline that deploys an application to staging and production
environments automatically based on GitHub branch activity.
Deliverables:
1. Create a Public GitHub repository containing a web application.
Use below Java webapp project
https://github.com/raghuck/tomcat-sample-webapp

2. A GitHub repository with the application code and separate branches for staging and
production.

3. A GitHub Actions pipeline with:

a. Deployment to a staging environment on a push to the staging branch.
b. Deployment to a production environment on a push to the production branch.

4. Documentation explaining environment-specific configurations.
Mention your Github repo link as well in which you have setup this pipeline.

5. Screenshots or logs showing successful deployments to both environments.

   WORKFLOW INLINE

   https://grok.com/chat/cd8ff4b3-6ab8-48f6-b5f9-a9ec662f7bfa?referrer=website
   
# Tomcat Sample Webapp Deployment Pipeline

This repository contains a Java web application deployed to staging and production environments using GitHub Actions.

## Repository Structure
- `main`: Development branch for new features.
- `staging`: Branch for staging environment deployment.
- `production`: Branch for production environment deployment.

## Environment-Specific Configurations
### Staging Environment
- **Tomcat Path**: `/opt/tomcat-staging/webapps`
- **URL**: `http://<server-ip>:8081/sample-webapp` (example)
- **Purpose**: Testing and validation before production.
- **Configuration**: Uses default settings from `src/main/webapp/WEB-INF/web.xml`.

### Production Environment
- **Tomcat Path**: `/opt/tomcat-production/webapps`
- **URL**: `http://<server-ip>:8080/sample-webapp` (example)
- **Purpose**: Live application for end users.
- **Configuration**: Same as staging, but can be modified (e.g., database connection) in a real-world scenario.

## GitHub Actions Pipeline
- **File**: `.github/workflows/deploy.yml`
- **Trigger**: Push to `staging` or `production` branches.
- **Steps**:
  1. Checkout code.
  2. Set up JDK 17.
  3. Build WAR file with Maven.
  4. Deploy to the respective environment using SCP.

## Setup Instructions
1. Fork this repository: `https://github.com/<your-username>/tomcat-sample-webapp`.
2. Configure secrets in GitHub Settings > Secrets and Variables > Actions:
   - `SERVER_IP`: Your server's IP address.
   - `SERVER_USER`: SSH username.
   - `SERVER_PASSWORD`: SSH password.
3. Set up two Tomcat instances on your server:
   - Staging: `/opt/tomcat-staging` (e.g., port 8081).
   - Production: `/opt/tomcat-production` (e.g., port 8080).
4. Push changes to `staging` or `production` to trigger deployment.

## GitHub Repository Link
- `https://github.com/<your-username>/tomcat-sample-webapp`
