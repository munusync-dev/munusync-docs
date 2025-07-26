# Login

**POST** `/api/auth/login` - `Public`

## Overview

User authentication for system access. Securely validates credentials and issues a JWT for session management.

## Behavior

Frontend collects user email and password, sends to backend via POST request. Backend validates credentials, issues JWT on success, or error on failure.

## Flow (Frontend to Backend)

1. User enters email and password in login form.
2. Backend receives request, validates against User table.
3. If valid, backend returns JWT and user info.
4. Frontend stores JWT (secure storage) and redirects user.
5. If invalid, frontend displays error message.

## Request

**POST**

```json
{
  "email": "user@example.com",
  "password": "userPassword"
}
```

## Response

**Success (200):**

```json
{
  "token": "<JWT>",
  "user": {
    "id": "<uuid>",
    "email": "user@example.com",
    "role": "user"
  }
}
```

**Failure (401/403/400):**

```json
{
  "error": "Invalid credentials"
}
```

## Table(s) Involved

- User

## Fields Used

- email
- password

## Security

- Passwords must be hashed and salted.
- JWT must be signed and have expiration.
- Rate limiting and brute-force protection required.

## Edge Cases

- Invalid credentials
- Inactive or locked account
- Expired password

## Errors

- 401 Unauthorized
- 403 Forbidden (locked/inactive)
- 400 Bad Request (missing fields)
