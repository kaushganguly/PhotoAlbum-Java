# Configuration & Externalized Settings Inventory

Configuration is split across three Spring property files, container/build definitions, an environment template, and database/cloud provisioning scripts. The default and Docker configurations inject credentials from environment variables; the test profile defines test-local credentials, all redacted here.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Spring defaults | Properties | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application.properties` | Runtime defaults and environment placeholders |
| Docker overrides | Properties | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application-docker.properties` | Database/upload settings repeated; logging overrides |
| Test overrides | Properties | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/test/resources/application-test.properties` | H2, test upload path and test administrator |
| Admin bean configuration | Source placeholders | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/config/SecurityConfig.java` | Reads `app.admin.username` and required `app.admin.password` |
| Upload settings consumer | Source placeholders | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java` | Reads byte limit and MIME allowlist |
| Build | Maven POM | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml` | Parent, language level, dependencies, packaging |
| Container | Dockerfile | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/Dockerfile` | Multi-stage build and JVM options |
| Local orchestration | Compose YAML | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml` | Environment bindings, network, volume, startup gate |
| Environment template | Dotenv template | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.env.example` | User-supplied local configuration; no secret values reproduced |
| Oracle initialization | SQL/shell | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/oracle-init/` | Schema-user grants/verification and optional shell wait |
| Azure resource setup | PowerShell | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1` | ACR/AKS/PostgreSQL resources; generated local dotenv output, not an app runtime profile |
| Azure resource reset | PowerShell | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-reset.ps1` | Operational registry/cluster cleanup; not an application startup configuration |

No bootstrap file, Spring Cloud Config connection, external configuration repository, Kubernetes manifest, Key Vault/Vault client, or remote feature/configuration service was found in the analyzed application/deployment files. No live environment or actual `.env` contents were read.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Default Maven build; no named profiles | Normal Maven invocation | Executable JAR; UTF-8; Java source/target 8 | Spring Boot Maven plugin; dependency versions inherited from parent |
| Docker build invocation; not a Maven profile | Dockerfile | Multi-stage packaging | `mvn dependency:go-offline -B`, then `mvn clean package -DskipTests`; recorded only, not executed for this assessment |

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Default | No active profile supplied | Base properties | Oracle, verbose application/web logs |
| `docker` | Compose sets `SPRING_PROFILES_ACTIVE=docker` | Base plus Docker properties | Application INFO, web WARN, Hibernate SQL DEBUG |
| `test` | `@ActiveProfiles("test")` on existing context test | Base plus test properties | H2 connection/dialect, schema lifecycle, SQL logging, test-local administrator |

No `@Profile` beans, default active-profile property, or profile-composition logic is defined. Ordinary Spring environment/system/command-line overrides remain available; Compose dotenv interpolation is not the same as Spring loading `.env` itself.

## Properties Inventory

