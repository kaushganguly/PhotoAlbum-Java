# Configuration & Externalized Settings Inventory

Configuration is spread across three Spring properties files, container/build definitions, an environment template, and Oracle/Azure provisioning scripts. Two named runtime profiles (`docker`, `test`) are present; credentials are supplied through environment variables or test-only properties, with every credential value and default masked below.

Evidence references use repository-relative `path:line` locations. This is a static inventory, not verification of deployed settings or infrastructure.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Base Spring configuration | Packaged properties | `src/main/resources/application.properties:1-34` | Default runtime settings and environment placeholders. |
| Docker profile | Packaged profile properties | `src/main/resources/application-docker.properties:1-35` | Database settings, logging overrides, and repeated upload settings. |
| Test profile | Test-classpath properties | `src/test/resources/application-test.properties:1-23` | H2 settings and test-only admin credentials. |
| Environment template | Compose interpolation input template | `.env.example:1-17` | Documents five credential variable names; instructs copying to `.env`. Values omitted, including examples. |
| Local environment file | Operator/generated external file | `.env.example:1-3`; `azure-setup.ps1:282-299` | Compose documentation expects `.env`; Azure script separately writes a PostgreSQL-oriented `.env` to the project root. `.gitignore:201-204,251-252` excludes environment files except `.env.example`. |
| Container orchestration | Compose environment, networking, volume, readiness | `docker-compose.yml:1-51` | Two services; app profile activation and database environment overrides. |
| Container build/startup | Dockerfile | `Dockerfile:1-31` | Maven builder, Java runtime image, exposed port, JVM options, entrypoint. |
| Build definition | Maven XML | `pom.xml:8-110` | Parent BOM, Java target, dependencies, Spring Boot packaging plugin; no project-defined Maven profiles. |
| Security configuration | Java property injection and bean configuration | `src/main/java/com/photoalbum/config/SecurityConfig.java:25-61` | Admin properties are injected in code, rather than declared in production properties files. |
| Upload settings consumers | Java property injection and fixed client constants | `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:34-47`; `src/main/resources/static/js/upload.js:65-69` | Server consumes two external properties; client has independent fixed constants. |
| Oracle initialization | SQL and shell scripts mounted by Compose | `oracle-init/01-create-user.sql:1-35`; `oracle-init/02-verify-user.sql:1-14`; `oracle-init/create-user.sh:1-47`; `oracle-init/healthcheck.sql:1-3` | Database privileges, user verification, credential-driven initialization, and standalone SQL check. Mount: `docker-compose.yml:12-14`. |
| Azure provisioning | PowerShell script parameters/environment and generated file | `azure-setup.ps1:26-41,56-158,267-299` | Creates ACR, AKS, PostgreSQL, and a local `.env`; does not bind settings into an application deployment. |
| Azure maintenance controls | PowerShell parameters | `azure-reset.ps1:7-17,34-40,63-132` | Resource group and reset-selection switches; not application configuration. |
| Developer run instructions | Documented shell environment | `README.md:127-158` | Local datasource overrides and Maven/JAR startup commands; documentation is not an automatically loaded source. |
| Frontend library versions | Template CDN references | `src/main/resources/templates/layout.html:7,42` | Bootstrap version is embedded in asset URLs, not externalized. |
| Repository workflow configuration | GitHub Actions YAML | `.github/workflows/{squad-ci,squad-docs,squad-heartbeat,squad-insider-release,squad-issue-assign,squad-label-enforce,squad-preview,squad-promote,squad-release,squad-triage,sync-squad-labels}.yml` | Repository automation, not an app deployment/configuration server. CI and preview builds are placeholders (`squad-ci.yml:20-28`; `squad-preview.yml:17-30`). |
| Dependency update configuration | Dependabot YAML | `.github/dependabot.yml:1-11` | GitHub Actions updates only; weekly schedule, grouped updates, seven-day cooldown. |
| Developer integration template | MCP JSON | `.copilot/mcp-config.json:2-12` | Example Trello integration using credential references; not a Spring runtime source. |

