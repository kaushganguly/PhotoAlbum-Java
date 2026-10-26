# Configuration & Externalized Settings Inventory

Configuration is spread across three Spring property files, Compose, a Dockerfile, an environment template, Oracle initialization scripts, and Azure provisioning scripts. Two named runtime profiles are present; secrets are supplied through environment variables or generated during provisioning, with no application secret-store integration found.

Scope: repository configuration as checked in, not deployed state. All password and secret values, including test values and template defaults, are shown as `[MASKED]`. References below are repository-relative paths and line numbers.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Base Spring configuration | Properties | `src/main/resources/application.properties:1-34` | Shared defaults; Oracle datasource placeholders. |
| Docker Spring configuration | Profile properties | `src/main/resources/application-docker.properties:1-35` | Docker-specific logging; repeats shared settings. Upload properties appear twice with identical values (lines 20-22, 28-30). |
| Test Spring configuration | Profile properties | `src/test/resources/application-test.properties:1-23` | Test-classpath H2 settings and masked test credentials. |
| Bean injection defaults | Java configuration | `src/main/java/com/photoalbum/config/SecurityConfig.java:34-42`; `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:41-47` | Admin username default and required admin password; upload property consumers. |
| Local environment template | Environment file | `.env.example:1-17` | Template for an operator-created `.env`; not a Spring configuration file itself. |
| Container orchestration | Compose YAML | `docker-compose.yml:1-51` | Environment bindings, required-value checks, profile selection, ports, volume, network, readiness gating. |
| Container runtime/build defaults | Dockerfile | `Dockerfile:1-31` | Build/runtime images, Maven commands, JVM options. |
| Build configuration | Maven XML | `pom.xml:8-110` | Parent-managed dependency versions, Java target, packaging plugin. |
| Oracle initialization | Shell and SQL | `oracle-init/create-user.sh:9-45`; `oracle-init/01-create-user.sql:12-35`; `oracle-init/02-verify-user.sql:2-14`; `oracle-init/healthcheck.sql:1-3` | Environment-driven user creation, fixed-name grants and verification, standalone SQL check. |
| Azure infrastructure defaults and generated environment | PowerShell | `azure-setup.ps1:25-41,69-127,274-299` | Provisioning configuration for ACR, AKS and PostgreSQL; writes root `.env`. Not a Spring runtime profile. |
| Azure maintenance parameters | PowerShell | `azure-reset.ps1:6-18,125-132` | Required resource group; optional cleanup switches; fixed `photo-album` namespace and 60-second deletion timeout. |
| Usage examples | Documentation | `README.md:40-57,127-148` | Compose setup and local datasource exports; examples are not automatically loaded. |
| CI/repository automation | GitHub Actions YAML | `.github/workflows/squad-ci.yml:14-28`; secret references listed below | CI currently has no Java build command. Repository automation tokens are separate from application credentials. |
| Secret exclusion | Git ignore rules | `.gitignore:201-204,251-255` | Ignores `.env`, other `.env.*` files except `.env.example`, and `.azure/`. |

No application `bootstrap.*`, external configuration repository URI, Spring Cloud Config, Azure App Configuration, Vault/Key Vault binding, Kubernetes application ConfigMap/Secret manifest, or Maven wrapper was discovered in the inspected application configuration.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Default Maven build; no explicit named profiles | Normal Maven invocation; no `<profiles>` declaration | Java 8 compilation and executable JAR packaging | Spring Boot Maven plugin; web, Thymeleaf, Data JPA, validation, security, JSON, Oracle runtime driver, Commons IO; test-scoped H2 and test starter; optional DevTools (`pom.xml:23-110`). |
| Container build mode, not a Maven profile | Docker build executes `mvn clean package -DskipTests` | Package without executing tests | Same dependencies/plugin; dependency prefetch uses `mvn dependency:go-offline -B` (`Dockerfile:6-14`). |

