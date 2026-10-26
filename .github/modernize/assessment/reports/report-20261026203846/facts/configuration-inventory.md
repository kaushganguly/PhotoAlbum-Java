# Configuration & Externalized Settings Inventory

Three Spring property files define 23 distinct file-backed keys across the base configuration and the `docker` and `test` runtime profiles. Container settings, an environment template, Java configuration, and Azure PowerShell scripts supply additional settings; credentials are externally supplied or generated, and all credential values are represented here as `[REDACTED]`.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| Base application settings | Spring properties | `src/main/resources/application.properties` | 19 keys; packaged application defaults and environment placeholders. |
| Docker profile | Spring properties | `src/main/resources/application-docker.properties` | 20 distinct keys, 23 assignments; three upload properties are repeated with identical values. |
| Test profile | Spring properties | `src/test/resources/application-test.properties` | 14 keys; H2 settings and test-only credentials `[REDACTED]`. |
| Environment template | Compose interpolation input | `.env.example` | Five variables covering Oracle and application credentials; values `[REDACTED]`. README instructs copying to `.env`. |
| Local environment file | External/local configuration | `.env` | Not present in inspected files; ignored by `.gitignore:201-204,251-252`. Can be supplied manually or written by Azure setup; these two workflows produce different keys. |
| Container service settings | Compose YAML | `docker-compose.yml` | Environment bindings, profile selection, ports, Oracle volume, network, dependency and health settings. |
| Image/build/startup settings | Dockerfile | `Dockerfile` | Build/runtime images, Maven commands, JVM options and entrypoint. |
| Build definition | Maven XML | `pom.xml` | Parent dependency management, Java target, dependencies and packaging plugin; no Maven profiles. |
| Security settings | Java configuration | `src/main/java/com/photoalbum/config/SecurityConfig.java:25-60` | Two `@Value` properties; in-memory administrator, BCrypt encoding and fixed HTTP Basic/security settings. |
| Upload setting consumers | Java property injection | `src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:35-44` | Injects size and MIME settings; also contains a fixed image-pixel limit, not an external property. |
| Test profile activation | Java annotation | `src/test/java/com/photoalbum/PhotoAlbumApplicationTests.java:7-8` | `@ActiveProfiles("test")`. |
| Oracle initialization | SQL and shell | `oracle-init/01-create-user.sql`, `02-verify-user.sql`, `create-user.sh`, `healthcheck.sql` | Mounted into the image initialization directory; schema provisioning, grants, verification and standalone health SQL. |
| Azure provisioning settings | PowerShell variables and generated environment | `azure-setup.ps1` | Resource naming, location, node sizing, PostgreSQL provisioning and generated `.env`; not an application deployment manifest. |
| Azure cleanup parameters | PowerShell parameters | `azure-reset.ps1:6-17` | Required resource group plus `Force`, `AcrOnly` and `AksOnly` switches. |
| Operator guidance | Markdown | `README.md` | Local datasource override and startup commands; some database/version guidance differs from executable configuration. |
| Repository automation | GitHub Actions YAML | `.github/workflows/squad-{ci,docs,heartbeat,insider-release,issue-assign,label-enforce,preview,promote,release,triage}.yml`; `.github/workflows/sync-squad-labels.yml` | Repository maintenance/release automation, not runtime Spring sources. CI and docs build steps are placeholders. |
| Dependency update settings | Dependabot YAML | `.github/dependabot.yml` | GitHub Actions updates only; weekly schedule, grouped actions, seven-day cooldown. |
| Developer-tool integration | JSON | `.copilot/mcp-config.json` | Example Trello MCP server via `npx -y @trello/mcp-server`; environment references `TRELLO_API_KEY` and `TRELLO_TOKEN`, values `[REDACTED]`. Not application configuration. |

No `bootstrap.*`, application YAML, Spring Cloud Config server, external configuration Git URI, Azure App Configuration, Consul, Vault, Key Vault, AWS secret/configuration service, or Kubernetes ConfigMap/Secret manifest was found in application/deployment sources. Assessment artifacts and skill/template material are not treated as deployed configuration.

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Default Maven build; no named profiles | Standard Maven invocation; no `<profiles>` in `pom.xml` | Java 8 JAR compilation and Spring Boot packaging | Spring Boot parent `2.7.18`; Web, Thymeleaf, Data JPA, Validation, Security, JSON; runtime `ojdbc8`; Commons IO; test starter and H2; optional DevTools; Spring Boot Maven plugin. |
| Container build path; not a Maven profile | Docker/Compose image build | Dependency preparation and executable JAR packaging | `mvn dependency:go-offline -B`, then `mvn clean package -DskipTests` (`Dockerfile:8,14`). |

