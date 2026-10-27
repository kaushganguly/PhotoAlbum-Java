# Configuration & Externalized Settings Inventory

Configuration comprises three Spring properties files, a Compose definition, a Dockerfile, an environment template, Oracle initialization files, and separate Azure provisioning scripts. There are no explicit Maven profiles; runtime configuration uses default, Docker, and test settings, with environment-supplied credentials rather than a configured remote secret store.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Default application settings | Spring properties | `src/main/resources/application.properties` | Shared runtime defaults and datasource environment placeholders. |
| Docker settings | Spring profile properties | `src/main/resources/application-docker.properties` | Overrides shared settings when `docker` is active; repeats several defaults. |
| Test settings | Spring profile properties | `src/test/resources/application-test.properties` | Test-classpath H2 configuration and test-only admin credentials. |
| Code-level settings | Spring `@Value` | `src/main/java/com/photoalbum/config/SecurityConfig.java`; `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java` | Admin username fallback and required admin password; upload-property injection. |
| Build configuration | Maven XML | `pom.xml` | Java/compiler settings, parent-managed dependencies, executable JAR plugin. |
| Container configuration | Dockerfile | `Dockerfile` | Build/runtime images, exposed port, JVM heap defaults and entrypoint. |
| Local orchestration | Compose YAML | `docker-compose.yml` | Environment binding, required credential checks, ports, network, volume, database readiness. |
| Environment template | dotenv template | `.env.example` | `ORACLE_PASSWORD`, `APP_USER`, `APP_USER_PASSWORD`, `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD`; credential values `<redacted>`. |
| Local secret file | dotenv, operator-created | `.env` | Not present at inspection; ignored by `.gitignore`. Compose reads this file; Spring does not automatically load dotenv files. |
| Oracle initialization | SQL/shell | `oracle-init/01-create-user.sql`, `02-verify-user.sql`, `create-user.sh`, `healthcheck.sql` | Mounted into `/container-entrypoint-initdb.d`; privilege grants, verification and environment-dependent user creation. |
| Azure provisioning | PowerShell | `azure-setup.ps1` | Creates ACR, AKS and PostgreSQL; generates/replaces root `.env` with Azure settings. Not application deployment configuration. |
| Azure reset options | PowerShell parameters | `azure-reset.ps1` | Mandatory `ResourceGroupName`; switches `Force`, `AcrOnly`, `AksOnly`. Uses namespace `photo-album` and deletion timeout `60s`. |
| Operational documentation | Markdown | `README.md` | Manual Maven commands, local datasource override, memory guidance; some Oracle version information differs from Compose. |
| CI build placeholder | GitHub Actions | `.github/workflows/squad-ci.yml` | `ubuntu-latest`; no actual Java build/test command configured. Other Squad workflows are repository automation, not application runtime sources. |

No `bootstrap.*`, external configuration repository URI, Spring Cloud Config, Azure App Configuration, Vault, Key Vault, ConfigMap, or Kubernetes Secret/application deployment manifest was found in the application configuration sources.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Single default Maven build | Normal Maven execution; no `<profiles>` defined | Compile/package `com.photoalbum:photo-album:1.0.0` as JAR | Spring Boot Maven plugin; web, Thymeleaf, Data JPA, validation, security, JSON starters; runtime Oracle JDBC; Commons IO; optional DevTools; test starter and H2. |
| Docker image build, not a Maven profile | `docker compose build` / image build | Build JAR inside Maven image | `mvn dependency:go-offline -B`, then `mvn clean package -DskipTests`. Tests are skipped for image packaging. |

Build properties: `java.version=1.8`, `maven.compiler.source=8`, `maven.compiler.target=8`, `project.build.sourceEncoding=UTF-8`. No Gradle build, Maven wrapper, profile-specific dependency sets, or toolchain configuration is present.

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Default | No explicitly active profile | `application.properties` | Oracle defaults; application and Spring Web logging `DEBUG`; required datasource/admin secrets. No `spring.profiles.active` setting in source properties. |
| `docker` | Compose sets `SPRING_PROFILES_ACTIVE=docker` | Default file plus `application-docker.properties` | Application logging `INFO`, Spring Web `WARN`, Hibernate SQL `DEBUG`; repeated Oracle, encoding, upload and port settings. |
| `test` | `@ActiveProfiles("test")` in `PhotoAlbumApplicationTests` | Default file plus test-classpath `application-test.properties` | H2 datasource/dialect, `create-drop`, SQL logging disabled, test-only admin credentials and upload-path setting. |