No build-time dependency switches or profile-specific repositories are declared. `spring-boot-devtools` is optional, not controlled by a named Maven profile (`pom.xml:95-100`).

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Default/shared | No explicit active profile in base configuration | `src/main/resources/application.properties:1-34` | Oracle defaults, DEBUG application/web logging. Database and admin passwords must be supplied externally. |
| `docker` | Compose sets `SPRING_PROFILES_ACTIVE=docker` (`docker-compose.yml:31`) | Base plus `src/main/resources/application-docker.properties:1-35` | Application logging INFO, web WARN, Hibernate SQL DEBUG; remaining declared shared values match base. |
| `test` | `@ActiveProfiles("test")` (`src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java:7-8`) | Base plus `src/test/resources/application-test.properties:1-23` | H2 datasource/dialect, `create-drop`, SQL display false, test credentials, test upload path. |

No `@Profile` bean declarations, profile groups, combined activation, or additional environment-specific application files were found in `src`. Profiles are distinct from the Azure infrastructure script.

## Properties Inventory

### Application module: `photo-album`

Types are indicated in the default column. These are declared configuration values, not a catalog of framework implicit defaults.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | Integer `8080` | Base and docker | `src/main/resources/application.properties:2`; `src/main/resources/application-docker.properties:25` |
| `server.servlet.encoding.charset` | String `UTF-8` | Base and docker | `src/main/resources/application.properties:5`; `src/main/resources/application-docker.properties:9` |
| `server.servlet.encoding.enabled` | Boolean `true` | Base and docker | `src/main/resources/application.properties:6`; `src/main/resources/application-docker.properties:10` |
| `server.servlet.encoding.force` | Boolean `true` | Base and docker | `src/main/resources/application.properties:7`; `src/main/resources/application-docker.properties:11` |
| `spring.datasource.url` | String `${SPRING_DATASOURCE_URL:jdbc:oracle:thin:@oracle-db:1521/FREEPDB1}` | Base/docker; test `jdbc:h2:mem:testdb` | `src/main/resources/application.properties:12`; `src/main/resources/application-docker.properties:3`; `src/test/resources/application-test.properties:2` |
| `spring.datasource.username` | String `${SPRING_DATASOURCE_USERNAME:photoalbum}` | Base/docker; test `sa` | `src/main/resources/application.properties:13`; `src/main/resources/application-docker.properties:4`; `src/test/resources/application-test.properties:4` |
| `spring.datasource.password` | `[MASKED]`; required environment reference `SPRING_DATASOURCE_PASSWORD`, no fallback in base/docker | Test override `[MASKED]` | `src/main/resources/application.properties:10-14`; `src/main/resources/application-docker.properties:2-5`; `src/test/resources/application-test.properties:5` |
| `spring.datasource.driver-class-name` | Class `oracle.jdbc.OracleDriver` | Base/docker; test `org.h2.Driver` | `src/main/resources/application.properties:15`; `src/main/resources/application-docker.properties:6`; `src/test/resources/application-test.properties:3` |
| `spring.jpa.database-platform` | Class `org.hibernate.dialect.OracleDialect` | Base/docker; test `org.hibernate.dialect.H2Dialect` | `src/main/resources/application.properties:18`; `src/main/resources/application-docker.properties:14`; `src/test/resources/application-test.properties:8` |
| `spring.jpa.hibernate.ddl-auto` | Enum/string `create` | Base/docker; test `create-drop` | `src/main/resources/application.properties:19`; `src/main/resources/application-docker.properties:15`; `src/test/resources/application-test.properties:9` |
| `spring.jpa.show-sql` | Boolean `true` | Base/docker; test `false` | `src/main/resources/application.properties:20`; `src/main/resources/application-docker.properties:16`; `src/test/resources/application-test.properties:10` |
| `spring.jpa.properties.hibernate.format_sql` | Boolean `true` | Base/docker; inherited in test | `src/main/resources/application.properties:21`; `src/main/resources/application-docker.properties:17` |
| `spring.servlet.multipart.max-file-size` | Data size `10MB` | Base/docker; inherited in test | `src/main/resources/application.properties:24`; `src/main/resources/application-docker.properties:26` |
| `spring.servlet.multipart.max-request-size` | Data size `50MB` | Base/docker; inherited in test | `src/main/resources/application.properties:25`; `src/main/resources/application-docker.properties:27` |
| `app.file-upload.max-file-size-bytes` | Long integer `10485760` | Base/docker/test | `src/main/resources/application.properties:28`; `src/main/resources/application-docker.properties:20,28`; `src/test/resources/application-test.properties:14`; consumer `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:43` |
| `app.file-upload.allowed-mime-types` | String list `image/jpeg,image/png,image/gif,image/webp` | Base/docker/test | `src/main/resources/application.properties:29`; `src/main/resources/application-docker.properties:21,29`; `src/test/resources/application-test.properties:15`; consumer `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:44` |
| `app.file-upload.max-files-per-upload` | Integer `10` | Base/docker/test | `src/main/resources/application.properties:30`; `src/main/resources/application-docker.properties:22,30`; `src/test/resources/application-test.properties:16` |
| `app.file-upload.upload-path` | String path `target/test-uploads`; absent from base/docker | Test only | `src/test/resources/application-test.properties:13` |
| `logging.level.com.photoalbum` | Log level `DEBUG` | Base/test; docker `INFO` | `src/main/resources/application.properties:33`; `src/main/resources/application-docker.properties:33`; `src/test/resources/application-test.properties:19` |
| `logging.level.org.springframework.web` | Log level `DEBUG` | Base; docker `WARN`; inherited in test | `src/main/resources/application.properties:34`; `src/main/resources/application-docker.properties:34` |
| `logging.level.org.hibernate.SQL` | Log level `DEBUG`; not explicitly set in base | Docker only | `src/main/resources/application-docker.properties:35` |
| `app.admin.username` | String `admin`; relaxed environment binding `APP_ADMIN_USERNAME` | All; test explicitly `admin` | `src/main/java/com/photoalbum/config/SecurityConfig.java:36`; `docker-compose.yml:35`; `src/test/resources/application-test.properties:22` |
| `app.admin.password` | `[MASKED]`; no Java injection fallback; environment binding `APP_ADMIN_PASSWORD` | Required outside test; test override `[MASKED]` | `src/main/java/com/photoalbum/config/SecurityConfig.java:37`; `docker-compose.yml:36`; `src/test/resources/application-test.properties:23` |

