# Terraform AWS GOAT

[![Follow on Twitter](https://img.shields.io/twitter/follow/opendevsecops.svg?logo=twitter)](https://twitter.com/opendevsecops)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/c19ccb0ca68a4b5dbc6a9cdd122339e3)](https://www.codacy.com/app/OpenDevSecOps/terraform-aws-goat)

A Terraform module that deliberately deploys vulnerable AWS resources for education, security testing, and understanding AWS security vulnerabilities.

## Warning

**DO NOT deploy this in production environments or connect it to sensitive AWS accounts!** 
This module intentionally creates insecure resources that violate security best practices.

## Overview

This module creates several intentionally vulnerable AWS resources:

- IAM roles that can be assumed by anyone
- S3 buckets with public read access
- S3 buckets with public read/write access
- SNS topics with public subscribe permissions
- SNS topics with public subscribe and publish permissions

## Usage

```terraform
module "goat" {
  source = "opendevsecops/goat/aws"
}

# Access the created resources
output "vulnerable_role_arn" {
  value = module.goat.iam_role_public_assumerole_arn
}

output "public_bucket_id" {
  value = module.goat.s3_bucket_public_read_id
}