Build properties are `java.version=1.8`, `maven.compiler.source=8`, `maven.compiler.target=8`, and `project.build.sourceEncoding=UTF-8` (`pom.xml:23-28`). Test scope and optional DevTools are dependency declarations, not profile activation conditions. No Gradle, MSBuild or JavaScript build definition was found.

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Base/default | No explicit active profile supplied | `src/main/resources/application.properties` | Oracle datasource, base logging, server and upload settings. No `spring.profiles.active` default in the file. |
| `docker` | Compose supplies `SPRING_PROFILES_ACTIVE=docker` | Base plus `src/main/resources/application-docker.properties` | Application logging `INFO`, Spring Web logging `WARN`, additional Hibernate SQL logging `DEBUG`; Oracle and upload settings largely restate base values. |
| `test` | `@ActiveProfiles("test")` in the context test | Base plus `src/test/resources/application-test.properties` on test classpath | H2 datasource and dialect, `create-drop`, SQL logging disabled, test upload path and credentials `[REDACTED]`. |

No `@Profile` beans, profile groups, profile includes, production-specific configuration or prescribed combined profiles were found. Standard Spring multi-profile activation is available, but no project-specific composition is configured.

## Properties Inventory

### Spring application and test configuration

Defaults below are repository defaults, not inferred framework defaults. Types are inferred from property names and injection targets; no additional external-property ranges are declared. References: base file lines 2-34; Docker file lines 3-35; test file lines 2-23; `SecurityConfig.java:36-37`.

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `server.port` | `8080` (integer TCP port) | Base; Docker repeats | Base:2; Docker:25 |
| `server.servlet.encoding.charset` | `UTF-8` (charset string) | Base; Docker repeats | Base:5; Docker:9 |
| `server.servlet.encoding.enabled` | `true` (boolean) | Base; Docker repeats | Base:6; Docker:10 |
| `server.servlet.encoding.force` | `true` (boolean) | Base; Docker repeats | Base:7; Docker:11 |
| `spring.datasource.url` | `${SPRING_DATASOURCE_URL:jdbc:oracle:thin:@oracle-db:1521/FREEPDB1}` (JDBC URL string) | Base/Docker; test: `jdbc:h2:mem:testdb` | Base:12; Docker:3; Test:2 |
| `spring.datasource.username` | `[REDACTED]`; optional `SPRING_DATASOURCE_USERNAME` reference with fallback | Base/Docker; test literal `[REDACTED]` | Base:13; Docker:4; Test:4 |
| `spring.datasource.password` | `[REDACTED]`; required `${SPRING_DATASOURCE_PASSWORD}`, no fallback | Base/Docker; test value `[REDACTED]` | Base:14; Docker:5; Test:5 |
| `spring.datasource.driver-class-name` | `oracle.jdbc.OracleDriver` (class name) | Base/Docker; test: `org.h2.Driver` | Base:15; Docker:6; Test:3 |
| `spring.jpa.database-platform` | `org.hibernate.dialect.OracleDialect` (class name) | Base/Docker; test: `org.hibernate.dialect.H2Dialect` | Base:18; Docker:14; Test:8 |
| `spring.jpa.hibernate.ddl-auto` | `create` (enum-like string) | Base/Docker; test: `create-drop` | Base:19; Docker:15; Test:9 |
| `spring.jpa.show-sql` | `true` (boolean) | Base/Docker; test: `false` | Base:20; Docker:16; Test:10 |
| `spring.jpa.properties.hibernate.format_sql` | `true` (boolean) | Base/Docker; inherited in test | Base:21; Docker:17 |
| `spring.servlet.multipart.max-file-size` | `10MB` (data size) | Base/Docker; inherited in test | Base:24; Docker:26 |
| `spring.servlet.multipart.max-request-size` | `50MB` (data size) | Base/Docker; inherited in test | Base:25; Docker:27 |
| `app.file-upload.max-file-size-bytes` | `10485760` (Java `long`) | Base/Docker/test | Base:28; Docker:20,28; Test:14; injected in `PhotoServiceImpl.java:43` |
| `app.file-upload.allowed-mime-types` | `image/jpeg,image/png,image/gif,image/webp` (comma-separated list, injected as `String[]`) | Base/Docker/test | Base:29; Docker:21,29; Test:15; injected in `PhotoServiceImpl.java:44` |
| `app.file-upload.max-files-per-upload` | `10` (integer-like value) | Base/Docker/test | Base:30; Docker:22,30; Test:16; no Java property consumer found |
| `app.file-upload.upload-path` | Not set in base; test: `target/test-uploads` (path string) | Test only | Test:13; no Java property consumer found |
| `logging.level.com.photoalbum` | `DEBUG` (logging level) | Docker: `INFO`; test: `DEBUG` | Base:33; Docker:33; Test:19 |
| `logging.level.org.springframework.web` | `DEBUG` (logging level) | Docker: `WARN`; inherited in test | Base:34; Docker:34 |
| `logging.level.org.hibernate.SQL` | No repository base value; Docker: `DEBUG` | Docker only | Docker:35 |
| `app.admin.username` | Java fallback `[REDACTED]`; externally overridable | Base/Docker use Java binding; test literal `[REDACTED]` | `SecurityConfig.java:36`; Test:22 |
| `app.admin.password` | `[REDACTED]`; required Java placeholder, no fallback | Base/Docker require external input; test literal `[REDACTED]` | `SecurityConfig.java:37`; Test:23 |