No Java consumer of `app.file-upload.max-files-per-upload` or `app.file-upload.upload-path` was found in `src/main/java`; their presence in property files does not establish an active runtime setting. No additional numeric ranges are declared in the configuration sources.

**Resolution chain:** Compose interpolates its environment from the shell/operator `.env`, applies `:-` defaults for usernames, and rejects missing/empty required passwords through `:?` (`docker-compose.yml:7-9,33-36`). It injects `APP_USER` into `SPRING_DATASOURCE_USERNAME` and `APP_USER_PASSWORD` into `SPRING_DATASOURCE_PASSWORD`; Spring then resolves those environment properties over packaged base/profile values. Profile-specific files override base values. Direct Spring execution does not automatically import the root `.env`; the local instructions use exported variables (`README.md:139-148`). Spring command-line/system-property overrides remain available, but none are prescribed by the checked-in entrypoint (`Dockerfile:31`).

### Infrastructure and initialization settings

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `ORACLE_PASSWORD`, `APP_USER_PASSWORD`, `APP_ADMIN_PASSWORD` | Each `[MASKED]`; required by Compose; template values also masked | Local Compose | `.env.example:5-17`; `docker-compose.yml:7-9,34-36` |
| `APP_USER`, `APP_ADMIN_USERNAME` | Strings `photoalbum`, `admin` | Local Compose | `.env.example:8-16`; `docker-compose.yml:8,33,35` |
| Oracle session/tablespaces | `_ORACLE_SCRIPT=true`; `USERS` default, `TEMP` temporary; unlimited `USERS` quota | Initialization | `oracle-init/01-create-user.sql:12,26-30`; `oracle-init/create-user.sh:34-35` |
| Azure `RESOURCE_GROUP`, `LOCATION`, `ACR_NAME` | Generated `photo-album-resources-<suffix>`, `westus3`, generated `photoalbumacr<number>` | Provisioning only | `azure-setup.ps1:25-29` |
| `POSTGRES_SERVER_NAME`, `POSTGRES_DATABASE_NAME` | `<RESOURCE_GROUP>-postgresql`, `photoalbum` | Provisioning only | `azure-setup.ps1:31-33` |
| `POSTGRES_ADMIN_USER`, `POSTGRES_APP_USER` | Environment override; otherwise `photoalbum_admin`, `photoalbum` | Provisioning only | `azure-setup.ps1:38,40` |
| `POSTGRES_ADMIN_PASSWORD`, `POSTGRES_APP_PASSWORD` | `[MASKED]`; environment override or per-run generation | Provisioning only | `azure-setup.ps1:35-41` |
| ACR SKU and administrator access | `Basic`; administrator access enabled | Provisioning only | `azure-setup.ps1:69-74` |
| PostgreSQL version/storage/retention/public access | `15`; storage `32` GB; retention `7` days; `0.0.0.0` public-access setting | Provisioning only | `azure-setup.ps1:117-127` |
| PostgreSQL firewall | `AllowAzureServices`: start/end `0.0.0.0`; `AllowCurrentIP`: detected public IP | Provisioning only | `azure-setup.ps1:153-176` |
| `POSTGRES_SERVER`, `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_CONNECTION_STRING` | Generated FQDN; selected app username; `[MASKED]`; `jdbc:postgresql://<FQDN>:5432/photoalbum` | Generated process environment and root `.env` | `azure-setup.ps1:266-299` |
| Generated `.env` resource metadata | `RESOURCE_GROUP`, `ACR_NAME`, `AKS_CLUSTER_NAME=<RESOURCE_GROUP>-aks`, `LOCATION` | Provisioning output | `azure-setup.ps1:292-299` |
| Cleanup `ResourceGroupName`, `Force`, `AcrOnly`, `AksOnly` | Required string; optional switches default off | Maintenance only | `azure-reset.ps1:6-18` |

