# Elastic Beanstalk App

## What is Elastic Beanstalk?
AWS Elastic Beanstalk is a managed service that makes it easy to deploy and run web applications. You upload your code, and it automatically handles the servers, load balancing, and scaling for you. It supports Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker.

## Key Concepts
- **Application** — your project as a whole
- **Environment** — the running infrastructure (servers, load balancer) that hosts your app
- **Version** — a specific deployment of your code; you can roll back anytime

## How It Works
1. Upload your code (zip or Docker image)
2. Elastic Beanstalk provisions EC2 instances, a load balancer, and auto-scaling
3. It deploys your app and monitors its health
4. Push updates anytime — EB handles the redeploy