No application `bootstrap.*`, YAML Spring configuration, external configuration repository URI, Spring Cloud Config/Consul/Azure App Configuration integration, Kubernetes ConfigMap/Secret manifest, or secret-store binding was discovered in the application and deployment files inspected. Repository automation/assessment templates are not evidence of such runtime integrations.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| No project-defined Maven profile | Ordinary Maven invocation; no `<profiles>` in `pom.xml:1-111` | One JAR build targeting Java 8 | Spring Boot parent/plugin; Web, Thymeleaf, Data JPA, Validation, Security, JSON starters; runtime Oracle JDBC; Commons IO; optional DevTools; test-scoped H2 and starter-test (`pom.xml:30-109`). |
| Docker builder path — not a Maven profile | Docker build / Compose `build` (`docker-compose.yml:26-28`) | Resolve dependencies, then package the JAR | `mvn dependency:go-offline -B`, then `mvn clean package -DskipTests` (`Dockerfile:6-14`); no profile-specific dependencies. |
| Test dependency scope — not a Maven profile | Maven test lifecycle | Add test libraries to test classpath | H2 and Spring Boot starter-test (`pom.xml:81-93`); runtime `test` profile is activated separately by annotation. |

Build properties: `java.version=1.8`, `maven.compiler.source=8`, `maven.compiler.target=8`, and `project.build.sourceEncoding=UTF-8` (`pom.xml:23-28`). Artifact coordinates are `com.photoalbum:photo-album:1.0.0`, packaging `jar` (`pom.xml:15-18`). Workflow branch names such as `dev`, `preview`, `main`, and `insider` are release-automation branches, not Maven or Spring profiles.

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Base / no explicit profile | Normal startup without profile selection | `src/main/resources/application.properties` | Oracle datasource, port 8080, DEBUG application/web logging, upload settings. No `spring.profiles.active` default is declared in this file. |
| `docker` | `SPRING_PROFILES_ACTIVE=docker` in `docker-compose.yml:31` | Base plus `src/main/resources/application-docker.properties` | Application logging INFO, Spring web WARN, Hibernate SQL DEBUG; remaining repeated settings match base values (`application-docker.properties:3-35`). |
| `test` | `@ActiveProfiles("test")` (`src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java:7-8`) | Base plus `src/test/resources/application-test.properties` on test classpath | H2 driver/URL/dialect, `create-drop`, SQL logging false, upload-path property, and test-only admin values. |

No `@Profile` beans, profile groups/includes, combined profile activation, or dev/prod-specific Spring files were found in `src`. The test file is not a production resource; selecting `test` on the packaged JAR alone does not provide that test-classpath configuration.

## Properties Inventory

### Spring application module

