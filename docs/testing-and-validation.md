# Testing and Validation

## 1. Overview

This document describes the checks required to validate the AWS Cloud Architecting Capstone Project.

## 2. Application Accessibility

- Obtain the DNS name of Oyama-ALB.
- Open the DNS name in a web browser.
- Confirm that the PHP application loads successfully.
- Check that the application displays the expected country statistics.

## 3. Load Balancer Health

- Open the EC2 Load Balancers console.
- Select Oyama-ALB.
- Inspect its associated target group.
- Confirm that application instances are registered.
- Check that registered targets become healthy.

## 4. Auto Scaling Validation

- Open the EC2 Auto Scaling console.
- Select Oyama-ASG.
- Confirm that the Auto Scaling group uses the intended launch template.
- Verify that EC2 instances are launched in the designated private subnets.
- Check the Auto Scaling activity history for launch errors.

## 5. Database Validation

- Open the Amazon RDS console.
- Confirm that Oyama-CapstoneDB is available.
- Verify that public accessibility is disabled.
- Confirm that the initial database name is countries.
- Verify that the supplied SQL data has been imported.
- Confirm that the application can retrieve the database records.

## 6. Secrets Manager Validation

- Open AWS Secrets Manager.
- Confirm that the database credentials are stored in a secret.
- Verify that the application has the required IAM permissions to retrieve the secret.

## 7. Validation Results

Record the actual results of each test below.

| Test | Result | Evidence |
|---|---|---|
| Application accessible through ALB | Pending verification | |
| Load balancer targets healthy | Pending verification | |
| EC2 instances launched in private subnets | Pending verification | |
| Auto Scaling group operational | Pending verification | |
| RDS database available | Pending verification | |
| Database not publicly accessible | Pending verification | |
| Database data imported successfully | Pending verification | |
| Credentials stored in Secrets Manager | Pending verification | |
| Application retrieves database records | Pending verification | |

Update each result only after performing the corresponding test.
