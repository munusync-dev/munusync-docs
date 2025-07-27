# Create Job

**POST** `/recruiters/jobs` - `Recruiter`

## Overview

Allows a recruiter to create a new job posting for a company. Collects all required job information and returns the created job data.

## Behavior

Frontend collects job details from the user, including required skills, sends to backend via POST request. Backend validates input, creates job record, associates skills, and returns job info on success or error on failure.

## Flow (Frontend to Backend)

1. User enters job details in the create job form.
2. Backend receives request, validates input, checks for existing job (by title and office).
3. If valid and job does not exist, backend creates job, returns job info.
4. Frontend redirects user or displays success message.
5. If invalid or job exists, frontend displays error message.

## Request

**POST**

```json
{
  "officeId": "<office-uuid>",
  "title": "Software Engineer",
  "description": "Develop and maintain software applications.",
  "employmentType": "Full-time",
  "workType": "Remote",
  "salaryMin": 60000,
  "salaryMax": 90000,
  "requirements": "BSc in Computer Science, 2+ years experience.",
  "responsibilities": "Write code, review PRs, collaborate with team.",
  "benefits": "Health insurance, remote work, flexible hours.",
  "skills": ["<skill-uuid-1>", "<skill-uuid-2>", "<skill-uuid-3>"],
  "postedAt": "2025-07-27T12:00:00Z",
  "updatedAt": "2025-07-27T12:00:00Z"
}
```

## Response

**Success (201):**

```json
{
  "job": {
    "id": "<uuid>",
    "officeId": "<office-uuid>",
    "userId": "<recruiter-user-uuid>",
    "title": "Software Engineer",
    "description": "Develop and maintain software applications.",
    "employmentType": "Full-time",
    "workType": "Remote",
    "salaryMin": 60000,
    "salaryMax": 90000,
    "requirements": "BSc in Computer Science, 2+ years experience.",
    "responsibilities": "Write code, review PRs, collaborate with team.",
    "benefits": "Health insurance, remote work, flexible hours.",
    "skills": [
      {
        "id": "<skill-uuid-1>",
        "name": "JavaScript"
      },
      {
        "id": "<skill-uuid-2>",
        "name": "React"
      }
    ],
    "postedAt": "2025-07-27T12:00:00Z",
    "updatedAt": "2025-07-27T12:00:00Z"
  }
}
```

**Failure (400/409):**

- **400 Bad Request / 409 Conflict**
  Job title already exists for this office.
