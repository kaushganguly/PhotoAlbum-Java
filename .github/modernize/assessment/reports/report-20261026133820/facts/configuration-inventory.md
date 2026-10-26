# Configuration Inventory

| Setting | Location | Value / Source |
|---|---|---|
| `server.port` | application.properties | 8080 |
| `spring.datasource.url` | application*.properties | env `SPRING_DATASOURCE_URL`, default `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` |
| `spring.datasource.username` | application*.properties | env `SPRING_DATASOURCE_USERNAME`, default `photoalbum` |
| `spring.datasource.password` | application*.properties | env `SPRING_DATASOURCE_PASSWORD` (required, secret) |
| `app.admin.username` | SecurityConfig | env `APP_ADMIN_USERNAME`, default `admin` |
| `app.admin.password` | SecurityConfig | env `APP_ADMIN_PASSWORD` (required, secret) |
| `spring.jpa.hibernate.ddl-auto` | application*.properties | `create` |
| `spring.jpa.show-sql` | application.properties | `true` |
| `spring.servlet.multipart.max-file-size / max-request-size` | application*.properties | 10MB / 50MB |
| `app.file-upload.max-file-size-bytes` | application*.properties | 10485760 |
| `app.file-upload.allowed-mime-types` | application*.properties | jpeg, png, gif, webp |
| `app.file-upload.max-files-per-upload` | application*.properties | 10 |
| `logging.level.*` | application*.properties | DEBUG (default), INFO/WARN (docker profile) |
| Spring profile | docker-compose.yml | `SPRING_PROFILES_ACTIVE=docker` |
| Compose variables | `.env` | `ORACLE_PASSWORD`, `APP_USER`, `APP_USER_PASSWORD`, `APP_ADMIN_*` |

Secrets are injected through environment variables and are not hard-coded in main configuration; the test profile contains non-secret placeholder values.
