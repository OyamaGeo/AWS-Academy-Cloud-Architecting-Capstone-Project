# Implementation Guide

## 1. Project Overview

This project is designed to implement a highly available PHP web application backed by an Amazon RDS MySQL database.

The architecture uses an Application Load Balancer to distribute incoming requests across EC2 application servers in private subnets. An Auto Scaling group manages the application servers.

## 2. Database Setup

The project requires an Amazon RDS for MySQL database.

Key requirements:
- Database identifier: Oyama-CapstoneDB
- Initial database name: countries
- Database credentials stored in AWS Secrets Manager
- Database hosted in the provisioned DB subnet group
- Database not publicly accessible
- Database security group permits access from the application servers only

## 3. Application Load Balancer

The Application Load Balancer is named Oyama-ALB.

It receives incoming web traffic and distributes requests to registered application instances through a target group.

The load balancer is deployed in public subnets across multiple Availability Zones.

## 4. Application Servers

The application servers are managed by an Auto Scaling group named Oyama-ASG.

The servers:
- Use the provided Example-LT launch template.
- Run the supplied PHP application.
- Are deployed in private subnets.
- Receive application traffic through the load balancer.
- Connect to the RDS MySQL database.

## 5. Database Migration

The supplied SQL dump is used to import the country statistics data into the RDS MySQL database.

Database credentials are retrieved from AWS Secrets Manager.

## 6. Application Access

Users access the application through the DNS name assigned to Oyama-ALB.

The application servers and database are not intended to be directly accessible from the public internet.

## 7. Validation

The deployment should be validated by checking:
- Application access through the load balancer DNS name.
- Target group health.
- Application server placement in private subnets.
- Auto Scaling group configuration.
- Database connectivity and application data retrieval.
- Database credential storage in Secrets Manager.
