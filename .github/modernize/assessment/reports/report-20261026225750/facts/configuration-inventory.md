# Configuration & Externalized Settings Inventory

Configuration consists of three Spring property files, two explicit runtime profiles, container/build configuration, an environment template, and separate Azure provisioning scripts. Secrets are supplied through environment variables or generated into an ignored `.env` file; all sensitive values and credential defaults below are `[REDACTED]`.

## Configuration Sources

Paths and line references are relative to the workspace root.

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Base application settings | Spring properties | `src/main/resources/application.properties:1-34` | Common settings and environment-backed datasource properties. |
| Docker overrides | Spring profile properties | `src/main/resources/application-docker.properties:1-35` | Database, logging, encoding, and upload settings; three upload properties appear twice with identical values. |
| Test overrides | Spring profile properties | `src/test/resources/application-test.properties:1-23` | H2, test credentials `[REDACTED]`, logging, and upload settings. |
| Local environment template | Compose interpolation input | `.env.example:1-17` | Copy to `.env`; contains database and administrator credential placeholders `[REDACTED]`. `.env` and `.env.*` are ignored, except the example (`.gitignore:201-204`). Actual `.env` contents were not inspected. |
| Container services | Docker Compose | `docker-compose.yml:1-51` | Oracle environment, application environment overrides, ports, storage, network, startup health gate. |
| Build and runtime image | Dockerfile | `Dockerfile:1-31` | Maven build stage, Java runtime stage, heap options, executable JAR. |
| Build settings | Maven XML | `pom.xml:8-28,30-110` | Parent-managed dependencies, compiler properties, packaging plugin. |
| Code-defined configuration | Spring Java configuration | `src/main/java/com/photoalbum/config/SecurityConfig.java:25-61` | Administrator property injection and security beans; not profile-specific. |
| Code property consumers | Spring `@Value` | `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:38-47` | Two upload properties injected without inline defaults. |
| Database initialization | Shell and SQL | `oracle-init/create-user.sh:1-47`; `oracle-init/01-create-user.sql:1-35`; `oracle-init/02-verify-user.sql:1-14`; `oracle-init/healthcheck.sql:1-3` | Environment-based user setup, fixed-schema grants, verification, standalone SQL check. Mounted by Compose. |
| Azure provisioning | PowerShell | `azure-setup.ps1:26-41,56-127,274-299` | Resource settings and generated PostgreSQL `.env`; separate from checked-in Oracle runtime settings. |
| Azure maintenance | PowerShell parameters | `azure-reset.ps1:6-18` | Resource-group input and cleanup switches; not an application runtime configuration source. |
| Frontend constants | JavaScript and template | `src/main/resources/static/js/upload.js:68-69`; `src/main/resources/templates/layout.html:7,42` | Fixed frontend upload settings and Bootstrap CDN version; not externalized. |
| CI automation | GitHub Actions | `.github/workflows/squad-ci.yml:19-27`; `.github/workflows/squad-release.yml:19-31`; `.github/workflows/squad-heartbeat.yml:254` | Build-command templates and automation secret references, not application property providers. |
| Tooling-only example | MCP JSON | `.copilot/mcp-config.json:1-15` | Example Trello tool command and two sensitive environment slots `[REDACTED]`; not read by Spring. |

No application `bootstrap.*`, external configuration repository, Spring Cloud Config, Azure App Configuration, Vault, Key Vault, Kubernetes ConfigMap/Secret manifest, or Gradle configuration was found in the inspected application/deployment sources. Tooling and assessment artifacts are not treated as application configuration.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Default Maven build; no named profiles | Ordinary Maven invocation; no `<profiles>` block | Java 8 JAR compilation and packaging | Spring Boot Maven plugin; web, Thymeleaf, JPA, validation, security, JSON, Oracle JDBC, Commons IO; test-scoped Boot test and H2; optional DevTools (`pom.xml:18-110`). |
| Container build mode, not a Maven profile | Docker build executes `mvn clean package -DskipTests` | Package without running tests | Same Maven dependency/plugin set; prior `dependency:go-offline -B` step (`Dockerfile:6-14`). |

