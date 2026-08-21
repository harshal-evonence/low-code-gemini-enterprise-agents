# API Specification

## API Standards

- REST API Design
- JSON Request/Response
- Versioned Endpoints
- Stateless Communication

---

## Authentication

OAuth 2.0 Bearer Token

Authorization Header

Authorization: Bearer <Access_Token>

---

## Existing APIs

### User Service

GET /users/me

Description

Returns authenticated user profile.

---

PATCH /users/me

Description

Updates authenticated user's profile information.

---

POST /users/change-password

Description

Updates user password.

---

### Ticket Service

POST /tickets

Creates a new support ticket.

---

GET /tickets/{ticketId}

Returns ticket details.

---

PATCH /tickets/{ticketId}

Updates ticket information.

---

## Standard Response

Success

{
  "status":"success",
  "message":"Operation completed successfully"
}

Failure

{
  "status":"error",
  "message":"Validation failed"
}

---

## API Guidelines

- Use HTTP Status Codes.
- Validate all input.
- Never expose sensitive information.
- Log all errors.