No `@Profile` beans, profile groups, include directives, or dev/prod-specific files were found. Spring supports multiple active profiles, but the repository does not configure a composed profile combination.

## Properties Inventory

### Spring application module

`B` = base `application.properties`, `D` = Docker file, `T` = test file, `S` = `SecurityConfig.java`. Values are source defaults, not observations of a running environment. Secret values are always `<redacted>`.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | `8080` (integer TCP port) | Base; D repeats | B, D |
| `server.servlet.encoding.charset` | `UTF-8` (string) | Base; D repeats | B, D |
| `server.servlet.encoding.enabled` | `true` (boolean) | Base; D repeats | B, D |
| `server.servlet.encoding.force` | `true` (boolean) | Base; D repeats | B, D |
| `spring.datasource.url` | `${SPRING_DATASOURCE_URL:jdbc:oracle:thin:@oracle-db:1521/FREEPDB1}` (JDBC string) | Base/D; T=`jdbc:h2:mem:testdb` | B, D, T; environment |
| `spring.datasource.username` | `${SPRING_DATASOURCE_USERNAME:photoalbum}` (string) | Base/D; T=`sa` | B, D, T; environment |
| `spring.datasource.password` | `<redacted>`; required `SPRING_DATASOURCE_PASSWORD` reference without fallback | Base/D; T explicitly empty, represented as `<redacted>` | B, D, T; environment |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` | Base/D; T=`org.h2.Driver` | B, D, T |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` | Base/D; T=`org.hibernate.dialect.H2Dialect` | B, D, T |
| `spring.jpa.hibernate.ddl-auto` | `create` (enum string) | Base/D; T=`create-drop` | B, D, T |
| `spring.jpa.show-sql` | `true` (boolean) | Base/D; T=`false` | B, D, T |
| `spring.jpa.properties.hibernate.format_sql` | `true` (boolean) | Base/D; inherited by T | B, D |
| `spring.servlet.multipart.max-file-size` | `10MB` (data size) | Base; D repeats; inherited by T | B, D |
| `spring.servlet.multipart.max-request-size` | `50MB` (data size) | Base; D repeats; inherited by T | B, D |
| `app.file-upload.max-file-size-bytes` | `10485760` (long, bytes) | Base/D/T | B, D, T; injected in `PhotoServiceImpl` |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` (string array) | Base/D/T | B, D, T; injected in `PhotoServiceImpl` |
| `app.file-upload.max-files-per-upload` | `10` (integer setting) | Base/D/T | B, D, T; no property injection/reference found in Java |
| `app.file-upload.upload-path` | No base default; T=`target/test-uploads` (path string) | T only | T; no property injection/reference found in Java |
| `app.admin.username` | `admin` (string `@Value` fallback) | All; T explicitly `admin` | S, T; `APP_ADMIN_USERNAME` via Spring environment mapping |
| `app.admin.password` | `<redacted>`; no code fallback | All; T supplies test-only value | S, T; `APP_ADMIN_PASSWORD` via Spring environment mapping |
| `logging.level.com.photoalbum` | `DEBUG` (log-level string) | D=`INFO`; T=`DEBUG` | B, D, T |
| `logging.level.org.springframework.web` | `DEBUG` | D=`WARN`; inherited by T | B, D |
| `logging.level.org.hibernate.SQL` | Not explicitly set in base | D=`DEBUG` | D |

The Docker file repeats each of the three `app.file-upload.*` defaults twice with identical values. These are duplicates, not additional properties.

Resolution for supplied configuration is Spring command-line arguments/system properties/environment overrides before profile-specific properties, then base properties, then explicitly coded placeholder fallbacks. Compose separately resolves `${NAME:-default}` from its interpolation environment and rejects missing/empty `${NAME:?...}` credentials before containers start. A `.env` entry only reaches the application when explicitly passed through Compose or exported into its process.

### Compose and environment bindings

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `ORACLE_PASSWORD` | `<redacted>`; required, no fallback | Oracle container | `.env.example` → Compose environment |
| `APP_USER` | `photoalbum` | Oracle container | `.env.example`; Compose `${APP_USER:-photoalbum}` |
| `APP_USER_PASSWORD` | `<redacted>`; required, no fallback | Oracle container | `.env.example` → Compose environment |
| `SPRING_DATASOURCE_URL` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` | Application container | Compose literal |
| `SPRING_DATASOURCE_USERNAME` | `${APP_USER:-photoalbum}` | Application container | Compose interpolation |
| `SPRING_DATASOURCE_PASSWORD` | `<redacted>`; bound from required `APP_USER_PASSWORD` | Application container | Compose interpolation |
| `APP_ADMIN_USERNAME` | `${APP_ADMIN_USERNAME:-admin}` | Application container | `.env.example` → Compose |
| `APP_ADMIN_PASSWORD` | `<redacted>`; required, no fallback | Application container | `.env.example` → Compose |