Resolution chain: Compose resolves `${...}` from its invocation environment/local `.env` before creating containers. The application receives only declared container environment entries; Spring does not itself load the root `.env` file. Spring then resolves its property sources: command-line arguments, JVM system properties and operating-system environment can override packaged property files; active-profile files override base settings. Environment names such as `APP_ADMIN_PASSWORD` map to `app.admin.password` through Spring environment resolution. The datasource placeholders explicitly reference `SPRING_DATASOURCE_*`.

### Oracle/container environment

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `ORACLE_PASSWORD` | `[REDACTED]`; required, nonempty Compose input using `:?` | Oracle container | `.env.example:6`; Compose:7 |
| `APP_USER` | `[REDACTED]`; Compose `:-` fallback | Oracle container; also mapped to application `SPRING_DATASOURCE_USERNAME` | `.env.example:9`; Compose:8,33 |
| `APP_USER_PASSWORD` | `[REDACTED]`; required, nonempty `:?` input | Oracle container; also mapped to application `SPRING_DATASOURCE_PASSWORD` | `.env.example:12`; Compose:9,34 |
| `SPRING_DATASOURCE_URL` | `jdbc:oracle:thin:@oracle-db:1521/FREEPDB1` | Application container; explicit Compose value, not root-variable interpolation | Compose:32 |
| `SPRING_DATASOURCE_USERNAME` | `[REDACTED]`; derived from `APP_USER` | Application container | Compose:33 |
| `SPRING_DATASOURCE_PASSWORD` | `[REDACTED]`; derived from `APP_USER_PASSWORD` | Application container | Compose:34 |
| `APP_ADMIN_USERNAME` | `[REDACTED]`; Compose `:-` fallback | Application container | `.env.example:16`; Compose:35 |
| `APP_ADMIN_PASSWORD` | `[REDACTED]`; required, nonempty `:?` input | Application container | `.env.example:17`; Compose:36 |

### Azure setup and cleanup settings

