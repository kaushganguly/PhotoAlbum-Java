# Configuration & Externalized Settings Inventory

Configuration comprises three Spring property files, Maven settings, Docker build/Compose definitions, an environment template, and provisioning/initialization scripts. Two named runtime profiles (`docker`, `test`) are present; runtime passwords are external inputs, while test credential literals and all credential defaults are masked below.

Assessment root: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java`. Static inspection only: no application, scripts, builds, or tests were executed; agents directories were excluded.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Base application settings | Spring properties | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application.properties` | Database, encoding, multipart, logging, and application settings. |
| Docker overrides | Spring profile properties | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application-docker.properties` | Overrides base settings when `docker` is active; upload settings are repeated within this file with identical values. |
| Test overrides | Spring profile properties | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/test/resources/application-test.properties` | H2 and test credentials; only on the test classpath. |
| Build configuration | Maven XML | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml` | Parent dependency management, Java target, dependencies, executable-JAR plugin. |
| Container build/runtime | Dockerfile | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/Dockerfile` | Multi-stage build; runtime heap defaults. |
| Local environment | Docker Compose | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml` | Environment binding, database readiness, networking, ports, persistent database volume. |
| Environment template | dotenv template | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.env.example` | Five Oracle/application identity inputs; credential examples are not reproduced. |
| External local input | dotenv | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.env` | Referenced by instructions and Azure script; not read as part of this assessment. Spring has no explicit dotenv importer. |
| Secret-file exclusion | Git configuration | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.gitignore` | Ignores `.env` and `.env.*`, except `.env.example`. |
| Oracle initialization | Bash/SQL configuration | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/oracle-init/create-user.sh` | Environment-driven schema-user setup and grants. |
| Azure provisioning | PowerShell/Azure CLI | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1` | Creates ACR, AKS, PostgreSQL; generates configuration into root `.env`. These are provisioning settings, not an active Spring profile. |
| Azure cleanup | PowerShell/CLI parameters | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-reset.ps1` | Resource-group input and cleanup switches; namespace `photo-album`, deletion timeout `60s`. |
| Code-bound settings | Spring bean configuration | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/config/SecurityConfig.java` | Admin properties, BCrypt encoder, stateless HTTP Basic, CSRF disabled; not externally configurable flags. |
| Code-bound upload settings | Spring property injection | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java` | Injects upload size and MIME settings. |
| Profile activation | Test annotation | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java` | `@ActiveProfiles("test")`. |
| CI/repository automation | GitHub Actions YAML | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/workflows/` | Eleven workflows: squad-ci, squad-docs, squad-heartbeat, squad-insider-release, squad-issue-assign, squad-label-enforce, squad-preview, squad-promote, squad-release, squad-triage, sync-squad-labels. Java build examples in CI/release workflows are comments, not configured builds. |
| Workflow templates | YAML templates | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.squad-templates/workflows/` | Corresponding eleven workflow templates; not runtime application configuration. |
| Dependency automation | Dependabot YAML | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/dependabot.yml` | GitHub Actions ecosystem only; weekly updates, grouped `*`, seven-day cooldown. |
| Operator guidance | Documentation | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/README.md` | Local environment overrides and Docker memory recommendation. |
| Browser library configuration | Template CDN references | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/templates/layout.html`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/templates/index.html`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/templates/detail.html` | Bootstrap version pinned in CDN references. |

No application bootstrap properties/YAML, Spring Cloud Config connection, external configuration Git repository URI, Azure App Configuration, Vault/Key Vault integration, or Kubernetes ConfigMap/Secret manifests were discovered in the inspected application/deployment sources.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Default Maven build; no named profiles | Normal Maven invocation; no `<profiles>` in POM | Compile Java 8 and package JAR | Spring Boot Maven plugin; web, Thymeleaf, JPA, validation, security, JSON starters; Oracle runtime JDBC; Commons IO; test starter and H2; optional DevTools. |
| Docker build procedure, not Maven profile | Dockerfile build stage | Resolve dependencies then package without running tests | `mvn dependency:go-offline -B`; `mvn clean package -DskipTests`. |

Build properties in `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml`: `java.version=1.8`, `maven.compiler.source=8`, `maven.compiler.target=8`, `project.build.sourceEncoding=UTF-8`. No Gradle build, Maven wrapper, environment-conditioned dependencies, or profile-specific plugins were discovered. The `docker` and `test` names below are runtime profiles, not Maven profiles.

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Base/default | No explicit named profile | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application.properties` | Oracle defaults, DEBUG application/web logging. |
| `docker` | Compose `SPRING_PROFILES_ACTIVE=docker`; can also be selected externally through Spring | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application-docker.properties` | Application logging INFO, web WARN, Hibernate SQL DEBUG; repeats Oracle/upload/encoding configuration. |
| `test` | `@ActiveProfiles("test")` in `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java` | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/test/resources/application-test.properties` | H2 URL/driver/dialect, `create-drop`, SQL logging false, test credential literals masked. |

