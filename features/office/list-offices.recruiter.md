# List Offices

**GET** `/recruiter/offices` - `Recruiter`

## Overview

Returns all offices for the recruiter's company. The recruiter is identified via JWT.

## Behavior

- Backend authenticates recruiter via JWT.
- Finds the company associated with the recruiter.
- Returns all offices for that company.

## Request

`GET /recruiter/offices`

No body required. JWT must be sent in Authorization header.

## Response

**Success (200):**

```json
{
  "content": [
    {
      "id": "<office-uuid>",
      "companyId": "<company-uuid>",
      "name": "Main Office",
      "phone": "123-456-7890",
      "email": "office@company.com",
      "timezone": "UTC",
      "address": {
        "id": "<address-uuid>",
        "addressLine1": "123 Main St",
        "addressLine2": "Suite 100",
        "city": "San Francisco",
        "state": "CA",
        "postalCode": "94105",
        "country": {
          "id": "<country-uuid>",
          "name": "United States",
          "code": "US"
        },
        "latitude": "37.7749",
        "longitude": "-122.4194"
      },
      "createdAt": "2025-07-27T12:00:00Z",
      "updatedAt": "2025-07-27T12:00:00Z"
    }
  ]
}
```

**Errors**

- **401 Unauthorized**
- **404 Not Found**
