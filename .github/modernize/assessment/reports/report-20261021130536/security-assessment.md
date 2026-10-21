# Security Assessment Report

**Generated:** 2026-10-21T13:15:21.598469+00:00

## Summary

| Metric | Count |
| --- | --- |
| TotalFindings | 63 |
| CveCount | 60 |
| CweCount | 3 |
| TotalRulesAssessed | 59 |
| RulesPassed | 56 |

### By severity

| Severity | Count |
| --- | --- |
| mandatory | 60 |
| optional | 1 |
| potential | 2 |

## Scope and limitations

- Static source assessment only; no dynamic penetration testing or deployment validation was performed.
- Maven dependency:tree resolved 101 dependencies. Authenticated GitHub CLI requests failed; unauthenticated GitHub API requests succeeded, including pagination.
- Only high and critical CVE findings are included (60 of 120 dependency-version matches). Affected versions are not proof that application-specific exploitation prerequisites are satisfied.
- AppCAT completed source analysis but reported dependency output unavailable; dependency assessment is supplied by the separate Maven/GitHub advisory scan.

## CVE Findings (Dependency Vulnerabilities)

### CVE-2026-47884: Spring Framework Improper Path Limitation in XsltView

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-47884](https://github.com/advisories/GHSA-pc63-qcmh-9cmg)
Severity: CRITICAL
Affected dependencies: org.springframework:spring-webmvc:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-65905: Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-65905](https://github.com/advisories/GHSA-9xv2-5v5q-p794)
Severity: CRITICAL
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.121 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-65182: Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-65182](https://github.com/advisories/GHSA-gcx9-497g-6cp6)
Severity: CRITICAL
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.121 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-68525: Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-68525](https://github.com/advisories/GHSA-h3x4-894j-xpx5)
Severity: CRITICAL
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.121 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41850: Spring Framework Algorithmic Denial of Service via SpEL Expressions

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-41850](https://github.com/advisories/GHSA-r5w3-xv2f-j59q)
Severity: HIGH
Affected dependencies: org.springframework:spring-expression:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41849: Spring Framework Denial of Service via Integer Overflow in SpEL Expressions

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-41849](https://github.com/advisories/GHSA-775g-4xr8-78h8)
Severity: HIGH
Affected dependencies: org.springframework:spring-expression:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41845: Spring Framework Cross-site Scripting via JavaScriptUtils

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-41845](https://github.com/advisories/GHSA-3chg-m5w7-qfv5)
Severity: HIGH
Affected dependencies: org.springframework:spring-webmvc:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41842: Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-41842](https://github.com/advisories/GHSA-x23c-287f-qqv5)
Severity: HIGH
Affected dependencies: org.springframework:spring-webmvc:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41284: Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-41284](https://github.com/advisories/GHSA-gx5v-xp9w-j4cg)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.118 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-43512: Apache Tomcat - Digest authenticator will authenticate any unknown user

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-43512](https://github.com/advisories/GHSA-h6fc-48rj-7qqh)
Severity: CRITICAL
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.118 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-43513: Apache Tomcat: LockOutRealm treats user names as case-sensitive

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-43513](https://github.com/advisories/GHSA-5mp6-jrq3-r938)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.118 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-43515: Apache Tomcat - Security constraints not correctly applied

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-43515](https://github.com/advisories/GHSA-5m62-pw8w-7w9f)
Severity: CRITICAL
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.118 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41293: Apache Tomcat - HTTP/2 request headers not validated

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-41293](https://github.com/advisories/GHSA-r29c-68gh-xp6x)
Severity: CRITICAL
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.118 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-42498: Apache Tomcat - WebSocket authentication header exposure

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-42498](https://github.com/advisories/GHSA-fv25-8xcx-gqjc)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.118 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41901: Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:40

[CVE-2026-41901](https://github.com/advisories/GHSA-c9ph-gxww-7744)
Severity: CRITICAL
Affected dependencies: org.thymeleaf:thymeleaf:3.0.15.RELEASE (compile; via spring-boot-starter-thymeleaf at pom.xml:40). Upgrade to 3.1.5.RELEASE or a later patched release.; org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (compile; via spring-boot-starter-thymeleaf at pom.xml:40). Upgrade to 3.1.5.RELEASE or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-40478: Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:40

[CVE-2026-40478](https://github.com/advisories/GHSA-xjw8-8c5c-9r79)
Severity: CRITICAL
Affected dependencies: org.thymeleaf:thymeleaf:3.0.15.RELEASE (compile; via spring-boot-starter-thymeleaf at pom.xml:40). Upgrade to 3.1.4.RELEASE or a later patched release.; org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (compile; via spring-boot-starter-thymeleaf at pom.xml:40). Upgrade to 3.1.4.RELEASE or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-40477: Improper restriction of the scope of accessible objects in Thymeleaf expressions

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:40

[CVE-2026-40477](https://github.com/advisories/GHSA-r4v4-5mwr-2fwr)
Severity: CRITICAL
Affected dependencies: org.thymeleaf:thymeleaf:3.0.15.RELEASE (compile; via spring-boot-starter-thymeleaf at pom.xml:40). Upgrade to 3.1.4.RELEASE or a later patched release.; org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (compile; via spring-boot-starter-thymeleaf at pom.xml:40). Upgrade to 3.1.4.RELEASE or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-34483: Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-34483](https://github.com/advisories/GHSA-rv64-5gf8-9qq8)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.116 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-34487: Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-34487](https://github.com/advisories/GHSA-x4m4-345f-5h5g)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.117 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-24880: Apache Tomcat has an HTTP Request/Response Smuggling vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-24880](https://github.com/advisories/GHSA-563x-q5rq-57qp)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.116 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-24734: Apache Tomcat has an Improper Input Validation vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2026-24734](https://github.com/advisories/GHSA-mgp5-rv84-w37q)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.115 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-55752: Apache Tomcat Vulnerable to Relative Path Traversal

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2025-55752](https://github.com/advisories/GHSA-wmwf-9ccg-fff5)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.109 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-48989: Apache Tomcat Improper Resource Shutdown or Release vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2025-48989](https://github.com/advisories/GHSA-gqp3-2cvr-x8m3)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.108 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-53506: Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2025-53506](https://github.com/advisories/GHSA-25xr-qj8w-c4vf)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.107 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-52520: Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2025-52520](https://github.com/advisories/GHSA-wr62-c79q-cv37)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.107 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-48988: Apache Tomcat - DoS in multipart upload

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2025-48988](https://github.com/advisories/GHSA-h3gc-qfqq-6h8f)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.106 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-24813: Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2025-24813](https://github.com/advisories/GHSA-83qj-6fr2-vhqg)
Severity: CRITICAL
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.99 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-56337: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-56337](https://github.com/advisories/GHSA-27hp-xhwr-wr2m)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.98 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-38819: Spring Framework Path Traversal vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-38819](https://github.com/advisories/GHSA-g5vr-rgqm-vf78)
Severity: HIGH
Affected dependencies: org.springframework:spring-webmvc:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-50379: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-50379](https://github.com/advisories/GHSA-5j33-cvvr-w245)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.98 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-38286: Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-38286](https://github.com/advisories/GHSA-7jqf-v358-p8g7)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.90 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-38816: Path traversal vulnerability in functional web frameworks

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-38816](https://github.com/advisories/GHSA-cx7f-g6mp-7hqm)
Severity: HIGH
Affected dependencies: org.springframework:spring-webmvc:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-34750: Apache Tomcat - Denial of Service

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-34750](https://github.com/advisories/GHSA-wm9w-rjj3-j356)
Severity: HIGH
Affected dependencies: org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 9.0.90 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-22262: Spring Framework URL Parsing with Host Validation

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-22262](https://github.com/advisories/GHSA-2wrp-6fg6-hmc5)
Severity: HIGH
Affected dependencies: org.springframework:spring-web:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 5.3.34 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-22259: Spring Framework URL Parsing with Host Validation Vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-22259](https://github.com/advisories/GHSA-hgjh-9rj2-g67j)
Severity: HIGH
Affected dependencies: org.springframework:spring-web:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 5.3.33 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-22243: Spring Web vulnerable to Open Redirect or Server Side Request Forgery

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2024-22243](https://github.com/advisories/GHSA-ccgv-vj62-xf9h)
Severity: HIGH
Affected dependencies: org.springframework:spring-web:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 5.3.32 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2023-6481: Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2023-6481](https://github.com/advisories/GHSA-gm62-rw4g-vrc4)
Severity: HIGH
Affected dependencies: ch.qos.logback:logback-core:1.2.12 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 1.2.13 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2023-6378: logback serialization vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2023-6378](https://github.com/advisories/GHSA-vmq6-5m68-f53m)
Severity: HIGH
Affected dependencies: ch.qos.logback:logback-core:1.2.12 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 1.2.13 or a later patched release.; ch.qos.logback:logback-classic:1.2.12 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 1.2.13 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2022-1471: SnakeYaml Constructor Deserialization Remote Code Execution

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2022-1471](https://github.com/advisories/GHSA-mjmj-j48q-9wg2)
Severity: HIGH
Affected dependencies: org.yaml:snakeyaml:1.30 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 2.0 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2022-25857: Uncontrolled Resource Consumption in snakeyaml

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2022-25857](https://github.com/advisories/GHSA-3mc7-4q67-w48m)
Severity: HIGH
Affected dependencies: org.yaml:snakeyaml:1.30 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 1.31 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2016-1000027: Pivotal Spring Framework contains unsafe Java deserialization methods

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:34

[CVE-2016-1000027](https://github.com/advisories/GHSA-4wrc-f8pq-fpqp)
Severity: CRITICAL
Affected dependencies: org.springframework:spring-web:5.3.31 (compile; via spring-boot-starter-web at pom.xml:34). Upgrade to 6.0.0 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-41716: Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:46

[CVE-2026-41716](https://github.com/advisories/GHSA-9fw2-h3hf-293r)
Severity: HIGH
Affected dependencies: org.springframework.data:spring-data-commons:2.7.18 (compile; via spring-boot-starter-data-jpa at pom.xml:46). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-22732: Spring Security HTTP Headers Are not Written Under Some Conditions

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:65

[CVE-2026-22732](https://github.com/advisories/GHSA-mf92-479x-3373)
Severity: CRITICAL
Affected dependencies: org.springframework.security:spring-security-web:5.7.11 (compile; via spring-boot-starter-security at pom.xml:65). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-22228: Spring Security Does Not Enforce Password Length

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:65

[CVE-2025-22228](https://github.com/advisories/GHSA-mg83-c7gq-rv5c)
Severity: HIGH
Affected dependencies: org.springframework.security:spring-security-crypto:5.7.11 (compile; via spring-boot-starter-security at pom.xml:65). Upgrade to 5.7.16 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-38821: Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:65

[CVE-2024-38821](https://github.com/advisories/GHSA-c4q5-6c82-3qpw)
Severity: CRITICAL
Affected dependencies: org.springframework.security:spring-security-web:5.7.11 (compile; via spring-boot-starter-security at pom.xml:65). Upgrade to 5.7.13 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-22257: Erroneous authentication pass in Spring Security

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:65

[CVE-2024-22257](https://github.com/advisories/GHSA-f3jh-qvm4-mg39)
Severity: HIGH
Affected dependencies: org.springframework.security:spring-security-core:5.7.11 (compile; via spring-boot-starter-security at pom.xml:65). Upgrade to 5.7.12 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-89425: jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:78

[CVE-2026-89425](https://github.com/advisories/GHSA-7hhh-6rmp-j9qf)
Severity: HIGH
Affected dependencies: com.fasterxml.jackson.core:jackson-core:2.13.5 (compile; via spring-boot-starter-json at pom.xml:78). Upgrade to 2.18.11 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-91777: jackson-databind quadratic forward-reference completion

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:78

[CVE-2026-91777](https://github.com/advisories/GHSA-cxp5-3px4-pw24)
Severity: HIGH
Affected dependencies: com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; via spring-boot-starter-json at pom.xml:78). Upgrade to 2.18.11 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-91776: jackson-databind retains every unknown raw type ID

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:78

[CVE-2026-91776](https://github.com/advisories/GHSA-wv8q-qhhj-9h54)
Severity: HIGH
Affected dependencies: com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; via spring-boot-starter-json at pom.xml:78). Upgrade to 2.18.11 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-68494: jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:78

[CVE-2026-68494](https://github.com/advisories/GHSA-r7wm-3cxj-wff9)
Severity: HIGH
Affected dependencies: com.fasterxml.jackson.core:jackson-core:2.13.5 (compile; via spring-boot-starter-json at pom.xml:78). Upgrade to 2.18.8 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-54513: jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:78

[CVE-2026-54513](https://github.com/advisories/GHSA-rmj7-2vxq-3g9f)
Severity: HIGH
Affected dependencies: com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; via spring-boot-starter-json at pom.xml:78). Upgrade to 2.18.8 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-54512: jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:78

[CVE-2026-54512](https://github.com/advisories/GHSA-j3rv-43j4-c7qm)
Severity: HIGH
Affected dependencies: com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; via spring-boot-starter-json at pom.xml:78). Upgrade to 2.18.8 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-24400: AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:84

[CVE-2026-24400](https://github.com/advisories/GHSA-rqfh-9r24-8c9r)
Severity: HIGH
Affected dependencies: org.assertj:assertj-core:3.22.0 (test; via spring-boot-starter-test at pom.xml:84). Upgrade to 3.27.7 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-52999: jackson-core can throw a StackoverflowError when processing deeply nested data

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:78

[CVE-2025-52999](https://github.com/advisories/GHSA-h46c-h94j-95f3)
Severity: HIGH
Affected dependencies: com.fasterxml.jackson.core:jackson-core:2.13.5 (compile; via spring-boot-starter-json at pom.xml:78). Upgrade to 2.15.0 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2024-47554: Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:71

[CVE-2024-47554](https://github.com/advisories/GHSA-78wr-2p64-hpwj)
Severity: HIGH
Affected dependencies: commons-io:commons-io:2.11.0 (compile; via commons-io at pom.xml:71). Upgrade to 2.14.0 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-40973: Spring Boot accepts predictable temp directory without ownership verification

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:98

[CVE-2026-40973](https://github.com/advisories/GHSA-wwpq-f5c3-7hvx)
Severity: HIGH
Affected dependencies: org.springframework.boot:spring-boot:2.7.18 (compile; via spring-boot-devtools at pom.xml:98). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2026-40972: Spring Boot DevTools remote secret comparison is vulnerable to timing attacks

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:98

[CVE-2026-40972](https://github.com/advisories/GHSA-56v8-86gj-66jp)
Severity: HIGH
Affected dependencies: org.springframework.boot:spring-boot-devtools:2.7.18 (compile; via spring-boot-devtools at pom.xml:98). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-41249: Spring Framework annotation detection mechanism may result in improper authorization

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:84

[CVE-2025-41249](https://github.com/advisories/GHSA-jmp9-x22r-554x)
Severity: HIGH
Affected dependencies: org.springframework:spring-core:5.3.31 (compile; via spring-boot-starter-test at pom.xml:84). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2025-22235: Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:98

[CVE-2025-22235](https://github.com/advisories/GHSA-rc42-6c7j-7h5r)
Severity: HIGH
Affected dependencies: org.springframework.boot:spring-boot:2.7.18 (compile; via spring-boot-devtools at pom.xml:98). No first patched version supplied for this affected release branch; move to a supported patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.

### CVE-2022-45868: Password exposure in H2 Database

- **Category:** CVE
- **Severity:** mandatory
- **Story points:** 1
- **Files:** pom.xml:91

[CVE-2022-45868](https://github.com/advisories/GHSA-22wj-vf5f-wrvj)
Severity: HIGH
Affected dependencies: com.h2database:h2:2.1.214 (test; via h2 at pom.xml:91). Upgrade to 2.2.220 or a later patched release.
Affected-version inventory only: exploitation prerequisites have not been established for this application.


## CWE Findings (Code-Level Vulnerabilities)

### CWE-789: Memory Allocation with Excessive Size Value

- **Category:** Code Quality
- **Severity:** potential
- **Story points:** 5
- **Files:** src/main/java/com/photoalbum/repository/PhotoRepository.java, src/main/java/com/photoalbum/controller/HomeController.java, src/main/java/com/photoalbum/model/Photo.java, src/main/java/com/photoalbum/config/SecurityConfig.java, Dockerfile

Unbounded aggregate BLOB allocation on public gallery requests: HomeController.index() at lines 37-41 calls PhotoServiceImpl.getAllPhotos() at lines 53-57, whose PhotoRepository.findAllOrderByUploadedAtDesc() query at lines 22-27 selects PHOTO_DATA for every row without a row/aggregate byte limit. Photo.photoData is a byte[] @Lob with default eager loading (lines 39-41), so the entire uploaded corpus is materialized in heap even though the template only needs metadata. Any anonymous caller can trigger this through GET / (SecurityConfig lines 54-58). Once normal authenticated uploads build a corpus near/exceeding the Docker JVM 512 MB heap (Dockerfile line 28), a single or concurrent anonymous gallery requests can exhaust heap. The 10 MB per-file limit does not bound this aggregate allocation; the attacker triggering reads does not need upload credentials.

### CWE-778: Insufficient Logging

- **Category:** Credentials & Secrets
- **Severity:** potential
- **Story points:** 3
- **Files:** src/main/java/com/photoalbum/config/SecurityConfig.java, src/main/resources/application-docker.properties, src/main/resources/application.properties

Authentication failures are not audit-logged under the supplied runtime configuration. SecurityConfig.securityFilterChain() (lines 46-61) protects POST /upload and /detail/*/delete with HTTP Basic but installs no logging authentication entry point, authentication failure listener, or audit handler. No authentication event listener exists elsewhere in src/main. Failed Basic authentication is rejected before the controller/service log statements execute. The configured log levels (application-docker.properties lines 32-35; application.properties lines 32-34) do not enable Spring Security DEBUG failure diagnostics, and no HTTP access log is enabled. Consequently failed credential attempts against these security-critical endpoints leave no application audit event identifying the failed login/source, impairing detection of credential attacks. This conclusion concerns supplied application logging, not any unprovided proxy/SIEM.

### CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')

- **Category:** Injection Attacks
- **Severity:** optional
- **Story points:** 8
- **Files:** src/main/resources/static/js/upload.js

DOM cross-site scripting: handleFiles() embeds the externally supplied File.name in validation errors at lines 71-82; showErrors() inserts those strings unescaped into innerHTML at lines 215-218. A victim selecting or dropping an attacker-supplied file with HTML/event-handler markup in its filename executes that markup in the gallery origin. This path runs before any authenticated upload and does not require successful server storage. The server-rendered gallery uses escaped Thymeleaf output; this finding is the client validation flow, not a claim of persistent XSS on normal gallery GET.