**Configuration disconnect:** the Azure script produces `POSTGRES_*` values, but the application POM and Spring files still select Oracle; no `POSTGRES_*` → Spring binding or PostgreSQL JDBC dependency is declared (`azure-setup.ps1:274-299`; `pom.xml:49-54`; `src/main/resources/application.properties:12-18`). The script overwrites root `.env` with Azure values rather than merging the Compose-required Oracle/admin keys (`azure-setup.ps1:279-299`; `docker-compose.yml:7-9,34-36`).

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| `photoalbum-java-app` | `java $JAVA_OPTS -jar app.jar`; `JAVA_OPTS="-Xmx512m -Xms256m"`; Compose `SPRING_PROFILES_ACTIVE=docker`; no startup `-D` system properties | JVM initial heap 256 MiB / max heap 512 MiB; no container memory/CPU request or limit | One service container by default; no replicas/autoscaling declared (`Dockerfile:27-31`; `docker-compose.yml:25-44`). |
| `oracle-db` | Image entrypoint; environment credentials; host/container TCP mapping `1521:1521` | No Compose memory/CPU limit; README recommends minimum 4 GB available for Oracle | One service container by default; persistent `oracle_data` volume (`docker-compose.yml:3-22,46-51`; `README.md:26-30`). |
| AKS infrastructure | VM size `Standard_D8ds_v5`; generated SSH keys | Node SKU specified, not per-application resource requests/limits | Two nodes; no node autoscaling or application replica manifest declared (`azure-setup.ps1:30,85-91`). |
| Azure PostgreSQL infrastructure | SKU `Standard_D4ads_v5` | Compute SKU specified; storage 32 GB | One server provisioned; no HA/scaling arguments shown (`azure-setup.ps1:32,117-127`). |

Compose maps application TCP port `8080:8080`, uses bridge network `photoalbum-network`, and restarts the application `on-failure` (`docker-compose.yml:37-51`). Heap values are not a full container memory budget; no mapping to an explicit container allocation is available.

## Startup Dependency Chain

