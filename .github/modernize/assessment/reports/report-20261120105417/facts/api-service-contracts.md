# API & Service Communication Contracts

The application exposes five HTTP routes: three page-oriented GET routes and two write operations. All interactions are synchronous and remain within one application process.

## Service Catalog

| Service | Port | Category | Purpose |
|---|---:|---|---|
| photo-album | 8080 | API Layer | Serves the gallery, photo details, image bytes, and upload/delete operations |
| oracle-db | 1521 | Infrastructure | Stores photo metadata and binary image content; third-party database container |

## API Endpoints Inventory

| Service | Method | Path | Request Type | Response Type |
|---|---|---|---|---|
| photo-album / HomeController | GET | `/` | No body | Thymeleaf gallery page |
| photo-album / HomeController | POST | `/upload` | Multipart `files` list | JSON map with uploaded and failed photos; 400 when empty |
| photo-album / DetailController | GET | `/detail/{id}` | Path parameter `id` | Thymeleaf detail page or redirect |
| photo-album / DetailController | POST | `/detail/{id}/delete` | Path parameter `id` | Redirect with flash result |
| photo-album / PhotoFileController | GET | `/photo/{id}` | Path parameter `id` | Binary `Resource` with stored MIME type; 404 if absent |

## Management & Observability Endpoints

| Service | Endpoint | Custom Metrics |
|---|---|---|
| photo-album | None identified; Spring Boot Actuator is not declared | None identified |

## DTOs & Contracts

`Photo` is the service-level JPA entity used in page models and as the source for photo-file responses. `UploadResult` is an internal service result; the upload endpoint assembles a response from maps rather than a dedicated request/response DTO. No gateway aggregation DTO, OpenAPI/Swagger specification, protobuf schema, or GraphQL schema was found. JSON serialization is provided by the Spring Boot JSON/Jackson stack.

## Communication Patterns

The browser communicates with the application over synchronous HTTP. Controllers call `PhotoService` directly; the service calls `PhotoRepository`, which accesses Oracle through JPA/native SQL. No asynchronous broker, service discovery, application gateway, retry policy, circuit breaker, or inter-service REST client was found. Docker Compose waits for the Oracle health check before starting the application. Stateless HTTP Basic authentication is configured for upload and delete; gallery and read routes are public. TLS termination is not configured in the application files examined.

## Service Technology Matrix

| Service | Web | Data Access | Discovery | Gateway | Actuator | Cache | Metrics |
|---|---|---|---|---|---|---|---|
| photo-album | Spring MVC | Spring Data JPA | None | None | Not detected | Not detected | Not detected |
| oracle-db | N/A | Oracle Database | N/A | N/A | Container health check | N/A | N/A |

## Service Communication Sequence

```mermaid
sequenceDiagram
    participant Client as "Browser"
    participant Web as "Spring MVC Controller"
    participant Service as "PhotoService"
    participant Repo as "PhotoRepository"
    participant DB as "Oracle Database"
    Client->>Web: POST /upload multipart files
    Web->>Service: uploadPhoto(file)
    Service->>Service: Check submitted MIME and size; inspect image header
    Service->>Repo: save(Photo metadata and bytes)
    Repo->>DB: Persist row and BLOB
    DB-->>Repo: Persisted photo
    Repo-->>Service: Photo with generated identifier
    Service-->>Web: UploadResult
    Web->>Service: getPhotoById(identifier)
    Service->>Repo: findById(identifier)
    Repo->>DB: Retrieve photo metadata
    DB-->>Repo: Photo record
    Repo-->>Service: Photo
    Service-->>Web: Photo metadata
    Web-->>Client: JSON upload result
```
