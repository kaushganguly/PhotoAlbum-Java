# Architecture Diagram

Photo Album is a single-deployable Spring Boot 2.7.18 (Java 8) monolith that serves a server-rendered Thymeleaf gallery and stores uploaded photos as BLOBs in an Oracle database.

```mermaid
graph TD
    Browser["Browser (Thymeleaf pages + upload.js)"]
    subgraph App["photo-album (Spring Boot, port 8080)"]
        Sec["SecurityConfig<br/>HTTP Basic, POST /upload & /detail/*/delete protected"]
        Home["HomeController<br/>GET / , POST /upload"]
        Detail["DetailController<br/>GET /detail/{id}, POST /detail/{id}/delete"]
        File["PhotoFileController<br/>GET /photo/{id}"]
        Svc["PhotoServiceImpl"]
        Repo["PhotoRepository (Spring Data JPA, native Oracle SQL)"]
    end
    DB[("Oracle DB (FREEPDB1)<br/>PHOTOS table with BLOB")]
    Browser --> Sec --> Home & Detail & File
    Home & Detail & File --> Svc --> Repo --> DB
```

## Components

| Component | Responsibility |
|-----------|----------------|
| `HomeController` | Gallery page and multi-file upload JSON API |
| `DetailController` | Photo detail page, previous/next navigation, delete |
| `PhotoFileController` | Streams photo bytes from the BLOB column |
| `PhotoServiceImpl` | Validation (MIME type, size, pixel limit), persistence, navigation queries |
| `PhotoRepository` | Oracle-specific native queries (ROWNUM, NVL, TO_CHAR) |
| `SecurityConfig` | Stateless HTTP Basic auth with an in-memory admin user |

Deployment: `docker-compose.yml` runs the app and `gvenzl/oracle-free`; Azure setup scripts (`azure-setup.ps1`) exist for cloud provisioning.