No `dev`/`prod` files, `@Profile` beans, profile groups, or explicit combined-profile configuration were found. Profile properties overlay base properties; environment/system/command-line overrides follow Spring Boot precedence. Docker Compose interpolation occurs before Spring starts. A root dotenv file is Compose input, not automatically a Spring property source.

## Properties Inventory

### Spring application

Sources: **B** = `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application.properties`; **D** = `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/application-docker.properties`; **T** = `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/test/resources/application-test.properties`; **S** = `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/config/SecurityConfig.java`.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | `8080` (integer TCP port, 1–65535) | Base, docker | B, D |
| `server.servlet.encoding.charset` | `UTF-8` (charset string) | Base, docker | B, D |
| `server.servlet.encoding.enabled` | `true` (boolean) | Base, docker | B, D |
| `server.servlet.encoding.force` | `true` (boolean) | Base, docker | B, D |
| `spring.datasource.url` | `${SPRING_DATASOURCE_URL:jdbc:oracle:thin:@oracle-db:1521/FREEPDB1}` (JDBC string) | Base/docker; test: `jdbc:h2:mem:testdb` | B, D, T |
| `spring.datasource.username` | `SPRING_DATASOURCE_USERNAME` with fallback `[MASKED]` | Base/docker; test literal `[MASKED]` | B, D, T |
| `spring.datasource.password` | Required `SPRING_DATASOURCE_PASSWORD`; no fallback | Base/docker; test literal `[MASKED]` | B, D, T |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` (class name) | Base/docker; test: `org.h2.Driver` | B, D, T |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` (class name) | Base/docker; test: `org.hibernate.dialect.H2Dialect` | B, D, T |
| `spring.jpa.hibernate.ddl-auto` | `create` (mode string) | Base/docker; test: `create-drop` | B, D, T |
| `spring.jpa.show-sql` | `true` (boolean) | Base/docker; test: `false` | B, D, T |
| `spring.jpa.properties.hibernate.format_sql` | `true` (boolean) | Base/docker; inherited by test | B, D |
| `spring.servlet.multipart.max-file-size` | `10MB` (data size) | Base, docker; inherited by test | B, D |
| `spring.servlet.multipart.max-request-size` | `50MB` (data size) | Base, docker; inherited by test | B, D |
| `app.file-upload.max-file-size-bytes` | `10485760` (long byte count) | Base, docker, test | B, D, T; injected by service constructor |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` (comma-separated string array) | Base, docker, test | B, D, T; injected by service constructor |
| `app.file-upload.max-files-per-upload` | `10` (integer) | Base, docker, test | B, D, T; no Java property binding found |
| `app.file-upload.upload-path` | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/target/test-uploads` (resolved test-relative path) | Test only | T; no Java property binding found |
| `logging.level.com.photoalbum` | `DEBUG` (logging level) | Docker: `INFO`; test: `DEBUG` | B, D, T |
| `logging.level.org.springframework.web` | `DEBUG` (logging level) | Docker: `WARN`; test inherits base | B, D |
| `logging.level.org.hibernate.SQL` | No explicit base value | Docker: `DEBUG`; test has no explicit override | D |
| `app.admin.username` | Code fallback `[MASKED]`; environment binding `APP_ADMIN_USERNAME` | All runtime profiles; test literal `[MASKED]` | S, T; Compose environment |
| `app.admin.password` | Required; no code fallback; environment binding `APP_ADMIN_PASSWORD` | All runtime profiles; test literal `[MASKED]` | S, T; Compose environment |

Spring environment variables can override the corresponding property keys using relaxed binding. Explicit datasource placeholders resolve environment inputs first, then any declared fallback; required password placeholders have no fallback. Upload type/size values are inventoried as configuration only; no entity or business-rule analysis is included.

### Compose and environment inputs

