# Create Office

**POST** `/recruiter/offices` - `Recruiter`

## Overview

Allows a recruiter to create a new office for their company. The recruiter provides office details, including address, and the backend creates the office record.

## Behavior

- Backend authenticates recruiter via JWT.
- Validates input and associates the new office with the recruiter's company.
- Creates address and office records.
- Returns the created office data.

## Flow (Frontend to Backend)

1. Frontend sends office creation request.
2. Backend authenticates recruiter via JWT.
3. Backend validates and creates office and address records.
4. Backend returns created office data or error.

## Request

`POST /recruiter/offices`

```json
{
  "companyId": "<company-uuid>",
  "name": "Main Office",
  "phone": "123-456-7890",
  "email": "office@company.com",
  "timezone": "UTC",
  "address": {
    "addressLine1": "123 Main St",
    "addressLine2": "Suite 100",
    "city": "San Francisco",
    "state": "CA",
    "postalCode": "94105",
    "countryId": "<country-uuid>",
    "latitude": "37.7749",
    "longitude": "-122.4194"
  }
}
```

## Response

**Success (201):**

```json
{
  "office": {
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
    "updatedAt": "2025-07-27T12:00:00Z"

```

**Errors**

- **400 Invalid input**
- **401 Unauthorized**