### Azure setup settings, separate from application runtime

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `RESOURCE_GROUP` | `photo-album-resources-<random hexadecimal suffix>` | Provisioning only | `azure-setup.ps1`; written to `.env` |
| `LOCATION` | `westus3` | Provisioning only | Script; written to `.env` |
| `ACR_NAME` | `photoalbumacr<random integer>` | Provisioning only | Script; written to `.env` |
| ACR SKU / administrator access | `Basic` / `true` | Provisioning only | Script CLI flags |
| `POSTGRES_SERVER_NAME` | `<RESOURCE_GROUP>-postgresql` | Provisioning only | Script |
| `POSTGRES_DATABASE_NAME` | `photoalbum` | Provisioning only | Script |
| `POSTGRES_ADMIN_USER` | Environment override; otherwise `photoalbum_admin` | Provisioning only | Script input |
| `POSTGRES_ADMIN_PASSWORD` | `<redacted>`; environment override or generated | Provisioning only | Script input/generator |
| `POSTGRES_APP_USER` | Environment override; otherwise `photoalbum` | Provisioning only | Script input |
| `POSTGRES_APP_PASSWORD` | `<redacted>`; environment override or generated | Provisioning only | Script input/generator |
| PostgreSQL version / SKU | `15` / `Standard_D4ads_v5` | Provisioning only | Script CLI flags |
| PostgreSQL storage / backup retention | `32` GiB / `7` days | Provisioning only | Script CLI flags |
| PostgreSQL public access / Azure-services firewall rule | `0.0.0.0`; also current public IP allowed | Provisioning only | Script; current IP obtained from `https://api.ipify.org` |
| `POSTGRES_SERVER` | `<POSTGRES_SERVER_NAME>.postgres.database.azure.com` | Provisioning output | Process environment and `.env` |
| `POSTGRES_USER` | Value of `POSTGRES_APP_USER` | Provisioning output | Process environment and `.env` |
| `POSTGRES_PASSWORD` | `<redacted>`; value of `POSTGRES_APP_PASSWORD` | Provisioning output | Process environment and `.env` |
| `POSTGRES_CONNECTION_STRING` | `jdbc:postgresql://<server-FQDN>:5432/photoalbum` | Provisioning output | Process environment and `.env`; URL has no embedded credentials |
| `AKS_CLUSTER_NAME` | `<RESOURCE_GROUP>-aks` | Provisioning output | `.env` |

