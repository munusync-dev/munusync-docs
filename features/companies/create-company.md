# Create Company

**POST** `/api/companies` - `Recruiter`

## Overview

Allows a recruiter to create a new company profile in the system. Collects all required company information and returns the created company data.

## Behavior

Frontend collects company details from the user, sends to backend via POST request. Backend validates input, creates company record, and returns company info on success or error on failure.

## Flow (Frontend to Backend)

1. User enters company details in the create company form.
2. Backend receives request, validates input, checks for existing company (by name or code).
3. If valid and company does not exist, backend creates company, returns company info.
4. Frontend redirects user or displays success message.
5. If invalid or company exists, frontend displays error message.

## Request

**POST**

```json
{
  "name": "Acme Corp",
  "industryId": "<industry-uuid>",
  "description": "Leading provider of widgets.",
  "profilePictureUrl": "https://example.com/profile.jpg",
  "bannerUrl": "https://example.com/banner.jpg",
  "foundedYear": 1999,
  "companySize": "100-500",
  "createdAt": "2025-07-27T12:00:00Z",
  "updatedAt": "2025-07-27T12:00:00Z"
}
```

## Response

**Success (201):**

```json
{
  "company": {
    "id": "<uuid>",
    "name": "Acme Corp",
    "industryId": "<industry-uuid>",
    "description": "Leading provider of widgets.",
    "profilePictureUrl": "https://example.com/profile.jpg",
    "bannerUrl": "https://example.com/banner.jpg",
    "foundedYear": 1999,
    "verified": false,
    "companySize": "100-500",
    "createdAt": "2025-07-27T12:00:00Z",
    "updatedAt": "2025-07-27T12:00:00Z"
  }
}
```

**Failure (400/409):**

```json
{
  "error": "Company name already exist"
}
```
