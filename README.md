# AWS-Academy-Cloud-Architecting-Capstone-Project
# AWS Cloud Architecting Capstone Project

## Building a Secure, Scalable, and Highly Available Web Application on AWS

## 1. Project Overview

This project demonstrates the design and deployment of a secure, scalable, and highly available three-tier web application infrastructure using Amazon Web Services (AWS).

The project was completed as part of the AWS Academy Cloud Architecting course. The objective was to improve an existing PHP-based web application that initially operated on a single EC2 instance with a locally hosted MySQL database.

The redesigned architecture separates the application and database layers, introduces load balancing and automatic scaling, and implements secure database credential management.

## 2. Project Objectives

The major objectives were to:

- Deploy a MySQL database using Amazon RDS.
- Host the PHP application on EC2 instances in private subnets.
- Implement an Application Load Balancer for traffic distribution.
- Configure an Auto Scaling Group for automatic instance management.
- Securely store database credentials using AWS Secrets Manager.
- Import existing country statistics into the RDS MySQL database.
- Implement network security to prevent direct public access to backend resources.

## 3. AWS Services Used

| AWS Service | Purpose |
|---|---|
| Amazon VPC | Provides network isolation and infrastructure connectivity. |
| Public and Private Subnets | Separates public-facing and backend resources. |
| Internet Gateway | Provides internet connectivity to public-facing resources. |
| Application Load Balancer | Distributes incoming application traffic across EC2 instances. |
| Amazon EC2 | Hosts the PHP web application. |
| EC2 Auto Scaling | Automatically manages application server capacity. |
| Launch Template | Defines the configuration for EC2 instances. |
| Amazon RDS MySQL | Provides managed relational database hosting. |
| AWS Secrets Manager | Securely stores database credentials. |
| Security Groups | Controls communication between infrastructure components. |

## 4. Infrastructure Architecture

The solution follows a three-tier architecture:

### Presentation Layer
- Application Load Balancer (Oyama-ALB).
- Deployed across two public subnets in separate Availability Zones.
- Receives HTTP traffic from public users.

### Application Layer
- Auto Scaling Group (Oyama-ASG).
- EC2 application servers running the PHP application.
- Instances deployed across two private subnets.
- Application traffic received through the Application Load Balancer.

### Database Layer
- Amazon RDS MySQL (Oyama-DB).
- Hosts the `countries` database.
- Not publicly accessible.
- Database access restricted to the application servers.

### Credential Management
- AWS Secrets Manager stores the database username and password.
- Application configuration uses the stored credentials rather than hardcoding them.

## 5. Network Design

The project uses the preconfigured Capstone VPC in the AWS Academy environment.

The application infrastructure is distributed across two Availability Zones:

**Availability Zone A – us-east-1a**
- Public subnet 1: Application Load Balancer.
- Private subnet 1: EC2 application server.
- Database subnet: RDS, according to the provisioned DB subnet group.

**Availability Zone B – us-east-1b**
- Public subnet 2: Application Load Balancer.
- Private subnet 2: EC2 application server.
- Database subnet: Available through the provisioned DB subnet group.

## 6. Application Traffic Flow

The application follows this communication flow:

1. A user accesses the application through the Application Load Balancer DNS endpoint.
2. The Application Load Balancer distributes incoming requests to registered EC2 instances.
3. The PHP application processes user requests.
4. The application connects to Amazon RDS MySQL to retrieve country statistics.
5. RDS returns the requested information to the application.
6. The response is returned to the user through the load balancer.

## 7. Security Implementation

Security was incorporated into the architecture through:

- Private subnet placement for application servers.
- Private database deployment with public accessibility disabled.
- Security group rules restricting database access to the application tier.
- AWS Secrets Manager for database credential storage.
- Controlled communication between the load balancer, application servers, and database.

## 8. High Availability and Scalability

The architecture incorporates:

- An Application Load Balancer distributed across two Availability Zones.
- An Auto Scaling Group to manage EC2 application server capacity.
- A launch template to maintain consistent EC2 configurations.
- A target tracking scaling policy to adjust capacity based on application demand.

These components help improve application availability and accommodate changing traffic levels.

## 9. Testing and Validation

The following areas are included in the project validation:

- RDS MySQL database creation.
- Database private accessibility.
- Secrets Manager credential configuration.
- Application Load Balancer creation.
- EC2 deployment in private subnets.
- Auto Scaling Group configuration.
- Application accessibility through the load balancer DNS endpoint.
- Successful retrieval of country statistics through the application query functionality.

Actual validation results and screenshots will be documented in the `screenshots/` directory and `docs/testing-and-validation.md`.

## 10. Key Learning Outcomes

This project strengthened my practical understanding of:

- AWS network architecture and VPC configuration.
- Public and private subnet design.
- Application Load Balancing.
- EC2 Auto Scaling and launch templates.
- Amazon RDS database administration.
- AWS Secrets Manager.
- Security groups and network access control.
- High availability and fault-tolerant architecture.

## 11. Project Architecture Diagram

See [`architecture/capstone-architecture.png`](architecture/capstone-architecture.png).

## 12. Conclusion

This Capstone Project provided practical experience in designing and implementing AWS infrastructure using architectural principles focused on security, scalability, reliability, and operational efficiency.

It demonstrates how a traditional single-server application can be redesigned into a more resilient cloud-based architecture using managed AWS services.

**Project:** AWS Academy Cloud Architecting Capstone Project  
**AWS Region:** us-east-1 (Northern Virginia)  
**Application:** PHP  
**Database:** MySQL  
**Infrastructure:** Amazon Web Services
