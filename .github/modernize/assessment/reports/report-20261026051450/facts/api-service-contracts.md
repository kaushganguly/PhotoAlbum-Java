# API & Service Communication Contracts

Five explicitly mapped HTTP endpoints provide gallery HTML, photo bytes, multipart upload, and deletion. Browser requests and server-side operations are synchronous request/response interactions; no backend messaging or inter-service HTTP API was found.

## Service Catalog

| Service | Port | Category | Purpose |
|---|---|---|---|
| `photoalbum-java-app` / Maven `com.photoalbum:photo-album` | HTTP 8080; Compose publishes 8080 | API Layer / Business | One source-built application serving the gallery and photo operations; controllers and business services are not separate deployments. |
| `oracle-db` | TCP 1521; Compose publishes 1521 | Infrastructure | Third-party Oracle container supporting photo operations through JDBC, not an HTTP API. |

The build has one module. Application dependencies include Spring Boot 2.7.18 Web/MVC, Thymeleaf, Data JPA, Security, Validation, JSON/Jackson, and the Oracle JDBC driver. No additional deployable application modules, gateway, discovery service, or observability service were identified.

Evidence: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:8-101`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml:1-44`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/Dockerfile:25`.

## API Endpoints Inventory

All endpoints belong to `photoalbum-java-app`. No URL, header, or query-based API versioning is implemented.

| Service / Controller | Method | Path | Request Type | Response Type |
|---|---|---|---|---|
| App / `HomeController` | GET | `/` | No bound parameters | 200 HTML `index` view, populated from `List<Photo>`; retrieval exceptions produce an empty gallery rather than an error response. |
| App / `HomeController` | POST | `/upload` | Multipart form with repeated `files` parts bound to `List<MultipartFile>`; HTTP Basic authentication | 200 JSON `Map<String,Object>` containing upload outcomes, including partial or total per-file rejection; 400 JSON for the explicit empty-list guard; missing required parts normally produce framework 400; unauthenticated requests receive 401. |
| App / `DetailController` | GET | `/detail/{id}` | String path parameter `id` | 200 HTML `detail` view using `Photo` and neighboring-photo identifiers; redirect to `/` (normally 302) for missing photos or caught exceptions. |
| App / `DetailController` | POST | `/detail/{id}/delete` | String path parameter `id`; HTTP Basic authentication; no request DTO | Redirect to `/` (normally 302) with success/error flash attributes, including not-found and caught failure outcomes; unauthenticated requests receive 401. |
| App / `PhotoFileController` | GET | `/photo/{id}` | String path parameter `id`; browser also sends an ignored `_t` cache-busting query parameter | 200 `Resource` backed by `ByteArrayResource`, with the stored MIME type; 404 for missing photo or absent bytes; 500 for caught exceptions. |

**Contract details**

- Upload JSON uses `success`, `uploadedPhotos`, and `failedUploads`; the explicit empty-list error uses `success` and `error` instead. Clients must inspect per-file outcomes even on HTTP 200. There is no typed upload-response DTO or uniform error envelope.
- Application-level file rejection normally appears inside HTTP 200, not HTTP 400. Multipart parsing/size failures occur before controller handling; no custom multipart exception contract was found.
- A successful upload is followed by a separate metadata lookup before it is included in the response. Lookup failures are not caught by `HomeController.uploadPhotos`; the response is not an atomic batch-success guarantee.
- Photo responses set `Cache-Control: no-cache, no-store, must-revalidate, private`, `Pragma: no-cache`, `Expires: 0`, and `X-Photo-ID`, `X-Photo-Name`, `X-Photo-Size`. No explicit content-disposition, range, ETag, or conditional-download handling is implemented by the controller.
- Templates also reference framework-served static CSS/JavaScript. The legacy `/uploads/` path returned in metadata is not the current database-backed photo-serving contract; clients use `/photo/{id}`.
- Framework-provided static-resource and error handling are not additional explicitly mapped business endpoints.

Evidence: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/controller/HomeController.java:37-97`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/controller/DetailController.java:18-78`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/controller/PhotoFileController.java:23-86`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/static/js/upload.js:97-131,176-179`.

## Management & Observability Endpoints

| Service | Endpoint | Custom Metrics (if any) |
|---|---|---|
| `photoalbum-java-app` | No dedicated health, Actuator, metrics, Prometheus, Swagger UI, or OpenAPI endpoint identified | No custom timed metrics, meter registrations, or metrics exporter identified; controllers/services use SLF4J logs. |
| `oracle-db` | No application HTTP management API identified | Compose container health monitoring is not a public API contract. |

No Actuator or API-documentation dependency is declared. Evidence: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:30-101`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/controller/PhotoFileController.java:26`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml:17-23`.

