# Configuration & Externalized Settings Inventory

Configuration comprises three Spring properties files, Docker build/Compose definitions, an environment template, Java-injected settings, Oracle initialization scripts, and Azure provisioning scripts. Two named runtime profiles are present; secrets are supplied through environment variables rather than a configured remote secret store.

All password, key, token, and credential values—including example defaults and usernames—are omitted or masked. Citations use repository-relative paths and line numbers. This inventory reflects checked-in configuration, not verified deployed state.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Base runtime configuration | Spring properties | `src/main/resources/application.properties:1-34` | Default server, encoding, datasource, JPA, upload, and logging settings. |
| Docker runtime configuration | Spring profile properties | `src/main/resources/application-docker.properties:1-35` | Overrides base properties when `docker` is active. Upload properties are repeated at lines 20-22 and 28-30 with identical values. |
| Test runtime configuration | Spring profile properties | `src/test/resources/application-test.properties:1-23` | H2, test upload path, and masked test authentication settings. |
| Environment template | Compose interpolation input | `.env.example:1-17` | Instructs copying to `.env`; credential examples are intentionally not reproduced. `.env` and `.env.*` are ignored, with the example explicitly retained (`.gitignore:201-204`). Spring does not directly import this file. |
| Container orchestration | Compose YAML | `docker-compose.yml:1-51` | Supplies environment overrides; persistent Oracle volume, initialization mount, network, startup dependency, and database health check. |
| Container runtime/build | Dockerfile | `Dockerfile:1-31` | Multi-stage Maven/Java build and configurable JVM options. |
| Build configuration | Maven POM | `pom.xml:8-110` | Parent/BOM, compiler properties, dependencies, packaging, and Boot plugin. |
| Code-level properties/security | Java configuration | `src/main/java/com/photoalbum/config/SecurityConfig.java:25-61`; `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:41-47` | Administrator properties and required upload-property injection. Security policy is coded, not an external feature flag. |
| Oracle initialization | SQL/shell | `oracle-init/01-create-user.sql:1-35`; `oracle-init/02-verify-user.sql:1-14`; `oracle-init/create-user.sh:1-47`; `oracle-init/healthcheck.sql:1-3` | Environment-based user creation, schema grants, verification, and a standalone SQL health query. |
| Azure infrastructure configuration | PowerShell | `azure-setup.ps1:26-41,56-158,267-299` | Resource names, location, SKUs, PostgreSQL parameters, and generated root `.env`; not a Spring profile. |
| Azure cleanup controls | PowerShell parameters | `azure-reset.ps1:6-18,132` | `ResourceGroupName` required; `Force`, `AcrOnly`, `AksOnly` switches; namespace cleanup timeout 60s. |
| Developer integration settings | MCP JSON; not application runtime | `.copilot/mcp-config.json:1-15` | Example Trello integration launched through `npx`; `TRELLO_API_KEY` and `TRELLO_TOKEN` references only. |
| Repository automation | GitHub Actions; not application runtime | `.github/workflows/squad-ci.yml:1-28`; `.github/workflows/squad-heartbeat.yml:254`; `.github/workflows/squad-issue-assign.yml:121`; `.github/workflows/squad-release.yml:30-31`; `.github/workflows/squad-insider-release.yml:30-31`; `.github/workflows/squad-promote.yml:24,77` | Workflow permissions and repository secret references; CI build/test command remains a placeholder. |
| Operational documentation | README | `README.md:19-30,65-78,139-158` | Describes local environment overrides. Oracle image/version descriptions differ from executable Compose configuration. |

No application `bootstrap.*`, YAML profile files, Spring Cloud Config repository, Azure App Configuration, Vault, Key Vault, Kubernetes manifests, or remote secret-store integration was found in the application/deployment sources examined. Agent definition files were not read.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Default Maven build; no named `<profiles>` | Standard Maven invocation | Java 8 JAR compilation/package | Boot web, Thymeleaf, Data JPA, validation, security, JSON; Oracle runtime driver; Commons IO; test starter/H2; optional DevTools; Boot Maven plugin (`pom.xml:18,23-110`). |
| Docker build stage; not a Maven profile | Docker build / Compose `build` | Resolve dependencies, then package without running tests | `mvn dependency:go-offline -B`, `mvn clean package -DskipTests` (`Dockerfile:6-14`; `docker-compose.yml:26-28`). |