Build properties: `java.version=1.8`, `maven.compiler.source=8`, `maven.compiler.target=8`, and `project.build.sourceEncoding=UTF-8` (`pom.xml:23-28`). The checked-in CI build step contains TODO/example commands rather than an implemented Java build (`.github/workflows/squad-ci.yml:19-27`).

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Unprofiled base | No active profile explicitly set in base properties or application entry point | `src/main/resources/application.properties` | Oracle settings, port 8080, DEBUG application/web logging (`application.properties:2-34`; `src/main/java/com/photoalbum/PhotoAlbumApplication.java:9-14`). |
| `docker` | Compose sets `SPRING_PROFILES_ACTIVE=docker` | Base plus `src/main/resources/application-docker.properties` | Application INFO, web WARN, Hibernate SQL DEBUG; repeated common settings (`docker-compose.yml:30-36`; Docker properties:3-35). |
| `test` | `@ActiveProfiles("test")` on context test | Base plus `src/test/resources/application-test.properties` on test classpath | H2 driver/dialect, `create-drop`, SQL logging off, test credential entries `[REDACTED]`, test upload path (`src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java:7-8`; test properties:2-23). |

No custom `@Profile` beans, combined-profile activation, or additional profile-specific application files were found in `src`. The Azure provisioning script does not establish a Spring runtime profile.

## Properties Inventory

### Spring application

