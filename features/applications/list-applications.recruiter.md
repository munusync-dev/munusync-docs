# List Applications

**GET** `/recruiter/jobs/{jobId}/applications` - `Recruiter`

## Overview

Allows a recruiter to view all applications submitted for a specific job posting. Returns detailed information about each application, including candidate profile, resume, status, and analytics. Only recruiters associated with the company/job can access this endpoint.

## Behavior

- Backend authenticates recruiter via JWT.
- Validates that the recruiter has access to the job (by company association).
- Fetches all applications for the specified job, including candidate details, resume, and application status.
- Supports filtering, sorting, and pagination.
- Returns a paginated list of applications with all relevant details for review and action.

## Flow (Frontend to Backend)

1. Recruiter navigates to the job details page and selects the "Applications" tab.
2. Frontend requests the list of applications for the selected job (with optional filters/sorting).
3. Backend authenticates recruiter and validates access.
4. Backend fetches applications, joins candidate/user/profile data, and returns paginated results.
5. Frontend displays applications with candidate info, status, and actions (view, shortlist, reject, etc).

## Request

`GET /recruiter/jobs/{jobId}/applications?page=0&size=20&status=APPLIED&sort=appliedAt,desc`

### Query Parameters
- `page` (int): Page number (default: 0)
- `size` (int): Page size (default: 20)
- `status` (string): Filter by application status (e.g., APPLIED, SHORTLISTED, REJECTED, HIRED)
- `sort` (string): Sort field and direction (e.g., appliedAt,desc)
- `search` (string): Search by candidate name or email

## Response

**Success (200):**

```json
{
  "content": [
    {
      "id": "<application-uuid>",
      "jobId": "<job-uuid>",
      "userId": "<candidate-user-uuid>",
      "fname": "John",
      "lname": "Doe",
      "email": "john.doe@email.com",
      "phone": "+1234567890",
      "resumeUrl": "https://example.com/resume.pdf",
      "status": "APPLIED",
      "appliedAt": "2025-07-27T12:00:00Z",
      "updatedAt": "2025-07-27T12:00:00Z",
      "candidate": {
        "bio": "Experienced software engineer...",
        "socialLinks": [
          "https://linkedin.com/in/johndoe",
          "https://github.com/johndoe"
        ],
        "profile": {
          "firstName": "John",
          "lastName": "Doe",
          "profilePicture": "https://example.com/profile.jpg"
        },
        "experience": [
          {
            "title": "Senior Developer",
            "company": "Acme Corp",
            "startDate": "2021-01-01",
            "endDate": "2023-06-01",
            "description": "Worked on..."
          }
        ],
        "education": [
          {
            "school": "MIT",
            "degree": "BSc Computer Science",
            "fieldOfStudy": "Computer Science",
            "startDate": "2017-09-01",
            "endDate": "2021-06-01",
            "description": "Studied..."
          }
        ],
        "skills": [
          { "id": "<skill-uuid-1>", "name": "JavaScript" },
          { "id": "<skill-uuid-2>", "name": "React" }
        ]
      },
      "analytics": {
        "views": 3,
        "lastViewedAt": "2025-07-28T09:00:00Z"
      }
    }
  ],
  "pageable": {
    "pageNumber": 0,
    "pageSize": 20,
    "offset": 0,
    "paged": true,
    "unpaged": false,
    "sort": { "sorted": true, "unsorted": false, "empty": false }
  },
  "totalPages": 1,
  "totalElements": 1,
  "last": true,
  "first": true,
  "sort": { "sorted": true, "unsorted": false, "empty": false },
  "numberOfElements": 1,
  "size": 20,
  "number": 0,
  "empty": false
}
```

**Errors**

- **401 Unauthorized**
  Recruiter is not authenticated.
- **403 Forbidden**
  Recruiter does not have access to this job or company.
- **404 Not Found**
  Job not found.

## Notes
- Only recruiters associated with the job's company can access this endpoint.
- Application status values: APPLIED, SHORTLISTED, INTERVIEW, OFFERED, REJECTED, HIRED, WITHDRAWN.
- Candidate details are joined from User, Profile, Candidate, Experience, Education, and Skill tables (see ERD).
- Analytics may include views, last viewed timestamp, and other recruiter-specific metrics.
- Pagination follows the shared pagination response format.