No Gradle, Node package build, Maven wrapper, or named build-profile activation is present in the discovered application build files. CI does not currently execute the documented Maven test example (`.github/workflows/squad-ci.yml:20-28`).

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Default/base | No explicit active profile | `src/main/resources/application.properties` | Oracle datasource, DEBUG application/web logging, shared upload and servlet settings (`:2-34`). |
| `docker` | Compose sets `SPRING_PROFILES_ACTIVE=docker` (`docker-compose.yml:31`) | Base plus `src/main/resources/application-docker.properties` | Application INFO, web WARN, Hibernate SQL DEBUG; Oracle/server/upload properties restated (`:3-35`). |
| `test` | `@ActiveProfiles("test")` (`src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java:7-8`) | Base plus `src/test/resources/application-test.properties` | H2, create-drop schema setting, SQL logging disabled, test upload path, masked test credentials (`:2-23`). |

No `@Profile` beans, profile groups, combined activation, or `spring.profiles.active` declaration was found in application source. Standard Spring Boot resolution applies: command-line/system/environment overrides can supersede packaged properties, and active profile properties override base properties. Explicit datasource placeholders select their named environment variable before a configured fallback; the password placeholder has no fallback.

## Properties Inventory

### Single Maven application: packaged and injected properties

Values below are declared configuration, not inferred production values. Credential defaults are masked even where non-secret-looking or empty.

| Property Key | Default | Profiles / Type | Source |
|---|---|---|---|
| `server.port` | `8080` | Base/docker; integer TCP port | `src/main/resources/application.properties:2`; `src/main/resources/application-docker.properties:25` |
| `server.servlet.encoding.charset` | `UTF-8` | Base/docker; charset string | `src/main/resources/application.properties:5`; `src/main/resources/application-docker.properties:9` |
| `server.servlet.encoding.enabled` | `true` | Base/docker; boolean | `src/main/resources/application.properties:6`; `src/main/resources/application-docker.properties:10` |
| `server.servlet.encoding.force` | `true` | Base/docker; boolean | `src/main/resources/application.properties:7`; `src/main/resources/application-docker.properties:11` |
| `spring.datasource.url` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1`; environment `SPRING_DATASOURCE_URL` | Base/docker; JDBC URL. Test: `jdbc:h2:mem:testdb` | `src/main/resources/application.properties:12`; `src/main/resources/application-docker.properties:3`; `src/test/resources/application-test.properties:2` |
| `spring.datasource.username` | `[MASKED]`; environment `SPRING_DATASOURCE_USERNAME` | Base/docker; test credential also masked | `src/main/resources/application.properties:13`; `src/main/resources/application-docker.properties:4`; `src/test/resources/application-test.properties:4` |
| `spring.datasource.password` | `[MASKED]`; required `SPRING_DATASOURCE_PASSWORD`, no base/docker fallback | Test supplies masked value | `src/main/resources/application.properties:14`; `src/main/resources/application-docker.properties:5`; `src/test/resources/application-test.properties:5` |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` | Base/docker; test: `org.h2.Driver` | `src/main/resources/application.properties:15`; `src/main/resources/application-docker.properties:6`; `src/test/resources/application-test.properties:3` |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` | Base/docker; test: `org.hibernate.dialect.H2Dialect` | `src/main/resources/application.properties:18`; `src/main/resources/application-docker.properties:14`; `src/test/resources/application-test.properties:8` |
| `spring.jpa.hibernate.ddl-auto` | `create` | Base/docker; test: `create-drop`; enum string | `src/main/resources/application.properties:19`; `src/main/resources/application-docker.properties:15`; `src/test/resources/application-test.properties:9` |
| `spring.jpa.show-sql` | `true` | Base/docker; test: `false`; boolean | `src/main/resources/application.properties:20`; `src/main/resources/application-docker.properties:16`; `src/test/resources/application-test.properties:10` |
| `spring.jpa.properties.hibernate.format_sql` | `true` | Base/docker; inherited by test; boolean | `src/main/resources/application.properties:21`; `src/main/resources/application-docker.properties:17` |
| `spring.servlet.multipart.max-file-size` | `10MB` | Base/docker; data-size value | `src/main/resources/application.properties:24`; `src/main/resources/application-docker.properties:26` |
| `spring.servlet.multipart.max-request-size` | `50MB` | Base/docker; data-size value | `src/main/resources/application.properties:25`; `src/main/resources/application-docker.properties:27` |
| `app.file-upload.max-file-size-bytes` | `10485760` | Base/docker/test; injected Java `long` | `src/main/resources/application.properties:28`; `src/main/resources/application-docker.properties:20,28`; `src/test/resources/application-test.properties:14`; `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:43` |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` | Base/docker/test; injected `String[]` | `src/main/resources/application.properties:29`; `src/main/resources/application-docker.properties:21,29`; `src/test/resources/application-test.properties:15`; `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:44` |
| `app.file-upload.max-files-per-upload` | `10` | Base/docker/test; integer-looking; no Java consumer found | `src/main/resources/application.properties:30`; `src/main/resources/application-docker.properties:22,30`; `src/test/resources/application-test.properties:16` |
| `app.file-upload.upload-path` | `target/test-uploads` | Test only; path string; no Java consumer found | `src/test/resources/application-test.properties:13` |
| `logging.level.com.photoalbum` | `DEBUG` | Docker: `INFO`; test: `DEBUG`; log-level string | `src/main/resources/application.properties:33`; `src/main/resources/application-docker.properties:33`; `src/test/resources/application-test.properties:19` |
| `logging.level.org.springframework.web` | `DEBUG` | Docker: `WARN`; test inherits base | `src/main/resources/application.properties:34`; `src/main/resources/application-docker.properties:34` |
| `logging.level.org.hibernate.SQL` | Not explicitly set in base | Docker: `DEBUG`; log-level string | `src/main/resources/application-docker.properties:35` |
| `app.admin.username` | `[MASKED]` code fallback; environment `APP_ADMIN_USERNAME` | All profiles; masked test override | `src/main/java/com/photoalbum/config/SecurityConfig.java:36`; `src/test/resources/application-test.properties:22`; `docker-compose.yml:35` |
| `app.admin.password` | `[MASKED]`; required, no code fallback; environment `APP_ADMIN_PASSWORD` | All profiles; masked test override | `src/main/java/com/photoalbum/config/SecurityConfig.java:37`; `src/test/resources/application-test.properties:23`; `docker-compose.yml:36` |

