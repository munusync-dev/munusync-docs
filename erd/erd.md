```mermaid
erDiagram
    USER {
        string username
        string email
        string password
        datetime created_at
        datetime updated_at
        enum roles
    }

    ROLES {
        recruiter
        admin
        user
    }

    COMPANY {
        string name
        string industry
        string description
        datetime created_at
        datetime updated_at
    }

    USER ||--o{ COMPANY : "creates"
    USER }o--o{ COMPANY : "joins"

```
