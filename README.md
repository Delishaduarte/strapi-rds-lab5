# Strapi Application with AWS RDS PostgreSQL

## 1. Project Overview

This project demonstrates the deployment of a Strapi application on an Amazon EC2 instance and its connection to an Amazon RDS PostgreSQL database.

The application provides content management functionality through Strapi and stores its data in PostgreSQL hosted on Amazon RDS.

## 2. AWS Architecture

The application uses the following architecture:

EC2 Instance
    |
    | Strapi Application
    |
    v
Amazon RDS PostgreSQL
    |
    +-- articles
    +-- authors

The EC2 instance hosts the Strapi application, while Amazon RDS provides the managed PostgreSQL database.

## 3. Technologies Used

- Amazon EC2
- Amazon RDS PostgreSQL
- Strapi
- Node.js
- PostgreSQL
- Git and GitHub

## 4. RDS Database Configuration

Database engine: PostgreSQL

Database name: strapi_db

Database port: 5432

RDS endpoint:

strapi-rds-lab5.cxum6uisg7jh.ap-south-1.rds.amazonaws.com

The database credentials are stored securely in the EC2 environment configuration and are not included in this repository.

## 5. Strapi Database Connection

The Strapi application is configured using environment variables:

DATABASE_CLIENT=postgres

DATABASE_HOST=<RDS_ENDPOINT>

DATABASE_PORT=5432

DATABASE_NAME=strapi_db

DATABASE_USERNAME=postgres

DATABASE_PASSWORD=<RDS_PASSWORD>

DATABASE_SSL=true

Sensitive values such as the database password are stored in the `.env` file and are excluded from GitHub using `.gitignore`.

## 6. Security Configuration

The RDS PostgreSQL security group allows inbound traffic on port 5432 only from the EC2 security group.

No public database access using 0.0.0.0/0 is configured.

This prevents direct public access to the PostgreSQL database.

## 7. Running the Application

Navigate to the Strapi project:

cd /var/www/strapi-app

Start Strapi:

npm run start

The Strapi administration panel is available at:

http://<EC2_PUBLIC_IP>:1337/admin

## 8. CRUD Operations

The application demonstrates all required CRUD operations.

### Create

A new Article can be created through the Strapi Content Manager.

### Read

Existing Articles can be viewed through the Strapi Content Manager.

### Update

An Article can be edited and the updated data is stored in the RDS PostgreSQL database.

### Delete

An Article can be deleted from Strapi and the corresponding database record is removed.

## 9. Database Tables

The Strapi PostgreSQL database contains multiple tables including:

- articles
- authors
- categories
- admin_users

The Articles and Authors content types demonstrate relationships between application entities.

## 10. Database Verification

Database records can be verified using PostgreSQL from the EC2 instance.

Example:

SELECT id, title, description, published_at FROM articles;

## 11. Security of Credentials

Passwords, database credentials, API tokens and other secrets are not committed to GitHub.

The `.env` file is excluded through `.gitignore`.

## 12. Repository

GitHub Repository:

https://github.com/Delishaduarte/strapi-rds-lab5