These are script variables/outputs, not Spring properties or an active PostgreSQL runtime profile (`azure-setup.ps1:26-41,117-158,267-299`).

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `RANDOM_SUFFIX` / `RESOURCE_GROUP` | Three random bytes formatted as six hexadecimal characters; `photo-album-resources-${RANDOM_SUFFIX}` | Setup | Script:26-27; resource group exported to `.env` |
| `LOCATION` | `westus3` | Setup | Script:28; exported to `.env` |
| `ACR_NAME` | `photoalbumacr` plus random integer below 99999 | Setup | Script:29; exported to `.env` |
| ACR SKU / admin access | `Basic` / enabled | Setup | Script:69-74 |
| `AKS_CLUSTER_NAME` | Resource group plus `-aks` | Setup | Script:87; `.env` output:295 |
| `POSTGRES_SERVER_NAME` | Resource group plus `-postgresql` | Setup | Script:31 |
| `PostgreSQL_SKU` | `Standard_D4ads_v5` | Setup | Script:32 |
| `POSTGRES_DATABASE_NAME` | `photoalbum` | Setup | Script:33 |
| `POSTGRES_ADMIN_USER` / `POSTGRES_APP_USER` | `[REDACTED]`; corresponding process environment or script fallback | Setup | Script:38,40 |
| `POSTGRES_ADMIN_PASSWORD` / `POSTGRES_APP_PASSWORD` | `[REDACTED]`; corresponding process environment or generated value | Setup | Script:39,41 |
| PostgreSQL storage / backup retention | `32` GiB / `7` days | Setup | Script:125-126 |
| PostgreSQL public-access/firewall values | `0.0.0.0`; `AllowAzureServices` rule; additional `AllowCurrentIP` rule from current public IP | Setup | Script:127,153-176 |
| Current-IP discovery URI | `https://api.ipify.org` | Setup | Script:167 |
| `DATASOURCE_URL` | `jdbc:postgresql://${SERVER_FQDN}:5432/photoalbum` | Setup | Script:267 |
| `POSTGRES_SERVER` | `${POSTGRES_SERVER_NAME}.postgres.database.azure.com` | Setup process environment and `.env` output | Script:274,287 |
| `POSTGRES_USER` / `POSTGRES_PASSWORD` | `[REDACTED]`; derived from PostgreSQL application account | Setup process environment and `.env` output | Script:275-276,288-289 |
| `POSTGRES_CONNECTION_STRING` | `[REDACTED]`; treat generated connection metadata as sensitive | Setup process environment and `.env` output | Script:277,290 |
| `ResourceGroupName` | No default; mandatory string | Cleanup | `azure-reset.ps1:6-8` |
| `Force` / `AcrOnly` / `AksOnly` | Switches; false unless supplied | Cleanup | `azure-reset.ps1:10-17` |

The setup script writes a new `.env` using `Out-File`, rather than merging with an existing Oracle/application `.env`. Its `POSTGRES_*` output is not mapped by the current Oracle Compose configuration; there is no PostgreSQL JDBC dependency or Spring PostgreSQL profile in `pom.xml`/resources. Script SQL grants also contain fixed account/database identifiers despite configurable provisioning variables.

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| Application image | `JAVA_OPTS="-Xmx512m -Xms256m"`; `sh -c "java $JAVA_OPTS -jar app.jar"`; working directory `/app`; exposed/published port `8080` | Initial heap 256 MiB, maximum heap 512 MiB; no Compose memory or CPU reservation/limit | One Compose container; no explicit replicas/autoscaling; `restart: on-failure` |
| Application in Compose | `SPRING_PROFILES_ACTIVE=docker`; datasource/admin environment bindings above; no configured JVM `-D` runtime arguments | Inherits image JVM settings; no enforced resource allocation | Same application container |
| Local application | README uses `mvn spring-boot:run` or `java -jar target/photo-album-1.0.0.jar`; local datasource URL must be supplied for a host database connection | No repository local JVM heap/CPU setting | Operator-managed process |
| Oracle container | `gvenzl/oracle-free:latest`; port `1521:1521`; initialization directory mounted; named volume `oracle_data:/opt/oracle/oradata` | No Compose memory/CPU limits; README recommends at least 4 GB available for the database/container environment | One container; persistent named volume |
| Azure AKS infrastructure | Node VM `Standard_D8ds_v5`; no committed application Deployment or per-pod settings | VM SKU selected, but no application requests/limits or heap-to-node mapping | `--node-count 2`; no autoscaler configuration |
| Azure PostgreSQL infrastructure | PostgreSQL `15`, SKU `Standard_D4ads_v5`, storage 32 GiB, retention 7 days | Compute chosen by SKU; no separate memory setting in script | One server creation; no explicit scaling/HA setting |