The two upload `@Value` expressions have no code fallback; values come from the property files (`src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:41-47`). The configured upload-count and test-path keys have no matching Java injection in the examined source; do not assume they are enforced runtime controls. No supported numeric range is declared for these custom properties.

### Environment and provisioning settings

| Property Key | Default | Profiles / Type | Source |
|---|---|---|---|
| `APP_USER`, `APP_USER_PASSWORD`, `ORACLE_PASSWORD` | Credential values `[MASKED]`; passwords required | Compose interpolation; `APP_USER` has a masked fallback; Oracle container environment | `.env.example:6-12`; `docker-compose.yml:7-9`; `oracle-init/create-user.sh:11-13` |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD` | Credential values `[MASKED]`; password required | Compose → application environment | `.env.example:16-17`; `docker-compose.yml:35-36` |
| `SPRING_DATASOURCE_URL` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` | Literal Compose application environment override | `docker-compose.yml:32` |
| `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD` | `[MASKED]` | Compose maps from `APP_USER`, `APP_USER_PASSWORD` | `docker-compose.yml:33-34` |
| `RESOURCE_GROUP` | `photo-album-resources-` plus randomized suffix | Azure script variable; exported to generated `.env` | `azure-setup.ps1:26-27,293` |
| `LOCATION` | `westus3` | Azure script variable; generated `.env` | `azure-setup.ps1:28,296` |
| `ACR_NAME` | `photoalbumacr` plus randomized number | Azure script variable; Basic SKU; admin access enabled | `azure-setup.ps1:29,69-74,294` |
| `POSTGRES_SERVER_NAME` | Resource-group name plus `-postgresql` | Azure script variable | `azure-setup.ps1:31` |
| `POSTGRES_DATABASE_NAME` | `photoalbum` | Azure script variable | `azure-setup.ps1:33,139-142` |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | `[MASKED]` | Optional environment inputs; username fallback and generated password otherwise | `azure-setup.ps1:38-39` |
| `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD` | `[MASKED]` | Optional environment inputs; username fallback and generated password otherwise | `azure-setup.ps1:40-41` |
| PostgreSQL version/storage/backup/public-access settings | `15`; `32` GiB; `7` days; `0.0.0.0` access selector | Azure CLI provisioning arguments; firewall rules also allow Azure services/current caller IP | `azure-setup.ps1:117-127,153-176` |
| `POSTGRES_SERVER` | Derived PostgreSQL server FQDN | Process environment and generated `.env` | `azure-setup.ps1:274,287` |
| `POSTGRES_USER`, `POSTGRES_PASSWORD` | `[MASKED]` | Process environment and generated `.env`; application credentials | `azure-setup.ps1:275-276,288-289` |
| `POSTGRES_CONNECTION_STRING` | `[MASKED]` | Process environment and generated `.env`; connection configuration location only | `azure-setup.ps1:267,277,290` |
| `AKS_CLUSTER_NAME` | Resource-group name plus `-aks` | Generated `.env` | `azure-setup.ps1:87,295` |