`Base`, `Docker`, and `Test` below refer to the three property files listed above. Types are inferred from Spring conventions and constructor parameters; ranges are not custom-validated configuration constraints in the inspected code.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | `8080` (integer TCP port) | Base; Docker repeats | Base:2; Docker:25 |
| `server.servlet.encoding.charset` | `UTF-8` (string) | Base; Docker repeats | Base:5; Docker:9 |
| `server.servlet.encoding.enabled` | `true` (boolean) | Base; Docker repeats | Base:6; Docker:10 |
| `server.servlet.encoding.force` | `true` (boolean) | Base; Docker repeats | Base:7; Docker:11 |
| `spring.datasource.url` | `[REDACTED]` (connection string); `SPRING_DATASOURCE_URL` placeholder has a fallback `[REDACTED]` | Base/Docker environment-backed; Test literal `[REDACTED]` | Base:12; Docker:3; Test:2 |
| `spring.datasource.username` | `[REDACTED]`; `SPRING_DATASOURCE_USERNAME` placeholder has fallback `[REDACTED]` | Base/Docker; Test override `[REDACTED]` | Base:13; Docker:4; Test:4 |
| `spring.datasource.password` | `[REDACTED]`; required `SPRING_DATASOURCE_PASSWORD` placeholder, no fallback | Base/Docker; Test explicit value `[REDACTED]` | Base:14; Docker:5; Test:5 |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` (class name) | Base/Docker; Test `org.h2.Driver` | Base:15; Docker:6; Test:3 |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` | Base/Docker; Test `org.hibernate.dialect.H2Dialect` | Base:18; Docker:14; Test:8 |
| `spring.jpa.hibernate.ddl-auto` | `create` (enum string) | Base/Docker; Test `create-drop` | Base:19; Docker:15; Test:9 |
| `spring.jpa.show-sql` | `true` (boolean) | Base/Docker; Test `false` | Base:20; Docker:16; Test:10 |
| `spring.jpa.properties.hibernate.format_sql` | `true` (boolean) | Base/Docker; inherited by Test | Base:21; Docker:17 |
| `spring.servlet.multipart.max-file-size` | `10MB` (data size) | Base/Docker; inherited by Test | Base:24; Docker:26 |
| `spring.servlet.multipart.max-request-size` | `50MB` (data size) | Base/Docker; inherited by Test | Base:25; Docker:27 |
| `app.file-upload.max-file-size-bytes` | `10485760` (long bytes) | Base/Docker/Test | Base:28; Docker:20,28; Test:14; injection: `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:41-47` |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` (comma-separated string array) | Base/Docker/Test | Base:29; Docker:21,29; Test:15; injection: service implementation:43-47 |
| `app.file-upload.max-files-per-upload` | `10` (integer) | Base/Docker/Test | Base:30; Docker:22,30; Test:16; no matching Java property consumer found |
| `app.file-upload.upload-path` | Not set in Base | Test: `target/test-uploads` (path string) | Test:13; no matching Java property consumer found |
| `logging.level.com.photoalbum` | `DEBUG` (log-level enum) | Docker `INFO`; Test `DEBUG` | Base:33; Docker:33; Test:19 |
| `logging.level.org.springframework.web` | `DEBUG` | Docker `WARN`; Test inherits Base | Base:34; Docker:34 |
| `logging.level.org.hibernate.SQL` | Not explicitly set in Base | Docker `DEBUG` | Docker:35 |
| `app.admin.username` | Inline credential default `[REDACTED]`; environment binding `APP_ADMIN_USERNAME` | All runtime modes; Test explicit `[REDACTED]` | `src/main/java/com/photoalbum/config/SecurityConfig.java:34-37`; Test:22; Compose:35 |
| `app.admin.password` | Required property, no inline fallback; environment binding `APP_ADMIN_PASSWORD` | All runtime modes; Test explicit `[REDACTED]` | Security configuration:34-37; Test:23; Compose:36 |

**Resolution chain:** Compose interpolates process environment/`.env` into its service environment first (`docker-compose.yml:6-9,30-36`; `.env.example:1-3`). Spring then resolves external environment properties and `${...}` placeholders against its environment; profile-specific packaged properties override base packaged properties. Security properties use Spring's environment binding and `@Value`, not an application `.env` reader. The executable passes arguments through standard `SpringApplication.run` (`src/main/java/com/photoalbum/PhotoAlbumApplication.java:12-13`); no custom property loader was found.

### Container and provisioning settings

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `ORACLE_PASSWORD` | `[REDACTED]`; Compose requires a value | Oracle container environment | `.env.example:6`; `docker-compose.yml:7`; `oracle-init/create-user.sh:11` |
| `APP_USER` | Credential default `[REDACTED]` | Oracle environment; also mapped to application datasource username | `.env.example:9`; Compose:8,33; initializer:12 |
| `APP_USER_PASSWORD` | `[REDACTED]`; Compose requires a value | Oracle environment; also mapped to application datasource password | `.env.example:12`; Compose:9,34; initializer:13 |
| `SPRING_DATASOURCE_URL` | `[REDACTED]` (connection string) | Application container | Compose:32 |
| `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD` | `[REDACTED]`; sourced respectively from `APP_USER`, `APP_USER_PASSWORD` | Application container | Compose:33-34 |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD` | `[REDACTED]`; required Compose inputs | Application container | `.env.example:16-17`; Compose:35-36 |
| Oracle host/container port | `1521:1521` | Compose | Compose:10-11 |
| Application host/container port | `8080:8080` | Compose | Compose:37-38 |
| Oracle data/init mounts | `oracle_data:/opt/oracle/oradata`; `./oracle-init:/container-entrypoint-initdb.d` | Compose | Compose:12-14,46-47 |
| Network driver | `bridge` for `photoalbum-network` | Compose | Compose:49-51 |
| Application restart policy | `on-failure` | Compose | Compose:44 |
| Azure `$RESOURCE_GROUP` | `photo-album-resources-` plus generated suffix | Provisioning script only | `azure-setup.ps1:26-27` |
| Azure `$LOCATION` | `westus3` | Provisioning script; written as `LOCATION` | Setup:28,296 |
| Azure `$ACR_NAME` | `photoalbumacr` plus generated number | Provisioning script; written as `ACR_NAME` | Setup:29,294 |
| Azure registry SKU/admin mode | `Basic`; admin enabled | Provisioning script | Setup:69-74 |
| Azure `$POSTGRES_SERVER_NAME` | Derived from resource-group name with `-postgresql` suffix | Provisioning script | Setup:31 |
| Azure `$POSTGRES_DATABASE_NAME` | `photoalbum` | Provisioning script | Setup:33,139-143 |
| `POSTGRES_ADMIN_USER`, `POSTGRES_APP_USER` | Environment inputs with credential defaults `[REDACTED]` | Provisioning process | Setup:38,40 |
| `POSTGRES_ADMIN_PASSWORD`, `POSTGRES_APP_PASSWORD` | Environment input or generated value `[REDACTED]` | Provisioning process | Setup:15-22,39,41 |
| Generated `POSTGRES_SERVER` | Derived Azure PostgreSQL hostname | `.env` output | Setup:274,287 |
| Generated `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_CONNECTION_STRING` | `[REDACTED]` | `.env` output; no binding to checked-in Spring datasource placeholders found | Setup:275-277,288-290 |
| Generated `RESOURCE_GROUP`, `AKS_CLUSTER_NAME` | Derived resource names | `.env` output | Setup:293,295 |
| PostgreSQL storage/backup/public-access inputs | `32` GiB; `7` days; `0.0.0.0` public-access argument | Provisioning script | Setup:125-127 |
| Reset script inputs | `ResourceGroupName` required string; `Force`, `AcrOnly`, `AksOnly` switches | Maintenance execution only | `azure-reset.ps1:6-18` |

