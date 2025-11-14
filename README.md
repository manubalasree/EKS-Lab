# EKS-Lab

## Overview
Simple VPC setup for running mini projects and lab exercises.

## CloudFormation Template (eks-vpc.yaml)

Creates a basic VPC infrastructure with:
- 1 VPC (10.0.0.0/16)
- 2 Availability Zones (us-east-1a, us-east-1b)
- 2 Public Subnets
- 2 Private Subnets
- Internet Gateway
- 2 NAT Gateways (one per AZ)
- Route Tables configured for public and private subnets

## Usage

Deploy the stack:
```bash
aws cloudformation create-stack \
  --stack-name my-vpc \
  --template-body file://eks-vpc.yaml \
  --parameters ParameterKey=ClusterName,ParameterValue=observability
```

## Parameters
- **ClusterName**: Name for resource tagging (default: observability)
- **VpcCIDR**: VPC CIDR block (default: 10.0.0.0/16)
- Subnet CIDRs are configurable via parameters