## DTOs & Contracts

| Class / Type | Contract role | Mutability |
|---|---|---|
| `Photo` | Service-owned domain entity used in HTML view models, projected into upload JSON, and read to obtain photo bytes; not accepted as an HTTP request body | Mutable POJO |
| `UploadResult` | Internal result of `PhotoService.uploadPhoto`; translated by the controller into public response maps, not returned directly | Mutable POJO |
| `Map<String,Object>` and nested lists/maps | Public upload JSON response; success entries project photo metadata and failures carry filename/error information | Mutable, untyped contract |
| `MultipartFile` | Framework multipart request type, repeated under `files` | Framework-managed request object |
| `Resource` / `ByteArrayResource` | Binary photo response abstraction | Not an application DTO |

There are no gateway aggregation DTOs, Java records, immutable application DTOs, or separately versioned shared contracts. Jackson serialization is supplied by the JSON/Web dependencies; no custom serializers or application-specific ObjectMapper configuration were identified. Dates in upload metadata use `LocalDateTime`, without a custom wire-format declaration. HTML is rendered with Thymeleaf.

No OpenAPI/Swagger document, protobuf schema, or GraphQL schema was found. Entity field definitions and persistence details belong in `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/modernize/assessment/copilot/engines/facts/data-architecture.md`, rather than this contract inventory.

Evidence: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/model/Photo.java:19-199`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/model/UploadResult.java:6-62`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/controller/HomeController.java:57-95`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:30-79`.

## Communication Patterns

- **Synchronous:** Browser GETs and multipart POSTs invoke MVC controllers, which call `PhotoService` directly. `PhotoServiceImpl` invokes `PhotoRepository` through JPA/JDBC. No REST client, Feign, gRPC, or calls to independently deployed business APIs were found.
- **Browser interaction:** JavaScript uses `fetch('/upload')` and then updates the gallery from JSON; image bytes are fetched separately. JavaScript `async`/`await` does not represent asynchronous backend messaging. Templates load Bootstrap CSS/JavaScript from an external HTTPS CDN; this is browser asset delivery, not server-to-server business communication.
- **Asynchronous:** No broker, pub/sub, event bus, background API job, WebSocket, or server-sent event contract identified.
- **Gateway/discovery/load balancing:** None identified. Browser paths are same-origin. Compose provides a database service hostname; no application service registration or client-side load balancer is implemented. No cross-service aggregation or downstream fallback exists.
- **Resilience:** No application retry, circuit breaker, bulkhead, explicit outbound request timeout, or application-configured JDBC timeout was identified. Browser upload has no explicit timeout/AbortController and offers a manual retry message, not automatic retry. Compose restarts the application on failure; this is process recovery, not request retry.
- **Failure behavior:** Gallery retrieval falls back to an empty list; detail and delete handlers redirect on caught failures. Upload processing is sequential per file, returning internal failures as per-file results where caught. Transaction completion or the subsequent metadata lookup can still fail outside the returned `UploadResult`; no controller-wide handler guarantees JSON for such failures. Binary retrieval returns 404 or 500 as described above.
- **Availability:** Compose starts the application after the database becomes healthy. Required administrative credentials must also be supplied for the security bean to initialize. Deployment/configuration details belong in `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/modernize/assessment/copilot/engines/facts/configuration-inventory.md`.
- **Authentication/authorization:** Stateless HTTP Basic protects POST `/upload` and POST `/detail/*/delete`. Other requests are permitted without authentication. An in-memory administrator principal is configured, but endpoint rules require only authentication, not an ADMIN role check or per-photo ownership check. No JWT/OAuth2 or method-level authorization was found. CSRF is disabled; no login-page endpoint is configured.
- **Transport:** The application/container expose HTTP 8080; no application TLS configuration or HTTPS enforcement was identified. CDN asset requests use HTTPS, but that does not secure the application's HTTP Basic credentials. External TLS termination cannot be confirmed from these application contracts.

