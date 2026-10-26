# Configuration & Externalized Settings Inventory

Three Spring property files define the base, Docker, and test settings, supplemented by Compose, an environment template, code-level property injection, and Azure provisioning scripts. Credentials are supplied through environment variables or test-only configuration; all credential values, including usernames and defaults, are redacted here.

> Static source inventory only. No application, provisioning script, build, or test was executed. File references are workspace-relative; line numbers identify evidence. External service state and effective dependency versions were not verified.

## Configuration Sources

| Source | Type | Path/Location | Notes |
| --- | --- | --- | --- |
| Base application settings | Spring properties | `src/main/resources/application.properties:1-34` | Default configuration; Oracle connection placeholders, HTTP encoding, logging, multipart and application upload settings. |
| Docker overrides | Spring profile properties | `src/main/resources/application-docker.properties:1-35` | Activated by Compose; repeats several base values and changes logging. Upload keys appear twice with identical values. |
| Test overrides | Spring profile properties | `src/test/resources/application-test.properties:1-23` | H2 and test-only credentials; activated by the context test. |
| Runtime environment template | dotenv template | `.env.example:1-17` | User-managed input for Compose interpolation. Actual `.env` contents are not inspected. `.env` and `.env.*` are ignored, except `.env.example` (`.gitignore:201-204`). |
| Service environment and orchestration | Docker Compose | `docker-compose.yml:1-51` | Two services, environment bindings, published ports, Oracle initialization volume, health gate, and persistent named volume. |
| Image build/runtime defaults | Dockerfile | `Dockerfile:1-31` | Maven build image, JRE runtime image, executable JAR, `JAVA_OPTS`, and container port. |
| Build and dependency configuration | Maven XML | `pom.xml:8-110` | Parent-managed versions, Java/compiler properties, dependencies, Spring Boot Maven plugin. |
| Code-level property consumers | Spring `@Value` | `src/main/java/com/photoalbum/config/SecurityConfig.java:28-42`; `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:43-44` | Administrator credential properties; upload size and MIME-type properties. |
| Oracle initialization | SQL and shell | `oracle-init/01-create-user.sql`, `02-verify-user.sql`, `create-user.sh`, `healthcheck.sql` | Mounted into database initialization directory. Shell consumes credential variables; SQL grants and verification target a fixed schema identity, redacted here. |
| Azure provisioning and generated environment | PowerShell / Azure CLI | `azure-setup.ps1:25-41,56-299` | Provisions ACR, AKS, and PostgreSQL; writes root `.env`. This is not an application deployment manifest. |
| Azure maintenance switches | PowerShell | `azure-reset.ps1:6-17` | Required resource-group argument and optional `Force`, `AcrOnly`, `AksOnly` switches; not application configuration. |
| Operational examples | Documentation | `README.md:26-30,142-158,170,222` | Local datasource override and launch commands; memory guidance. Documentation is not an automatically loaded property source. |
| Repository automation | GitHub Actions YAML | `.github/workflows/{squad-ci,squad-docs,squad-heartbeat,squad-insider-release,squad-issue-assign,squad-label-enforce,squad-preview,squad-promote,squad-release,squad-triage,sync-squad-labels}.yml` | Ancillary repository workflows, not Spring profiles or application secret provisioning. |
| Dependency-update policy | Dependabot YAML | `.github/dependabot.yml:1-11` | Weekly GitHub Actions updates, one grouped update pattern, seven-day cooldown. |
| Example developer tooling | MCP JSON | `.copilot/mcp-config.json` | `EXAMPLE-trello` server launched via `npx`; `TRELLO_API_KEY` and `TRELLO_TOKEN` entries are tooling-only credentials, redacted. |

