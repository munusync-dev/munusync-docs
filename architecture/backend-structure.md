# Backend Folder Structure

```plaintext
backend/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── yourcompany/
│   │   │           └── yourapp/
│   │   │               ├── config/            # Security and app configurations
│   │   │               ├── controller/        # REST controllers (API endpoints)
│   │   │               ├── dto/               # Data Transfer Objects
│   │   │               │   ├── request/       # API request payload classes
│   │   │               │   └── response/      # API response payload classes
│   │   │               ├── model/             # JPA entities (e.g., User)
│   │   │               ├── repository/        # Interfaces for DB access
│   │   │               ├── security/          # JWT, filters, and auth logic
│   │   │               ├── service/           # Business logic
│   │   │               └── YourAppApplication.java  # Main Spring Boot class
│   │   └── resources/
│   │       ├── application.properties         # Application config file
│   │       └── static/                        # Static assets (if needed)
│   └── test/
│       └── java/
│           └── com/
│               └── yourcompany/
│                   └── yourapp/
│                       └── (test classes)
├── pom.xml                                     # Maven config file
└── README.md                                   # Project documentation
```