Values below are declared configuration, not framework-wide implicit defaults. Types are inferred from literals and consumers; unspecified ranges are not asserted.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | `8080` (integer TCP port) | Base; docker repeats | `src/main/resources/application.properties:2`; `src/main/resources/application-docker.properties:25` |
| `server.servlet.encoding.charset` | `UTF-8` (string) | Base; docker repeats | Base `:5`; docker `:9` |
| `server.servlet.encoding.enabled` | `true` (boolean) | Base; docker repeats | Base `:6`; docker `:10` |
| `server.servlet.encoding.force` | `true` (boolean) | Base; docker repeats | Base `:7`; docker `:11` |
| `spring.datasource.url` | `SPRING_DATASOURCE_URL`, fallback `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` (JDBC string) | Base/docker; test overrides with `jdbc:h2:mem:testdb` | Base `:12`; docker `:3`; test `:2`; Compose `:32` |
| `spring.datasource.username` | `[MASKED]`; reference `SPRING_DATASOURCE_USERNAME`; credential fallback exists | Base/docker; test supplies `[MASKED]` | Base `:13`; docker `:4`; test `:4`; Compose `:33` |
| `spring.datasource.password` | `[MASKED]`; reference `SPRING_DATASOURCE_PASSWORD`; no placeholder fallback | Base/docker; test supplies `[MASKED]` | Base `:14`; docker `:5`; test `:5`; Compose `:34` |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` (class name) | Base/docker; test `org.h2.Driver` | Base `:15`; docker `:6`; test `:3` |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` (class name) | Base/docker; test `org.hibernate.dialect.H2Dialect` | Base `:18`; docker `:14`; test `:8` |
| `spring.jpa.hibernate.ddl-auto` | `create` (enum-like string) | Base/docker; test `create-drop` | Base `:19`; docker `:15`; test `:9` |
| `spring.jpa.show-sql` | `true` (boolean) | Base/docker; test `false` | Base `:20`; docker `:16`; test `:10` |
| `spring.jpa.properties.hibernate.format_sql` | `true` (boolean) | Base/docker; inherited by test | Base `:21`; docker `:17` |
| `spring.servlet.multipart.max-file-size` | `10MB` (data size) | Base/docker; inherited by test | Base `:24`; docker `:26` |
| `spring.servlet.multipart.max-request-size` | `50MB` (data size) | Base/docker; inherited by test | Base `:25`; docker `:27` |
| `app.file-upload.max-file-size-bytes` | `10485760` (long, bytes) | Base/docker/test | Base `:28`; docker `:20,28`; test `:14`; injected at `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:43` |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` (comma-separated string array) | Base/docker/test | Base `:29`; docker `:21,29`; test `:15`; injected at `PhotoServiceImpl.java:44` |
| `app.file-upload.max-files-per-upload` | `10` (integer literal) | Base/docker/test | Base `:30`; docker `:22,30`; test `:16`; no property consumer found in Java source |
| `app.file-upload.upload-path` | No base declaration; test `target/test-uploads` (path string) | Test only | Test `:13`; no property consumer found in Java source |
| `logging.level.com.photoalbum` | `DEBUG` (log-level string) | Docker `INFO`; test `DEBUG` | Base `:33`; docker `:33`; test `:19` |
| `logging.level.org.springframework.web` | `DEBUG` (log-level string) | Docker `WARN`; test inherits base | Base `:34`; docker `:34` |
| `logging.level.org.hibernate.SQL` | Not explicitly set in base | Docker `DEBUG` | Docker `:35` |
| `app.admin.username` | `[MASKED]`; credential default declared at injection site | All; Compose supplies `APP_ADMIN_USERNAME`; test supplies `[MASKED]` | `src/main/java/com/photoalbum/config/SecurityConfig.java:36`; Compose `:35`; test `:22` |
| `app.admin.password` | `[MASKED]`; required injection placeholder without default | All; Compose supplies `APP_ADMIN_PASSWORD`; test supplies `[MASKED]` | `SecurityConfig.java:37`; Compose `:36`; test `:23` |

In this table, **Base**, **docker**, **test**, and **Compose** mean `src/main/resources/application.properties`, `src/main/resources/application-docker.properties`, `src/test/resources/application-test.properties`, and `docker-compose.yml`, respectively. Java basename references refer to the full paths already given in the table.

**Resolution chain:** Compose interpolates host/environment-file variables into container environment settings; required `:?` expressions reject missing/empty values. Spring resolves container environment overrides and explicit `${SPRING_DATASOURCE_*}` placeholders, then profile-specific properties over base declarations; placeholders use their declared fallback only where present. `APP_ADMIN_USERNAME` and `APP_ADMIN_PASSWORD` map to injected `app.admin.*` properties through Spring environment-name resolution. For direct local startup, an arbitrary `.env` is not loaded by the application code; variables must reach the Java process. Evidence: `docker-compose.yml:7-9,31-36`, the three properties files, and `SecurityConfig.java:34-39`.

The docker file declares the same three `app.file-upload.*` keys twice with identical values (`application-docker.properties:20-22,28-30`); these are duplicate declarations, not additional properties.

### Provisioning and external environment settings

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `ORACLE_PASSWORD` | `[MASKED]`; required, no Compose value fallback | Oracle container | `.env.example:6`; `docker-compose.yml:7`; `oracle-init/create-user.sh:11` |
| `APP_USER` | `[MASKED]`; credential fallback present | Oracle container; mapped to `SPRING_DATASOURCE_USERNAME` for app | `.env.example:9`; Compose `:8,33`; initialization shell `:12` |
| `APP_USER_PASSWORD` | `[MASKED]`; required, no Compose value fallback | Oracle container; mapped to `SPRING_DATASOURCE_PASSWORD` for app | `.env.example:12`; Compose `:9,34`; initialization shell `:13` |
| `APP_ADMIN_USERNAME` | `[MASKED]`; credential fallback present | App container | `.env.example:16`; Compose `:35` |
| `APP_ADMIN_PASSWORD` | `[MASKED]`; required, no Compose value fallback | App container | `.env.example:17`; Compose `:36` |
| `POSTGRES_ADMIN_USER`, `POSTGRES_APP_USER` | `[MASKED]`; environment overrides or script credential defaults | Azure setup only | `azure-setup.ps1:38,40` |
| `POSTGRES_ADMIN_PASSWORD`, `POSTGRES_APP_PASSWORD` | `[MASKED]`; environment overrides or generated credentials | Azure setup only | `azure-setup.ps1:39,41` |
| `POSTGRES_SERVER` | `${POSTGRES_SERVER_NAME}.postgres.database.azure.com` (hostname string) | Exported/generated Azure settings | `azure-setup.ps1:274,287` |
| `POSTGRES_USER`, `POSTGRES_PASSWORD` | `[MASKED]`; assigned from PostgreSQL application credential variables | Exported/generated Azure settings | `azure-setup.ps1:275-276,288-289` |
| `POSTGRES_CONNECTION_STRING` | `jdbc:postgresql://${SERVER_FQDN}:5432/${POSTGRES_DATABASE_NAME}` (JDBC URL assembled without credentials) | Exported/generated Azure settings | `azure-setup.ps1:267,277,290` |
| `RESOURCE_GROUP` | `photo-album-resources-${RANDOM_SUFFIX}` (generated suffix) | Azure setup; generated `.env` | `azure-setup.ps1:26-27,293` |
| `LOCATION` | `westus3` (Azure region string) | Azure setup; generated `.env` | `azure-setup.ps1:28,296` |
| `ACR_NAME` | `photoalbumacr` plus random integer suffix; SKU `Basic` | Azure setup; generated `.env` | `azure-setup.ps1:29,69-74,294` |
| `AKS_CLUSTER_NAME` | `${RESOURCE_GROUP}-aks` | Generated `.env` | `azure-setup.ps1:85-91,295` |
| `POSTGRES_SERVER_NAME` | `${RESOURCE_GROUP}-postgresql` | Azure setup | `azure-setup.ps1:31` |
| `POSTGRES_DATABASE_NAME` | `[MASKED]` (literal also used as a credential identifier elsewhere) | Azure setup | `azure-setup.ps1:33,139-142` |
| PostgreSQL version/storage/backup/network settings | `15`; storage `32` GB; retention `7` days; public-access and Azure-services firewall addresses `0.0.0.0` | Azure setup | `azure-setup.ps1:117-127,153-158` |
| Current-client firewall rule | Public IP discovered using `https://api.ipify.org`; start/end addresses both set to that IP | Azure setup | `azure-setup.ps1:167-176` |

