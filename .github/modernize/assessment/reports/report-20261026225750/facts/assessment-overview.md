# Assessment Overview

Supplementary analysis of the checked-in application. These documents describe
source and configuration evidence, not a verified running deployment.

| Document | Description |
|---|---|
| [Architecture diagram](architecture-diagram.md) | Application layers, deployment topology, and component relationships. |
| [Dependency map](dependency-map.md) | Declared libraries, dependency management, and version-resolution limitations. |
| [API and service contracts](api-service-contracts.md) | HTTP endpoints, request and response contracts, and communication sequences. |
| [Data architecture](data-architecture.md) | Entity model, database ownership, persistence queries, and data handling. |
| [Configuration inventory](configuration-inventory.md) | Profiles, externalized settings, environment variables, and deployment configuration, with sensitive values redacted. |
| [Business workflows](business-workflows.md) | Upload, browsing, retrieval, deletion, and related business rules. |

Security findings are provided in the [assessment report](../report.md) and
[security assessment](../security/security-assessment.md). The latter includes
coverage and exploitability limitations; raw scan results accompany it.