Source: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml`; template: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.env.example`.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `ORACLE_PASSWORD` | Required nonempty input through `${ORACLE_PASSWORD:?...}`; template `[MASKED]` | Compose Oracle service | Compose, environment template |
| `APP_USER` | Credential identifier fallback `[MASKED]`; template `[MASKED]` | Compose Oracle service; maps to `SPRING_DATASOURCE_USERNAME` | Compose, environment template |
| `APP_USER_PASSWORD` | Required nonempty input through `${APP_USER_PASSWORD:?...}`; template `[MASKED]` | Both Oracle and application bindings | Compose, environment template |
| `SPRING_DATASOURCE_URL` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` | Docker | Compose application environment |
| `SPRING_DATASOURCE_USERNAME` | Interpolated `APP_USER`; fallback `[MASKED]` | Docker | Compose application environment |
| `SPRING_DATASOURCE_PASSWORD` | Interpolated required `APP_USER_PASSWORD` | Docker | Compose application environment |
| `APP_ADMIN_USERNAME` | Credential fallback `[MASKED]`; template `[MASKED]` | Docker | Compose, environment template |
| `APP_ADMIN_PASSWORD` | Required nonempty input through `${APP_ADMIN_PASSWORD:?...}`; template `[MASKED]` | Docker | Compose, environment template |

Compose uses caller environment/dotenv inputs; the dotenv template itself is not automatically loaded. Oracle initialization separately requires `ORACLE_PASSWORD` and `APP_USER_PASSWORD` and defaults the `APP_USER` identifier to `[MASKED]`. `SPRING_PROFILES_ACTIVE` and `JAVA_OPTS` are startup controls listed below.

### Azure provisioning and cleanup settings

Source: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1`. These variables do not constitute a deployed Spring datasource configuration.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `RANDOM_SUFFIX` | Three random bytes formatted as six hexadecimal characters | Provisioning | Setup script |
| `RESOURCE_GROUP` | `photo-album-resources-<random suffix>` | Provisioning; emitted to dotenv | Setup script |
| `LOCATION` | `westus3` | Provisioning; emitted to dotenv | Setup script |
| `ACR_NAME` | `photoalbumacr<random integer below 99999>` | Provisioning; emitted to dotenv | Setup script |
| `POSTGRES_SERVER_NAME` | `<resource group>-postgresql` | Provisioning | Setup script |
| `POSTGRES_DATABASE_NAME` | `photoalbum` | Provisioning | Setup script |
| `POSTGRES_ADMIN_USER` | Environment override or credential default `[MASKED]` | Provisioning | Setup script |
| `POSTGRES_ADMIN_PASSWORD` | Environment override or generated value `[MASKED]` | Provisioning | Setup script |
| `POSTGRES_APP_USER` | Environment override or credential default `[MASKED]` | Provisioning | Setup script |
| `POSTGRES_APP_PASSWORD` | Environment override or generated value `[MASKED]` | Provisioning | Setup script |
| `POSTGRES_SERVER` | `<server name>.postgres.database.azure.com` | Emitted to dotenv | Setup script |
| `POSTGRES_USER` | Derived from `POSTGRES_APP_USER`; `[MASKED]` | Emitted to dotenv | Setup script |
| `POSTGRES_PASSWORD` | Derived from `POSTGRES_APP_PASSWORD`; `[MASKED]` | Emitted to dotenv | Setup script |
| `DATASOURCE_URL` / `POSTGRES_CONNECTION_STRING` | `jdbc:postgresql://<server FQDN>:5432/photoalbum` | Provisioning/output | Setup script; no application consumer found |
| `AKS_CLUSTER_NAME` | `<resource group>-aks` | Emitted to dotenv | Setup script |
| ACR SKU / admin access | `Basic` / enabled | Provisioning | Setup script CLI arguments |
| PostgreSQL storage / backup retention | `32` GiB / `7` days | Provisioning | Setup script CLI arguments |
| PostgreSQL public access / Azure-services firewall | `0.0.0.0`; current public IP added separately | Provisioning | Setup script CLI arguments |
| `CURRENT_IP` | Retrieved from `https://api.ipify.org` | Provisioning firewall rule | Setup script |
| `ResourceGroupName` | Required string; no default | Cleanup | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-reset.ps1` |
| `Force`, `AcrOnly`, `AksOnly` | Absent/false switches | Cleanup | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-reset.ps1` |