Sources: `Dockerfile:17-31`, `docker-compose.yml:3-44`, `azure-setup.ps1:30-32,85-91,117-127`, `README.md:30,140-158,170`. README's Oracle XE limits are documentation, not resource enforcement for the floating Oracle Free image. `-DskipTests` is a build option, not a runtime system property.

## Startup Dependency Chain

1. **Compose invocation → required environment inputs**: interpolation requires nonempty `ORACLE_PASSWORD`, `APP_USER_PASSWORD` and `APP_ADMIN_PASSWORD` before service creation (`docker-compose.yml:7,9,36`).
2. **Oracle container → database initialization**: database files use `oracle_data`; `./oracle-init` is mounted into `/container-entrypoint-initdb.d`. Image environment provisions the application account; SQL files grant/verify access. `create-user.sh` has required environment checks and a fixed 30-second sleep before its SQL connection, not a polling retry (`oracle-init/create-user.sh:9-22`).
3. **Application container → waits for → healthy Oracle container**: Compose `depends_on.oracle-db.condition=service_healthy`. The actual configured health command is image-provided `healthcheck.sh`, interval 30 seconds, timeout 10 seconds, 15 retries and start period 180 seconds (`docker-compose.yml:17-22,39-41`). The separate `oracle-init/healthcheck.sql` is not the command configured in Compose.
4. **Spring application → required datasource/admin properties and database**: the password placeholders have no application fallback. No application healthcheck, readiness probe, startup timeout, explicit connection retry policy or config/discovery-server dependency is configured. Compose restart-on-failure applies after process failure, not as an application readiness probe.
5. **Azure setup script, separate provisioning path**: Azure account context → resource group → ACR → two-node AKS → ACR attachment → PostgreSQL server/database → firewall rules → FQDN lookup → fixed 30-second wait → database account/grants → `.env` output (`azure-setup.ps1:45-299`). This is infrastructure ordering, not evidence that the application has been deployed or migrated.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `ORACLE_PASSWORD` | Oracle administrative password | Operator environment/local `.env` → Oracle container; `[REDACTED]` |
| `APP_USER`, `APP_USER_PASSWORD` | Application database credentials | `.env.example` template/local `.env` → Oracle and application container bindings; `[REDACTED]` |
| `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD` | Spring datasource credentials | Environment placeholders in base/Docker properties; `[REDACTED]` |
| `APP_ADMIN_USERNAME`, `APP_ADMIN_PASSWORD` / `app.admin.username`, `app.admin.password` | Application administrator credentials | Environment → Java property injection → in-memory user; `[REDACTED]` |
| Test datasource/admin properties | Test-only credentials | `src/test/resources/application-test.properties`; `[REDACTED]` |
| `POSTGRES_ADMIN_USER`, `POSTGRES_ADMIN_PASSWORD` | PostgreSQL administrator credentials | Setup process environment or generated password; CLI provisioning inputs; `[REDACTED]` |
| `POSTGRES_APP_USER`, `POSTGRES_APP_PASSWORD`; exported `POSTGRES_USER`, `POSTGRES_PASSWORD` | PostgreSQL application credentials | Setup environment/generation → SQL account creation → process environment and local `.env`; `[REDACTED]` |
| `POSTGRES_CONNECTION_STRING` | Connection metadata | Setup process environment/local `.env`; `[REDACTED]` |
| `secrets.COPILOT_ASSIGN_TOKEN`, `secrets.GITHUB_TOKEN` | GitHub repository automation credentials | GitHub Actions secret references in issue-assignment/heartbeat and release/promote workflows; `[REDACTED]`; not passed to the Java application |
| `TRELLO_API_KEY`, `TRELLO_TOKEN` | Optional developer-tool API credentials | Environment references in `.copilot/mcp-config.json`; `[REDACTED]`; separate from application startup |

### Secrets Provisioning Workflow

