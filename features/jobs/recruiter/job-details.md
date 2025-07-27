# Recruiter: Job Details

**GET** `/recruiter/jobs/{jobId}` - `Recruiter`

## Overview

Returns detailed information for a single job post, including all related data needed by the recruiter. This endpoint aggregates job, office, company, skills, analytics, and application details in one response.

## Behavior

- Backend authenticates recruiter via JWT.
- Fetches job by `jobId`.
- Aggregates all related data from the schema: job, office, company, skills, analytics, applications, etc.
- Returns a detailed job object.

## Request

`GET /recruiter/jobs/{jobId}`

No body required. JWT must be sent in Authorization header.

## Response

**Success (200):**

```json
{
  "job": {
    "id": "<uuid>",
    "title": "Software Engineer",
    "description": "Develop and maintain software applications.",
    "employmentType": "Full-time",
    "workType": "Remote",
    "salaryMin": 60000,
    "salaryMax": 90000,
    "requirements": "BSc in Computer Science, 2+ years experience.",
    "responsibilities": "Write code, review PRs, collaborate with team.",
    "matchRate": 0.92,
    "benefits": "Health insurance, remote work, flexible hours.",
    "postedAt": "2025-07-27T12:00:00Z",
    "updatedAt": "2025-07-27T12:00:00Z",
    "skills": [
      { "id": "<skill-uuid-1>", "name": "JavaScript" },
      { "id": "<skill-uuid-2>", "name": "React" }
    ],
    "analytics": {
      "views": 123,
      "applications": 10,
      "clicks": 45,
      "saves": 7,
      "shares": 2,
      "interviews": 3,
      "offers": 1,
      "hires": 1,
      "updatedAt": "2025-07-27T12:00:00Z"
    }
  }
}
```

**Errors**

- **401 Unauthorized**
  You must be logged in to access this resource.
- **404 Not Found**
  Job not found or you do not have access.