No application `bootstrap.*`, YAML application files, Spring Cloud Config repository URI, remote configuration service, Vault/Key Vault integration, Kubernetes manifest, or ConfigMap/Secret binding was discovered in the inspected application and root deployment sources. Assessment outputs and skill/template files are not treated as active runtime configuration; `.github/agents` was not read.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
| --- | --- | --- | --- |
| Default Maven build; no explicit `<profiles>` | Normal Maven invocation | Compile/package the single `photo-album` JAR | Boot web, Thymeleaf, JPA, validation, security, JSON starters; runtime Oracle driver; Commons IO; test-scoped Boot test/H2; optional DevTools; Boot Maven plugin (`pom.xml:30-110`). |
| Docker build stage; not a Maven profile | Docker build or Compose build | Resolve dependencies and package JAR | `mvn dependency:go-offline -B`, then `mvn clean package -DskipTests` (`Dockerfile:8,14`). Test skipping is a build-system property, not runtime profile activation. |

Build properties: `java.version=1.8`, `maven.compiler.source=8`, `maven.compiler.target=8`, and `project.build.sourceEncoding=UTF-8` (`pom.xml:23-28`). No Gradle configuration or application JavaScript/TypeScript package manifest was discovered.

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
| --- | --- | --- | --- |
| Base/default | No explicit active profile required by repository settings | `src/main/resources/application.properties` | Oracle datasource; DEBUG application/web logging; base upload and HTTP settings. |
| `docker` | `SPRING_PROFILES_ACTIVE=docker` in Compose (`docker-compose.yml:31`) | Base + `application-docker.properties` | Application logging INFO, Spring web WARN, Hibernate SQL DEBUG; other listed properties largely repeat base values. |
| `test` | `@ActiveProfiles("test")` (`src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java:7-8`) | Base + test-classpath `application-test.properties` | H2 URL/driver/dialect; `create-drop`; SQL display disabled; test credential values redacted. |

No `spring.profiles.active` assignment in the property files, `@Profile` annotation, profile groups, or combined-profile activation was found. Docker and test profiles are independent; simultaneous activation and precedence between them are not explicitly configured.

## Properties Inventory

### Application module: Spring and code-bound settings

`B` = `src/main/resources/application.properties`; `D` = `src/main/resources/application-docker.properties`; `T` = `src/test/resources/application-test.properties`. Sources below use `file:line`. “Default” denotes repository configuration, not every framework-provided default.

