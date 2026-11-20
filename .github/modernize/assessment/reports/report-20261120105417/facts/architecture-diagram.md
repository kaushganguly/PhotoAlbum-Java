# Architecture Diagram

Photo Album is a single Spring MVC application that renders a server-side gallery and handles photo operations. Uploaded image data and metadata are persisted together in Oracle.

## Application Architecture

```mermaid
flowchart TD
    subgraph Client["Client Layer"]
        Browser["Browser"]
    end
    subgraph App["Application Layer - Spring Boot 2.7.18"]
        Web["Spring MVC controllers"]
        Views["Thymeleaf templates"]
        Security["Spring Security HTTP Basic"]
        Service["PhotoService transactional logic"]
        Repo["Spring Data JPA repository"]
    end
    subgraph Data["Data Layer"]
        Oracle[("Oracle Database")]
        Blobs["Photo metadata and BLOBs"]
    end
    Browser -->|"HTTP requests"| Security
    Security -->|"authorized state changes"| Web
    Web -->|"render model"| Views
    Web -->|"photo operations"| Service
    Service -->|"CRUD and queries"| Repo
    Repo -->|"JPA and SQL"| Oracle
    Oracle --> Blobs
    Views -->|"HTML response"| Browser
```

### Technology Stack Summary

| Layer | Technology | Version | Purpose |
|---|---|---|---|
| Presentation | Spring MVC and Thymeleaf | Spring Boot 2.7.18 | Server-rendered gallery and detail pages |
| Security | Spring Security, HTTP Basic | 5.7.11 | Protect upload and delete operations |
| Business Logic | Java | 8 | Photo upload, retrieval, navigation, deletion |
| Persistence | Spring Data JPA and Hibernate | 2.7.18 / 5.6.15.Final | Data access and transactions |
| Database | Oracle Database | Oracle Free container image | Photo metadata and binary storage |

### Data Storage & External Services

Oracle is the production/default database; each `Photo` record stores metadata and image bytes as a BLOB. H2 is used only by the test profile. No cache, message broker, or external API integration was identified.

### Key Architectural Decisions

- A single deployable Spring Boot application owns the presentation, business, and persistence layers.
- Photo payloads are stored in the relational database rather than on the application filesystem.
- Reads are public, while upload and delete operations use stateless HTTP Basic authentication.

## Component Relationships

```mermaid
flowchart LR
    subgraph Presentation["Presentation"]
        HomeCtrl["HomeController"]
        DetailCtrl["DetailController"]
        FileCtrl["PhotoFileController"]
        Templates["Thymeleaf templates"]
    end
    subgraph Business["Business Logic"]
        PhotoSvc["PhotoServiceImpl"]
        UploadResult["UploadResult"]
    end
    subgraph DataAccess["Data Access"]
        PhotoRepo["PhotoRepository"]
        PhotoEntity["Photo entity"]
    end
    subgraph Infrastructure["Infrastructure"]
        SecurityCfg["SecurityConfig"]
        OracleDb[("Oracle database")]
    end
    HomeCtrl -->|"gallery and upload"| PhotoSvc
    DetailCtrl -->|"view, navigation, delete"| PhotoSvc
    FileCtrl -->|"serve bytes"| PhotoSvc
    HomeCtrl -->|"returns rendered view"| Templates
    DetailCtrl -->|"returns rendered view"| Templates
    PhotoSvc -->|"returns operation result"| UploadResult
    PhotoSvc -->|"queries and persists"| PhotoRepo
    PhotoRepo -->|"maps"| PhotoEntity
    PhotoRepo -->|"JPA and native queries"| OracleDb
    SecurityCfg -.->|"protects write requests"| HomeCtrl
    SecurityCfg -.->|"protects delete request"| DetailCtrl
```

### Component Inventory

| Component | Layer | Type | Responsibility |
|---|---|---|---|
| HomeController | Presentation | MVC controller | Displays gallery and accepts multipart uploads |
| DetailController | Presentation | MVC controller | Displays one photo, navigates adjacent photos, and deletes |
| PhotoFileController | Presentation | MVC controller | Returns stored photo bytes |
| PhotoServiceImpl | Business Logic | Spring service | Validates and coordinates photo operations |
| PhotoRepository | Data Access | Spring Data repository | Persists photos and runs ordered/navigation queries |
| Photo | Data Access | JPA entity | Represents photo metadata and content |
| SecurityConfig | Infrastructure | Security configuration | Configures HTTP Basic and authorization |
