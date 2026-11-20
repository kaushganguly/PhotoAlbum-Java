# Configuration & Externalized Settings Inventory

The application uses Maven configuration, Spring property files for default/Docker/test environments, Docker Compose settings, and environment variables for database and administrator credentials. No remote configuration service or managed secret store was detected.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Spring default properties | Runtime configuration | `src/main/resources/application.properties` | Port, datasource, JPA, multipart, upload validation, and logging settings |
| Docker Spring properties | Runtime profile | `src/main/resources/application-docker.properties` | Oracle container connection, upload limits, encoding, and logging |
| Test Spring properties | Test runtime profile | `src/test/resources/application-test.properties` | H2 in-memory database and test-specific settings |
| Docker Compose | Container deployment | `docker-compose.yml` | Environment forwarding, port mappings, persistent volume, database health wait |
| Dockerfile | Container build/runtime | `Dockerfile` | Java 8 build/runtime images and JVM options |
| Maven POM | Build/dependency configuration | `pom.xml` | Java 8 target, Spring Boot parent and dependency declarations |
| Environment template | Secret/configuration template | `.env.example` | Documents required database and admin password variables; values are not copied here |
| Oracle init scripts | Database bootstrap | `oracle-init/` | Creates/verifies the application database user during initial container setup |

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Maven default | No `<profiles>` defined; normal Maven invocation | Builds the executable Spring Boot JAR | Spring Boot Maven plugin; Java source/target 8 |
| Docker build | Dockerfile build stages | Packages with Maven and runs the JAR in a Java 8 runtime image | Maven 3.9.6 / Eclipse Temurin 8 build image; Temurin 8 JRE runtime |

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Default | Spring default when no profile is selected | `application.properties` | Oracle URL can be overridden by environment; port 8080 |
| `docker` | `SPRING_PROFILES_ACTIVE=docker` in Compose | `application-docker.properties` | Oracle Compose host, same port and upload limits, less verbose application/web logs |
| `test` | `@ActiveProfiles("test")` on the context test | `application-test.properties` | H2 database, schema create/drop, SQL display off |

## Properties Inventory

| Property Key | Default / Source | Profiles | Notes |
|---|---|---|---|
| `server.port` | `8080` | Default, docker | HTTP server port |
| `spring.datasource.url` | `${SPRING_DATASOURCE_URL:jdbc:oracle:thin:@oracle-db:1521/FREEPDB1}` | Default, docker | Externalized URL with Docker Oracle fallback |
| `spring.datasource.username` | `${SPRING_DATASOURCE_USERNAME:photoalbum}` | Default, docker | Environment override; application user fallback |
| `spring.datasource.password` | `SPRING_DATASOURCE_PASSWORD` environment variable | Default, docker | Required secret; value intentionally omitted |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` | Default, docker | Oracle runtime driver |
| `spring.jpa.database-platform` | Oracle dialect | Default, docker | Test profile overrides with H2 dialect |
| `spring.jpa.hibernate.ddl-auto` | `create` | Default, docker | Test profile uses `create-drop` |
| `spring.jpa.show-sql` | `true` | Default, docker | Test profile sets `false` |
| `spring.jpa.properties.hibernate.format_sql` | `true` | Default, docker | SQL formatting |
| `spring.servlet.multipart.max-file-size` | `10MB` | Default, docker | Per-file multipart cap |
| `spring.servlet.multipart.max-request-size` | `50MB` | Default, docker | Request multipart cap |
| `app.file-upload.max-file-size-bytes` | `10485760` | Default, docker, test | Service upload cap (10 MiB) |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` | Default, docker, test | Configured allowed MIME types |
| `app.file-upload.max-files-per-upload` | `10` | Default, docker, test | Configured upload count setting |
| `app.admin.username` | `APP_ADMIN_USERNAME` environment variable; default `admin` in security injection | docker / application | HTTP Basic account name |
| `app.admin.password` | `APP_ADMIN_PASSWORD` environment variable | docker / application | Required secret; value intentionally omitted |
| `logging.level.com.photoalbum` | `DEBUG` (default), `INFO` (docker) | Default, docker, test | Application log level |
| `logging.level.org.springframework.web` | `DEBUG` (default), `WARN` (docker) | Default, docker | Framework web logging |
| `logging.level.org.hibernate.SQL` | `DEBUG` | docker | SQL log level |
| `server.servlet.encoding.*` | UTF-8, enabled, forced | Default, docker | Request/response encoding |

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| Photo Album | `JAVA_OPTS=-Xmx512m -Xms256m` | JVM heap capped at 512 MiB; container memory limit not specified | Compose defines one application container; no scaling configuration |
| Oracle database | Image defaults | No explicit container memory limit | Compose defines one database container |

## Startup Dependency Chain

1. Oracle database starts and runs its internal `healthcheck.sh` every 30 seconds (10-second timeout, 15 retries, 180-second start period).
2. Docker Compose starts the Photo Album application only after `oracle-db` reports healthy; the application restarts on failure.
3. No independent application readiness probe, config server, service registry, or other startup dependency is defined.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrator password | Supplied through ignored `.env`; Compose requires it; value not included |
| `APP_USER_PASSWORD` / `SPRING_DATASOURCE_PASSWORD` | Application database password | Supplied through ignored `.env` and injected as environment variable; value not included |
| `APP_ADMIN_PASSWORD` | Application HTTP Basic password | Supplied through ignored `.env` and injected as environment variable; value not included |

### Secrets Provisioning Workflow

For Compose deployments, operators copy `.env.example` to `.env` and provide unique passwords. Compose requires the database administrator, application DB user, and application admin password variables before starting; it forwards the application-user password as `SPRING_DATASOURCE_PASSWORD` and the admin password as `APP_ADMIN_PASSWORD`. For local runs, datasource values are supplied through Spring environment variables. No Key Vault, Vault, AWS Secrets Manager, managed identity, or encrypted property mechanism is configured.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| None detected | — | No feature flag framework or conditional feature toggle was identified |

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Java source/target and runtime | 8 | `pom.xml`, Dockerfile |
| Spring Boot | 2.7.18 | Maven parent POM |
| Spring Framework | 5.3.31 | Resolved Maven dependency tree |
| Spring Security | 5.7.11 | Resolved Maven dependency tree |
| Hibernate ORM | 5.6.15.Final | Resolved Maven dependency tree |
| Oracle JDBC | 21.5.0.0 | Maven dependency tree |
| Maven | 3.9.6 in Docker build image; host Maven not pinned | Dockerfile / Maven wrapper absent |
| Oracle database image | `gvenzl/oracle-free:latest` | `docker-compose.yml` |
| Servlet container | Embedded Tomcat 9.0.83 | Resolved Maven dependency tree |
