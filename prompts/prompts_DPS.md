**1st iteration
You are an expert Devops. Your task is to create a deployment pipeline for EC2 usign Github actions
I need to create the deployment running:
1. Backend tests. If there are not test to run please ignore this step
2. Generate the execution build
3. Deployment in Ec2 Bucket.

Please when defining the secret consider the variables I have already setup in Github for EC2 Access.
AWS_ACCESS_KEY
AWS_REGION
EC2_ACCESS_ID
EC2_INSTANCE
EC2_SSH_PRIVATE_KEY
EC2_USER

Before creating the file please ask me any question you need to create it without errors

**Copilot answer
To create a deployment pipeline for EC2 using GitHub Actions, I need to clarify a few details:

Backend Tests:

What command should be used to run the backend tests?
What testing framework are you using (e.g., pytest, unittest)?
Generate the Execution Build:

What command should be used to generate the build?
Are there any specific build tools or frameworks involved (e.g., Maven, Gradle, npm)?
Deployment in EC2 Bucket:

Are you deploying a specific directory or the entire repository?
Do you have any specific deployment steps or commands that need to be executed on the EC2 instance?
Once I have this information, I can create the GitHub Actions workflow for you.

**new iteration
review the @codebase to decide and create them if necesary.
review the @codebase and decide
the entire repository
no, I need your support for it

**copilot answerThe workflow uses your existing secrets
Assumes Node.js project structure (modify build commands if different)
Uses PM2 for process management (install if not present)
Deployment directory is assumed to be /home/EC2_USER/app
Do you need to modify any of these assumptions or add specific build/deployment commands?

**new iteration:
I need to deploy when a Push to main is run

**copilot answer
EC2 Deployment Pipeline Plan
Pipeline Triggers

On push to main branch
Optional: On pull request to main (for testing)
Environment Setup

Ubuntu latest runner
Node.js setup (or your specific runtime)
Test Phase

Install dependencies
Run unit tests if present
Build Phase

Generate production build
Create artifacts
Deploy Phase

Connect to EC2 via SSH
Deploy code to target directory
Restart application services
Here's the implementation:

Key changes from your current file:

Updated trigger to main branch
Added test and build phases
Using appleboy/ssh-action for more reliable SSH deployment
Added proper Node.js setup and dependency caching
Added conditional deployment only on main branch
Included PM2 process management
Remember to:

Update branch protection rules for main
Ensure all secrets are properly configured
Install PM2 on your EC2 instance
Set up proper NODE_ENV variables