- **Local/Compose**: operator copies `.env.example` to git-ignored `.env` and replaces placeholder credentials → Compose interpolates required inputs → Oracle receives administrative/application credentials → Java receives datasource credentials and administrator credentials. The application password has no packaged fallback. Oracle SQL initialization grants schema-scoped privileges; the SQL file uses a fixed schema identifier even though `APP_USER` is configurable.
- **Application access model**: the datasource uses database credentials; the administrator is held in an `InMemoryUserDetailsManager` with BCrypt password encoding (`SecurityConfig.java:28-42`). No external identity provider or secret-store client is configured.
- **Azure setup**: existing Azure CLI account context authenticates provisioning. `POSTGRES_ADMIN_PASSWORD` and `POSTGRES_APP_PASSWORD` come from the process environment when provided, otherwise from the script's `System.Security.Cryptography.RandomNumberGenerator` helper. Administrator credentials create the PostgreSQL application account and grants; application credentials are exported and persisted in `.env`. ACR admin access is enabled and AKS is attached to ACR. No explicit application managed identity, service-principal configuration, Key Vault policy or application-specific RBAC binding is declared.
- **Repository automation**: GitHub-provided/action secret references are consumed by repository workflows, not by an Azure application deployment workflow. No application secret publication to Kubernetes or cloud secret stores was found.
- **Storage/encryption boundary**: `.env` is ignored, but there is no repository-defined encryption-at-rest workflow, Jasypt, sealed secrets, DPAPI or vault integration. BCrypt protects the in-memory administrator representation; it does not encrypt source environment files.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| No dedicated application feature flags found | Not configured | No LaunchDarkly, Unleash, feature-management dependency, `@ConditionalOnProperty` or `@ConditionalOnExpression` found |
| `spring.servlet.encoding.enabled`, `spring.servlet.encoding.force` | `true` | Base/Docker properties; framework configuration switches, not rollout flags |
| `spring.jpa.show-sql` | Base/Docker `true`; test `false` | Runtime property files; diagnostic switch, not rollout flag |
| Cleanup `Force`, `AcrOnly`, `AksOnly` | False unless supplied | PowerShell command-line switches; operational controls only |

The `docker` and `test` profiles select environments rather than gradual-rollout behavior. No remote flag source or A/B configuration was identified.

## Framework & Runtime Versions

| Component | Version | Source |
|---|---|---|
| Application artifact | `com.photoalbum:photo-album:1.0.0`, JAR | `pom.xml:15-18` |
| Spring Boot parent/platform | `2.7.18` | `pom.xml:8-13` |
| Java language/compiler target | Java 8 (`1.8`; source/target `8`) | `pom.xml:23-27` |
| Docker build image / Maven | `maven:3.9.6-eclipse-temurin-8`; Maven `3.9.6` | `Dockerfile:2` |
| Docker Java runtime | `eclipse-temurin:8-jre`; Java 8, patch/image digest unpinned | `Dockerfile:17` |
| Spring Web, Data JPA, Security, Validation, Thymeleaf, JSON, DevTools and test starters | Managed by Spring Boot `2.7.18`; resolved individual versions not inspected | `pom.xml:30-100` |
| Hibernate / embedded servlet container | Transitive through Data JPA/Web starters; Boot-managed, no explicit repository version | `pom.xml:33-46` |
| Oracle JDBC | `com.oracle.database.jdbc:ojdbc8`; Boot-managed, no explicit version | `pom.xml:49-54` |
| Commons IO | `2.11.0` | `pom.xml:68-73` |
| H2 | Test-scoped; Boot-managed, no explicit version | `pom.xml:88-93` |
| Spring Boot Maven plugin | Parent-managed; no explicit plugin version | `pom.xml:103-109` |
| Oracle image | `gvenzl/oracle-free:latest`; comment says Oracle Free 23ai, actual version not pinned | `docker-compose.yml:2-4` |
| Azure PostgreSQL server | Major version `15` | `azure-setup.ps1:123` |
| AKS / Azure CLI / PowerShell / kubectl | Not version-pinned by repository deployment scripts | `azure-setup.ps1`; `azure-reset.ps1` |
| Repository GitHub Actions | Checkout `v4.4.0`, github-script `v7.1.0`, both commit-pinned; runner `ubuntu-latest` | `.github/workflows/*.yml` |
| Optional Trello MCP / Node.js / npm | MCP package and local Node/npm versions unpinned | `.copilot/mcp-config.json` |

> Note: Some configuration sources or properties could not be fully identified. This is a static repository inventory: local `.env`, deployed resource state, resolved dependency versions and floating image contents were not inspected. No builds, tests, deployments or credential retrieval were performed.