The Azure script provisions PostgreSQL, but the committed application uses the Oracle driver and dialect, and `pom.xml:30-101` does not declare a PostgreSQL driver. Its generated `POSTGRES_*` names are not the application's `SPRING_DATASOURCE_*` contract; the provisioning script is not evidence of a working PostgreSQL runtime configuration.

Frontend settings are fixed separately at `10 * 1024 * 1024` bytes and the same four MIME types (`src/main/resources/static/js/upload.js:68-69`); they do not dynamically consume Spring properties. Backend image-size code constants are not externalized settings and are outside this property inventory.

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| Application container | `java $JAVA_OPTS -jar app.jar`; `JAVA_OPTS="-Xmx512m -Xms256m"`; `SPRING_PROFILES_ACTIVE=docker` | Initial heap 256 MiB, maximum heap 512 MiB; no container memory/CPU limit declared | One service container in checked-in Compose; no scaling policy (`Dockerfile:25-31`; `docker-compose.yml:24-44`). |
| Local executable JAR | README uses `java -jar target/photo-album-1.0.0.jar`; no explicit JVM system properties | Not specified | Not specified (`README.md:155-158`). |
| Oracle container | Image entry point; credential environment `[REDACTED]` | No Compose memory/CPU limits; README recommends at least 4 GB available for database container | One service container; no scaling policy (`docker-compose.yml:3-22`; `README.md:28-30`). |
| Azure AKS infrastructure | Node VM size `Standard_D8ds_v5`; SSH key generation requested | VM SKU specified; no workload requests/limits or application JVM mapping supplied | Two nodes, not two application replicas; no application replica/autoscaler definition (`azure-setup.ps1:30,85-91`). |
| Azure PostgreSQL infrastructure | PostgreSQL 15, SKU `Standard_D4ads_v5` | SKU-based allocation; storage 32 GiB; no application heap mapping | One server creation; no HA/replica option in command (`azure-setup.ps1:32,117-127`). |

No startup `-D` application system properties, Kubernetes workload resource allocations, or readiness/liveness probes were found. Docker build `-DskipTests` is a build option, not a runtime system property. No runtime was started to validate resource sufficiency.

## Startup Dependency Chain