`POSTGRES_*` exports do **not** replace the checked-in Oracle Spring configuration: no PostgreSQL JDBC dependency, PostgreSQL runtime profile, or binding from these exported names to `spring.datasource.*` is declared in `pom.xml` or `src`. The setup script writes `.env` rather than merging the Compose template's credential variables (`azure-setup.ps1:283-299`).

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| App container | `java $JAVA_OPTS -jar app.jar`; image `JAVA_OPTS="-Xmx512m -Xms256m"`; `SPRING_PROFILES_ACTIVE=docker`; datasource/admin container overrides | Initial heap 256 MiB, max heap 512 MiB; no Compose memory/CPU limit or reservation | One service container; no replicas/scaling declaration |
| Oracle container | Image entrypoint; port mapping `1521:1521`; `oracle_data:/opt/oracle/oradata`; init scripts mounted | No Compose memory/CPU limit or reservation | One service container |
| Local app | `mvn spring-boot:run` or `java -jar target/photo-album-1.0.0.jar` | No local JVM heap or resource budget documented | Operator-controlled; no scaling configuration |
| Azure AKS infrastructure | Node VM size `Standard_D8ds_v5`; generated SSH keys; ACR attachment | VM SKU selection only; no pod requests/limits or per-app JVM settings | Two AKS nodes; application replica count and autoscaling unspecified |
| Azure PostgreSQL infrastructure | SKU `Standard_D4ads_v5`; engine version `15`; storage `32` GB | SKU selection only; no per-app allocation | One server creation; no HA/replica configuration declared |

