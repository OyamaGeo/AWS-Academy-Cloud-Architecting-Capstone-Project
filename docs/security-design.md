# Security Design

## 1. Overview

Security is an important part of the AWS Academy Cloud Architecting Capstone Project.

The architecture separates the public entry point, application servers and database into different network layers.

## 2. Network Security

### Public Subnets
- Host the Application Load Balancer.
- Receive incoming application traffic from internet users.

### Private Subnets
- Host the EC2 application servers.
- Prevent direct public access to the application servers.
- Allow application traffic through the load balancer.

### Database Subnets
- Host the Amazon RDS MySQL database using the provisioned DB subnet group.
- Keep the database inaccessible directly from the public internet.

## 3. Security Groups

Security groups control communication between the architecture components.

The intended access rules are:

- Load Balancer: Allow public web traffic.
- Application Servers: Allow application traffic from the load balancer.
- Database: Allow MySQL traffic from the application servers only.
- Administrative Access: Restrict SSH access to authorised administrators.

## 4. AWS Secrets Manager

AWS Secrets Manager is used to store the database username and password.

This avoids placing database credentials directly in application documentation or exposing them unnecessarily.

The application requires appropriate permissions to retrieve the secret.

## 5. IAM Permissions

IAM roles and policies should grant AWS resources only the permissions required to perform their tasks.

The application servers must have appropriate permissions if they need to retrieve database credentials from Secrets Manager.

## 6. Security Objectives

The security design aims to:
- Prevent direct public access to application servers.
- Prevent public access to the database.
- Restrict database connections to the application servers.
- Protect database credentials using Secrets Manager.
- Limit administrative access.
- Apply least-privilege IAM permissions.