| Property Key | Default | Profiles | Source |
| --- | --- | --- | --- |
| `server.port` | `8080` — integer TCP port; generally 1–65535 | Base; same in Docker; inherited by test | B:2; D:25 |
| `server.servlet.encoding.charset` | `UTF-8` — charset string | Base; same in Docker | B:5; D:9 |
| `server.servlet.encoding.enabled` | `true` — boolean | Base; same in Docker | B:6; D:10 |
| `server.servlet.encoding.force` | `true` — boolean | Base; same in Docker | B:7; D:11 |
| `spring.datasource.url` | `${SPRING_DATASOURCE_URL:jdbc:oracle:thin:@oracle-db:1521/FREEPDB1}` — JDBC string | Base/Docker; test `jdbc:h2:mem:testdb` | B:12; D:3; T:2 |
| `spring.datasource.username` | `SPRING_DATASOURCE_USERNAME`, fallback `[REDACTED]` | Base/Docker; test `[REDACTED]` | B:13; D:4; T:4 |
| `spring.datasource.password` | Required `SPRING_DATASOURCE_PASSWORD`; no placeholder fallback; value `[REDACTED]` | Base/Docker; test `[REDACTED]` | B:14; D:5; T:5 |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` — class name | Base/Docker; test `org.h2.Driver` | B:15; D:6; T:3 |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` — class name | Base/Docker; test `org.hibernate.dialect.H2Dialect` | B:18; D:14; T:8 |
| `spring.jpa.hibernate.ddl-auto` | `create` — string mode | Base/Docker; test `create-drop` | B:19; D:15; T:9 |
| `spring.jpa.show-sql` | `true` — boolean | Base/Docker; test `false` | B:20; D:16; T:10 |
| `spring.jpa.properties.hibernate.format_sql` | `true` — boolean | Base/Docker; inherited by test | B:21; D:17 |
| `spring.servlet.multipart.max-file-size` | `10MB` — data-size string | Base; same in Docker; inherited by test | B:24; D:26 |
| `spring.servlet.multipart.max-request-size` | `50MB` — data-size string | Base; same in Docker; inherited by test | B:25; D:27 |
| `app.file-upload.max-file-size-bytes` | `10485760` — injected Java `long`, bytes; no explicit property-binding range | Base/Docker/test | B:28; D:20,28; T:14; `PhotoServiceImpl.java:43` |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` — comma-delimited `String[]` | Base/Docker/test | B:29; D:21,29; T:15; `PhotoServiceImpl.java:44` |
| `app.file-upload.max-files-per-upload` | `10` — integer-like configuration value | Base/Docker/test | B:30; D:22,30; T:16; no Java consumer found |
| `app.file-upload.upload-path` | No base value; test `target/test-uploads` — path string | Test only | T:13; no Java consumer found |
| `logging.level.com.photoalbum` | `DEBUG` — log-level string | Docker `INFO`; test `DEBUG` | B:33; D:33; T:19 |
| `logging.level.org.springframework.web` | `DEBUG` — log-level string | Docker `WARN`; inherited base in test | B:34; D:34 |
| `logging.level.org.hibernate.SQL` | Not set in base | Docker `DEBUG` | D:35 |
| `app.admin.username` | Code fallback `[REDACTED]`; environment form `APP_ADMIN_USERNAME` | Compose supplies value; test explicit `[REDACTED]` | `SecurityConfig.java:36`; `docker-compose.yml:35`; T:22 |
| `app.admin.password` | Required property, no code fallback; environment form `APP_ADMIN_PASSWORD`; `[REDACTED]` | Compose requires value; test explicit `[REDACTED]` | `SecurityConfig.java:37`; `docker-compose.yml:36`; T:23 |

Property resolution: Compose reads shell/`.env` interpolation inputs and supplies container environment variables; Spring then loads base/profile files and resolves placeholders against its environment. For these settings, Spring command-line arguments and Java system properties can override environment/file values through standard Boot precedence. `.env` is not automatically loaded by a standalone Spring process. `APP_ADMIN_*` binds through Spring’s relaxed environment lookup to `app.admin.*`; no dotenv loader is declared.

### Environment and infrastructure settings

| Property Key | Default | Profiles | Source |
| --- | --- | --- | --- |
| `ORACLE_PASSWORD` | Required Compose `:?` input; `[REDACTED]` | Oracle container; shell initialization | `.env.example:6`; `docker-compose.yml:7`; `oracle-init/create-user.sh:11` |
| `APP_USER` | Credential identity default `[REDACTED]` | Database `APP_USER`; application `SPRING_DATASOURCE_USERNAME` | `.env.example:9`; `docker-compose.yml:8,33`; `oracle-init/create-user.sh:12` |
| `APP_USER_PASSWORD` | Required Compose/shell input; `[REDACTED]` | Database initialization; mapped to application datasource password | `.env.example:12`; `docker-compose.yml:9,34`; `oracle-init/create-user.sh:13` |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD` | Identity fallback `[REDACTED]`; password required `[REDACTED]` | Compose application | `.env.example:16-17`; `docker-compose.yml:35-36` |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | Optional process-environment inputs; identity fallback `[REDACTED]`; password generated if absent | Azure provisioning only | `azure-setup.ps1:38-39` |
| `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD` | Optional process-environment inputs; identity fallback `[REDACTED]`; password generated if absent | Azure provisioning only | `azure-setup.ps1:40-41` |
| `POSTGRES_SERVER` | Generated server FQDN | Azure-generated `.env` | `azure-setup.ps1:274,287` |
| `POSTGRES_USER`, `POSTGRES_PASSWORD` | Derived application credentials `[REDACTED]` | Azure-generated `.env` | `azure-setup.ps1:275-276,288-289` |
| `POSTGRES_CONNECTION_STRING` | `jdbc:postgresql://${SERVER_FQDN}:5432/${POSTGRES_DATABASE_NAME}`; script-variable interpolation, not Spring placeholder | Azure-generated `.env` | `azure-setup.ps1:267,277,290` |
| `RESOURCE_GROUP` | Generated `photo-album-resources-` plus random suffix | Azure script; persisted to `.env` | `azure-setup.ps1:26-27,293` |
| `ACR_NAME` | Generated `photoalbumacr` plus random number; ACR SKU `Basic` | Azure script; name persisted to `.env` | `azure-setup.ps1:29,69-74,294` |
| `AKS_CLUSTER_NAME` | Resource-group name plus `-aks` | Azure-generated `.env` | `azure-setup.ps1:87,295` |
| `LOCATION` | `westus3` | Azure script / generated `.env` | `azure-setup.ps1:28,296` |
| `POSTGRES_SERVER_NAME`, `POSTGRES_DATABASE_NAME` | Resource-group name plus `-postgresql`; database `photoalbum` | Azure script variables | `azure-setup.ps1:31,33` |
| PostgreSQL create options | Version `15`; storage size `32` GiB; backup retention `7` days; public-access argument `0.0.0.0` | Azure provisioning | `azure-setup.ps1:117-127` |
| PostgreSQL firewall | Azure-services rule start/end `0.0.0.0`; additional rule uses caller public IP obtained from `https://api.ipify.org` | Azure provisioning | `azure-setup.ps1:150-180` |
| Oracle persistence/init locations | `oracle_data:/opt/oracle/oradata`; `./oracle-init:/container-entrypoint-initdb.d` | Compose database | `docker-compose.yml:12-14,46-47` |
| Container networking | Bridge network `photoalbum-network`; published mappings `1521:1521`, `8080:8080` | Compose | `docker-compose.yml:10-11,37-38,49-51` |