These `POSTGRES_*` names are not mapped to `spring.datasource.*` in the current application or Compose definition. Current build/runtime configuration still selects Oracle; PostgreSQL provisioning alone does not configure the application to use PostgreSQL. The setup script replaces `.env` with its Azure output rather than merging the Oracle/admin template settings.

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| `photoalbum-java-app` | `JAVA_OPTS="-Xmx512m -Xms256m"`; `java $JAVA_OPTS -jar app.jar`; `SPRING_PROFILES_ACTIVE=docker`; port `8080:8080`; `restart: on-failure` | JVM maximum heap 512 MiB, initial heap 256 MiB; no container memory/CPU limit | No explicit replica count; normal Compose deployment creates one |
| `oracle-db` | Image-provided entrypoint; environment credentials; port `1521:1521`; named `oracle_data` volume | No enforced memory/CPU limit; README recommends at least 4 GB available for Oracle | No explicit replica count; normal Compose deployment creates one |
| Manual Maven application | README: `mvn spring-boot:run`; local datasource example `jdbc:oracle:thin:@localhost:1521:XE` | No explicit heap/resource settings | Not specified |
| Azure AKS infrastructure | `Standard_D8ds_v5` node VM size; no application pod manifest | Node SKU selected, but no per-pod CPU/memory requests or limits | Two nodes; application replicas/autoscaling unspecified |
| Azure PostgreSQL infrastructure | PostgreSQL 15, `Standard_D4ads_v5`, storage 32 GiB | Service SKU selected; no application JVM relationship | One server creation; no HA/scaling flags specified |

No application startup `-D` system properties, readiness probe, autoscaler, or application resource-to-heap mapping is defined. The 512 MiB Java maximum heap is not a container memory limit and does not include other process memory. `-DskipTests` is a build flag, not a runtime setting.

## Startup Dependency Chain

1. **Compose interpolation → required environment values**: `ORACLE_PASSWORD`, `APP_USER_PASSWORD`, and `APP_ADMIN_PASSWORD` must be supplied before services can be created.
2. **Oracle container → database initialization**: persistent data volume and `oracle-init` directory are mounted; the container uses `APP_USER`/`APP_USER_PASSWORD` to provision its application user. Initialization SQL grants privileges to the literal `photoalbum` user; changing `APP_USER` alone does not update those statements.
3. **Initialization shell → fixed wait**: `oracle-init/create-user.sh` checks required credentials, defaults `APP_USER=photoalbum`, waits 30 seconds, then uses SQL*Plus with administrator credentials to create/grant the application user if absent.
4. **Application container → Oracle healthy**: Compose `depends_on.oracle-db.condition=service_healthy`; image-provided `healthcheck.sh` runs every `30s`, timeout `10s`, retries `15`, start period `180s`. No `dockerize` or separate application readiness check is configured.
5. **Application context → datasource and admin configuration**: datasource and security beans require their configured credentials; there is no remote configuration/discovery startup tier.
6. **Azure setup, separate path**: existing Azure CLI login/default subscription → resource group → ACR → two-node AKS → attach ACR pull permissions → PostgreSQL → database/firewall → obtain FQDN → fixed 30-second wait → user/grant commands → environment/`.env` output. This provisions infrastructure; it does not deploy or establish readiness for the Java application.

`oracle-init/healthcheck.sql` contains `SELECT 1 FROM DUAL`, but Compose points to the image's `healthcheck.sh`, not this SQL file. Some Azure grant commands catch errors and continue; completion of the script is not evidence that the application is ready.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrator password | Operator environment / ignored `.env` → Oracle container environment; `<redacted>` |
| `APP_USER_PASSWORD` → `SPRING_DATASOURCE_PASSWORD` → `spring.datasource.password` | Application database password | Operator environment / ignored `.env` → database and application environments; `<redacted>` |
| `APP_ADMIN_PASSWORD` → `app.admin.password` | Application administrator password | Operator environment / ignored `.env` → application environment; `<redacted>` |
| Test `spring.datasource.password` | Test datasource credential | `src/test/resources/application-test.properties`; explicitly empty; `<redacted>` |
| Test `app.admin.password` | Test-only administrator credential | `src/test/resources/application-test.properties`; `<redacted>` |
| `POSTGRES_ADMIN_PASSWORD` | Azure PostgreSQL administrator password | Environment override or generated in PowerShell; CLI command argument; `<redacted>` |
| `POSTGRES_APP_PASSWORD` → `POSTGRES_PASSWORD` | Azure PostgreSQL application password | Environment override or generated in PowerShell; process environment and ignored `.env`; `<redacted>` |

### Secrets Provisioning Workflow