Evidence: `Dockerfile:25-31`; `docker-compose.yml:3-44`; `README.md:148-158`; `azure-setup.ps1:30-32,85-105,117-127`. No startup `-D` application system properties are declared in these paths. `-DskipTests` is a **build** option, not a runtime setting.

README suggests at least 4 GB of Docker memory (`README.md:168-170`), but that is host troubleshooting guidance, not an enforced service allocation. Its Oracle XE sizing note (`README.md:222`) must not be interpreted as a configured limit for the actual `gvenzl/oracle-free:latest` image.

## Startup Dependency Chain

1. **Operator environment → Compose interpolation:** `ORACLE_PASSWORD`, `APP_USER_PASSWORD`, and `APP_ADMIN_PASSWORD` must be supplied before Compose can resolve required expressions; credential usernames have masked fallbacks (`docker-compose.yml:7-9,33-36`).
2. **Oracle container → database initialization:** Compose mounts `oracle-init` into the image initialization directory and persists database files in `oracle_data` (`docker-compose.yml:12-14`). `01-create-user.sql` applies schema privileges, `02-verify-user.sql` queries grants, and `create-user.sh` checks/creates the configured user (`oracle-init/01-create-user.sql:14-33`; `02-verify-user.sql:4-12`; `create-user.sh:24-41`). Several SQL statements target a fixed credential identifier, whereas the shell uses `APP_USER`; arbitrary username overrides are not consistently propagated through the SQL files.
3. **Initialization shell → fixed delay:** `create-user.sh:15-17` waits 30 seconds before its SQL session; it does not implement a polling/retry loop. SQL runs against the Oracle pluggable database (`create-user.sh:22`).
4. **App container → healthy Oracle:** Compose `depends_on` requires `oracle-db` to be `service_healthy` (`docker-compose.yml:39-41`). The actual configured readiness command is the image's `healthcheck.sh`, with 30-second interval, 10-second timeout, 15 retries, and 180-second start period (`docker-compose.yml:17-22`). The separate `oracle-init/healthcheck.sql:1-3` is not the Compose healthcheck command.
5. **Application context → datasource and admin configuration:** Spring uses the selected datasource settings and mandatory admin-password placeholder (`application.properties:12-21`; `SecurityConfig.java:34-42`). Compose applies `restart: on-failure` to the app (`docker-compose.yml:44`); no application readiness probe, explicit connection retry policy, or overall startup deadline is declared.
6. **Azure setup tooling → infrastructure sequence:** Existing Azure CLI authentication is checked, then resource group → ACR → AKS → ACR attachment → PostgreSQL server/database/firewall rules → server FQDN → fixed 30-second delay → SQL role/grant setup → local environment-file output (`azure-setup.ps1:45-197,206-299`). This provisions infrastructure only; no checked-in deployment establishes a PostgreSQL-backed app readiness chain. No config-server/discovery-server startup dependency was found.

## Secrets & Sensitive Configuration