The Azure script writes `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.env` with replacement semantics, not a merge. Its PostgreSQL variables do not match the Oracle/application inputs in the Compose template. The POM includes Oracle JDBC but no PostgreSQL JDBC dependency, and no Azure/PostgreSQL Spring profile or application deployment binding was discovered.

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| Application container | `java $JAVA_OPTS -jar app.jar`; `JAVA_OPTS=-Xmx512m -Xms256m`; `SPRING_PROFILES_ACTIVE=docker`; port `8080` published to host `8080`; restart `on-failure` | Initial heap 256 MiB, maximum heap 512 MiB; no Compose memory/CPU limit | One Compose container; fixed container name; no scaling policy |
| Oracle container | `gvenzl/oracle-free:latest`; port `1521` published to host `1521`; database volume at `/opt/oracle/oradata`; init scripts at `/container-entrypoint-initdb.d` | No explicit Compose limit/request; README recommends at least 4 GB Docker allocation overall | One Compose container |
| Local JVM | README documents `mvn spring-boot:run` with externally supplied datasource settings | No local heap flags or CPU settings declared | Not specified |
| AKS infrastructure | `AKS_NODE_VM_SIZE=Standard_D8ds_v5`; generated SSH keys | VM SKU selected; no application pod CPU/memory requests or limits declared | Two cluster nodes; application replicas/autoscaling unspecified |
| PostgreSQL infrastructure | Version `15`, SKU `Standard_D4ads_v5`, storage `32` GiB | SKU-based allocation; no explicit byte-valued RAM setting | No explicit instance/scaling/HA setting |

Sources: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/Dockerfile:24-31`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml:10-44`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1:25-33,85-91,117-127`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/README.md:127-170`.

No runtime `-D` system properties, Kubernetes application resource requirements, or Java heap-to-container-limit mapping are declared. Docker build `-DskipTests` is a build flag, not a runtime setting.

## Startup Dependency Chain

1. **Operator inputs → Compose interpolation**: Supply required Oracle and admin passwords before container creation; missing/empty required inputs cause interpolation errors.
2. **Oracle container → initialization**: Compose mounts `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/oracle-init` for database initialization. The script requires database credentials, sleeps `30` seconds, and invokes SQL*Plus to ensure the application identity and grants exist.
3. **Application → healthy Oracle**: Compose `depends_on.oracle-db.condition=service_healthy` gates application startup. Oracle runs `healthcheck.sh` every `30s`, timeout `10s`, retries `15`, start period `180s`. No additional application retry/backoff setting is declared.
4. **Application context → required properties**: Datasource password and `app.admin.password` must resolve; HTTP Basic credentials are created in memory with BCrypt encoding. Compose readiness gating does not apply when launching the JVM directly.
5. **Application readiness**: No application Docker health check, readiness/liveness probe, configured startup timeout, or Actuator starter was found. `restart: on-failure` is restart policy, not readiness verification.
6. **Separate Azure provisioning order**: Existing Azure CLI login → resource group → ACR → AKS → attach ACR → PostgreSQL server → database/firewall rules → FQDN lookup → fixed `30s` sleep → application identity/grants → dotenv output. This script does not establish an application pod startup/readiness chain.

