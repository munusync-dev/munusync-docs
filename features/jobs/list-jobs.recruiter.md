# List Jobs

**GET** `/recruiter/jobs` - `Recruiter`

## Overview

Returns all job posts created by the recruiter for their company. The recruiter is identified via the JWT user ID.

## Behavior

- Backend extracts recruiter user ID from JWT.
- Finds the company associated with the recruiter.
- Returns all jobs posted by the recruiter/company.

## Flow (Frontend to Backend)

1. Frontend requests job list for recruiter.
2. Backend authenticates recruiter via JWT, fetches jobs for their company.
3. Backend returns job list.
4. Frontend displays jobs or error message.

## Request

`GET /recruiter/jobs?title=Engineer&employmentType=Full-time&salaryMin=50000&skillId=<uuid>&page=0&size=20&sort=postedAt,desc`

### Filters

You can filter jobs using the following query parameters:

- `title` (string): Filter by job title (exact or partial match)
- `officeId` (uuid): Filter by office
- `employmentType` (string): Filter by employment type (e.g., Full-time, Part-time)
- `workType` (string): Filter by work type (e.g., Remote, Onsite)
- `salaryMin` (int): Minimum salary
- `salaryMax` (int): Maximum salary
- `postedAfter` (datetime): Jobs posted after this date
- `postedBefore` (datetime): Jobs posted before this date
- `skillId` (uuid, multi): Filter jobs requiring one or more specific skills. Pass multiple skill IDs as a comma-separated list (e.g., `skillId=uuid1,uuid2,uuid3`)
- `matchRateMin` (float): Minimum match rate

### Sorting

You can sort jobs by any field in the Job table using the following query parameters:

- `sortBy` (string): The field to sort by (e.g., title, postedAt, salaryMin, matchRate, etc.)
- `sortOrder` (string): Sort direction, either `asc` (ascending) or `desc` (descending)

Example:

`GET /recruiter/jobs?sortBy=postedAt&sortOrder=desc`

## Response

**Success (200):**

```json
{
  "content": [
    {
      "id": "<uuid>",
      "officeId": "<office-uuid>",
      "userId": "<recruiter-user-uuid>",
      "title": "Software Engineer",
      "postedAt": "2025-07-27T12:00:00Z",
      "updatedAt": "2025-07-27T12:00:00Z"
      "analytics": {
        "applications": 10,
        "shares": 2,
        "interviews": 3,
        "offers": 1,
        "hires": 1
      }
    }
  ]
}
```

**Errors**

- **401 Unauthorized**
  You must be logged in to access this resource.
