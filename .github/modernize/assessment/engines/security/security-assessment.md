# Security Assessment Report

**Generated:** 2026-11-20T11:01:31.131838Z

## Summary

| Metric | Count |
|--------|-------|
| Total Findings | 65 |
| CVE Vulnerabilities | 63 |
| CWE Vulnerabilities | 2 |
| Total Rules Assessed | 59 |
| Rules Passed | 57 |

### By Severity

| Severity | Count |
|----------|-------|
| mandatory | 64 |
| optional | 0 |
| potential | 1 |

## CVE Findings (Dependency Vulnerabilities)

### CVE-2016-1000027: Pivotal Spring Framework contains unsafe Java deserialization methods
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2016-1000027](https://github.com/advisories/GHSA-4wrc-f8pq-fpqp): Pivotal Spring Framework contains unsafe Java deserialization methods

Severity: CRITICAL

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 6.0.0; first patched version 6.0.0

### CVE-2024-38821: Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-38821](https://github.com/advisories/GHSA-c4q5-6c82-3qpw): Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications

Severity: CRITICAL

Affected dependencies:
  - org.springframework.security:spring-security-web:5.7.11 (via org.springframework.boot:spring-boot-starter-security:2.7.18; declared at pom.xml:65); affected range >= 5.8.0, < 5.8.15; first patched version 5.8.15

### CVE-2025-24813: Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-24813](https://github.com/advisories/GHSA-83qj-6fr2-vhqg): Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.3; first patched version 11.0.3

### CVE-2026-22732: Spring Security HTTP Headers Are not Written Under Some Conditions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2026-22732](https://github.com/advisories/GHSA-mf92-479x-3373): Spring Security HTTP Headers Are not Written Under Some Conditions

Severity: CRITICAL

Affected dependencies:
  - org.springframework.security:spring-security-web:5.7.11 (via org.springframework.boot:spring-boot-starter-security:2.7.18; declared at pom.xml:65); affected range <= 5.7.14; first patched version not specified

### CVE-2026-40477: Improper restriction of the scope of accessible objects in Thymeleaf expressions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-40477](https://github.com/advisories/GHSA-r4v4-5mwr-2fwr): Improper restriction of the scope of accessible objects in Thymeleaf expressions

Severity: CRITICAL

Affected dependencies:
  - org.thymeleaf:thymeleaf:3.0.15.RELEASE (via org.springframework.boot:spring-boot-starter-thymeleaf:2.7.18; declared at pom.xml:40); affected range <= 3.1.3.RELEASE; first patched version 3.1.4.RELEASE
  - org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (via org.springframework.boot:spring-boot-starter-thymeleaf:2.7.18; declared at pom.xml:40); affected range <= 3.1.3.RELEASE; first patched version 3.1.4.RELEASE

### CVE-2026-40478: Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-40478](https://github.com/advisories/GHSA-xjw8-8c5c-9r79): Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf

Severity: CRITICAL

Affected dependencies:
  - org.thymeleaf:thymeleaf:3.0.15.RELEASE (via org.springframework.boot:spring-boot-starter-thymeleaf:2.7.18; declared at pom.xml:40); affected range <= 3.1.3.RELEASE; first patched version 3.1.4.RELEASE
  - org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (via org.springframework.boot:spring-boot-starter-thymeleaf:2.7.18; declared at pom.xml:40); affected range <= 3.1.3.RELEASE; first patched version 3.1.4.RELEASE

### CVE-2026-41293: Apache Tomcat - HTTP/2 request headers not validated
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41293](https://github.com/advisories/GHSA-r29c-68gh-xp6x): Apache Tomcat - HTTP/2 request headers not validated

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 10.1.0-M1, < 10.1.55; first patched version 10.1.55

### CVE-2026-41901: Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-41901](https://github.com/advisories/GHSA-c9ph-gxww-7744): Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns

Severity: CRITICAL

Affected dependencies:
  - org.thymeleaf:thymeleaf:3.0.15.RELEASE (via org.springframework.boot:spring-boot-starter-thymeleaf:2.7.18; declared at pom.xml:40); affected range <= 3.1.4.RELEASE; first patched version 3.1.5.RELEASE
  - org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (via org.springframework.boot:spring-boot-starter-thymeleaf:2.7.18; declared at pom.xml:40); affected range <= 3.1.4.RELEASE; first patched version 3.1.5.RELEASE

### CVE-2026-43512: Apache Tomcat - Digest authenticator will authenticate any unknown user
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43512](https://github.com/advisories/GHSA-h6fc-48rj-7qqh): Apache Tomcat - Digest authenticator will authenticate any unknown user

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 9.0.118; first patched version 9.0.118

### CVE-2026-43515: Apache Tomcat - Security constraints not correctly applied
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43515](https://github.com/advisories/GHSA-5m62-pw8w-7w9f): Apache Tomcat - Security constraints not correctly applied

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 9.0.118; first patched version 9.0.118

### CVE-2026-47884: Spring Framework Improper Path Limitation in XsltView
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-47884](https://github.com/advisories/GHSA-pc63-qcmh-9cmg): Spring Framework Improper Path Limitation in XsltView

Severity: CRITICAL

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range <= 5.2.25.RELEASE; first patched version not specified

### CVE-2026-55276: Apache Tomcat has an Always-Incorrect Control Flow Implementation vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-55276](https://github.com/advisories/GHSA-mqg3-r7h5-24x4): Apache Tomcat has an Always-Incorrect Control Flow Implementation vulnerability

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.23; first patched version 11.0.23

### CVE-2026-65182: Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-65182](https://github.com/advisories/GHSA-gcx9-497g-6cp6): Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.25; first patched version 11.0.25

### CVE-2026-65905: Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-65905](https://github.com/advisories/GHSA-9xv2-5v5q-p794): Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.25; first patched version 11.0.25

### CVE-2026-68525: Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-68525](https://github.com/advisories/GHSA-h3x4-894j-xpx5): Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.25; first patched version 11.0.25

### CVE-2022-1471: SnakeYaml Constructor Deserialization Remote Code Execution
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-1471](https://github.com/advisories/GHSA-mjmj-j48q-9wg2): SnakeYaml Constructor Deserialization Remote Code Execution

Severity: HIGH

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range <= 1.33; first patched version 2.0

### CVE-2022-25857: Uncontrolled Resource Consumption in snakeyaml
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-25857](https://github.com/advisories/GHSA-3mc7-4q67-w48m): Uncontrolled Resource Consumption in snakeyaml

Severity: HIGH

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 1.31; first patched version 1.31

### CVE-2022-45868: Password exposure in H2 Database 
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:91

[CVE-2022-45868](https://github.com/advisories/GHSA-22wj-vf5f-wrvj): Password exposure in H2 Database 

Severity: HIGH

Affected dependencies:
  - com.h2database:h2:2.1.214 (via com.h2database:h2:2.1.214; declared at pom.xml:91); affected range >= 1.4.198, < 2.2.220; first patched version 2.2.220

### CVE-2023-6378: logback serialization vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2023-6378](https://github.com/advisories/GHSA-vmq6-5m68-f53m): logback serialization vulnerability

Severity: HIGH

Affected dependencies:
  - ch.qos.logback:logback-classic:1.2.12 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 1.4.0, < 1.4.12; first patched version 1.4.12
  - ch.qos.logback:logback-core:1.2.12 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 1.4.0, < 1.4.12; first patched version 1.4.12

### CVE-2023-6481: Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2023-6481](https://github.com/advisories/GHSA-gm62-rw4g-vrc4): Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data

Severity: HIGH

Affected dependencies:
  - ch.qos.logback:logback-core:1.2.12 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range = 1.4.13; first patched version 1.4.14

### CVE-2024-22243: Spring Web vulnerable to Open Redirect or Server Side Request Forgery
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22243](https://github.com/advisories/GHSA-ccgv-vj62-xf9h): Spring Web vulnerable to Open Redirect or Server Side Request Forgery

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 6.1.0, < 6.1.4; first patched version 6.1.4

### CVE-2024-22257: Erroneous authentication pass in Spring Security
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-22257](https://github.com/advisories/GHSA-f3jh-qvm4-mg39): Erroneous authentication pass in Spring Security

Severity: HIGH

Affected dependencies:
  - org.springframework.security:spring-security-core:5.7.11 (via org.springframework.boot:spring-boot-starter-security:2.7.18; declared at pom.xml:65); affected range < 5.7.12; first patched version 5.7.12

### CVE-2024-22259: Spring Framework URL Parsing with Host Validation Vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22259](https://github.com/advisories/GHSA-hgjh-9rj2-g67j): Spring Framework URL Parsing with Host Validation Vulnerability

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 6.1.0, < 6.1.5; first patched version 6.1.5

### CVE-2024-22262: Spring Framework URL Parsing with Host Validation
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22262](https://github.com/advisories/GHSA-2wrp-6fg6-hmc5): Spring Framework URL Parsing with Host Validation

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 5.3.34; first patched version 5.3.34

### CVE-2024-34750: Apache Tomcat - Denial of Service
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-34750](https://github.com/advisories/GHSA-wm9w-rjj3-j356): Apache Tomcat - Denial of Service

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.0-M21; first patched version 11.0.0-M21

### CVE-2024-38286: Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38286](https://github.com/advisories/GHSA-7jqf-v358-p8g7): Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.0-M21; first patched version 11.0.0-M21

### CVE-2024-38816: Path traversal vulnerability in functional web frameworks
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38816](https://github.com/advisories/GHSA-cx7f-g6mp-7hqm): Path traversal vulnerability in functional web frameworks

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 6.1.0, < 6.1.13; first patched version 6.1.13

### CVE-2024-38819: Spring Framework Path Traversal vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38819](https://github.com/advisories/GHSA-g5vr-rgqm-vf78): Spring Framework Path Traversal vulnerability

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 6.1.0, < 6.1.14; first patched version 6.1.14

### CVE-2024-47554: Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:71

[CVE-2024-47554](https://github.com/advisories/GHSA-78wr-2p64-hpwj): Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader

Severity: HIGH

Affected dependencies:
  - commons-io:commons-io:2.11.0 (via commons-io:commons-io:2.11.0; declared at pom.xml:71); affected range >= 2.0, < 2.14.0; first patched version 2.14.0

### CVE-2024-50379: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-50379](https://github.com/advisories/GHSA-5j33-cvvr-w245): Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.2; first patched version 11.0.2

### CVE-2024-56337: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-56337](https://github.com/advisories/GHSA-27hp-xhwr-wr2m): Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.2; first patched version 11.0.2

### CVE-2025-22228: Spring Security Does Not Enforce Password Length
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2025-22228](https://github.com/advisories/GHSA-mg83-c7gq-rv5c): Spring Security Does Not Enforce Password Length

Severity: HIGH

Affected dependencies:
  - org.springframework.security:spring-security-crypto:5.7.11 (via org.springframework.boot:spring-boot-starter-security:2.7.18; declared at pom.xml:65); affected range >= 6.3.0, < 6.3.8; first patched version 6.3.8

### CVE-2025-22235: Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2025-22235](https://github.com/advisories/GHSA-rc42-6c7j-7h5r): Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed

Severity: HIGH

Affected dependencies:
  - org.springframework.boot:spring-boot:2.7.18 (via org.springframework.boot:spring-boot-devtools:2.7.18; declared at pom.xml:98); affected range <= 2.7.24.2; first patched version not specified

### CVE-2025-41249: Spring Framework annotation detection mechanism may result in improper authorization
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2025-41249](https://github.com/advisories/GHSA-jmp9-x22r-554x): Spring Framework annotation detection mechanism may result in improper authorization

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-core:5.3.31 (via org.springframework.boot:spring-boot-starter-test:2.7.18; declared at pom.xml:84); affected range >= 5.3.0, <= 5.3.44; first patched version not specified

### CVE-2025-48988: Apache Tomcat - DoS in multipart upload
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-48988](https://github.com/advisories/GHSA-h3gc-qfqq-6h8f): Apache Tomcat - DoS in multipart upload

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, <= 11.0.7; first patched version 11.0.8

### CVE-2025-48989: Apache Tomcat Improper Resource Shutdown or Release vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-48989](https://github.com/advisories/GHSA-gqp3-2cvr-x8m3): Apache Tomcat Improper Resource Shutdown or Release vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.10; first patched version 11.0.10

### CVE-2025-52520: Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-52520](https://github.com/advisories/GHSA-wr62-c79q-cv37): Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.9; first patched version 11.0.9

### CVE-2025-52999: jackson-core can throw a StackoverflowError when processing deeply nested data
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2025-52999](https://github.com/advisories/GHSA-h46c-h94j-95f3): jackson-core can throw a StackoverflowError when processing deeply nested data

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-core:2.13.5 (via org.springframework.boot:spring-boot-starter-json:2.7.18; declared at pom.xml:78); affected range < 2.15.0; first patched version 2.15.0

### CVE-2025-53506: Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-53506](https://github.com/advisories/GHSA-25xr-qj8w-c4vf): Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 8.5.0, <= 8.5.100; first patched version not specified

### CVE-2025-55752: Apache Tomcat Vulnerable to Relative Path Traversal
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-55752](https://github.com/advisories/GHSA-wmwf-9ccg-fff5): Apache Tomcat Vulnerable to Relative Path Traversal

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.11; first patched version 11.0.11

### CVE-2026-24400: AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2026-24400](https://github.com/advisories/GHSA-rqfh-9r24-8c9r): AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion

Severity: HIGH

Affected dependencies:
  - org.assertj:assertj-core:3.22.0 (via org.springframework.boot:spring-boot-starter-test:2.7.18; declared at pom.xml:84); affected range >= 1.4.0, <= 3.27.6; first patched version 3.27.7

### CVE-2026-24734: Apache Tomcat has an Improper Input Validation vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-24734](https://github.com/advisories/GHSA-mgp5-rv84-w37q): Apache Tomcat has an Improper Input Validation vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.18; first patched version 11.0.18

### CVE-2026-24880: Apache Tomcat has an HTTP Request/Response Smuggling vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-24880](https://github.com/advisories/GHSA-563x-q5rq-57qp): Apache Tomcat has an HTTP Request/Response Smuggling vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 7.0.0, < 9.0.116; first patched version 9.0.116

### CVE-2026-34483: Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-34483](https://github.com/advisories/GHSA-rv64-5gf8-9qq8): Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 9.0.40, < 9.0.116; first patched version 9.0.116

### CVE-2026-34487: Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-34487](https://github.com/advisories/GHSA-x4m4-345f-5h5g): Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 9.0.13, < 9.0.117; first patched version 9.0.117

### CVE-2026-40972: Spring Boot DevTools remote secret comparison is vulnerable to timing attacks
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-40972](https://github.com/advisories/GHSA-56v8-86gj-66jp): Spring Boot DevTools remote secret comparison is vulnerable to timing attacks

Severity: HIGH

Affected dependencies:
  - org.springframework.boot:spring-boot-devtools:2.7.18 (via org.springframework.boot:spring-boot-devtools:2.7.18; declared at pom.xml:98); affected range >= 4.0.0, < 4.0.6; first patched version 4.0.6

### CVE-2026-40973: Spring Boot accepts predictable temp directory without ownership verification
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-40973](https://github.com/advisories/GHSA-wwpq-f5c3-7hvx): Spring Boot accepts predictable temp directory without ownership verification

Severity: HIGH

Affected dependencies:
  - org.springframework.boot:spring-boot:2.7.18 (via org.springframework.boot:spring-boot-devtools:2.7.18; declared at pom.xml:98); affected range >= 4.0.0, < 4.0.6; first patched version 4.0.6

### CVE-2026-41284: Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41284](https://github.com/advisories/GHSA-gx5v-xp9w-j4cg): Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 9.0.118; first patched version 9.0.118

### CVE-2026-41716: Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:46

[CVE-2026-41716](https://github.com/advisories/GHSA-9fw2-h3hf-293r): Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys

Severity: HIGH

Affected dependencies:
  - org.springframework.data:spring-data-commons:2.7.18 (via org.springframework.boot:spring-boot-starter-data-jpa:2.7.18; declared at pom.xml:46); affected range >= 4.0.0, <= 4.0.5; first patched version 4.0.6

### CVE-2026-41842: Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41842](https://github.com/advisories/GHSA-x23c-287f-qqv5): Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 7.0.0, <= 7.0.7; first patched version 7.0.8

### CVE-2026-41845: Spring Framework Cross-site Scripting via JavaScriptUtils
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41845](https://github.com/advisories/GHSA-3chg-m5w7-qfv5): Spring Framework Cross-site Scripting via JavaScriptUtils

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 7.0.0, <= 7.0.7; first patched version 7.0.8

### CVE-2026-41849: Spring Framework Denial of Service via Integer Overflow in SpEL Expressions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41849](https://github.com/advisories/GHSA-775g-4xr8-78h8): Spring Framework Denial of Service via Integer Overflow in SpEL Expressions

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-expression:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range <= 5.3.39; first patched version not specified

### CVE-2026-41850: Spring Framework Algorithmic Denial of Service via SpEL Expressions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41850](https://github.com/advisories/GHSA-r5w3-xv2f-j59q): Spring Framework Algorithmic Denial of Service via SpEL Expressions

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-expression:5.3.31 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 7.0.0, <= 7.0.7; first patched version 7.0.8

### CVE-2026-42498: Apache Tomcat - WebSocket authentication header exposure
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-42498](https://github.com/advisories/GHSA-fv25-8xcx-gqjc): Apache Tomcat - WebSocket authentication header exposure

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 9.0.118; first patched version 9.0.118

### CVE-2026-43513: Apache Tomcat: LockOutRealm treats user names as case-sensitive
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43513](https://github.com/advisories/GHSA-5mp6-jrq3-r938): Apache Tomcat: LockOutRealm treats user names as case-sensitive

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range < 9.0.118; first patched version 9.0.118

### CVE-2026-53404: Apache Tomcat's rewrite valve has an Always-Incorrect Control Flow Implementation vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-53404](https://github.com/advisories/GHSA-h792-v28v-ppgr): Apache Tomcat's rewrite valve has an Always-Incorrect Control Flow Implementation vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.23; first patched version 11.0.23

### CVE-2026-54512: jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54512](https://github.com/advisories/GHSA-j3rv-43j4-c7qm): jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (via org.springframework.boot:spring-boot-starter-json:2.7.18; declared at pom.xml:78); affected range >= 2.10.0, <= 2.18.7; first patched version 2.18.8

### CVE-2026-54513: jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54513](https://github.com/advisories/GHSA-rmj7-2vxq-3g9f): jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (via org.springframework.boot:spring-boot-starter-json:2.7.18; declared at pom.xml:78); affected range >= 2.10.0, < 2.18.8; first patched version 2.18.8

### CVE-2026-55957: Apache Tomcat has a Missing Critical Step in Authentication vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-55957](https://github.com/advisories/GHSA-7895-gffq-w6jq): Apache Tomcat has a Missing Critical Step in Authentication vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (via org.springframework.boot:spring-boot-starter-web:2.7.18; declared at pom.xml:34); affected range >= 11.0.0-M1, < 11.0.5; first patched version 11.0.5

### CVE-2026-68494: jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-68494](https://github.com/advisories/GHSA-r7wm-3cxj-wff9): jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-core:2.13.5 (via org.springframework.boot:spring-boot-starter-json:2.7.18; declared at pom.xml:78); affected range < 2.18.8; first patched version 2.18.8

### CVE-2026-89425: jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-89425](https://github.com/advisories/GHSA-7hhh-6rmp-j9qf): jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-core:2.13.5 (via org.springframework.boot:spring-boot-starter-json:2.7.18; declared at pom.xml:78); affected range >= 2.19.0, <= 2.21.6; first patched version 2.21.7

### CVE-2026-91776: jackson-databind retains every unknown raw type ID 
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-91776](https://github.com/advisories/GHSA-wv8q-qhhj-9h54): jackson-databind retains every unknown raw type ID 

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (via org.springframework.boot:spring-boot-starter-json:2.7.18; declared at pom.xml:78); affected range >= 2.0.0, <= 2.18.10; first patched version 2.18.11

### CVE-2026-91777: jackson-databind quadratic forward-reference completion 
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-91777](https://github.com/advisories/GHSA-cxp5-3px4-pw24): jackson-databind quadratic forward-reference completion 

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (via org.springframework.boot:spring-boot-starter-json:2.7.18; declared at pom.xml:78); affected range >= 2.19.0, <= 2.21.6; first patched version 2.21.7

## CWE Findings (Code-Level Vulnerabilities)

### CWE-606: Unchecked Input for Loop Condition
- **Category:** Code Quality
- **Severity:** potential
- **Story Points:** 3
- **Files:** src/main/java/com/photoalbum/controller/HomeController.java, src/main/resources/application.properties

HomeController.uploadPhotos iterates over every MultipartFile supplied in the request (lines 57-69) without enforcing an item-count cap. The configuration declares app.file-upload.max-files-per-upload=10, but it is not consumed by the controller or service, so an attacker can drive the loop with an oversized list of multipart parts.

### CWE-434: Unrestricted Upload of File with Dangerous Type
- **Category:** File & Path Security
- **Severity:** mandatory
- **Story Points:** 8
- **Files:** src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java, src/main/java/com/photoalbum/controller/PhotoFileController.java

PhotoServiceImpl.uploadPhoto (lines 87-94) validates only MultipartFile.getContentType(), which is controlled by the upload request. The bytes are then persisted even when ImageIO finds no reader (lines 122-149). PhotoFileController.servePhoto (lines 57-76) returns those bytes with the stored client-provided MIME type, so the content/type allowlist can be bypassed by labeling arbitrary bytes as an allowed image type.