The PostgreSQL script outputs `POSTGRES_*`, but no inspected application properties or Compose bindings consume those names. The POM declares an Oracle driver and no PostgreSQL driver (`pom.xml:49-54`); there is no PostgreSQL runtime profile. Thus the provisioning script and current application configuration are not an end-to-end PostgreSQL deployment configuration. Generated Azure `.env` also does not supply Compose’s required Oracle and application-admin passwords.

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
| --- | --- | --- | --- |
| `photoalbum-java-app` | `java $JAVA_OPTS -jar app.jar`; image default `JAVA_OPTS="-Xmx512m -Xms256m"`; Compose `SPRING_PROFILES_ACTIVE=docker` and datasource/admin environment bindings | JVM initial heap 256 MiB, maximum heap 512 MiB; no container memory/CPU requests or limits | No explicit replica/scaling setting; one service definition, fixed container name, `restart: on-failure` |
| `oracle-db` | Image default startup; required credential environment and mounted initialization scripts | No enforced Compose CPU/memory limits; README recommends at least 4 GB available for Oracle (`README.md:30`) | No explicit scaling setting; one service definition with fixed container name |
| Local application launch | `mvn spring-boot:run` or `java -jar target/photo-album-1.0.0.jar` (`README.md:148,155-158`) | No local JVM heap defaults documented | Not specified |
| Azure AKS infrastructure | `Standard_D8ds_v5` node SKU; generated SSH keys (`azure-setup.ps1:30,85-91`) | No application pod requests/limits or heap settings; node SKU is not a per-service allocation | Explicit `--node-count 2`; no autoscaler configuration found |
| Azure PostgreSQL infrastructure | `Standard_D4ads_v5` server SKU (`azure-setup.ps1:32,124`) | No application/JVM allocation; storage is listed separately above | No application replica configuration |

No application startup `-D` system properties are declared in the Docker entrypoint. Docker build `-DskipTests` is not a runtime option. The configured JVM heap cannot be compared to a declared application-container memory ceiling because none is present. README’s Oracle XE capacity notes (`README.md:222`) are documentation, not limits enforced on the current Compose image.

## Startup Dependency Chain