**Local containers:** copy `.env.example` to `.env`, replace credential placeholders with unique values, then run Compose. Compose validates required values, passes Oracle administrator/schema credentials to the database container and the schema password to the Java container as `SPRING_DATASOURCE_PASSWORD`. It passes administrator credentials separately as `APP_ADMIN_USERNAME`/`APP_ADMIN_PASSWORD`. Spring resolves the application configuration from those process variables; `SecurityConfig` BCrypt-encodes the configured administrator password into an in-memory user store.

**Oracle initialization:** the database container provisions the schema user from its environment; mounted scripts apply schema-scoped grants and verify the user. The shell initialization also consumes administrator/schema environment credentials. Credentials are not retrieved from a secret-management service.

**Azure infrastructure:** the script uses the already authenticated Azure CLI identity/default subscription. PostgreSQL passwords come from `POSTGRES_ADMIN_PASSWORD` and `POSTGRES_APP_PASSWORD` or a cryptographic random generator with default length 24. It supplies credentials to provisioning/SQL commands, exports application connection variables, and writes the application password to the git-ignored `.env`. The script attaches ACR to AKS for image-pull permission; this is not database managed-identity authentication. No application Key Vault binding, service principal workflow, Kubernetes Secret creation, or application deployment binding is defined.

`.gitignore` excludes `.env` and `.env.*` while permitting `.env.example`. The environment file is plaintext, not encrypted storage. No Jasypt, sealed secrets, Vault integration, or automated secret rotation is configured. The PostgreSQL output file does not supply the current Compose Oracle/admin requirements.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| Dedicated feature-flag framework | None found | No LaunchDarkly, Unleash, or equivalent dependency/configuration |
| Conditional Spring features | None found | No `@ConditionalOnProperty`, `@ConditionalOnExpression`, or `@Profile` application declarations |
| Operational switches, not business feature flags | Encoding enabled/forced; SQL logging enabled except tests | Spring properties listed above |
| Infrastructure cleanup switches | Unset/false: `Force`, `AcrOnly`, `AksOnly` | `azure-reset.ps1` invocation |

There are no repository-defined A/B tests or gradual-rollout settings. Runtime profile selection and upload settings are configuration, not a feature-flag system.

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Application artifact | `1.0.0` | `pom.xml` |
| Spring Boot parent/starter baseline | `2.7.18` | `pom.xml` |
| Java target/compiler source/compiler target | Java 8 (`1.8` / `8` / `8`) | `pom.xml` |
| Docker build image / Maven | `maven:3.9.6-eclipse-temurin-8` / Maven `3.9.6` | `Dockerfile` |
| Docker Java runtime image | `eclipse-temurin:8-jre`; exact patch not pinned | `Dockerfile` |
| Spring Boot Maven plugin | Parent-managed; no explicit child version | `pom.xml` |
| Spring Framework, Spring Security, Hibernate, Thymeleaf, Jackson, embedded Tomcat | Spring Boot parent-managed; no explicit versions in project POM | Starter dependencies in `pom.xml`; resolved dependency graph not regenerated |
| Oracle JDBC `ojdbc8` | Parent-managed; no explicit project version | `pom.xml` |
| Commons IO | `2.11.0` | `pom.xml` |
| H2 / Spring Boot test starter / DevTools | Parent-managed; no explicit project versions | `pom.xml` |
| Oracle container | `gvenzl/oracle-free:latest`; comment identifies Free 23ai, tag is mutable | `docker-compose.yml` |
| Oracle documentation reference | Oracle 21c XE; differs from current Compose image | `README.md` |
| Azure PostgreSQL | `15` | `azure-setup.ps1`; no matching current application PostgreSQL driver/configuration |
| Bootstrap frontend library | `5.3.0` | CDN references in `src/main/resources/templates/*.html` |
| Docker, Compose, host Maven, Azure CLI, PowerShell, AKS/Kubernetes | Not pinned | No corresponding explicit version constraints in inspected application/deployment sources |

> Note: Some configuration sources or properties could not be fully identified. Inventory describes checked-in defaults and code references, not live environment values, remotely provisioned resources, or a newly resolved dependency graph.
