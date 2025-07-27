# Pagination Response Format

This document describes the structure of the paginated API response used by the backend and expected by the frontend.

## Response Structure

- **content**
  Array of items for the current page (e.g., list of jobs).

- **pageable**
  Pagination metadata about the current request:

  - `pageNumber`: current page index (0-based)
  - `pageSize`: number of items per page
  - `offset`: total items skipped (`pageNumber * pageSize`)
  - `paged`: boolean, if pagination is applied
  - `unpaged`: boolean, if pagination is disabled
  - `sort`: sorting info with flags:

    - `sorted`: true if sorted
    - `unsorted`: true if not sorted
    - `empty`: true if no sorting info

- **totalPages**
  Total number of pages available.

- **totalElements**
  Total number of items across all pages.

- **last**
  Boolean indicating if this is the last page.

- **first**
  Boolean indicating if this is the first page.

- **sort**
  Same sorting info as inside `pageable` for convenience.

- **numberOfElements**
  Number of items in the current page.

- **size**
  Number of items requested per page.

- **number**
  Alias for `pageNumber`, current page index.

- **empty**
  True if no items in the current page.

---

## Example Response

```json
{
  "content": [
    {
      "id": "<uuid>",
      "officeId": "<office-uuid>",
      "userId": "<recruiter-user-uuid>"
      }
    }
  ],
  "pageable": {
    "sort": {
      "sorted": true,
      "unsorted": false,
      "empty": false
    },
    "pageNumber": 0,
    "pageSize": 10,
    "offset": 0,
    "paged": true,
    "unpaged": false
  },
  "totalPages": 5,
  "totalElements": 50,
  "last": false,
  "first": true,
  "sort": {
    "sorted": true,
    "unsorted": false,
    "empty": false
  },
  "numberOfElements": 10,
  "size": 10,
  "number": 0,
  "empty": false
}
```

---

## Notes for Frontend

- Use `content` to render current page items.
- Use `pageable.pageNumber` or `number` as current page index (0-based).
- Use `totalPages` to know how many pages exist.
- Use `size` or `pageable.pageSize` for items per page.
- Check `last` and `first` to disable next/previous buttons.
- Use `sort.sorted` to check if sorting is applied.

---

## Notes for Backend

- Return consistent pagination metadata for every paged response.
- Accept `page`, `size`, and `sort` params to generate the correct page.
- Populate all pagination fields according to Spring Data’s `Page` object.
- Keep `content` with the current page’s data only.