1. **Compose interpolation → required environment inputs:** Oracle and application administrator secrets must be supplied before containers can be created (`docker-compose.yml:6-9,30-36`). Values remain `[REDACTED]`.
2. **Oracle container → initialization scripts:** Compose mounts `oracle-init` into the image initialization directory and persists database files. The shell initializer checks required variables and waits a fixed 30 seconds before its SQL work (`docker-compose.yml:12-14`; `oracle-init/create-user.sh:9-22`). The image also receives application-user environment variables (`docker-compose.yml:8-9`).
3. **Application container → waits for Oracle healthy:** `depends_on` uses `condition: service_healthy`. Oracle runs the image-provided `healthcheck.sh` every 30 seconds, with a 10-second timeout, 15 retries, and 180-second start period (`docker-compose.yml:17-22,39-41`). These are health-check parameters, not a single declared overall startup timeout.
4. **Spring context → datasource and required administrator property:** Base/Docker datasource password placeholder and code-injected administrator password have no fallback (`src/main/resources/application.properties:14`; `src/main/resources/application-docker.properties:5`; `src/main/java/com/photoalbum/config/SecurityConfig.java:34-37`). No config-server/discovery-server stage, application health check, custom startup retry, or wait-for-TCP wrapper is defined.
5. **Azure script, separate provisioning chain:** Existing Azure CLI login → resource group → ACR → AKS → ACR attachment → PostgreSQL → database/firewall configuration → 30-second fixed wait → SQL initialization → `.env` output (`azure-setup.ps1:43-58,69-127,139-197,207-299`). No application deployment/readiness stage is established by these provisioning operations.

`oracle-init/healthcheck.sql:1-3` is a standalone SQL check; Compose invokes `healthcheck.sh`, not this SQL file directly. SQL grant/verification files contain fixed schema identifiers while the shell initializer accepts `APP_USER`; changing that credential input does not automatically parameterize all SQL scripts (`oracle-init/01-create-user.sql:15-30`; `oracle-init/02-verify-user.sql:5-12`).

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrative password | Environment/ignored `.env`: `[REDACTED]` (`.env.example:6`; Compose:7). |
| `APP_USER`, `APP_USER_PASSWORD` | Database application credentials | Environment/ignored `.env`; credential defaults/placeholders `[REDACTED]` (`.env.example:9-12`; Compose:8-9). |
| `SPRING_DATASOURCE_URL`, `spring.datasource.url` | Connection string | Environment or packaged fallback: `[REDACTED]` (Base:12; Docker:3; Compose:32). |
| `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD` | Runtime datasource credentials | Compose environment; Spring property bindings `[REDACTED]` (Compose:33-34; Base:13-14). |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD`; `app.admin.username`, `app.admin.password` | Application administrator credentials | Environment, inline username default, and test literals: `[REDACTED]` (Security configuration:34-39; Test:22-23). |
| Test datasource credentials/connection string | Test-only sensitive settings | Committed test property literals: `[REDACTED]` (Test:2-5). |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD`, `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD` | Azure database provisioning credentials | Script process environment or generated values: `[REDACTED]` (Setup:35-41). |
| `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_CONNECTION_STRING` | Generated application connection details | Ignored `.env`, plaintext output file: `[REDACTED]` (Setup:274-299). |
| `secrets.GITHUB_TOKEN`, `secrets.COPILOT_ASSIGN_TOKEN` | CI/issue automation tokens | GitHub Actions secret references: `[REDACTED]`; not injected into application runtime (`.github/workflows/squad-heartbeat.yml:254`; `.github/workflows/squad-issue-assign.yml:121`; `.github/workflows/squad-release.yml:30-31`). |
| MCP example environment slots | Tool API credentials | Example JSON values: `[REDACTED]`; unrelated to application runtime (`.copilot/mcp-config.json:9-12`). |

### Secrets Provisioning Workflow