1. **Operator environment → Compose validation → containers:** required Oracle, application-schema and admin passwords must be supplied before Compose can resolve the service definitions (`docker-compose.yml:7-9,34-36`).
2. **Oracle image initialization → mounted scripts:** Compose mounts `./oracle-init` at `/container-entrypoint-initdb.d`; the shell script requires Oracle credentials and sleeps 30 seconds before SQL execution (`docker-compose.yml:12-14`; `oracle-init/create-user.sh:11-22`). SQL grant and verification files assume the fixed `photoalbum` account even when `APP_USER` is overridden (`oracle-init/01-create-user.sql:15-30`; `oracle-init/02-verify-user.sql:4-12`).
3. **Application → waits for → healthy Oracle:** `depends_on.condition=service_healthy`; Oracle's image-provided `healthcheck.sh` runs every 30 seconds, timeout 10 seconds, retries 15, start period 180 seconds (`docker-compose.yml:17-22,39-41`). `oracle-init/healthcheck.sql:1-3` exists, but Compose does not directly reference it.
4. **Spring context → required external properties:** database and admin passwords must resolve before their consumers initialize (`src/main/resources/application.properties:10-14`; `src/main/java/com/photoalbum/config/SecurityConfig.java:34-42`). No application readiness/liveness probe, explicit datasource retry policy, or application startup timeout is declared in Compose.
5. **Separate Azure provisioning order:** existing Azure CLI login/account → resource group → ACR → AKS → ACR attachment → PostgreSQL server → database → firewall rules → FQDN lookup → fixed 30-second sleep → SQL user/grants → root `.env` output (`azure-setup.ps1:43-299`). This provisions resources; it does not establish a deployed application startup chain.

The Oracle shell script targets service `XE`, whereas the application uses `FREEPDB1`; this is an initialization/configuration mismatch to verify, not evidence that both are available (`oracle-init/create-user.sh:22`; `docker-compose.yml:32`). README's Oracle XE image/service description also differs from Compose's Oracle Free image (`README.md:65-70`; `docker-compose.yml:2-4`).

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrator password | `[MASKED]`; operator environment/root `.env` → Oracle container (`.env.example:5-6`; `docker-compose.yml:7`). |
| `APP_USER_PASSWORD` → `SPRING_DATASOURCE_PASSWORD` → `spring.datasource.password` | Application database password | `[MASKED]`; same operator secret bound to database and application containers (`docker-compose.yml:9,34`; `src/main/resources/application.properties:14`). |
| `APP_ADMIN_PASSWORD` → `app.admin.password` | Application admin password | `[MASKED]`; environment → Spring injection → BCrypt-encoded in-memory user (`docker-compose.yml:36`; `src/main/java/com/photoalbum/config/SecurityConfig.java:28-42`). |
| Test `spring.datasource.password`, `app.admin.password` | Test-only password entries | `[MASKED]`; committed test profile values, including empty/default values, deliberately not reproduced (`src/test/resources/application-test.properties:5,21-23`). |
| Template password entries | Example/default password values | `[MASKED]`; all three template assignments suppressed (`.env.example:5-17`). |
| `POSTGRES_ADMIN_PASSWORD`, `POSTGRES_APP_PASSWORD` | Azure database passwords | `[MASKED]`; environment or generated values (`azure-setup.ps1:35-41`). |
| Generated `POSTGRES_PASSWORD` | Azure application database password | `[MASKED]`; process environment and plaintext git-ignored `.env` (`azure-setup.ps1:274-299`). |
| `secrets.COPILOT_ASSIGN_TOKEN` | Repository automation credential | `[MASKED]`; GitHub Actions secret reference (`.github/workflows/squad-issue-assign.yml:121`; `.github/workflows/squad-heartbeat.yml:254`). |
| `secrets.GITHUB_TOKEN` → action token / `GH_TOKEN` | GitHub workflow token | `[MASKED]`; Actions runtime injection, not application configuration (`.github/workflows/squad-heartbeat.yml:254`; `.github/workflows/squad-release.yml:30-31`; `.github/workflows/squad-insider-release.yml:30-31`; `.github/workflows/squad-promote.yml:24,77`). |

### Secrets Provisioning Workflow

