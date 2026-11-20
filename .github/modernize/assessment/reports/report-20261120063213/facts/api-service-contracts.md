# API & Service Communication Contracts

The application exposes five HTTP routes: server-rendered gallery/detail pages, a multipart upload operation, a photo-byte response, and a delete operation. Requests are handled synchronously within one application process; no inter-service API calls or asynchronous messaging were found.

## Service Catalog

| Service | Port | Category | Purpose |
|---|---:|---|---|
| Photo Album (`photo-album`) | 8080 | API / Presentation | Serves gallery pages and manages photo uploads, display, and deletion |
| Oracle database container | 1521 | Infrastructure | Stores photo metadata and BLOB image bytes; not an application module |

## API Endpoints Inventory

| Service | Method | Path | Request Type | Response Type |
|---|---|---|---|---|
| Photo Album / HomeController | GET | `/` | None | Thymeleaf gallery view |
| Photo Album / HomeController | POST | `/upload` | Multipart `files` list | JSON map with uploaded and failed upload details; 400 when no files are supplied |
| Photo Album / DetailController | GET | `/detail/{id}` | Path `id` | Thymeleaf detail view or redirect to `/` |
| Photo Album / DetailController | POST | `/detail/{id}/delete` | Path `id` | Redirect to `/` with a flash result |
| Photo Album / PhotoFileController | GET | `/photo/{id}` | Path `id` | Binary photo resource with stored media type; 404 if missing |

No URL/header/query-based API versioning scheme or OpenAPI specification was found.

## Management & Observability Endpoints

| Service | Endpoint | Custom Metrics |
|---|---|---|
| Photo Album | No application management or Actuator endpoint detected | None detected |
| Oracle database container | Compose health check runs `healthcheck.sh` internally | No application-exported metrics detected |

## DTOs & Contracts

`Photo` is the service-level JPA entity used to represent a persisted photo and returned to server-rendered views. `UploadResult` is a mutable POJO used internally between the service and upload controller. The upload request is Spring's multipart file contract; the controller assembles a mutable `Map<String,Object>` response rather than a dedicated response DTO. No immutable records, gateway aggregation DTOs, protobuf/GraphQL schemas, or explicit OpenAPI documents were found. Spring Boot's Jackson support is present for JSON serialization.

## Communication Patterns

Controllers call the `PhotoService` interface synchronously; `PhotoServiceImpl` calls `PhotoRepository`, which uses Spring Data JPA/Hibernate and JDBC to access Oracle. There are no message brokers, asynchronous handlers, circuit breakers, retry policies, API gateway, or service discovery client. Docker Compose uses the logical hostname `oracle-db` for database connectivity. Database readiness gates application startup through Compose `depends_on: condition: service_healthy`; application readiness has no separately configured health endpoint. Authentication is HTTP Basic for `/upload` and `/detail/*/delete`; other requests are public. TLS/HTTPS is not configured in the repository, and CSRF is disabled for the stateless security configuration.

## Service Technology Matrix

| Service | Web | Data Access | Discovery | Gateway | Health | Cache | Metrics |
|---|---|---|---|---|---|---|---|
| Photo Album | Spring MVC / Thymeleaf | Spring Data JPA / Hibernate | None | None | No Actuator endpoint | None detected | None detected |
| Oracle database container | Oracle Database | JDBC server | Docker Compose DNS | None | Container health check | Not applicable | Not detected |

## Service Communication Sequence

```mermaid
sequenceDiagram
    participant Client as "Browser"
    participant Security as "Security Filter"
    participant Home as "HomeController"
    participant Service as "PhotoService"
    participant Repo as "PhotoRepository"
    participant DB as "Oracle Database"

    Client->>Security: POST /upload with multipart files
    Security->>Security: Check HTTP Basic credentials
    alt Authenticated request
        Security->>Home: Forward upload request
        Home->>Service: uploadPhoto(file)
        Service->>Service: Check declared MIME type and size; inspect image dimensions
        alt Upload accepted
            Service->>Repo: save(Photo with BLOB)
            Repo->>DB: INSERT photo record
            DB-->>Repo: Persisted photo
            Repo-->>Service: Saved Photo
            Service-->>Home: Successful UploadResult
            Home-->>Client: 200 JSON upload result
        else Upload rejected
            Service-->>Home: Failed UploadResult
            Home-->>Client: 200 JSON with failedUploads
        end
    else Authentication required
        Security-->>Client: 401 Unauthorized
    end
```