- **Local containers:** Operator copies `.env.example` to ignored `.env`, supplies secrets, then Compose interpolates them into Oracle and application environments (`.env.example:1-17`; `.gitignore:201-204`; Compose:6-9,30-36). Oracle receives its administrative password and application credentials; Spring receives datasource and administrator credentials. The initializer uses environment inputs for SQL authentication/user creation (`oracle-init/create-user.sh:11-35`). No external secret-store retrieval or encrypted-property layer is configured.
- **Application identity:** Spring creates an in-memory administrator from injected properties and encodes the supplied password with the configured password encoder (`src/main/java/com/photoalbum/config/SecurityConfig.java:28-42`). Database access uses username/password credentials; no application managed-identity binding is shown.
- **Azure provisioning:** The script requires an existing Azure CLI session, accepts or generates database passwords with a cryptographic random-number generator, provisions resources/users, and writes application connection material to ignored `.env` (`azure-setup.ps1:15-22,35-48,117-127,207-299`). AKS is attached to ACR for image-pull access (`azure-setup.ps1:99-105`); ACR administrative access is enabled (`azure-setup.ps1:69-74`). No application identity assignment, Key Vault permission grant, Kubernetes Secret binding, or PostgreSQL-to-Spring secret binding is present.
- **Storage/encryption limits:** `.env` is written as plaintext with `Out-File`; ignore rules prevent normal tracking but are not encryption or a file-permission policy (`azure-setup.ps1:283-299`; `.gitignore:201-204`). No Jasypt, sealed secrets, or equivalent application secret encryption configuration was found. All actual values are intentionally omitted here.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| Dedicated feature flags / remote flag framework | None found | No flag-provider dependency in `pom.xml:30-101` or custom `@ConditionalOnProperty`/`@ConditionalOnExpression` declaration in application sources. |
| `spring.jpa.show-sql` | `true`; Test `false` | Spring property files (Base:20; Docker:16; Test:10); operational boolean, not a business feature flag. |
| `spring.jpa.properties.hibernate.format_sql` | `true` | Base:21; Docker:17; operational formatting toggle. |
| `server.servlet.encoding.enabled`, `server.servlet.encoding.force` | Both `true` | Base:6-7; Docker:10-11; operational booleans. |

Runtime profiles select configuration sets, not gradual rollout or A/B testing behavior. No dedicated feature enablement switches were discovered.

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Application artifact | `com.photoalbum:photo-album:1.0.0`, JAR | `pom.xml:15-18` |
| Spring Boot parent/starter baseline | `2.7.18` | `pom.xml:8-13` |
| Java compilation target | Java 8 (`java.version=1.8`, source/target `8`) | `pom.xml:23-26` |
| Maven builder image | `maven:3.9.6-eclipse-temurin-8` | `Dockerfile:2` |
| Java runtime image | `eclipse-temurin:8-jre`; patch/digest not pinned | `Dockerfile:17` |
| Spring Web, Thymeleaf, Data JPA, Validation, Security, JSON, DevTools, test starter | Parent-managed; no individual literal versions declared | `pom.xml:30-101` |
| Hibernate/JPA implementation | Managed transitively through Data JPA; exact resolved version not verified | `pom.xml:43-47`; Oracle/H2 dialect configuration in Base:18 and Test:8 |
| Oracle JDBC `ojdbc8` | Parent-managed; exact resolved version not verified | `pom.xml:49-54` |
| H2 | Parent-managed, test scope; exact resolved version not verified | `pom.xml:88-93` |
| Commons IO | `2.11.0` | `pom.xml:68-73` |
| Oracle container | `gvenzl/oracle-free:latest`; mutable tag, no exact engine patch pin | `docker-compose.yml:2-4` |
| README Oracle baseline | Documents Oracle XE 21c / `21.3.0-xe`, unlike actual Compose image | `README.md:19-20,65-69`; Compose remains the executable source |
| Azure PostgreSQL | Major version `15` | `azure-setup.ps1:123` |
| Bootstrap frontend | `5.3.0`, CDN-loaded | `src/main/resources/templates/layout.html:7,42` |
| Docker Engine / Compose, local Maven/JDK, PowerShell / Azure CLI / kubectl, AKS Kubernetes | No exact versions pinned in the inspected deployment/runtime configuration | `Dockerfile:1-31`; `docker-compose.yml:1-51`; `azure-setup.ps1:1,43-127`; `azure-reset.ps1:111-118` |

> Note: Some configuration sources or properties could not be fully identified. This is a static inventory: ignored local environment contents, external cloud state, resolved transitive dependency versions, and image-provided initialization/health-check internals were not evaluated. No tests, builds, provisioning commands, or commits were run.
