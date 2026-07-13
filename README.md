# Elastic Beanstalk App

## What is Elastic Beanstalk?
AWS Elastic Beanstalk is a fully managed Platform-as-a-Service (PaaS) that simplifies deploying, provisioning, scaling, and monitoring web applications. You upload your code, and Elastic Beanstalk automatically handles the servers, load balancing, and scaling — while still giving you access to the underlying resources if you need to customize them. It supports Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker.

## Key Concepts
- **Application** — your project as a whole; a container for environments and versions
- **Environment** — the running infrastructure (EC2 instances, load balancer, auto-scaling group) that hosts your app
- **Version** — a specific deployment of your code; you can roll back to a previous version anytime
- **Environment Tier** — Web Server tier (handles HTTP traffic) or Worker tier (background jobs via SQS)
- **Environment Configuration** — settings like instance type, scaling rules, and environment variables, defined via the console, CLI, or `.ebextensions` config files

## How It Works
1. Upload your code (zip file or Docker image)
2. Elastic Beanstalk provisions EC2 instances, a load balancer, an Auto Scaling group, and an S3 bucket for your app versions
3. It deploys your app and starts monitoring health, traffic, and performance
4. Push updates anytime — EB handles the redeploy automatically

## Core AWS Services It Uses
- **EC2** — runs your application
- **Elastic Load Balancing** — distributes incoming traffic across instances
- **Auto Scaling** — adds/removes instances based on load
- **S3** — stores app versions and logs
- **CloudWatch** — monitors health, metrics, and alarms
- **VPC** — the private network your environment's resources run inside (uses your default VPC unless you specify a custom one)
- **RDS** (optional) — a managed database can be attached to your environment

## Deployment Methods
- **AWS Console** — upload a zip file through the browser UI
- **EB CLI** — command-line tool (`eb init`, `eb create`, `eb deploy`, `eb status`, `eb logs`)
- **CI/CD pipelines** — automate deployments with CodePipeline, GitHub Actions, or Jenkins

## Monitoring & Health
Elastic Beanstalk continuously checks application health (via HTTP requests or a custom health check URL) and reports status as OK, Warning, Degraded, or Severe in the console. CloudWatch alarms can be configured to trigger notifications or auto-scaling actions based on CPU, latency, or request count.

## Use Cases
- Deploying web apps and APIs quickly without manually managing servers
- Running background job processors (worker tier + SQS)
- Apps that need to auto-scale with unpredictable traffic
- Teams that want managed infrastructure but occasional low-level access to EC2/config

## Benefits
- Fast to set up — running environment in minutes
- Full control over underlying resources when needed
- Built-in monitoring, health checks, and rollback support
- No extra charge for Elastic Beanstalk itself — you only pay for the AWS resources it creates

## Prerequisites (for this project)
- AWS CLI installed and configured (`aws configure`)
- EB CLI installed (`pip install awsebcli`)

## Common EB CLI Commands
- `eb init` — set up a new application in the current directory
- `eb create [env-name]` — create and deploy a new environment
- `eb deploy` — deploy the latest code to an existing environment
- `eb status` — check environment health and status
- `eb logs` — pull recent logs from the environment
- `eb terminate [env-name]` — tear down an environment