# Security Assessment Report

**Generated:** 2026-10-26T05:24:48.407990+00:00

## Summary

| Metric | Count |
| --- | --- |
| TotalFindings | 110 |
| CveCount | 104 |
| CweCount | 6 |
| TotalRulesAssessed | 59 |
| RulesPassed | 53 |

CVE inclusion threshold: **medium**. All 101 resolved Maven dependencies were checked, including compile, runtime, and test scopes. Advisory version matches do not establish application exploitability. Sixteen low-severity matches remain in the raw CVE results but are excluded from this merged report.

### By severity

| Severity | Count |
| --- | --- |
| mandatory | 61 |
| optional | 46 |
| potential | 3 |

## Coverage and limitations

- Static source/data-flow assessment, not a penetration test, formal proof or guarantee of absence. NOT_FOUND means no confirmed pattern in reviewed application scope.
- No application execution, tests, builds, source modifications or commits performed. Maven dependency resolution only.
- Dependency version matches are valid findings even when advisory exploit prerequisites or application reachability are not established. All resolved compile/runtime/test dependencies included. Test and optional development dependency deployment is not assumed.
- Build plugin dependencies, container OS/JDK/Oracle image contents and externally CDN-loaded Bootstrap assets were not advisory-scanned. Resolved graph covers this Maven project and its transitive library dependencies, not every deployed artifact.
- Runtime/third-party implementation source, live database sizes, actual external authentication/audit systems and host file ACLs/umask were not inspected. CWE-732 exposure is conditional on default permissive file creation permissions; no current credential disclosure asserted.
- Authentication is required for upload/delete. Public gallery reads intentionally allow anonymous access.
- Assessment is limited to the requested 59 CWE rules and dependency advisories; it is not an exhaustive catalog of every possible CWE.
- Application .github/agents content was not read. Test/generated code excluded from CWE source assessment. Existing /tmp artifacts were not read or written by assessment commands; dependency resolution regenerated in project directory.

## CVE Findings (Dependency Vulnerabilities)