The following table covers the union of Spring property keys in the three files, plus the two administrator placeholders. Defaults come from base properties unless marked source-only. Credentials are represented only by variable names or redacted descriptions.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | `8080` (integer) | Repeated in `docker`; inherited in `test` | Base, Docker |
| `server.servlet.encoding.charset` | `UTF-8` | Repeated in `docker` | Base, Docker |
| `server.servlet.encoding.enabled` | `true` (boolean) | Repeated in `docker` | Base, Docker |
| `server.servlet.encoding.force` | `true` (boolean) | Repeated in `docker` | Base, Docker |
| `spring.datasource.url` | `${SPRING_DATASOURCE_URL:jdbc:oracle:thin:@oracle-db:1521/FREEPDB1}` | Same Docker fallback; test `jdbc:h2:mem:testdb` | Base, Docker, test |
| `spring.datasource.username` | `SPRING_DATASOURCE_USERNAME` with a schema-user fallback; literal omitted | Same Docker binding; test `[MASKED]` | Base, Docker, test |
| `spring.datasource.password` | Required `SPRING_DATASOURCE_PASSWORD`; no default | Same Docker binding; test `[MASKED]` | Base, Docker, test |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` | Test `org.h2.Driver` | Base, Docker, test |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` | Test `org.hibernate.dialect.H2Dialect` | Base, Docker, test |
| `spring.jpa.hibernate.ddl-auto` | `create` | Docker `create`; test `create-drop` | Base, Docker, test |
| `spring.jpa.show-sql` | `true` | Test `false` | Base, Docker, test |
| `spring.jpa.properties.hibernate.format_sql` | `true` | Inherited by test | Base, Docker |
| `spring.servlet.multipart.max-file-size` | `10MB` (data size) | Same Docker; test inherits | Base, Docker |
| `spring.servlet.multipart.max-request-size` | `50MB` (data size) | Same Docker; test inherits | Base, Docker |
| `app.file-upload.max-file-size-bytes` | `10485760` (long) | Same Docker/test | Base, Docker, test; consumed by service |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` (string array) | Same Docker/test | Base, Docker, test; consumed by service |
| `app.file-upload.max-files-per-upload` | `10` (integer) | Same Docker/test | Base, Docker, test; no application consumer found |
| `app.file-upload.upload-path` | Not set in base | Test `target/test-uploads` | Test only; no application consumer found |
| `logging.level.com.photoalbum` | `DEBUG` | Docker `INFO`; test `DEBUG` | Base, Docker, test |
| `logging.level.org.springframework.web` | `DEBUG` | Docker `WARN`; test inherits base | Base, Docker |
| `logging.level.org.hibernate.SQL` | Not explicitly set in base | Docker `DEBUG` | Docker |
| `app.admin.username` | Source-level administrator fallback; value omitted | Compose `APP_ADMIN_USERNAME`; test `[MASKED]` | `SecurityConfig`, Compose, test |
| `app.admin.password` | Required; no source-level default | Compose `APP_ADMIN_PASSWORD`; test `[MASKED]` | `SecurityConfig`, Compose, test |

Docker properties repeat the three `app.file-upload.*` keys with identical values within the same file. No extra effective configuration is introduced by the repeated entries.

### Container and Provisioning Settings

| Setting | Default / Reference | Source |
|---|---|---|
| `ORACLE_PASSWORD` | Required; `[MASKED]` | Compose environment interpolation |
| `APP_USER`, `APP_USER_PASSWORD` | Schema identifier fallback (value omitted); required password `[MASKED]` | Dotenv template and Compose |
| `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD` | Derived from `APP_USER`, `APP_USER_PASSWORD`; no password fallback | Compose application environment |
| `SPRING_DATASOURCE_URL` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` | Compose |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD` | Administrator identifier fallback (value omitted); required password `[MASKED]` | Dotenv template and Compose |
| Oracle persistence | `oracle_data:/opt/oracle/oradata` | Compose |
| Initialization mount | Project `oracle-init` directory to `/container-entrypoint-initdb.d` | Compose |
| Local network | `photoalbum-network`, bridge | Compose |
| Published ports | Application `8080:8080`; Oracle `1521:1521` | Compose |
| Application restart | `on-failure` | Compose |
| Azure `LOCATION`, `RESOURCE_GROUP`, `ACR_NAME`, `AKS_CLUSTER_NAME` | `westus3`; generated resource names | Setup script variables and generated dotenv |
| Azure `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | Environment-supplied identifiers/secrets or script defaults/generated password; values omitted | Setup script input |
| Azure `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD` | Environment-supplied identifiers/secrets or script defaults/generated password; values omitted | Setup script input |
| Azure `POSTGRES_SERVER`, `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_CONNECTION_STRING` | Script output; credential values `[MASKED]`; JDBC PostgreSQL URL on 5432 | Setup script environment and generated dotenv |
| Azure database settings | PostgreSQL 15, database `photoalbum`, 32 GiB storage, 7-day backup retention | Setup script |
| Build `java.version`, `maven.compiler.source`, `maven.compiler.target`, `project.build.sourceEncoding` | `1.8`, `8`, `8`, `UTF-8` | POM |

The `POSTGRES_*` names are not referenced by the application's Spring datasource placeholders. No PostgreSQL profile/driver or secret binding closes that configuration gap.

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| Photo Album container | `java $JAVA_OPTS -jar app.jar`; default `JAVA_OPTS=-Xmx512m -Xms256m`; Compose `SPRING_PROFILES_ACTIVE=docker` | Heap max 512 MiB, initial 256 MiB; no container memory/CPU request or limit | One Compose service instance; no replica/scaling policy |
| Oracle container | Image default entrypoint; initialization mount | No explicit Compose memory/CPU limit | One Compose instance |
| Azure infrastructure only | AKS `Standard_D8ds_v5`; PostgreSQL `Standard_D4ads_v5`; ACR Basic | VM/SKU selection, not application pod requests/limits | Two AKS nodes; no app deployment/replica specification |