1. **Compose interpolation → required environment inputs:** `ORACLE_PASSWORD`, `APP_USER_PASSWORD`, and `APP_ADMIN_PASSWORD` use required-value interpolation; missing inputs prevent a normal Compose launch (`docker-compose.yml:7,9,36`). These are configuration gates, not service-readiness probes.
2. **Oracle container → initialization scripts:** the initialization directory is mounted into the image’s startup hook location. `create-user.sh` validates required credential variables and sleeps 30 seconds before issuing SQL; this is a fixed delay, not a retry/readiness loop (`oracle-init/create-user.sh:9-22`). The numbered SQL scripts configure/verify a fixed schema identity; custom `APP_USER` values are not consistently reflected in those SQL files (`oracle-init/01-create-user.sql:14-30`; `02-verify-user.sql:4-12`).
3. **Application → waits for → healthy Oracle:** Compose `depends_on.oracle-db.condition=service_healthy` gates application startup (`docker-compose.yml:39-41`). The actual probe is the image-provided `healthcheck.sh`, interval 30 seconds, timeout 10 seconds, 15 retries, start period 180 seconds (`docker-compose.yml:17-22`). The mounted `oracle-init/healthcheck.sql` contains `SELECT 1 FROM DUAL`, but Compose does not explicitly reference it.
4. **Application context → datasource/admin configuration:** Oracle datasource configuration and the required `app.admin.password` property must be available. Test startup substitutes H2/test properties. No application-container healthcheck, custom startup timeout, application readiness probe, config-server retry, discovery dependency, or TCP-wait utility is configured in the inspected sources.
5. **Azure script sequence, separate from Compose:** existing Azure CLI login/subscription → resource group → ACR → AKS → ACR attachment → PostgreSQL server/database/firewall → server FQDN lookup → fixed 30-second wait → role/grant operations → generated `.env` (`azure-setup.ps1:43-299`). No application deployment/readiness gate is present in this script; successful infrastructure creation is not evidence that the application is running.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
| --- | --- | --- |
| `ORACLE_PASSWORD` | Database administrator password | Environment / user-managed `.env` → Oracle container and initialization shell; `[REDACTED]` |
| `APP_USER`, `APP_USER_PASSWORD` | Application database identity/password | Environment / `.env` → Oracle container; mapped to application datasource variables; `[REDACTED]` |
| `spring.datasource.username`, `spring.datasource.password` / `SPRING_DATASOURCE_*` | JDBC credentials | Placeholder references; test values in `application-test.properties:4-5`; all values `[REDACTED]` |
| `app.admin.username`, `app.admin.password` / `APP_ADMIN_*` | Application Basic-auth administrator credentials | Environment → Spring code injection; test values in test properties; `[REDACTED]` |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | Azure PostgreSQL administrative identity/password | Provisioning process inputs or generated password, passed to Azure CLI; `[REDACTED]` |
| `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD` → `POSTGRES_USER`, `POSTGRES_PASSWORD` | Azure PostgreSQL application identity/password | Process variables → generated root `.env`; `[REDACTED]` |
| `POSTGRES_CONNECTION_STRING` | Database connection configuration | Generated JDBC URL contains host/database, not embedded credentials in this script (`azure-setup.ps1:267`); separate credential fields remain `[REDACTED]` |
| `TRELLO_API_KEY`, `TRELLO_TOKEN` | Ancillary developer-tool credentials | `.copilot/mcp-config.json` environment entries; `[REDACTED]`; not application inputs |
| `GITHUB_TOKEN`, `COPILOT_ASSIGN_TOKEN` | Repository automation tokens | GitHub Actions secret references in heartbeat, issue assignment, promotion, and release workflows; `[REDACTED]`; not application credentials |

### Secrets Provisioning Workflow

- **Local Compose:** operator copies `.env.example` to ignored `.env` and provides required passwords → Compose substitutes inputs → Oracle receives administrator/application credentials → initialization creates/configures the schema → application receives datasource and admin credentials through its environment. No secret-store fetch or application managed-identity authentication is configured (`.env.example:1-17`; `docker-compose.yml:6-9,30-36`).
- **Application security:** Spring injects `app.admin.*`; the configured password is BCrypt-encoded for an in-memory user store (`SecurityConfig.java:28-42`). BCrypt is password hashing, not encryption of `.env` or environment values. The test profile supplies its own redacted credentials.
- **Azure provisioning:** caller must already have Azure CLI access; the script checks the active account (`azure-setup.ps1:43-50`). PostgreSQL administrator/application passwords come from optional process environment variables or a cryptographic-RNG helper with default length 24 (`azure-setup.ps1:15-22,38-41`). Administrative credentials are passed to Azure CLI for provisioning/SQL; application credentials are persisted in plaintext to ignored `.env` (`azure-setup.ps1:117-127,203-257,274-299`). AKS is attached to ACR for image-pull access (`azure-setup.ps1:99-105`); this is not a database secret-binding mechanism. No Kubernetes Secret creation, Key Vault binding, database managed-identity setup, or application deployment is shown.
- **Automation/tooling:** GitHub workflow tokens support repository operations; the example MCP token entries belong to developer tooling. Neither is shown supplying runtime application credentials.
- **Storage/access limitations:** git-ignore protection is present, but no explicit `.env` permission hardening, secret rotation, encrypted property mechanism, or cloud secret-manager policy is configured in the inspected provisioning/runtime files. The Azure script writes `.env` rather than merging with the Oracle template, so local Compose secrets are not preserved by that generation step.

