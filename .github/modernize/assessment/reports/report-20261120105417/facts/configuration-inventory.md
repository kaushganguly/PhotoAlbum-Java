# Configuration & Externalized Settings Inventory

Configuration is supplied through three Spring property files, Docker Compose, and environment-variable placeholders. Database and administrator passwords are externalized; no external configuration service or secret manager integration was identified.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Maven build | Build | `pom.xml` | Java 8 source/target, Spring Boot parent, dependencies |
| Default Spring settings | Runtime | `src/main/resources/application.properties` | Port, database, upload limits, logging |
| Docker Spring profile | Runtime | `src/main/resources/application-docker.properties` | Oracle settings and Docker logging overrides |
| Test Spring profile | Runtime | `src/test/resources/application-test.properties` | H2 and test-only properties |
| Docker Compose | Runtime/deployment | `docker-compose.yml` | Environment substitutions and Oracle health dependency |
| Environment template | Secret setup | `.env.example` | Placeholder values only; actual `.env` is ignored/not present |

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| None declared | N/A | No Maven `<profiles>` block found | Spring Boot Maven plugin is always active |

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| default | Spring Boot default when no profile is selected | `application.properties` | Oracle database and application defaults |
| docker | `SPRING_PROFILES_ACTIVE=docker` in Compose | `application-docker.properties` plus base properties | Oracle connection and quieter web/application logs |
| test | `@ActiveProfiles("test")` on the context test | `application-test.properties` | H2 in-memory database and test settings |

## Properties Inventory

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | `8080` | default, docker | Property file |
| `spring.datasource.url` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` | default, docker; environment override | `SPRING_DATASOURCE_URL` |
| `spring.datasource.username` | `photoalbum` | default, docker; environment override | `SPRING_DATASOURCE_USERNAME` |
| `spring.datasource.password` | Required external value | default, docker | `SPRING_DATASOURCE_PASSWORD` |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` | default, docker | Property file |
| `spring.jpa.database-platform` | Oracle dialect | default, docker | Property file |
| `spring.jpa.hibernate.ddl-auto` | `create` | default, docker; test overrides to `create-drop` | Property file |
| `spring.servlet.multipart.max-file-size` | `10MB` | default, docker | Property file |
| `spring.servlet.multipart.max-request-size` | `50MB` | default, docker | Property file |
| `app.file-upload.max-file-size-bytes` | `10485760` | default, docker, test | Property file |
| `app.file-upload.allowed-mime-types` | JPEG, PNG, GIF, WebP | default, docker, test | Property file |
| `app.file-upload.max-files-per-upload` | `10` | default, docker, test | Property file; enforcement was not identified in source |
| `app.admin.username` | `admin` | default fallback; Compose override | `APP_ADMIN_USERNAME` |
| `app.admin.password` | Required external value | default/docker | `APP_ADMIN_PASSWORD` |
| `logging.level.*` | Profile-specific | default, docker, test | Property files |

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| photo-album | `-Xms256m -Xmx512m` via Dockerfile `JAVA_OPTS` | Heap maximum 512 MB; container limit not specified | Not specified |
| oracle-db | Container defaults | Not specified | One Compose service |

## Startup Dependency Chain

1. `oracle-db` starts and must pass its Compose health check (30-second interval, 10-second timeout, 15 retries, 180-second start period).
2. Docker Compose starts `photoalbum-java-app` after `oracle-db` reports healthy; the application connects using the configured database URL.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrator password | Required environment substitution sourced from ignored `.env`; example file contains placeholder only |
| `APP_USER_PASSWORD` / `SPRING_DATASOURCE_PASSWORD` | Database application password | Required environment substitution; actual value not committed |
| `APP_ADMIN_PASSWORD` / `app.admin.password` | Inbound Basic-auth password | Required environment variable; hashed by BCrypt when configured |

### Secrets Provisioning Workflow

The operator copies `.env.example` to the ignored `.env` file and supplies unique values. Docker Compose passes database and administrator credentials into the Oracle container and application container; the app uses required environment placeholders. No managed identity, Key Vault, Vault, or cloud secret binding is configured in the repository.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| None identified | N/A | No feature-flag framework or conditional property toggle found |

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Java source/target | 8 | `pom.xml` |
| Spring Boot | 2.7.18 | `pom.xml` parent |
| Spring Framework | 5.3.31 | Resolved dependency tree |
| Spring Security | 5.7.11 | Resolved dependency tree |
| Hibernate | 5.6.15.Final | Resolved dependency tree |
| Oracle JDBC | 21.5.0.0 | Resolved dependency tree |
| Maven | 3.9.6 in build container | Dockerfile |
| Docker build JDK | Eclipse Temurin 8 | Dockerfile |
| Docker runtime | Eclipse Temurin 8 JRE | Dockerfile |