The Azure script writes PostgreSQL-oriented environment names, but current Spring configuration consumes `SPRING_DATASOURCE_*` and packages the Oracle driver. No `POSTGRES_*` → Spring binding, PostgreSQL JDBC dependency, or PostgreSQL runtime profile was found (`azure-setup.ps1:274-299`; `src/main/resources/application.properties:12-18`; `pom.xml:49-54`). These provisioning artifacts therefore do not establish that the current application is PostgreSQL-ready. Writing `.env` replaces its content rather than merging the Compose Oracle/admin settings (`azure-setup.ps1:285-299`).

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| Application container | `JAVA_OPTS="-Xmx512m -Xms256m"`; `java $JAVA_OPTS -jar app.jar`; Compose `SPRING_PROFILES_ACTIVE=docker`; port 8080 | JVM heap initial 256 MiB/max 512 MiB; no Compose memory/CPU limit | No explicit replica count; one service instance implied (`Dockerfile:25-31`; `docker-compose.yml:25-44`). |
| Oracle container | `gvenzl/oracle-free:latest`; host/container port 1521; named `oracle_data` volume; init scripts mounted | No executable Compose memory/CPU allocation. README recommends at least 4GB available RAM, not an enforced limit | No replicas/scaling configured (`docker-compose.yml:3-22,46-51`; `README.md:28-30,165-170`). |
| Azure AKS infrastructure | Node VM SKU `Standard_D8ds_v5`; SSH key generation requested | Node SKU selected, but no application pod requests/limits or JVM mapping provided | `--node-count 2`; no autoscaling arguments (`azure-setup.ps1:30,85-91`). |
| Azure PostgreSQL infrastructure | SKU `Standard_D4ads_v5`; storage 32 GiB; PostgreSQL 15 | SKU-level provisioning only; no application allocation | No HA/replica count explicitly configured (`azure-setup.ps1:32,117-127`). |
| Local application | `mvn spring-boot:run` or `java -jar target/photo-album-1.0.0.jar` | No documented JVM heap override | No scaling configured (`README.md:148-158`). |

No startup `-D` application system properties, Docker application health check, or application Kubernetes resource configuration was found. The Docker packaging flag `-DskipTests` is a build argument, not a runtime setting (`Dockerfile:14`). README Oracle XE resource-limit claims relate to its stale image description and should not be treated as limits for the current Compose image (`README.md:65-66,222`; `docker-compose.yml:4`).

## Startup Dependency Chain

1. **Compose interpolation → Oracle/application configuration:** resolve required `ORACLE_PASSWORD`, `APP_USER_PASSWORD`, and `APP_ADMIN_PASSWORD` before starting services. Missing/empty required inputs fail Compose interpolation (`docker-compose.yml:7-9,34-36`).
2. **Oracle container → database initialization:** mount `oracle-init` into `/container-entrypoint-initdb.d` and persist data in `oracle_data`. User creation/grant scripts consume credentials or expect the configured schema user; SQL grant/verification files retain a fixed user identifier and must stay aligned with `APP_USER` (`docker-compose.yml:12-14`; `oracle-init/01-create-user.sql:3-30`; `oracle-init/02-verify-user.sql:4-12`; `oracle-init/create-user.sh:11-44`).
3. **Application → waits for → healthy Oracle:** Compose uses `depends_on.oracle-db.condition=service_healthy`. Oracle runs the image-provided `healthcheck.sh` every 30s, timeout 10s, 15 retries, start period 180s. The separate `oracle-init/healthcheck.sql` is not the Compose health-check command (`docker-compose.yml:17-22,39-41`; `oracle-init/healthcheck.sql:1-3`).
4. **Application context → datasource and required admin/upload settings:** Boot starts the application and initializes configured beans; datasource/admin password inputs are required outside the test profile. The application container restarts on failure; no application-level readiness probe, custom datasource retry/backoff, or startup timeout is declared (`src/main/java/com/photoalbum/PhotoAlbumApplication.java:9-14`; `src/main/java/com/photoalbum/config/SecurityConfig.java:33-42`; `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:41-47`; `docker-compose.yml:44`).
5. **Azure script sequencing, separate from Compose:** existing Azure CLI authentication → resource group → registry → AKS → registry attachment → PostgreSQL → database/firewall → 30-second delay → user/grants → `.env`. This is infrastructure provisioning, not a checked-in application deployment/readiness chain (`azure-setup.ps1:45-58,69-105,117-197,207-299`).

