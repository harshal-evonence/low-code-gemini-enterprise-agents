# Customer Support Platform - Architecture Document

## System Overview

The Customer Support Platform enables customers to create and manage support tickets while allowing support teams to track, assign, and resolve issues efficiently.

The platform follows a microservices architecture hosted on Google Cloud Platform (GCP).

---

## Technology Stack

| Component | Technology |
|----------|------------|
| Frontend | React.js |
| Backend | Python FastAPI |
| Database | PostgreSQL (Google Cloud SQL) |
| Messaging | Google Pub/Sub |
| Authentication | OAuth 2.0 |
| Cloud Platform | Google Cloud Platform |

---

## Core Services

### User Service

Responsibilities

- User Authentication
- User Profile Management
- Password Management
- Role Management

---

### Ticket Service

Responsibilities

- Ticket Creation
- Ticket Assignment
- Ticket Status Updates
- Ticket History

---

### Notification Service

Responsibilities

- Email Notifications
- Chat Notifications
- Event Processing

---

## System Communication

- REST APIs are used for communication between frontend and backend.
- Services communicate asynchronously using Google Pub/Sub where required.

---

## Security

- OAuth 2.0 Authentication
- Role Based Access Control (RBAC)
- TLS Encryption
- Audit Logging

---

## Database

Primary Database

Google Cloud SQL (PostgreSQL)

Major Tables

- Users
- Tickets
- Roles
- Audit_Logs

---

## Engineering Constraints

- All APIs must be RESTful.
- All new APIs must support versioning.
- All services must maintain backward compatibility.
- Sensitive data must be encrypted.
- All critical operations must generate audit logs.