### CVE-2016-1000027: Pivotal Spring Framework contains unsafe Java deserialization methods

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2016-1000027](https://github.com/advisories/GHSA-4wrc-f8pq-fpqp): Pivotal Spring Framework contains unsafe Java deserialization methods

Severity: CRITICAL

- org.springframework:spring-web:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 6.0.0 => 6.0.0

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-1471: SnakeYaml Constructor Deserialization Remote Code Execution

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-1471](https://github.com/advisories/GHSA-mjmj-j48q-9wg2): SnakeYaml Constructor Deserialization Remote Code Execution

Severity: HIGH

- org.yaml:snakeyaml:1.30 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: <= 1.33 => 2.0

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-25857: Uncontrolled Resource Consumption in snakeyaml

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-25857](https://github.com/advisories/GHSA-3mc7-4q67-w48m): Uncontrolled Resource Consumption in snakeyaml

Severity: HIGH

- org.yaml:snakeyaml:1.30 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 1.31 => 1.31

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-38749: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38749](https://github.com/advisories/GHSA-c4r9-r8fh-9vj2): snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 1.31 => 1.31

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-38750: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38750](https://github.com/advisories/GHSA-hhhw-99gj-p3c3): snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 1.31 => 1.31

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-38751: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38751](https://github.com/advisories/GHSA-98wm-3w3q-mw94): snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 1.31 => 1.31

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-38752: snakeYAML before 1.32 vulnerable to Denial of Service due to Out-of-bounds Write

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38752](https://github.com/advisories/GHSA-9w3m-gqgf-c4p9): snakeYAML before 1.32 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 1.32 => 1.32

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-41854: Snakeyaml vulnerable to Stack overflow leading to denial of service

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-41854](https://github.com/advisories/GHSA-w37g-rhq8-7m4j): Snakeyaml vulnerable to Stack overflow leading to denial of service

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 1.32 => 1.32

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2022-45868: Password exposure in H2 Database 

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:91

[CVE-2022-45868](https://github.com/advisories/GHSA-22wj-vf5f-wrvj): Password exposure in H2 Database 

Severity: HIGH

- com.h2database:h2:2.1.214 [test; direct; pom.xml:91]. Advisory ranges => first patched: >= 1.4.198, < 2.2.220 => 2.2.220

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2023-51074: json-path Out-of-bounds Write vulnerability

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2023-51074](https://github.com/advisories/GHSA-pfh2-hfmq-phg5): json-path Out-of-bounds Write vulnerability

Severity: MEDIUM

- com.jayway.jsonpath:json-path:2.7.0 [test; transitive via spring-boot-starter-test; pom.xml:84]. Advisory ranges => first patched: >= 2.2.0, < 2.9.0 => 2.9.0

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2023-6378: logback serialization vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2023-6378](https://github.com/advisories/GHSA-vmq6-5m68-f53m): logback serialization vulnerability

Severity: HIGH

- ch.qos.logback:logback-classic:1.2.12 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 1.4.0, < 1.4.12 => 1.4.12; >= 1.3.0, < 1.3.12 => 1.3.12; < 1.2.13 => 1.2.13
- ch.qos.logback:logback-core:1.2.12 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 1.4.0, < 1.4.12 => 1.4.12; >= 1.3.0, < 1.3.12 => 1.3.12; < 1.2.13 => 1.2.13

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2023-6481: Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2023-6481](https://github.com/advisories/GHSA-gm62-rw4g-vrc4): Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data

Severity: HIGH

- ch.qos.logback:logback-core:1.2.12 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: = 1.4.13 => 1.4.14; = 1.3.13 => 1.3.14; = 1.2.12 => 1.2.13

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-12798: QOS.CH logback-core Expression Language Injection vulnerability

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-12798](https://github.com/advisories/GHSA-pr98-23f8-jwxv): QOS.CH logback-core Expression Language Injection vulnerability

Severity: MEDIUM

- ch.qos.logback:logback-core:1.2.12 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 1.4.0, < 1.5.13 => 1.5.13; < 1.3.15 => 1.3.15

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-22243: Spring Web vulnerable to Open Redirect or Server Side Request Forgery

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22243](https://github.com/advisories/GHSA-ccgv-vj62-xf9h): Spring Web vulnerable to Open Redirect or Server Side Request Forgery

Severity: HIGH

- org.springframework:spring-web:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 6.1.0, < 6.1.4 => 6.1.4; >= 6.0.0, < 6.0.17 => 6.0.17; >= 5.3.0, < 5.3.32 => 5.3.32; <= 5.2.25.RELEASE => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-22257: Erroneous authentication pass in Spring Security

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-22257](https://github.com/advisories/GHSA-f3jh-qvm4-mg39): Erroneous authentication pass in Spring Security

Severity: HIGH

- org.springframework.security:spring-security-core:5.7.11 [compile; transitive via spring-boot-starter-security; pom.xml:65]. Advisory ranges => first patched: < 5.7.12 => 5.7.12; >= 5.8.0, < 5.8.11 => 5.8.11; >= 6.0.0, < 6.1.8 => 6.1.8; >= 6.2.0, < 6.2.3 => 6.2.3

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-22259: Spring Framework URL Parsing with Host Validation Vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22259](https://github.com/advisories/GHSA-hgjh-9rj2-g67j): Spring Framework URL Parsing with Host Validation Vulnerability

Severity: HIGH

- org.springframework:spring-web:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 6.1.0, < 6.1.5 => 6.1.5; >= 6.0.0, < 6.0.18 => 6.0.18; < 5.3.33 => 5.3.33

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-22262: Spring Framework URL Parsing with Host Validation

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22262](https://github.com/advisories/GHSA-2wrp-6fg6-hmc5): Spring Framework URL Parsing with Host Validation

Severity: HIGH

- org.springframework:spring-web:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 5.3.34 => 5.3.34; >= 6.0.0, < 6.0.19 => 6.0.19; >= 6.1.0, < 6.1.6 => 6.1.6

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-23672: Denial of Service via incomplete cleanup vulnerability in Apache Tomcat

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-23672](https://github.com/advisories/GHSA-v682-8vv8-vpwr): Denial of Service via incomplete cleanup vulnerability in Apache Tomcat

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-websocket:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, <= 11.0.0-M16 => 11.0.0-M17; >= 10.1.0-M1, <= 10.1.18 => 10.1.19; >= 9.0.0-M1, <= 9.0.85 => 9.0.86; >= 8.5.0, <= 8.5.98 => 8.5.99

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-24549: Apache Tomcat Denial of Service due to improper input validation vulnerability for HTTP/2 requests

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-24549](https://github.com/advisories/GHSA-7w75-32cg-r6g2): Apache Tomcat Denial of Service due to improper input validation vulnerability for HTTP/2 requests

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 8.5.0, <= 8.5.98 => 8.5.99; >= 9.0.0-M1, <= 9.0.85 => 9.0.86; >= 10.1.0-M1, <= 10.1.18 => 10.1.19; >= 11.0.0-M1, <= 11.0.0-M16 => 11.0.0-M17

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-34750: Apache Tomcat - Denial of Service

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-34750](https://github.com/advisories/GHSA-wm9w-rjj3-j356): Apache Tomcat - Denial of Service

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.0-M21 => 11.0.0-M21; >= 10.1.0-M1, < 10.1.25 => 10.1.25; >= 9.0.0-M1, < 9.0.90 => 9.0.90; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38286: Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38286](https://github.com/advisories/GHSA-7jqf-v358-p8g7): Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.0-M21 => 11.0.0-M21; >= 10.1.0-M1, < 10.1.25 => 10.1.25; >= 9.0.13, < 9.0.90 => 9.0.90; >= 8.5.35, <= 8.5.100 => no patch specified; >= 7.0.92, <= 7.0.109 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38808: Spring Framework vulnerable to Denial of Service

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38808](https://github.com/advisories/GHSA-9cmq-m9j5-mvww): Spring Framework vulnerable to Denial of Service

Severity: MEDIUM

- org.springframework:spring-expression:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 5.3.39 => 5.3.39

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38809: Spring Framework DoS via conditional HTTP request

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38809](https://github.com/advisories/GHSA-2rmj-mq67-h97g): Spring Framework DoS via conditional HTTP request

Severity: MEDIUM

- org.springframework:spring-web:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 5.3.38 => 5.3.38; >= 6.0.0, < 6.0.23 => 6.0.23; >= 6.1.0, < 6.1.12 => 6.1.12

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38816: Path traversal vulnerability in functional web frameworks

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38816](https://github.com/advisories/GHSA-cx7f-g6mp-7hqm): Path traversal vulnerability in functional web frameworks

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 6.1.0, < 6.1.13 => 6.1.13; >= 6.0.0, <= 6.0.23 => no patch specified; >= 5.3.0, <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38819: Spring Framework Path Traversal vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38819](https://github.com/advisories/GHSA-g5vr-rgqm-vf78): Spring Framework Path Traversal vulnerability

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 6.1.0, < 6.1.14 => 6.1.14; <= 5.3.40 => no patch specified; >= 6.0.0, <= 6.0.24 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38820: Spring Framework DataBinder Case Sensitive Match Exception

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38820](https://github.com/advisories/GHSA-4gc7-5j7h-4qph): Spring Framework DataBinder Case Sensitive Match Exception

Severity: MEDIUM

- org.springframework:spring-web:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 6.1.0, < 6.1.14 => 6.1.14; >= 6.0.0, <= 6.0.24 => no patch specified; <= 5.3.40 => no patch specified
- org.springframework:spring-context:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 6.1.0, < 6.1.14 => 6.1.14; >= 6.0.0, <= 6.0.24 => no patch specified; <= 5.3.40 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38821: Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-38821](https://github.com/advisories/GHSA-c4q5-6c82-3qpw): Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications

Severity: CRITICAL

- org.springframework.security:spring-security-web:5.7.11 [compile; transitive via spring-boot-starter-security; pom.xml:65]. Advisory ranges => first patched: >= 5.8.0, < 5.8.15 => 5.8.15; >= 6.2.0, < 6.2.7 => 6.2.7; >= 6.0.0, < 6.0.13 => 6.0.13; >= 6.1.0, < 6.1.11 => 6.1.11; >= 6.3.0, < 6.3.4 => 6.3.4; >= 5.0.0, < 5.7.13 => 5.7.13

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38827: Spring Framework has Authorization Bypass for Case Sensitive Comparisons

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-38827](https://github.com/advisories/GHSA-q3v6-hm2v-pw99): Spring Framework has Authorization Bypass for Case Sensitive Comparisons

Severity: MEDIUM

- org.springframework.security:spring-security-core:5.7.11 [compile; transitive via spring-boot-starter-security; pom.xml:65]. Advisory ranges => first patched: < 5.7.14 => 5.7.14; >= 5.8.0, < 5.8.16 => 5.8.16; >= 6.0.0, < 6.0.14 => 6.0.14; >= 6.1.0, < 6.1.12 => 6.1.12; >= 6.2.0, < 6.2.8 => 6.2.8; >= 6.3.0, < 6.3.5 => 6.3.5

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-38828: Spring MVC controller vulnerable to a DoS attack

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38828](https://github.com/advisories/GHSA-w3c8-7r8f-9jp8): Spring MVC controller vulnerable to a DoS attack

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 5.3.0, < 5.3.42 => 5.3.42

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-47554: Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:71

[CVE-2024-47554](https://github.com/advisories/GHSA-78wr-2p64-hpwj): Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader

Severity: HIGH

- commons-io:commons-io:2.11.0 [compile; direct; pom.xml:71]. Advisory ranges => first patched: >= 2.0, < 2.14.0 => 2.14.0

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-50379: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-50379](https://github.com/advisories/GHSA-5j33-cvvr-w245): Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.2 => 11.0.2; >= 10.1.0-M1, < 10.1.34 => 10.1.34; >= 9.0.0.M1, < 9.0.98 => 9.0.98; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2024-56337: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-56337](https://github.com/advisories/GHSA-27hp-xhwr-wr2m): Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.2 => 11.0.2; >= 10.1.0-M1, < 10.1.34 => 10.1.34; >= 9.0.0.M1, < 9.0.98 => 9.0.98

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-11226: QOS.CH logback-core is vulnerable to Arbitrary Code Execution through file processing

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-11226](https://github.com/advisories/GHSA-25qh-j22f-pwp8): QOS.CH logback-core is vulnerable to Arbitrary Code Execution through file processing

Severity: MEDIUM

- ch.qos.logback:logback-core:1.2.12 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 1.4.0, < 1.5.19 => 1.5.19; < 1.3.16 => 1.3.16

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-22228: Spring Security Does Not Enforce Password Length

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2025-22228](https://github.com/advisories/GHSA-mg83-c7gq-rv5c): Spring Security Does Not Enforce Password Length

Severity: HIGH

- org.springframework.security:spring-security-crypto:5.7.11 [compile; transitive via spring-boot-starter-security; pom.xml:65]. Advisory ranges => first patched: >= 6.3.0, < 6.3.8 => 6.3.8; >= 6.4.0, < 6.4.4 => 6.4.4; >= 6.2.0, <= 6.2.9 => 6.2.10; >= 6.1.0, <= 6.1.13 => 6.1.14; >= 6.0.0, <= 6.0.15 => 6.0.16; >= 5.8.0, <= 5.8.17 => 5.8.18; <= 5.7.15 => 5.7.16

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-22235: Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2025-22235](https://github.com/advisories/GHSA-rc42-6c7j-7h5r): Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed

Severity: HIGH

- org.springframework.boot:spring-boot:2.7.18 [compile; transitive via spring-boot-devtools; pom.xml:98]. Advisory ranges => first patched: <= 2.7.24.2 => no patch specified; >= 3.1.0, <= 3.1.15.2 => no patch specified; >= 3.2.0, <= 3.2.13.2 => no patch specified; >= 3.3.0, <= 3.3.10 => 3.3.11; >= 3.4.0, <= 3.4.4 => 3.4.5

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-24813: Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-24813](https://github.com/advisories/GHSA-83qj-6fr2-vhqg): Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.3 => 11.0.3; >= 10.1.0-M1, < 10.1.35 => 10.1.35; >= 9.0.0.M1, < 9.0.99 => 9.0.99; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-31650: Apache Tomcat Denial of Service via invalid HTTP priority header

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-31650](https://github.com/advisories/GHSA-3p2h-wqq4-wf4h): Apache Tomcat Denial of Service via invalid HTTP priority header

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 9.0.76, <= 9.0.102 => 9.0.104; >= 10.1.10, < 10.1.40 => 10.1.40; >= 11.0.0-M2, < 11.0.6 => 11.0.6; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-41242: Spring Framework MVC Applications Path Traversal Vulnerability

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-41242](https://github.com/advisories/GHSA-r936-gwx5-v52f): Spring Framework MVC Applications Path Traversal Vulnerability

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 6.2.0, < 6.2.10 => 6.2.10; >= 6.1.0, <= 6.1.21 => no patch specified; >= 6.0.0, <= 6.0.29 => no patch specified; >= 5.3.0, <= 5.3.43 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-41249: Spring Framework annotation detection mechanism may result in improper authorization

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2025-41249](https://github.com/advisories/GHSA-jmp9-x22r-554x): Spring Framework annotation detection mechanism may result in improper authorization

Severity: HIGH

- org.springframework:spring-core:5.3.31 [compile; transitive via spring-boot-starter-test; pom.xml:84]. Advisory ranges => first patched: >= 5.3.0, <= 5.3.44 => no patch specified; >= 6.0.0, <= 6.1.22 => no patch specified; >= 6.2.0, <= 6.2.10 => 6.2.11

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-48988: Apache Tomcat - DoS in multipart upload

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-48988](https://github.com/advisories/GHSA-h3gc-qfqq-6h8f): Apache Tomcat - DoS in multipart upload

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, <= 11.0.7 => 11.0.8; >= 10.1.0-M1, <= 10.1.41 => 10.1.42; >= 9.0.0.M1, <= 9.0.105 => 9.0.106; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-48989: Apache Tomcat Improper Resource Shutdown or Release vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-48989](https://github.com/advisories/GHSA-gqp3-2cvr-x8m3): Apache Tomcat Improper Resource Shutdown or Release vulnerability

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.10 => 11.0.10; >= 10.1.0-M1, < 10.1.44 => 10.1.44; >= 9.0.0.M1, < 9.0.108 => 9.0.108

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-49124: Apache Tomcat installer for Windows has an untrusted search path vulnerability

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-49124](https://github.com/advisories/GHSA-42wg-hm62-jcwg): Apache Tomcat installer for Windows has an untrusted search path vulnerability

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.8 => 11.0.8; >= 10.1.0, < 10.1.42 => 10.1.42; >= 9.0.23, < 9.0.106 => 9.0.106

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-49125: Apache Tomcat - Security constraint bypass for pre/post-resources

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-49125](https://github.com/advisories/GHSA-wc4r-xq3c-5cf3): Apache Tomcat - Security constraint bypass for pre/post-resources

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, <= 11.0.7 => 11.0.8; >= 10.1.0-M1, <= 10.1.41 => 10.1.42; >= 9.0.0.M1, <= 9.0.105 => 9.0.106; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-52434: Apache Tomcat is vulnerable to resource exhaustion when using the APR/Native connector

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-52434](https://github.com/advisories/GHSA-4j3c-42xv-3f84): Apache Tomcat is vulnerable to resource exhaustion when using the APR/Native connector

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 9.0.0.M1, < 9.0.107 => 9.0.107; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-52520: Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-52520](https://github.com/advisories/GHSA-wr62-c79q-cv37): Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.9 => 11.0.9; >= 10.1.0-M1, < 10.1.43 => 10.1.43; >= 9.0.0.M1, < 9.0.107 => 9.0.107; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-52999: jackson-core can throw a StackoverflowError when processing deeply nested data

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2025-52999](https://github.com/advisories/GHSA-h46c-h94j-95f3): jackson-core can throw a StackoverflowError when processing deeply nested data

Severity: HIGH

- com.fasterxml.jackson.core:jackson-core:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: < 2.15.0 => 2.15.0

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-53506: Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-53506](https://github.com/advisories/GHSA-25xr-qj8w-c4vf): Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 8.5.0, <= 8.5.100 => no patch specified; >= 9.0.0.M1, < 9.0.107 => 9.0.107; >= 10.1.0-M1, < 10.1.43 => 10.1.43; >= 11.0.0-M1, < 11.0.9 => 11.0.9

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-55668: Apache Tomcat Session Fixation vulnerability

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-55668](https://github.com/advisories/GHSA-23hv-mwm6-g8jf): Apache Tomcat Session Fixation vulnerability

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.8 => 11.0.8; >= 10.1.0-M1, < 10.1.42 => 10.1.42; >= 9.0.0.M1, < 9.0.106 => 9.0.106

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-55752: Apache Tomcat Vulnerable to Relative Path Traversal

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-55752](https://github.com/advisories/GHSA-wmwf-9ccg-fff5): Apache Tomcat Vulnerable to Relative Path Traversal

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.11 => 11.0.11; >= 10.1.0-M1, < 10.1.45 => 10.1.45; >= 9.0.0-M11, < 9.0.109 => 9.0.109; >= 8.5.6, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2025-66614: Apache Tomcat - Client certificate verification bypass

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-66614](https://github.com/advisories/GHSA-fpj8-gq4v-p354): Apache Tomcat - Client certificate verification bypass

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.15 => 11.0.15; >= 10.1.0-M1, < 10.1.50 => 10.1.50; >= 9.0.0-M1, < 9.0.113 => 9.0.113; >= 8.5.0, <= 8.5.100 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-19032: jackson-databind: Path Deserialization Missing Scheme Allowlist for FileSystemProvider Resolution

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-19032](https://github.com/advisories/GHSA-wjgm-6hv5-3cvf): jackson-databind: Path Deserialization Missing Scheme Allowlist for FileSystemProvider Resolution

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.8.0, < 2.18.10 => 2.18.10; >= 2.19.0, < 2.21.6 => 2.21.6; >= 2.22.0, < 2.22.2 => 2.22.2

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-22732: Spring Security HTTP Headers Are not Written Under Some Conditions

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2026-22732](https://github.com/advisories/GHSA-mf92-479x-3373): Spring Security HTTP Headers Are not Written Under Some Conditions

Severity: CRITICAL

- org.springframework.security:spring-security-web:5.7.11 [compile; transitive via spring-boot-starter-security; pom.xml:65]. Advisory ranges => first patched: <= 5.7.14 => no patch specified; >= 5.8.0, <= 5.8.16 => no patch specified; >= 6.0.0, <= 6.3.10 => no patch specified; >= 6.4.0, <= 6.4.13 => no patch specified; >= 6.5.0, < 6.5.9 => 6.5.9; >= 7.0.0, < 7.0.4 => 7.0.4

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-22737: Spring Framework Improper Path Limitation with Script View Templates

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-22737](https://github.com/advisories/GHSA-4773-3jfm-qmx3): Spring Framework Improper Path Limitation with Script View Templates

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0-M1, < 7.0.6 => 7.0.6; >= 6.2.0, < 6.2.17 => 6.2.17; >= 6.0.0, <= 6.1.21 => no patch specified; >= 5.3.0, <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-22745: Spring MVC and WebFlux applications are vulnerable to Denial of Service attacks when resolving static resources

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-22745](https://github.com/advisories/GHSA-6p4f-wcwh-5vvm): Spring MVC and WebFlux applications are vulnerable to Denial of Service attacks when resolving static resources

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.6 => 7.0.7; >= 6.2.0, <= 6.2.17 => 6.2.18; >= 6.1.0, <= 6.1.26 => no patch specified; <= 5.3.47 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-24400: AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2026-24400](https://github.com/advisories/GHSA-rqfh-9r24-8c9r): AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion

Severity: HIGH

- org.assertj:assertj-core:3.22.0 [test; transitive via spring-boot-starter-test; pom.xml:84]. Advisory ranges => first patched: >= 1.4.0, <= 3.27.6 => 3.27.7

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-24734: Apache Tomcat has an Improper Input Validation vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-24734](https://github.com/advisories/GHSA-mgp5-rv84-w37q): Apache Tomcat has an Improper Input Validation vulnerability

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.18 => 11.0.18; >= 10.1.0-M7, < 10.1.52 => 10.1.52; >= 9.0.83, < 9.0.115 => 9.0.115

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-24880: Apache Tomcat has an HTTP Request/Response Smuggling vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-24880](https://github.com/advisories/GHSA-563x-q5rq-57qp): Apache Tomcat has an HTTP Request/Response Smuggling vulnerability

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, < 9.0.116 => 9.0.116; >= 10.1.0-M1, < 10.1.52 => 10.1.52; >= 11.0.0-M1, <= 11.0.18 => 11.0.20

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-25854: Apache Tomcat has an Open Redirect vulnerability

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-25854](https://github.com/advisories/GHSA-9m3c-qcxr-9x87): Apache Tomcat has an Open Redirect vulnerability

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 10.1.0-M1, < 10.1.53 => 10.1.53; >= 11.0.0-M1, < 11.0.20 => 11.0.20; >= 8.5.30, < 9.0.116 => 9.0.116

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-34483: Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-34483](https://github.com/advisories/GHSA-rv64-5gf8-9qq8): Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 9.0.40, < 9.0.116 => 9.0.116; >= 10.1.0-M1, < 10.1.54 => 10.1.54; >= 11.0.0-M1, < 11.0.21 => 11.0.21

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-34487: Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-34487](https://github.com/advisories/GHSA-x4m4-345f-5h5g): Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 9.0.13, < 9.0.117 => 9.0.117; >= 10.1.0-M1, < 10.1.54 => 10.1.54; >= 11.0.0-M1, < 11.0.21 => 11.0.21

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-40477: Improper restriction of the scope of accessible objects in Thymeleaf expressions

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-40477](https://github.com/advisories/GHSA-r4v4-5mwr-2fwr): Improper restriction of the scope of accessible objects in Thymeleaf expressions

Severity: CRITICAL

- org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE [compile; transitive via spring-boot-starter-thymeleaf; pom.xml:40]. Advisory ranges => first patched: <= 3.1.3.RELEASE => 3.1.4.RELEASE
- org.thymeleaf:thymeleaf:3.0.15.RELEASE [compile; transitive via spring-boot-starter-thymeleaf; pom.xml:40]. Advisory ranges => first patched: <= 3.1.3.RELEASE => 3.1.4.RELEASE

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-40478: Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-40478](https://github.com/advisories/GHSA-xjw8-8c5c-9r79): Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf

Severity: CRITICAL

- org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE [compile; transitive via spring-boot-starter-thymeleaf; pom.xml:40]. Advisory ranges => first patched: <= 3.1.3.RELEASE => 3.1.4.RELEASE
- org.thymeleaf:thymeleaf:3.0.15.RELEASE [compile; transitive via spring-boot-starter-thymeleaf; pom.xml:40]. Advisory ranges => first patched: <= 3.1.3.RELEASE => 3.1.4.RELEASE

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-40972: Spring Boot DevTools remote secret comparison is vulnerable to timing attacks

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-40972](https://github.com/advisories/GHSA-56v8-86gj-66jp): Spring Boot DevTools remote secret comparison is vulnerable to timing attacks

Severity: HIGH

- org.springframework.boot:spring-boot-devtools:2.7.18 [compile; direct; pom.xml:98]. Advisory ranges => first patched: >= 4.0.0, < 4.0.6 => 4.0.6; >= 3.5.0, < 3.5.14 => 3.5.14; >= 3.4.0, <= 3.4.15 => no patch specified; >= 3.3.0, <= 3.3.18 => no patch specified; <= 2.7.32 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-40973: Spring Boot accepts predictable temp directory without ownership verification

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-40973](https://github.com/advisories/GHSA-wwpq-f5c3-7hvx): Spring Boot accepts predictable temp directory without ownership verification

Severity: HIGH

- org.springframework.boot:spring-boot:2.7.18 [compile; transitive via spring-boot-devtools; pom.xml:98]. Advisory ranges => first patched: >= 4.0.0, < 4.0.6 => 4.0.6; >= 3.5.0, < 3.5.14 => 3.5.14; >= 3.4.0, <= 3.4.15 => no patch specified; >= 3.3.0, <= 3.3.18 => no patch specified; <= 2.7.32 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41001: Spring Boot: Predictable Temp Directory in Artemis Auto-configuration

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-41001](https://github.com/advisories/GHSA-ggg2-9786-hwc8): Spring Boot: Predictable Temp Directory in Artemis Auto-configuration

Severity: MEDIUM

- org.springframework.boot:spring-boot-autoconfigure:2.7.18 [compile; transitive via spring-boot-devtools; pom.xml:98]. Advisory ranges => first patched: >= 4.0.0, <= 4.0.6 => 4.0.7; >= 3.5.0, <= 3.5.14 => 3.5.15; >= 3.4.0, <= 3.4.16 => no patch specified; >= 3.3.0, <= 3.3.19 => no patch specified; >= 2.7.0, <= 2.7.33 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41284: Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41284](https://github.com/advisories/GHSA-gx5v-xp9w-j4cg): Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 9.0.118 => 9.0.118; >= 10.1.0-M1, < 10.1.55 => 10.1.55; >= 11.0.0-M1, < 11.0.22 => 11.0.22

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41293: Apache Tomcat - HTTP/2 request headers not validated

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41293](https://github.com/advisories/GHSA-r29c-68gh-xp6x): Apache Tomcat - HTTP/2 request headers not validated

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 10.1.0-M1, < 10.1.55 => 10.1.55; >= 11.0.0-M1, < 11.0.22 => 11.0.22; >= 8.5.0, < 9.0.118 => 9.0.118

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41706: Spring Security: Open Redirect via Unvalidated Post-Login Redirect URL Stored in CookieRequestCache

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2026-41706](https://github.com/advisories/GHSA-x2r2-rvhq-2mqv): Spring Security: Open Redirect via Unvalidated Post-Login Redirect URL Stored in CookieRequestCache

Severity: MEDIUM

- org.springframework.security:spring-security-web:5.7.11 [compile; transitive via spring-boot-starter-security; pom.xml:65]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.5 => 7.0.6; >= 6.5.0, <= 6.5.10 => 6.5.11; >= 6.3.0, <= 6.3.16 => no patch specified; >= 5.8.0, <= 5.8.25 => no patch specified; <= 5.7.23 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41711: Spring Data Commons: StackOverflowException when parsing Sort parameters (DoS)

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:46

[CVE-2026-41711](https://github.com/advisories/GHSA-5vpf-xvv7-c8vh): Spring Data Commons: StackOverflowException when parsing Sort parameters (DoS)

Severity: MEDIUM

- org.springframework.data:spring-data-commons:2.7.18 [compile; transitive via spring-boot-starter-data-jpa; pom.xml:46]. Advisory ranges => first patched: >= 4.0.0, <= 4.0.5 => 4.0.6; >= 3.5.0, <= 3.5.11 => 3.5.12; >= 3.4.0, <= 3.4.14 => no patch specified; >= 3.0.0, <= 3.3.16 => no patch specified; <= 2.7.19 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41716: Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:46

[CVE-2026-41716](https://github.com/advisories/GHSA-9fw2-h3hf-293r): Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys

Severity: HIGH

- org.springframework.data:spring-data-commons:2.7.18 [compile; transitive via spring-boot-starter-data-jpa; pom.xml:46]. Advisory ranges => first patched: >= 4.0.0, <= 4.0.5 => 4.0.6; >= 3.5.0, <= 3.5.11 => 3.5.12; >= 3.4.0, <= 3.4.14 => no patch specified; >= 3.3.0, <= 3.3.16 => no patch specified; <= 2.7.19 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41721: Spring Data Commons: Denial of Service via excessive memory allocation in projection binding

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:46

[CVE-2026-41721](https://github.com/advisories/GHSA-5m4m-73w9-8433): Spring Data Commons: Denial of Service via excessive memory allocation in projection binding

Severity: MEDIUM

- org.springframework.data:spring-data-commons:2.7.18 [compile; transitive via spring-boot-starter-data-jpa; pom.xml:46]. Advisory ranges => first patched: >= 4.0.0, <= 4.0.5 => 4.0.6; >= 3.5.0, <= 3.5.11 => 3.5.12; >= 3.4.0, <= 3.4.14 => no patch specified; >= 3.0.0, <= 3.3.16 => no patch specified; <= 2.7.19 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41841: Spring Framework Information Disclosure via Static Resource Cache in Spring MVC and WebFlux

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41841](https://github.com/advisories/GHSA-mq64-j8f9-9gcj): Spring Framework Information Disclosure via Static Resource Cache in Spring MVC and WebFlux

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41842: Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41842](https://github.com/advisories/GHSA-x23c-287f-qqv5): Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41843: Spring Framework Path Traversal via Versioned Static Resources in Spring MVC and WebFlux

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41843](https://github.com/advisories/GHSA-72pg-x5f8-j25j): Spring Framework Path Traversal via Versioned Static Resources in Spring MVC and WebFlux

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41844: Spring Framework Open Redirect in Spring MVC and WebFlux

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41844](https://github.com/advisories/GHSA-h3qp-gqrc-q736): Spring Framework Open Redirect in Spring MVC and WebFlux

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41845: Spring Framework Cross-site Scripting via JavaScriptUtils

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41845](https://github.com/advisories/GHSA-3chg-m5w7-qfv5): Spring Framework Cross-site Scripting via JavaScriptUtils

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41846: Spring Framework Cross-site Scripting via JSP Form Tags

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41846](https://github.com/advisories/GHSA-957g-f97v-vppc): Spring Framework Cross-site Scripting via JSP Form Tags

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41849: Spring Framework Denial of Service via Integer Overflow in SpEL Expressions

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41849](https://github.com/advisories/GHSA-775g-4xr8-78h8): Spring Framework Denial of Service via Integer Overflow in SpEL Expressions

Severity: HIGH

- org.springframework:spring-expression:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41850: Spring Framework Algorithmic Denial of Service via SpEL Expressions

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41850](https://github.com/advisories/GHSA-r5w3-xv2f-j59q): Spring Framework Algorithmic Denial of Service via SpEL Expressions

Severity: HIGH

- org.springframework:spring-expression:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41851: Spring Framework Denial of Service via Unbounded Cache in SpEL

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41851](https://github.com/advisories/GHSA-wxpp-56q6-5pcg): Spring Framework Denial of Service via Unbounded Cache in SpEL

Severity: MEDIUM

- org.springframework:spring-expression:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41853: Spring Framework Multipart Request Smuggling in Spring MVC and WebFlux

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41853](https://github.com/advisories/GHSA-cjpg-rgq5-fr37): Spring Framework Multipart Request Smuggling in Spring MVC and WebFlux

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 7.0.0, <= 7.0.7 => 7.0.8; >= 6.2.0, <= 6.2.18 => 6.2.19; >= 6.1.0, <= 6.1.21 => no patch specified; <= 5.3.39 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-41901: Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-41901](https://github.com/advisories/GHSA-c9ph-gxww-7744): Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns

Severity: CRITICAL

- org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE [compile; transitive via spring-boot-starter-thymeleaf; pom.xml:40]. Advisory ranges => first patched: <= 3.1.4.RELEASE => 3.1.5.RELEASE
- org.thymeleaf:thymeleaf:3.0.15.RELEASE [compile; transitive via spring-boot-starter-thymeleaf; pom.xml:40]. Advisory ranges => first patched: <= 3.1.4.RELEASE => 3.1.5.RELEASE

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-42498: Apache Tomcat - WebSocket authentication header exposure

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-42498](https://github.com/advisories/GHSA-fv25-8xcx-gqjc): Apache Tomcat - WebSocket authentication header exposure

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 9.0.118 => 9.0.118; >= 10.1.0-M1, < 10.1.55 => 10.1.55; >= 11.0.0-M1, < 11.0.22 => 11.0.22

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-43512: Apache Tomcat - Digest authenticator will authenticate any unknown user

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43512](https://github.com/advisories/GHSA-h6fc-48rj-7qqh): Apache Tomcat - Digest authenticator will authenticate any unknown user

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 9.0.118 => 9.0.118; >= 10.1.0-M1, < 10.1.55 => 10.1.55; >= 11.0.0-M1, < 11.0.22 => 11.0.22

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-43513: Apache Tomcat: LockOutRealm treats user names as case-sensitive

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43513](https://github.com/advisories/GHSA-5mp6-jrq3-r938): Apache Tomcat: LockOutRealm treats user names as case-sensitive

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 9.0.118 => 9.0.118; >= 10.1.0-M1, < 10.1.55 => 10.1.55; >= 11.0.0-M1, < 11.0.22 => 11.0.22

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-43515: Apache Tomcat - Security constraints not correctly applied

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43515](https://github.com/advisories/GHSA-5m62-pw8w-7w9f): Apache Tomcat - Security constraints not correctly applied

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: < 9.0.118 => 9.0.118; >= 10.1.0-M1, < 10.1.55 => 10.1.55; >= 11.0.0-M1, < 11.0.22 => 11.0.22

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-47838: Spring Security Vulnerable to Unauthorized User Impersonation when Using X.509 Client Certificates

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2026-47838](https://github.com/advisories/GHSA-293q-567p-wmwq): Spring Security Vulnerable to Unauthorized User Impersonation when Using X.509 Client Certificates

Severity: MEDIUM

- org.springframework.security:spring-security-web:5.7.11 [compile; transitive via spring-boot-starter-security; pom.xml:65]. Advisory ranges => first patched: >= 6.5.0, <= 6.5.10 => 6.5.11; >= 6.4.0, <= 6.4.13 => no patch specified; >= 6.0.0, <= 6.3.10 => no patch specified; >= 5.8.0, <= 5.8.16 => no patch specified; <= 5.7.14 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-47884: Spring Framework Improper Path Limitation in XsltView

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-47884](https://github.com/advisories/GHSA-pc63-qcmh-9cmg): Spring Framework Improper Path Limitation in XsltView

Severity: CRITICAL

- org.springframework:spring-webmvc:5.3.31 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: <= 5.2.25.RELEASE => no patch specified; >= 5.3.0, <= 5.3.49 => no patch specified; >= 6.0.0, <= 6.0.30 => no patch specified; >= 6.1.0, <= 6.1.28 => no patch specified; >= 6.2.0, <= 6.2.19 => no patch specified; >= 7.0.0, <= 7.0.8 => 7.0.9

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-49844: Apache Log4j API: Improper encoding of non-finite floating-point values during MapMessage JSON serialization

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-49844](https://github.com/advisories/GHSA-qv9r-c865-cp47): Apache Log4j API: Improper encoding of non-finite floating-point values during MapMessage JSON serialization

Severity: MEDIUM

- org.apache.logging.log4j:log4j-api:2.17.2 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 2.13.1, < 2.25.5 => 2.25.5; >= 2.26.0, < 2.26.1 => 2.26.1

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-50193: jackson-databind: Deeply nested JsonNode throws StackOverflowError for toString()

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-50193](https://github.com/advisories/GHSA-3wrr-7qpf-2prh): jackson-databind: Deeply nested JsonNode throws StackOverflowError for toString()

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.10.0, <= 2.13.5 => 2.14.0

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-54512: jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54512](https://github.com/advisories/GHSA-j3rv-43j4-c7qm): jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.10.0, <= 2.18.7 => 2.18.8; >= 3.0.0, <= 3.1.3 => 3.1.4; >= 2.19.0, <= 2.21.3 => 2.21.4

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-54513: jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54513](https://github.com/advisories/GHSA-rmj7-2vxq-3g9f): jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.10.0, < 2.18.8 => 2.18.8; >= 2.19.0, < 2.21.4 => 2.21.4; >= 3.0.0, < 3.1.4 => 3.1.4

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-54514: jackson-databind: InetSocketAddress deserialization triggers eager DNS resolution (SSRF)

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54514](https://github.com/advisories/GHSA-hgj6-7826-r7m5): jackson-databind: InetSocketAddress deserialization triggers eager DNS resolution (SSRF)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.0.0, < 2.18.8 => 2.18.8; >= 2.19.0, < 2.21.4 => 2.21.4; >= 3.0.0, < 3.1.4 => 3.1.4

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-54515: jackson-databind has case-insensitive deserialization bypasses per-property @JsonIgnoreProperties

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54515](https://github.com/advisories/GHSA-5jmj-h7xm-6q6v): jackson-databind has case-insensitive deserialization bypasses per-property @JsonIgnoreProperties

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 3.1.0, < 3.1.4 => 3.1.4; >= 2.8.0, < 2.18.9 => 2.18.9; >= 2.19.0, < 2.21.5 => 2.21.5; >= 2.22.0, < 2.22.1 => 2.22.1

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-59889: jackson-databind: @JsonView bypassed for @JsonUnwrapped container properties on deserialization

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-59889](https://github.com/advisories/GHSA-5gvw-p9qm-jgwh): jackson-databind: @JsonView bypassed for @JsonUnwrapped container properties on deserialization

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.22.0, < 2.22.1 => 2.22.1; >= 2.19.0, < 2.21.5 => 2.21.5; >= 2.0.0-RC1, < 2.18.9 => 2.18.9

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-65182: Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-65182](https://github.com/advisories/GHSA-gcx9-497g-6cp6): Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.25 => 11.0.25; >= 10.1.0-M1, < 10.1.58 => 10.1.58; >= 9.0.0-M1, < 9.0.121 => 9.0.121; >= 8.5.0, <= 8.5.100 => no patch specified; >= 7.0.0, <= 7.0.109 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-65905: Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-65905](https://github.com/advisories/GHSA-9xv2-5v5q-p794): Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.25 => 11.0.25; >= 10.1.0-M1, < 10.1.58 => 10.1.58; >= 9.0.0.M1, < 9.0.121 => 9.0.121; >= 8.5.0, <= 8.5.100 => no patch specified; >= 7.0.30, <= 7.0.109 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-68494: jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-68494](https://github.com/advisories/GHSA-r7wm-3cxj-wff9): jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-core:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: < 2.18.8 => 2.18.8; >= 2.19.0, < 2.21.4 => 2.21.4

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-68525: Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-68525](https://github.com/advisories/GHSA-h3x4-894j-xpx5): Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 [compile; transitive via spring-boot-starter-web; pom.xml:34]. Advisory ranges => first patched: >= 11.0.0-M1, < 11.0.25 => 11.0.25; >= 10.1.0-M1, < 10.1.58 => 10.1.58; >= 9.0.0-M1, < 9.0.121 => 9.0.121; >= 8.5.0, <= 8.5.100 => no patch specified; >= 7.0.0, <= 7.0.109 => no patch specified

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-77310: jackson-databind: Incomplete fix for CVE-2026-54514: eager DNS resolution (SSRF) still present in InetAddress deserialization

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-77310](https://github.com/advisories/GHSA-vvgp-rfg2-7rr6): jackson-databind: Incomplete fix for CVE-2026-54514: eager DNS resolution (SSRF) still present in InetAddress deserialization

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.0.0, < 2.18.9 => 2.18.9; >= 2.19.0, < 2.21.5 => 2.21.5; >= 2.22.0, < 2.22.1 => 2.22.1

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-83557: jackson-databind: Comparable missing from DefaultBaseTypeLimitingValidator's unsafe base types (incomplete PolymorphicTypeValidator denylist)

- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-83557](https://github.com/advisories/GHSA-gx83-3vf8-gh7j): jackson-databind: Comparable missing from DefaultBaseTypeLimitingValidator's unsafe base types (incomplete PolymorphicTypeValidator denylist)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.11.0, < 2.18.10 => 2.18.10; >= 2.19.0, < 2.21.6 => 2.21.6; >= 2.22.0, < 2.22.2 => 2.22.2

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-89425: jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-89425](https://github.com/advisories/GHSA-7hhh-6rmp-j9qf): jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-core:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.19.0, <= 2.21.6 => 2.21.7; >= 2.22.0, <= 2.22.2 => 2.22.3; >= 2.8.0, <= 2.18.10 => 2.18.11

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-91776: jackson-databind retains every unknown raw type ID 

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-91776](https://github.com/advisories/GHSA-wv8q-qhhj-9h54): jackson-databind retains every unknown raw type ID 

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.0.0, <= 2.18.10 => 2.18.11; >= 2.19.0, <= 2.21.6 => 2.21.7; >= 2.22.0, <= 2.22.2 => 2.22.3

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.

### CVE-2026-91777: jackson-databind quadratic forward-reference completion 

- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-91777](https://github.com/advisories/GHSA-cxp5-3px4-pw24): jackson-databind quadratic forward-reference completion 

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 [compile; transitive via spring-boot-starter-json; pom.xml:78]. Advisory ranges => first patched: >= 2.19.0, <= 2.21.6 => 2.21.7; >= 2.5.0, <= 2.18.10 => 2.18.11; >= 2.22.0, <= 2.22.2 => 2.22.3

Recommendation: upgrade to a compatible supported release outside the affected ranges (branch-specific first patches listed above). Installed-version match confirmed by GitHub Advisory affects API, not a claim of confirmed exploitation. Reachability and advisory prerequisites require deployment-specific validation. Test scope is not assumed deployed; optional devtools inclusion is unverified.


## CWE Findings (Code-Level Vulnerabilities)

### CWE-606: Unchecked Input for Loop Condition

- **Category:** Code Quality
- **Severity:** potential
- **Story Points:** 3
- **Files:** src/main/java/com/photoalbum/controller/HomeController.java:57, src/main/java/com/photoalbum/controller/HomeController.java:68, src/main/resources/application.properties:30

HomeController.uploadPhotos loops over the entire caller-supplied multipart files list (68-91), invoking upload parsing and database writes for each item, without checking a maximum count. The configured max-files-per-upload value is never injected or consulted. Authenticated callers can submit many small files and induce repeated ImageIO and repository work. The 50MB request limit bounds total request bytes, but does not enforce the intended ten-file processing budget; parser-specific part-count limits may further bound exposure and were not validated.

### CWE-789: Memory Allocation with Excessive Size Value

- **Category:** Code Quality
- **Severity:** potential
- **Story Points:** 5
- **Files:** src/main/java/com/photoalbum/controller/HomeController.java:40, src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:57, src/main/java/com/photoalbum/repository/PhotoRepository.java:22, Dockerfile:28

An anonymous GET / calls HomeController.index -> PhotoServiceImpl.getAllPhotos -> PhotoRepository.findAllOrderByUploadedAtDesc. The unpaginated query selects PHOTO_DATA for every persisted row (22-27), materializing all BLOB byte arrays and entities even though the page needs metadata only. Total allocation scales with the uploaded dataset without an aggregate bound; repeated requests can exhaust the configured 512MB heap. Authenticated uploads can grow the dataset; no particular current database size or successful denial of service is asserted.

### CWE-732: Incorrect Permission Assignment for Critical Resource

- **Category:** Credentials & Secrets
- **Severity:** optional
- **Story Points:** 5
- **Files:** azure-setup.ps1:283, azure-setup.ps1:289, azure-setup.ps1:299

azure-setup.ps1 stores the generated database password ([MASKED]) in the project .env via Out-File (299), without setting a restrictive Unix mode/umask or Windows ACL before or after creation. On a shared Unix host with the common 022 umask, a newly created file is readable by other local users, exposing application database credentials. This is a conditional deployment-script permission finding, not a claim that the current host has executed the script or that an existing .env currently has weak permissions. Git ignore does not restrict local file access.

### CWE-778: Insufficient Logging

- **Category:** Credentials & Secrets
- **Severity:** potential
- **Story Points:** 3
- **Files:** src/main/java/com/photoalbum/controller/DetailController.java:65, src/main/java/com/photoalbum/controller/DetailController.java:69, src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:212

The authenticated destructive DetailController.deletePhoto action logs the target photo ID and outcome (69), and PhotoServiceImpl.deletePhoto similarly logs only the target ID (212). Neither records the acting authenticated principal, source or an audit correlation identity. Consequently these security-critical mutation records do not identify the actor. SecurityConfig uses HTTP Basic without an application audit handler; external proxy/SIEM audit coverage is unknown. Operational logging exists, but relevant audit details are omitted.

### CWE-434: Unrestricted Upload of File with Dangerous Type

- **Category:** File & Path Security
- **Severity:** mandatory
- **Story Points:** 8
- **Files:** src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:88, src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:130, src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java:160, src/main/java/com/photoalbum/controller/PhotoFileController.java:75

PhotoServiceImpl.uploadPhoto trusts the multipart Content-Type allowlist (88), but a header-spoofed non-image with no ImageIO reader is not rejected (130-149) and is saved unchanged (160-174). Arbitrary unrecognized content can therefore be persisted and publicly served by PhotoFileController.servePhoto (75-83). Upload requires authenticated credentials. File extension is also unvalidated; no server-side script execution or browser MIME bypass is established.

### CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')

- **Category:** Injection Attacks
- **Severity:** optional
- **Story Points:** 8
- **Files:** src/main/resources/static/js/upload.js:73, src/main/resources/static/js/upload.js:82, src/main/resources/static/js/upload.js:216

upload.js handleFiles includes an untrusted local or dropped file name in validation error messages (73-82). showErrors interpolates each message into an li and assigns innerHTML (216-218), allowing filename markup to become active HTML in the uploader browser. No authentication or server response is needed for this client-side error path. This is a DOM XSS sink; victim interaction with a specially named file is required. The successful upload response also reaches unescaped originalFileName interpolation in createPhotoCard (185-189) and insertAdjacentHTML (157); server-rendered Thymeleaf th:text paths escape names.

