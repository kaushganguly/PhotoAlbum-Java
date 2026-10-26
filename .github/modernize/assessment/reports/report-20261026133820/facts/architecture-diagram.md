# Architecture Diagram

PhotoAlbum is a layered Spring Boot 2.7.18 (Java 8) monolith serving a server-rendered Thymeleaf gallery. Photos are stored as BLOBs in an Oracle database.

```mermaid
graph TD
    Browser[Browser - Thymeleaf pages + JS/CSS] -->|HTTP 8080| Sec[SecurityConfig - HTTP Basic, stateless]
    Sec --> HC[HomeController - / , /upload]
    Sec --> DC[DetailController - /detail/id, /detail/id/delete]
    Sec --> PC[PhotoFileController - /photo/id]
    HC --> PS[PhotoService / PhotoServiceImpl]
    DC --> PS
    PC --> PS
    PS --> PR[PhotoRepository - Spring Data JPA, native Oracle SQL]
    PR --> DB[(Oracle Database Free 23ai - PHOTOS table)]
```

| Component | Responsibility |
|---|---|
| `config/SecurityConfig` | In-memory admin user (BCrypt); POST `/upload` and `/detail/*/delete` require auth; rest public |
| `controller/*` | HTTP endpoints and view selection |
| `service/impl/PhotoServiceImpl` | Upload validation (MIME type, size, pixel limit), CRUD, prev/next navigation |
| `repository/PhotoRepository` | Native Oracle queries (ROWNUM, TO_CHAR, analytic functions) |
| `model/Photo`, `UploadResult` | JPA entity and upload outcome DTO |
| Deployment | `Dockerfile` + `docker-compose.yml` (app + `gvenzl/oracle-free`), Azure setup scripts |
