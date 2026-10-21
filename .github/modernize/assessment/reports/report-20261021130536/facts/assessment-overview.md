# Assessment overview

Supplementary documentation for the Photo Album application assessment:

| Document | Description |
| --- | --- |
| [Architecture diagram](architecture-diagram.md) | Application components, deployment boundaries, and external dependencies. |
| [Dependency map](dependency-map.md) | Maven dependencies, framework relationships, and runtime integrations. |
| [API and service contracts](api-service-contracts.md) | HTTP endpoints, request and response contracts, and service interactions. |
| [Data architecture](data-architecture.md) | Photo data model, Oracle persistence, and schema lifecycle. |
| [Configuration inventory](configuration-inventory.md) | Runtime profiles, external settings, and deployment configuration. |
| [Business workflows](business-workflows.md) | Gallery browsing, photo uploads, downloads, and deletion flows. |

## Assessment scope and limitations

The core assessment targets Java 25 and Azure App Service, Azure Kubernetes Service, and Azure Container Apps on Linux and Windows. AppCAT completed source analysis but reported that dependency output was unavailable. The separate CVE scan resolved 101 Maven dependencies and queried GitHub advisories using unauthenticated API requests after authenticated CLI requests failed.

The merged security report includes only high and critical CVE findings. Dependency-version matches do not establish that an advisory's exploitation prerequisites are present in this application. CWE results are a static assessment of the existing application, not a penetration test or a guarantee that no other vulnerabilities exist.
