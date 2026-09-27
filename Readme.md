# Highly Available 3-Tier AWS Application

A web application deployed on AWS using a 3-tier architecture.
The project explores network isolation, load balancing, scaling,
and managed database deployment.

> Project status: In progress / Completed
> Update this status to match what you have actually built and tested.

## Architecture

![AWS Architecture](architecture/architecture-diagram.png)

### Architecture overview

1. **Web tier:** React frontend served by Nginx on EC2 instances.
2. **Application tier:** Node.js/Express API hosted on private EC2 instances.
3. **Database tier:** Amazon RDS MySQL in private database subnets.

Traffic flows through an internet-facing Application Load Balancer
to the web tier. The web tier forwards API requests to an internal
Application Load Balancer, which routes them to the application tier.

## AWS Services

- Amazon VPC
- Public and private subnets across Availability Zones
- Internet Gateway and NAT Gateway
- Application Load Balancer (public and internal)
- Amazon EC2
- EC2 Auto Scaling Groups
- Amazon RDS MySQL
- IAM roles and security groups
- Amazon CloudWatch
- Amazon S3 (if used by the application)

## Key features

Only list features that you have implemented and verified:

- [ ] Public and private subnet separation
- [ ] Public ALB distributes web traffic
- [ ] Internal ALB routes API requests
- [ ] App EC2 instances run in private subnets
- [ ] RDS is private and accessible only from the app tier
- [ ] Auto Scaling configured for web and app tiers
- [ ] Health checks configured for target groups
- [ ] CloudWatch monitoring and alarms
- [ ] HTTPS configured using ACM
- [ ] Infrastructure provisioned with Terraform

## Repository structure

- `app/` - application source code
- `architecture/` - architecture diagram and screenshots
- `docs/` - deployment and configuration notes
- `infrastructure/` - infrastructure-as-code files, if available

## Deployment and testing

Document the actual steps you used to deploy the application.
Include how you checked target group health, tested API endpoints,
and verified that the application works through the public ALB.

## Security considerations

- Database is not publicly accessible.
- Security groups allow only required tier-to-tier traffic.
- EC2 instances use IAM roles where needed.
- Do not commit passwords, access keys, `.env` files, or private keys.

## What I learned

- Designing VPC networking with public and private subnets
- Configuring public and internal load balancers
- Deploying application components across Availability Zones
- Connecting a private application tier to RDS
- Testing health checks and instance availability

## Future improvements

- Automate infrastructure with Terraform
- Add deployment automation
- Configure HTTPS and a custom domain
- Add monitoring dashboards and alarms
- Test recovery from instance and Availability Zone failures