Evidence: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml:17-22,39-44`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/oracle-init/create-user.sh:9-45`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/config/SecurityConfig.java:33-42`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1`.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrative password | Caller environment/root dotenv → Oracle container; `[MASKED]` |
| `APP_USER`, `SPRING_DATASOURCE_USERNAME` | Database credential identifiers | Environment/fallback values `[MASKED]` |
| `APP_USER_PASSWORD`, `SPRING_DATASOURCE_PASSWORD`, `spring.datasource.password` | Application database password | Required environment/dotenv → database and application containers; `[MASKED]` |
| `APP_ADMIN_USERNAME`, `app.admin.username` | Application credential identifier | Environment/code fallback `[MASKED]` |
| `APP_ADMIN_PASSWORD`, `app.admin.password` | Application authentication password | Required environment → Spring bean → BCrypt in-memory encoding; `[MASKED]` |
| Test datasource and admin credentials | Test-only credential literals | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/test/resources/application-test.properties`; all values `[MASKED]`, including empty defaults |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | Azure database administrative credentials | Operator environment or generated/default inputs `[MASKED]`; passed to Azure CLI |
| `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD`, `POSTGRES_USER`, `POSTGRES_PASSWORD` | Azure database application credentials | Environment/generated inputs → plaintext ignored dotenv; `[MASKED]` |
| `secrets.GITHUB_TOKEN` | GitHub workflow token | GitHub-provided secret → checkout/script/release operations; `[MASKED]` |
| `secrets.COPILOT_ASSIGN_TOKEN` | GitHub assignment automation token | GitHub Actions secret reference; `[MASKED]`; heartbeat has `GITHUB_TOKEN` fallback |

### Secrets Provisioning Workflow

- **Local Compose**: Copy `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.env.example` to `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.env` and replace credential placeholders, or export equivalent variables. Compose maps one application database password to Oracle `APP_USER_PASSWORD` and application `SPRING_DATASOURCE_PASSWORD`; admin inputs bind to Spring `app.admin.*`.
- **Oracle access**: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/oracle-init/create-user.sh` authenticates as the database administrative identity using the environment password, creates the application identity if absent, and grants session/table/sequence privileges and tablespace quota. No secret-store lookup is present.
- **Application access**: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/config/SecurityConfig.java` requires the admin password, encodes it with BCrypt, and configures an in-memory identity. Encoding in memory is not encryption of dotenv/environment storage.
- **Azure setup**: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1` uses the current Azure CLI account. PostgreSQL passwords come from operator environment or its random generator (default length `24`); inputs are passed to provisioning/SQL commands. It exports application connection variables into the ignored root dotenv file. Administrative credentials are not among that file's emitted variables. There is no Key Vault, managed-identity database authentication, or encrypted configuration workflow.
- **Registry access**: Setup enables ACR admin access and attaches ACR to AKS using `--attach-acr`; no explicit application managed identity, service-principal secret, or Key Vault RBAC binding is configured in the inspected sources.
- **Repository automation**: `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/workflows/squad-heartbeat.yml` and `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/workflows/squad-issue-assign.yml` reference the assignment token; release/promotion workflows reference GitHub's token. These are not application/database secret bindings, and no Azure deployment-secret workflow was found.
- **Storage boundary**: Git ignoring prevents ordinary tracking but does not encrypt the dotenv file. No Jasypt, sealed secrets, DPAPI, or other at-rest secret encryption mechanism was discovered. Existing private dotenv values were not inspected.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| Dedicated feature-flag framework / conditional bean toggles | None discovered | No `@ConditionalOnProperty`, `@ConditionalOnExpression`, remote flag client, or rollout configuration found in application sources |
| `spring.profiles.active` / `SPRING_PROFILES_ACTIVE` | No explicit base profile; Compose `docker`; test annotation `test` | Runtime environment / test annotation; configuration selection rather than a business feature flag |
| Encoding `enabled` / `force`, SQL logging toggles | See properties inventory | Spring properties; framework switches, not rollout flags |
| Azure cleanup `Force`, `AcrOnly`, `AksOnly` | False when absent | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-reset.ps1`; operational switches only |

CSRF disabling, stateless sessions, and HTTP Basic are fixed code configuration, not environment-controlled feature switches.

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Application artifact | `com.photoalbum:photo-album:1.0.0`, JAR | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:15-18` |
| Spring Boot parent/starters | `2.7.18` | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:8-12` |
| Java source/target | Java `8` (`java.version=1.8`) | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:23-27` |
| Maven builder image | `maven:3.9.6-eclipse-temurin-8` | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/Dockerfile:2` |
| Runtime image | `eclipse-temurin:8-jre` (patch/digest not pinned) | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/Dockerfile:17` |
| Oracle database image | `gvenzl/oracle-free:latest` (mutable); Compose comment describes Free 23ai | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/docker-compose.yml:2-4` |
| Oracle JDBC | `ojdbc8`, version inherited from Spring Boot dependency management; not explicitly pinned in project | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:49-54` |
| Spring Framework, Spring Security, Hibernate, Thymeleaf, embedded Tomcat, H2, test libraries | Managed by Spring Boot `2.7.18`; exact resolved versions not determined without dependency resolution | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml` |
| Commons IO | `2.11.0` | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:68-73` |
| Bootstrap | `5.3.0`, CDN references | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/templates/layout.html:7,42`; also index/detail templates |
| Azure PostgreSQL server | `15` requested; no PostgreSQL JDBC dependency present | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1:123`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml` |
| GitHub Actions | Checkout SHA annotated `v4.4.0`; github-script SHA annotated `v7.1.0`; runner `ubuntu-latest` in CI | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/workflows/squad-ci.yml:16-18`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/.github/workflows/squad-heartbeat.yml:27-30` |
| Docker/Compose, local Maven, PowerShell, Azure CLI, kubectl, AKS Kubernetes | No tool/cluster version pinned in inspected application/deployment files | `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/README.md`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-setup.ps1`; `/home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/azure-reset.ps1` |

> Note: Some configuration sources or properties could not be fully identified. External/private environment values, resolved transitive dependency versions, live Azure settings, and actual container image digests were not queried. Presence of provisioning scripts is not evidence of an existing deployment.
