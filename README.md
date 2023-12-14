# Project README: PostgreSQL and Nextcloud Docker Stack

## Overview
This Docker Compose project sets up a Nextcloud application with a PostgreSQL database backend. It utilizes Docker secrets for secure handling of sensitive information like database credentials and Nextcloud admin details.

## Prerequisites
- Docker and Docker Compose installed
- Basic knowledge of Docker and containerization concepts

## Services

### PostgreSQL Database (db)
- **Image**: `postgres`
- **Restart Policy**: Always
- **Volumes**: Persistent storage for PostgreSQL data
- **Environment Variables**: Configurations are set via Docker secrets
- **Secrets**: `postgres_db`, `postgres_password`, `postgres_user`

### Nextcloud Application (app)
- **Image**: `nextcloud`
- **Restart Policy**: Always
- **Ports**: 8080 (mapped to internal port 80)
- **Volumes**: Persistent storage for Nextcloud data
- **Environment Variables**: Database and admin configurations set via Docker secrets
- **Dependencies**: Depends on `db` service
- **Secrets**: `nextcloud_admin_password`, `nextcloud_admin_user`, `postgres_db`, `postgres_password`, `postgres_user`

## Volumes
- `db`: Volume for PostgreSQL data
- `nextcloud`: Volume for Nextcloud data

## Secrets
- `nextcloud_admin_password`: File containing Nextcloud admin password
- `nextcloud_admin_user`: File containing Nextcloud admin username
- `postgres_db`: File containing PostgreSQL database name
- `postgres_password`: File containing PostgreSQL password
- `postgres_user`: File containing PostgreSQL username

## Setting Up Secrets
Create the following text files with the respective secret data:
- `nextcloud_admin_password.txt`
- `nextcloud_admin_user.txt`
- `postgres_db.txt`
- `postgres_password.txt`
- `postgres_user.txt`

## Deployment
1. Ensure all secret files are created as specified.
2. Run `docker-compose up -d` to start the services in detached mode.

## Accessing Nextcloud
- After deployment, access Nextcloud at `http://<your-ip>:8080`
- Log in with the Nextcloud admin credentials you set in the secrets.