Evidence: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:28-237`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/config/SecurityConfig.java:28-61`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/static/js/upload.js:90-132`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/templates/index.html:7,124`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml:37-44`.

## Service Technology Matrix

| Service | Web | Data Access | Discovery | Gateway | Actuator / Health | Cache | Metrics |
|---|---|---|---|---|---|---|---|
| `photoalbum-java-app` | MVC / Thymeleaf / JSON | JPA / JDBC | No registry | None | No dedicated application health endpoint | No application cache identified; binary HTTP caching explicitly disabled | Logs only; no exporter identified |
| `oracle-db` | Not HTTP | Database server | Compose hostname | None | Container-level check only | Not assessed as an application cache | No exporter defined in Compose |

Evidence: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:30-101`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/repository/PhotoRepository.java:15-16`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/controller/PhotoFileController.java:75-83`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml:1-44`.

## Service Communication Sequence

Primary upload-and-display flow. Solid arrows are synchronous calls; dashed arrows are responses, not broker messages. Internal service/repository participants run in the same application deployment.

```mermaid
sequenceDiagram
    participant Client as "Browser"
    participant Security as "Security Filter"
    participant Home as "HomeController"
    participant Service as "PhotoServiceImpl"
    participant Repo as "PhotoRepository"
    participant DB as "Oracle Database"
    participant File as "PhotoFileController"
    Client->>Security: POST /upload with multipart files and Basic auth
    alt Authentication missing or invalid
        Security-->>Client: 401 Unauthorized
    else Authenticated
        Security->>Home: uploadPhotos List of MultipartFile
        loop Each file sequentially
            Home->>Service: uploadPhoto MultipartFile
            alt File rejected or read fails
                Service-->>Home: UploadResult failure
            else Accepted file
                Service->>Repo: save Photo
                Repo->>DB: Persist photo
                alt Persistence succeeds
                    DB-->>Repo: Saved
                    Repo-->>Service: Photo
                    Service-->>Home: UploadResult success
                    Home->>Service: getPhotoById
                    Service->>Repo: findById
                    Repo->>DB: Read photo
                    DB-->>Repo: Photo
                    Repo-->>Service: Optional Photo
                    Service-->>Home: Optional Photo
                else Persistence exception caught in service
                    DB-->>Repo: Error
                    Repo-->>Service: Exception
                    Service-->>Home: UploadResult failure
                end
            end
        end
        Home-->>Client: 200 JSON upload outcomes
        Client->>File: GET /photo/id
        File->>Service: getPhotoById
        Service->>Repo: findById
        Repo->>DB: Read photo
        DB-->>Repo: Photo or absent
        Repo-->>Service: Optional Photo
        Service-->>File: Optional Photo
        File-->>Client: 200 image bytes or 404; caught errors give 500
    end
```

The diagram shows handled outcomes, not an all-or-nothing upload guarantee: uncaught metadata lookup or transaction-completion errors can terminate the request. No automatic retry or circuit-breaker path exists.