## Feature Flags

| Flag Name | Default | Controlled By |
| --- | --- | --- |
| Dedicated feature-flag system | None discovered | No LaunchDarkly, Unleash, feature-management dependency, `@ConditionalOnProperty`, or `@ConditionalOnExpression` found in application sources/POM. |
| `server.servlet.encoding.enabled`, `server.servlet.encoding.force` | `true` | Base/Docker properties; framework switches, not business feature flags. |
| `spring.jpa.show-sql`, `spring.jpa.properties.hibernate.format_sql` | `true`; test overrides show-SQL to `false` | Profile properties; diagnostic switches. |
| Runtime profile selection | Compose `docker`; tests `test` | Environment / test annotation; environment selection, not gradual rollout. |
| `Force`, `AcrOnly`, `AksOnly` | Switches absent unless supplied | `azure-reset.ps1:6-17`; maintenance-script switches only. |

No A/B-testing configuration or gradual rollout percentage was found. Upload limits/MIME settings are configuration parameters, not feature flags; no Java binding for `max-files-per-upload` or test `upload-path` was found.

## Framework & Runtime Versions

| Component | Version | Source |
| --- | --- | --- |
| Application artifact | `com.photoalbum:photo-album:1.0.0`, JAR | `pom.xml:15-18` |
| Spring Boot parent | `2.7.18` | `pom.xml:8-12` |
| Java target/compiler | Java 8 (`java.version=1.8`, source/target `8`) | `pom.xml:23-27` |
| Build image / Maven | `maven:3.9.6-eclipse-temurin-8` / Maven `3.9.6` | `Dockerfile:2`; local Maven version not pinned |
| Runtime image | `eclipse-temurin:8-jre` | `Dockerfile:17`; patch/digest not pinned |
| Oracle container | `gvenzl/oracle-free:latest` | `docker-compose.yml:4`; comment names Free 23ai, but mutable `latest` does not verify an installed release |
| Oracle JDBC | `com.oracle.database.jdbc:ojdbc8`, runtime scope; version parent-managed | `pom.xml:49-54`; resolved version not established |
| Spring web/Thymeleaf/JPA/validation/security/JSON starters | Boot parent-managed; no individual version pins | `pom.xml:30-66,75-79` |
| Hibernate ORM, Spring Framework/Security, embedded servlet container, Thymeleaf | Transitive/parent-managed; effective versions not resolved | Starter declarations in `pom.xml`; no dependency-resolution command run |
| Commons IO | `2.11.0` | `pom.xml:68-73` |
| Boot test / H2 | Test scope; parent-managed versions | `pom.xml:81-93` |
| Spring Boot DevTools | Optional; parent-managed version | `pom.xml:95-100` |
| Spring Boot Maven plugin | Parent-managed; no local explicit version | `pom.xml:103-109` |
| Azure PostgreSQL requested server version | `15` | `azure-setup.ps1:123`; script intent, not verified deployed state |
| Docker / Docker Compose | Not pinned | `README.md:28-29`; Dockerfile/Compose file supply no installed CLI version |
| PowerShell / Azure CLI | Not pinned | `azure-setup.ps1:1,45`; no minimum version check found |
| Ancillary GitHub Actions | Checkout comment `v4.4.0`; github-script comment `v7.1.0`, both SHA-pinned | `.github/workflows/squad-heartbeat.yml:27,30` and other workflows |

> Note: Runtime versions, external infrastructure state, effective parent-managed dependency versions, and actual operator-provided configuration could not be fully identified from static repository evidence.