Credential **names only** are listed; values, usernames, example literals, empty defaults, and generated outputs are intentionally not reproduced.

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrative password | `[MASKED]`; operator environment/ignored `.env` → Oracle container environment (`.env.example:6`; Compose `:7`) |
| `APP_USER`, `APP_USER_PASSWORD` | Oracle application credentials | `[MASKED]`; template/environment → Oracle and app container settings (Compose `:8-9,33-34`) |
| `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD` | Spring datasource credentials | `[MASKED]`; container/process environment; test profile also has credential literals (`application.properties:13-14`; test `:4-5`) |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD`; `app.admin.username`, `app.admin.password` | Application administrator credentials | `[MASKED]`; environment → Spring injection; masked code default for username and test-only property values (`SecurityConfig.java:36-39`; test `:22-23`) |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | PostgreSQL provisioning credentials | `[MASKED]`; process environment or script defaults/generated password (`azure-setup.ps1:38-39,121-122`) |
| `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD`; `POSTGRES_USER`, `POSTGRES_PASSWORD` | PostgreSQL application credentials | `[MASKED]`; environment/generated credentials → SQL provisioning, exported environment and root `.env` (`azure-setup.ps1:40-41,206-212,275-299`) |
| Fixed database account identifiers in Oracle SQL | Credential identifiers | `[MASKED]`; checked-in SQL (`oracle-init/01-create-user.sql:15-30`; `02-verify-user.sql:5-12`) |
| `COPILOT_ASSIGN_TOKEN`, `GITHUB_TOKEN`, `GH_TOKEN`, `github-token`, checkout `token` | Repository automation tokens and action-input/environment bindings | `[MASKED]`; GitHub Actions secret references, not app settings (`.github/workflows/squad-heartbeat.yml:254`; `squad-issue-assign.yml:121`; `squad-promote.yml:24,77`; `squad-release.yml:30-31`; `squad-insider-release.yml:30-31`) |
| `TRELLO_API_KEY`, `TRELLO_TOKEN` | Example developer-integration credentials | `[MASKED]`; environment references in `.copilot/mcp-config.json:9-12`; not used by application runtime |

No Key Vault URI, Vault path, AWS Secrets Manager reference, Jasypt encryption, sealed-secret resource, or workload secret-store identity binding was found in the application/deployment configuration examined.

### Secrets Provisioning Workflow

- **Local containers:** Operator copies `.env.example` to ignored `.env` and supplies credentials; Compose interpolates names and injects Oracle credentials into the database and datasource/admin credentials into the app. Required password expressions fail early if unset/empty. Evidence: `.env.example:1-17`; `.gitignore:201-204`; `docker-compose.yml:7-9,31-36`. There is no checked-in encrypted store or explicit `.env` permission-hardening step.
- **Database access:** The image receives application-user credentials; the mounted SQL scripts grant schema-scoped creation privileges, and the shell script authenticates administratively to create/check the configured application user. Evidence: `oracle-init/01-create-user.sql:3-10,15-30`; `create-user.sh:11-35`. Fixed SQL credential identifiers can diverge from overridden `APP_USER`; all identifiers remain masked here.
- **Application access:** `SecurityConfig.java:28-42,51-60` creates an in-memory admin identity, encodes the supplied password with BCrypt, and configures stateless HTTP Basic. BCrypt is password hashing in memory, not encryption of environment variables or deployment files.
- **Azure provisioning:** An already authenticated Azure CLI session creates resources (`azure-setup.ps1:45-58`). PostgreSQL username/password variables are taken from the process or script fallbacks; missing passwords are generated with `RandomNumberGenerator` using a default length of 24 (`:15-22,38-41`). Administrative credentials are passed to Azure CLI/SQL operations, which create the application role and grants (`:206-257`). The application credentials are exported and written to the project-root `.env` (`:274-299`); no Kubernetes Secret creation or application binding is present.
- **Azure identity/access boundary:** ACR is created with admin access enabled (`azure-setup.ps1:69-74`); AKS is attached to ACR (`:102-105`). No explicit database managed-identity/RBAC binding or Key Vault permissions are declared. The exact deployed identities/roles cannot be inferred from these commands alone.
- **Repository automation:** Workflow secret references supply GitHub API/release automation; they do not provision Oracle/PostgreSQL credentials into a running application. The MCP example likewise has a separate developer-tool credential flow.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| Application feature-management flags | None discovered | No LaunchDarkly, Unleash, FeatureManagement dependency, or `@ConditionalOnProperty` / `@ConditionalOnExpression` usage found in `pom.xml` and `src/main/java`. |
| `spring.profiles.active` / `SPRING_PROFILES_ACTIVE` | No base declaration; Compose selects `docker` | Spring profile selection (`docker-compose.yml:31`); configuration selector, not gradual rollout. |
| `spring.servlet.encoding.enabled`, `spring.servlet.encoding.force` | `true` | Properties files; framework configuration booleans, not business feature flags. |
| `dry_run` | String choice `false`; choices `false`, `true` | Manual repository-promotion workflow input (`.github/workflows/squad-promote.yml:4-11,42,66,112,120`); not an application runtime flag. |
| `Force`, `AcrOnly`, `AksOnly` | PowerShell switches not enabled unless supplied | Azure reset script parameters and branches (`azure-reset.ps1:11-17,34-40,63,99`); maintenance controls, not runtime flags. |

No A/B testing or progressive rollout configuration was discovered. Upload-size/type properties are configuration knobs; client constants are separately embedded (`src/main/resources/static/js/upload.js:68-69`), with no declared synchronization mechanism.

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Spring Boot parent and dependency management | `2.7.18` | `pom.xml:8-13` |
| Java target | `1.8` / compiler source and target `8` | `pom.xml:23-27` |
| Maven container builder | `3.9.6`, Eclipse Temurin Java 8 (`maven:3.9.6-eclipse-temurin-8`) | `Dockerfile:2` |
| Java runtime container | `eclipse-temurin:8-jre`; patch version unpinned | `Dockerfile:17` |
| Spring Framework, Spring Security, Hibernate/JPA, Thymeleaf, embedded servlet container, validation, Jackson | Spring Boot parent-managed; individual resolved versions not explicitly declared or resolved during this inventory | `pom.xml:30-66,75-85` |
| Oracle JDBC driver | `com.oracle.database.jdbc:ojdbc8`; runtime scope; version parent-managed, not explicitly pinned | `pom.xml:49-54` |
| Commons IO | `2.11.0` | `pom.xml:68-73` |
| H2 | Parent-managed version; test scope | `pom.xml:88-93` |
| Spring Boot DevTools / Maven packaging plugin | Parent-managed; no independent version declared | `pom.xml:95-109` |
| Oracle container | `gvenzl/oracle-free:latest`; mutable tag, exact engine/build not pinned | `docker-compose.yml:2-4`; comment describes 23ai, not an immutable version guarantee |
| Azure PostgreSQL | Major version `15` | `azure-setup.ps1:117-125` |
| Bootstrap frontend assets | `5.3.0` | `src/main/resources/templates/layout.html:7,42` |
| GitHub Actions checkout | Commit-pinned; inline annotation `v4.4.0` | `.github/workflows/squad-ci.yml:18` |
| GitHub Actions github-script | Commit-pinned; inline annotation `v7.1.0` | `.github/workflows/squad-heartbeat.yml:30` |
| Workflow runner / Azure CLI / kubectl / PowerShell / Docker Compose | Workflow runner `ubuntu-latest`; no tool versions pinned for the other listed tools | `.github/workflows/squad-ci.yml:16`; `azure-setup.ps1:1,45,85`; `azure-reset.ps1:118`; `README.md:28-29` |

> Note: Deployed values, externally supplied environment variables, mutable image contents, and resolved transitive dependency versions could not be fully identified from checked-in configuration alone. No builds, tests, provisioning scripts, or application startup commands were executed.
