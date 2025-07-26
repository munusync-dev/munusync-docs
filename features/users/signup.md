# Signup

**POST** `/api/auth/signup` - `Public`

## Overview

User registration for system access. Securely collects all required user and profile information, creates a new user and profile, and issues a JWT for session management.

## Behavior

Frontend collects user email, password, username, and profile details (first name, last name, profile picture), sends to backend via POST request. Backend validates input, checks for existing user, creates user and profile, issues JWT on success, or error on failure.

## Flow (Frontend to Backend)

1. User enters all required information in signup form:
   - email
   - password
   - username
   - first name
   - last name
   - profile picture (optional)
2. Backend receives request, validates input, checks for existing user/email/username.
3. If valid and user does not exist, backend creates user and profile, returns JWT and user info.
4. Frontend stores JWT (secure storage) and redirects user.
5. If invalid or user exists, frontend displays error message.

## Request

**POST**

```json
{
  "email": "user@example.com",
  "password": "userPassword",
  "username": "newuser",
  "firstName": "John",
  "lastName": "Doe",
  "role": "USER",
  "profilePicture": "https://example.com/profile.jpg"
}
```

## Response

**Success (201):**

```json
{
  "token": "<JWT>",
  "user": {
    "id": "<uuid>",
    "updatedAt": "2025-07-27T12:00:00Z"
    "firstName": "John",
    "lastName": "Doe",
    "profilePicture": "https://example.com/profile.jpg",
    "username": "newuser",
    "email": "user@example.com",
    "role": "user",
    "createdAt": "2025-07-27T12:00:00Z"
  }
}
```

**Failure (400/409):**

```json
{
  "error": "Email already exists or invalid input"
}
```

## Table(s) Involved

- User
- Profile

## Security

- Passwords must be hashed using bcrypt.
- JWT must be signed and have expiration.

## Edge Cases

- Email or username already exists
- Invalid email format
- Weak password
- Missing required fields

## Errors

- 400 Bad Request (missing/invalid fields)
- 409 Conflict (email or username exists)