The Oracle shell helper uses a fixed 30-second sleep rather than a readiness polling loop (`oracle-init/create-user.sh:15-17`). No config-server/discovery-server dependency exists in the inspected configuration.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrative credential | `[MASKED]`; `.env.example:6`; Compose environment (`docker-compose.yml:7`); shell reference (`oracle-init/create-user.sh:11,22`). |
| `APP_USER`, `APP_USER_PASSWORD` | Oracle application credentials | `[MASKED]`; `.env.example:9-12`; Compose and initialization references (`docker-compose.yml:8-9,33-34`; `oracle-init/create-user.sh:12-13,30`). |
| `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD`; `spring.datasource.username`, `spring.datasource.password` | Runtime datasource credentials | `[MASKED]`; environment binding and profile property locations (`src/main/resources/application.properties:13-14`; `src/main/resources/application-docker.properties:4-5`; `src/test/resources/application-test.properties:4-5`). |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD`; `app.admin.username`, `app.admin.password` | HTTP Basic administrator credentials | `[MASKED]`; Compose and Java injection; test-only values also masked (`docker-compose.yml:35-36`; `src/main/java/com/photoalbum/config/SecurityConfig.java:36-39`; `src/test/resources/application-test.properties:22-23`). |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | Azure PostgreSQL administrative credentials | `[MASKED]`; optional environment inputs/script-generated password, passed to Azure CLI (`azure-setup.ps1:38-39,121-122,209-210`). |
| `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD`; `POSTGRES_USER`, `POSTGRES_PASSWORD` | Azure PostgreSQL application credentials | `[MASKED]`; environment/script generation, database provisioning, then generated root `.env` (`azure-setup.ps1:40-41,212,275-276,288-289`). |
| `POSTGRES_CONNECTION_STRING` | Connection configuration | `[MASKED]`; environment and generated `.env` location (`azure-setup.ps1:277,290`). |
| AKS-generated SSH material | Infrastructure key | Values not inspected/reproduced; creation requested by CLI (`azure-setup.ps1:89`). |
| `secrets.GITHUB_TOKEN`, `secrets.COPILOT_ASSIGN_TOKEN` | Repository automation tokens | `[MASKED]`; GitHub Actions secret references, not application binding (`.github/workflows/squad-heartbeat.yml:254`; `.github/workflows/squad-issue-assign.yml:121`; `.github/workflows/squad-release.yml:31`; `.github/workflows/squad-promote.yml:24,77`). |
| `TRELLO_API_KEY`, `TRELLO_TOKEN` | Developer MCP integration credentials | `[MASKED]`; example MCP process environment (`.copilot/mcp-config.json:9-12`); unrelated to application startup. |

### Secrets Provisioning Workflow

- **Local/Compose:** operator copies `.env.example` to ignored `.env` and supplies credentials → Compose interpolation validates required password variables → Oracle receives its administrative/application credentials → the Java container receives datasource and administrator variables. Spring resolves datasource placeholders and relaxed environment binding for `app.admin.*` (`.env.example:1-17`; `.gitignore:201-204`; `docker-compose.yml:7-9,31-36`; `src/main/java/com/photoalbum/config/SecurityConfig.java:34-42`).
- **Oracle access:** the image creates the configured application user; checked-in SQL grants schema privileges and the shell helper can create the user through an administrative session. Fixed user identifiers in SQL are not dynamically driven by `APP_USER`; changing that environment variable alone does not update those scripts (`oracle-init/01-create-user.sql:3-30`; `oracle-init/create-user.sh:21-35`).
- **Application access:** administrator credentials create an in-memory user; BCrypt encoding is applied. This is application password hashing, not encryption of environment variables or `.env` (`src/main/java/com/photoalbum/config/SecurityConfig.java:28-42`).
- **Azure provisioning:** uses an already authenticated Azure CLI context; accepts environment-provided passwords or generates them with a cryptographic random-number generator. PostgreSQL administration creates/grants application access; the application password is exported and persisted in plaintext `.env`. The script's completion output also includes a password-bearing output location; no value is reproduced here (`azure-setup.ps1:15-22,38-45,207-257,274-299,319`).
- **Registry access:** provisioning enables the registry administrator and attaches ACR to AKS. No application Key Vault binding, explicit secret-specific managed-identity/RBAC role assignment, Jasypt encryption, sealed secret, or secret rotation procedure is declared (`azure-setup.ps1:69-74,102-105`; `pom.xml:30-100`).
- **Automation/developer tooling:** workflow tokens are obtained from GitHub secret references; example MCP credentials are process environment settings. Neither is evidence of a cloud application secret provisioning pipeline.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| Dedicated business feature flags | None found | No LaunchDarkly/Unleash/FeatureManagement dependency or application `@ConditionalOnProperty` / `@ConditionalOnExpression` was found in the inspected POM/Java source (`pom.xml:30-100`; `src/main/java/com/photoalbum/config/SecurityConfig.java:25-61`). |
| `spring.jpa.show-sql`, `spring.jpa.properties.hibernate.format_sql` | `true`; test disables `show-sql` | Diagnostic configuration, not rollout flags (`src/main/resources/application.properties:20-21`; `src/test/resources/application-test.properties:10`). |
| `server.servlet.encoding.enabled`, `server.servlet.encoding.force` | `true` | Servlet behavior booleans, not rollout flags (`src/main/resources/application.properties:6-7`). |
| Profile selection | Base unless activated | `SPRING_PROFILES_ACTIVE=docker` in Compose; `@ActiveProfiles("test")` for the context test. Profiles select configuration, not A/B cohorts (`docker-compose.yml:31`; `src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java:8`). |

Security switches are hardcoded: stateless sessions, HTTP Basic, and CSRF disabled; no property-controlled security toggle is exposed (`src/main/java/com/photoalbum/config/SecurityConfig.java:46-61`).

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Application artifact | `com.photoalbum:photo-album:1.0.0`, JAR | `pom.xml:15-18` |
| Spring Boot parent/starter line | `2.7.18` | `pom.xml:8-12` |
| Java target/source | `1.8` / `8` | `pom.xml:23-27` |
| Maven container build | `3.9.6`, Eclipse Temurin 8 | `Dockerfile:2` |
| Java runtime container | `eclipse-temurin:8-jre`; patch unpinned | `Dockerfile:17` |
| Oracle runtime container | `gvenzl/oracle-free:latest`; moving tag, exact version not pinned | `docker-compose.yml:2-4`; comment describes 23ai, not proof of resolved image version |
| Oracle JDBC | `com.oracle.database.jdbc:ojdbc8`; version inherited from Boot dependency management | `pom.xml:49-54` |
| Spring Framework, Spring Security, Hibernate/JPA, embedded servlet container, Thymeleaf, H2, JUnit | Versions inherited through Boot parent/starters; exact resolved versions not explicitly recorded in this inventory | `pom.xml:8-12,31-66,81-93` |
| Commons IO | `2.11.0` | `pom.xml:68-73` |
| Spring Boot DevTools | Parent-managed; optional dependency | `pom.xml:95-100` |
| Bootstrap frontend | `5.3.0`, CDN-loaded CSS/JavaScript | `src/main/resources/templates/index.html:7,124`; `src/main/resources/templates/detail.html:7,147`; `src/main/resources/templates/layout.html:7,42` |
| Azure PostgreSQL provisioning | Major version `15`; not the configured application datasource | `azure-setup.ps1:123`; `src/main/resources/application.properties:12-18` |
| Docker Compose, host Maven/JDK, Azure CLI, PowerShell, kubectl | No exact host-tool version pinned in inspected build/provisioning files | `docker-compose.yml:1`; `README.md:22,148-158`; `azure-setup.ps1:45-123`; `azure-reset.ps1:118` |

The README's Oracle 21c XE image/version does not match Compose's Oracle Free moving tag; executable configuration is the inventory's source of truth (`README.md:20,65-66`; `docker-compose.yml:4`). No build, deployment, dependency resolution, or runtime validation was performed for this documentation-only assessment.
