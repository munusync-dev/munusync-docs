# Authentication in Spring Boot

In this task, you will implement user authentication in Spring Boot. This means building the system that allows users to securely log in and access protected parts of the app.

---

## What You Need to Do

1. **Create a User table** in your database to store user information.  
   Typical fields:

   - `id` (unique identifier)
   - `username` (unique)
   - `email` (unique)
   - `password` (hashed)
   - `roles` or `authorities` (user permissions)

2. **Create APIs for authentication:**
   - **Register API** (`POST /auth/register`)  
     Accepts user details (username, email, password), validates and saves a new user with hashed password.
   - **Login API** (`POST /auth/login`)  
     Accepts username/email and password, verifies credentials, and returns a JWT token or session info on success.
   - **User Info API** (`GET /user/me`)  
     Returns current user details; protected and requires valid authentication token.

---

## What Data to Use

- Passwords **must be hashed** before saving to the database (e.g., using BCrypt).
- Use JWT (JSON Web Tokens) or sessions to manage user authentication state.
- Include roles or permissions to control access to different endpoints.

---

## Implementation Tips

- Use Spring Security for handling authentication and authorization.
- Configure password encoding with `BCryptPasswordEncoder`.
- Secure your APIs so only authenticated users can access protected endpoints.
- Validate user input to prevent duplicate usernames or weak passwords.

---

## Task Summary

- Design the `User` entity with proper fields.
- Implement the authentication REST APIs listed above.
- Use secure password hashing.
- Protect routes using Spring Security.
- Test your APIs to ensure authentication works correctly.

---

## Resources

- [Spring Security Guide](https://spring.io/guides/gs/securing-web/)
- [JWT Authentication with Spring Boot](https://www.baeldung.com/spring-security-oauth-jwt)
- [BCryptPasswordEncoder Usage](https://www.baeldung.com/spring-security-registration-password-encoding)

---

## Getting Started Guide

- [High Level Authentication](https://www.youtube.com/watch?v=sm-8qfMWEV8)
- [Building the Authentication](https://www.youtube.com/watch?v=dFzvVoS-sRE)
