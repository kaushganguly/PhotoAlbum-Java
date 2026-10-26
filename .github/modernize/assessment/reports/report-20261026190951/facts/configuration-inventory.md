# Configuration Inventory

| Property / Variable | Default | Purpose |
|---------------------|---------|---------|
| `server.port` | 8080 | HTTP port |
| `SPRING_DATASOURCE_URL` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` | Oracle JDBC URL |
| `SPRING_DATASOURCE_USERNAME` | `photoalbum` | DB user |
| `SPRING_DATASOURCE_PASSWORD` | none (required) | DB password (environment only) |
| `APP_ADMIN_USERNAME` / `app.admin.username` | `admin` | Admin user for upload/delete |
| `APP_ADMIN_PASSWORD` / `app.admin.password` | none (required) | Admin password |
| `spring.jpa.hibernate.ddl-auto` | `create` | Schema regenerated at startup |
| `spring.jpa.show-sql` | `true` | SQL logging (default profile) |
| `spring.servlet.multipart.max-file-size` / `max-request-size` | 10MB / 50MB | Multipart limits |
| `app.file-upload.max-file-size-bytes` | 10485760 | Upload size validation |
| `app.file-upload.allowed-mime-types` | jpeg,png,gif,webp | Allowed MIME types |
| `app.file-upload.max-files-per-upload` | 10 | Per-request file limit |
| `logging.level.*` | DEBUG (default), INFO/WARN (docker) | Log levels |

Profiles: default, `docker` (`application-docker.properties`), test (`application-test.properties`, H2). Docker Compose reads secrets from `.env` (template `.env.example`).
