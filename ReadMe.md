# AWS VPC Infrastructure Template

## Overview
This CloudFormation template provisions a secure, highly available VPC infrastructure with public and private subnets across multiple Availability Zones, designed for containerized applications.

## Architecture Components
- **VPC** with 10.0.0.0/16 CIDR
- **Public Subnets** (2) with Internet Gateway access
- **Private Subnets** (2) with NAT Gateway access
- **Route Tables** for proper traffic routing
- **Security Groups** for ALB and ECS tasks
- **NAT Gateways** for outbound private subnet traffic

## Key Features
- Multi-AZ deployment for high availability
- Isolated networking layers (public/private)
- Secure default configurations
- Outputs all necessary references for dependent stacks

## Parameters
| Parameter | Description | Default |
|-----------|-------------|---------|
| `EnvironmentName` | Prefix for all resources | `ImageApp` |

## Outputs
Exports all resource IDs needed for ECS deployment:
- VPC ID
- Public/Private Subnet IDs
- ALB/ECS Security Group IDs

## Deployment
```bash
aws cloudformation create-stack \
  --stack-name ImageApp-VPC \
  --template-body file://vpc.yaml \
  --capabilities CAPABILITY_IAM