- **Local containers:** copy `.env.example` to `.env`, replace every password placeholder with an operator-supplied value, then start Compose (`README.md:40-46`; `.env.example:1-17`). Compose rejects absent/empty passwords, passes the schema secret to both services and the admin secret only to the application (`docker-compose.yml:7-9,30-36`). Oracle initialization consumes environment credentials; SQL grants are schema-scoped rather than DBA (`oracle-init/create-user.sh:11-35`; `oracle-init/01-create-user.sql:7-30`).
- **Application binding:** datasource placeholders and Spring's environment property binding supply credentials. `SecurityConfig` BCrypt-encodes the injected admin password for its in-memory user; this is password hashing, not encryption of the source environment or `.env` (`src/main/resources/application.properties:10-15`; `src/main/java/com/photoalbum/config/SecurityConfig.java:28-42`).
- **Azure provisioning:** uses the already-authenticated Azure CLI account; no explicit service-principal login or application managed-identity secret access is defined (`azure-setup.ps1:43-50`). Passwords come from environment variables or a cryptographic RNG with default length 24 (`azure-setup.ps1:12-23,35-41`). They are passed to Azure CLI provisioning/SQL commands; only the app password is persisted as `POSTGRES_PASSWORD` in root `.env` (`azure-setup.ps1:117-127,206-212,274-299`). The script enables ACR administrator access and attaches ACR to AKS, but defines no Key Vault/Secret resource binding (`azure-setup.ps1:69-74,99-105`).
- **Storage/access boundaries:** `.env` is ignored by Git, not encrypted; filesystem access restrictions and rotation are not configured by these scripts (`.gitignore:201-204`; `azure-setup.ps1:299`). No Jasypt, sealed secrets, DPAPI, Vault, or Key Vault provisioning flow was found. Workflow GitHub tokens remain separate repository-automation credentials.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| Dedicated feature-flag framework / conditional feature beans | None discovered | No feature-flag dependency in `pom.xml:30-101`, and no `@ConditionalOnProperty`/`@ConditionalOnExpression` in application Java sources. |
| `spring.jpa.show-sql`, `spring.jpa.properties.hibernate.format_sql` | `true`; test show-sql `false` | Property files; operational toggles, not business feature rollout (`src/main/resources/application.properties:20-21`; `src/test/resources/application-test.properties:10`). |
| `server.servlet.encoding.enabled`, `server.servlet.encoding.force` | Both `true` | Base/docker properties; framework toggles (`src/main/resources/application.properties:5-7`; `src/main/resources/application-docker.properties:9-11`). |
| Cleanup `Force`, `AcrOnly`, `AksOnly` | Off unless supplied | Maintenance script switches, not application features (`azure-reset.ps1:6-18,33-40,63,99`). |

No remote flag service, A/B testing configuration, or gradual rollout configuration was discovered.

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Application artifact | `com.photoalbum:photo-album:1.0.0`, JAR | `pom.xml:15-18` |
| Spring Boot parent | `2.7.18` | `pom.xml:8-12` |
| Java language/compiler target | Java 8 (`java.version=1.8`, source/target `8`); UTF-8 source encoding | `pom.xml:23-27` |
| Container build JDK and Maven | `maven:3.9.6-eclipse-temurin-8` | `Dockerfile:2` |
| Container JRE | `eclipse-temurin:8-jre`; patch/digest not pinned | `Dockerfile:17` |
| Spring web, Thymeleaf, Data JPA, validation, security, JSON; transitive Hibernate | Parent-managed; exact resolved versions not independently verified | `pom.xml:30-66,75-79`; parent `pom.xml:8-12` |
| Oracle JDBC `ojdbc8` | Parent-managed; no direct version declaration | `pom.xml:49-54` |
| Commons IO | `2.11.0` | `pom.xml:68-73` |
| Spring Boot test starter, H2 | Parent-managed, test scope; exact resolved versions not verified | `pom.xml:81-93` |
| Spring Boot DevTools / Maven packaging plugin | Parent-managed | `pom.xml:95-108` |
| Oracle container | `gvenzl/oracle-free:latest`; mutable tag, no pinned database patch | `docker-compose.yml:2-4`; README instead describes XE `21.3.0-xe` (`README.md:65-70`). |
| Azure PostgreSQL server | Major version `15` | `azure-setup.ps1:123` |
| AKS Kubernetes, Azure CLI, PowerShell, Docker/Compose | Versions not pinned in inspected deployment sources | `azure-setup.ps1:1,43-91`; `docker-compose.yml:1-51` |

This inventory is based on static evidence only; no tests, builds, dependency resolution, deployments, or live configuration checks were performed.