No explicit `-D` startup properties are supplied. The heap limit does not account for native memory, threads, or in-flight uploads, and no whole-container budget is specified.

## Startup Dependency Chain

1. Local environment interpolation requires `ORACLE_PASSWORD`, `APP_USER_PASSWORD`, and `APP_ADMIN_PASSWORD` before Compose can create services; missing required values fail early.
2. Oracle starts with its data volume and initialization scripts. Its health check executes the image's `healthcheck.sh` every 30 seconds, with a 10-second timeout, 15 retries, and a 180-second start period.
3. Photo Album waits for Oracle via Compose `depends_on: condition: service_healthy`, then constructs the datasource, ORM context, and administrator bean. Oracle readiness does not prove all app-specific queries or credentials work.
4. `oracle-init/create-user.sh` contains a fixed 30-second delay; this is distinct from the Compose health check. The separate `healthcheck.sql` is not the command referenced by Compose.
5. No application health check/readiness probe, explicit application startup timeout, or config/discovery-server chain is defined.
6. The Azure script sequentially provisions resources and waits 30 seconds before database user setup; it does not start the application or establish runtime readiness.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrative password | User-provided local dotenv/environment; `[MASKED]` |
| `APP_USER_PASSWORD` to `SPRING_DATASOURCE_PASSWORD` | Application database password | Local dotenv to container environment; `[MASKED]` |
| `APP_ADMIN_PASSWORD` to `app.admin.password` | HTTP administrator password | Local dotenv/environment to Spring bean; `[MASKED]`; BCrypt hash in memory |
| `app.admin.username`, `spring.datasource.username` | Account identifiers | Environment/fallbacks; literal values omitted |
| Test datasource/admin credentials | Test-only values | Test properties; `[MASKED]` |
| `POSTGRES_ADMIN_PASSWORD`, `POSTGRES_APP_PASSWORD`, output `POSTGRES_PASSWORD` | Provisioning/database secrets | Setup environment or generated values; generated dotenv; `[MASKED]` |

### Secrets Provisioning Workflow

Local operation expects a user-created dotenv file based on `.env.example`. Compose interpolates required secret variables, passes Oracle administrative/schema credentials to the database container, and binds schema and administrator credentials into the application environment. Spring resolves datasource settings and the administrator bean; the administrator password is encoded with BCrypt for the in-memory user store. There is no detected encrypted-at-rest dotenv format, Jasypt layer, Vault/Key Vault integration, or managed identity for database access.

Oracle scripts create/grant the schema user using injected settings, though some grant/verification SQL assumes a fixed schema identifier; changing `APP_USER` alone does not update those SQL statements. The Azure setup script uses an existing Azure CLI login, accepts or generates PostgreSQL passwords, creates database access, and writes output settings to a git-ignored dotenv location. AKS is attached to ACR for image pull access; this is not application database secret delivery. The provisioning script and Compose use the same dotenv filename for different settings, so execution would need deliberate configuration coordination. No script was executed during this assessment.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| No dedicated feature flags detected | Not applicable | No feature framework or conditional feature beans found |
| Upload size/MIME policy (configuration, not a rollout flag) | Values in properties inventory | Spring properties consumed by service |
| `app.file-upload.max-files-per-upload` (declared only) | `10` | Property files; not enforced by an identified consumer |

Runtime profile selection is an environment switch, not an A/B or progressive rollout system.

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Application | 1.0.0 | POM |
| Spring Boot parent/starter line | 2.7.18 | POM |
| Java language/source/target | 8 (`1.8`) | POM |
| Build image | `maven:3.9.6-eclipse-temurin-8` | Dockerfile |
| Runtime image | `eclipse-temurin:8-jre` | Dockerfile; patch/digest unpinned |
| Oracle image | `gvenzl/oracle-free:latest` | Compose; exact database version not pinned |
| Oracle JDBC, Hibernate, Spring Security, Thymeleaf, H2 | Parent-managed; not explicitly versioned locally | POM |
| Commons IO | 2.11.0 | POM |
| Bootstrap browser assets | 5.3.0 | HTML templates, jsDelivr URLs |
| Provisioned PostgreSQL | 15 | Azure setup script; not an implemented runtime profile |
| Azure CLI / PowerShell / local Docker Compose | Not pinned | Provisioning scripts / Compose file |

This inventory is static. No live resource settings, resolved transitive library versions, builds, or tests were inspected/executed.
