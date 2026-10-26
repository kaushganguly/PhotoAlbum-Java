# Security Assessment Report

**Generated:** 2026-10-26T20:46:41.006107Z

Minimum CVE severity: **medium**. Dependency scope: resolved compile, runtime and test dependencies. Affected versions do not establish application-specific exploitability. CWE analysis is static; no exploits were executed.

## Summary

| Metric | Count |
|---|---|
| Total Findings | 109 |
| CVE Vulnerabilities | 104 |
| CWE Vulnerabilities | 5 |
| Total Rules Assessed | 59 |
| Rules Passed | 54 |

### By Severity

| Severity | Count |
|---|---|
| mandatory | 61 |
| optional | 45 |
| potential | 3 |

## CVE Findings (Dependency Vulnerabilities)

### CVE-2026-47884: Spring Framework Improper Path Limitation in XsltView
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-47884](https://github.com/advisories/GHSA-pc63-qcmh-9cmg): Spring Framework Improper Path Limitation in XsltView

Severity: CRITICAL

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 5.3.0, <= 5.3.49

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-65905: Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-65905](https://github.com/advisories/GHSA-9xv2-5v5q-p794): Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.121

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.121 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-65182: Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-65182](https://github.com/advisories/GHSA-gcx9-497g-6cp6): Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0-M1, < 9.0.121

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.121 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-68525: Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-68525](https://github.com/advisories/GHSA-h3x4-894j-xpx5): Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0-M1, < 9.0.121

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.121 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-49844: Apache Log4j API: Improper encoding of non-finite floating-point values during MapMessage JSON serialization
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-49844](https://github.com/advisories/GHSA-qv9r-c865-cp47): Apache Log4j API: Improper encoding of non-finite floating-point values during MapMessage JSON serialization

Severity: MEDIUM

Affected dependencies:
  - org.apache.logging.log4j:log4j-api:2.17.2 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 2.13.1, < 2.25.5

Recommended fix:
  - org.apache.logging.log4j:log4j-api: upgrade to 2.25.5 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41853: Spring Framework Multipart Request Smuggling in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41853](https://github.com/advisories/GHSA-cjpg-rgq5-fr37): Spring Framework Multipart Request Smuggling in Spring MVC and WebFlux

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41851: Spring Framework Denial of Service via Unbounded Cache in SpEL
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41851](https://github.com/advisories/GHSA-wxpp-56q6-5pcg): Spring Framework Denial of Service via Unbounded Cache in SpEL

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-expression:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-expression: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41850: Spring Framework Algorithmic Denial of Service via SpEL Expressions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41850](https://github.com/advisories/GHSA-r5w3-xv2f-j59q): Spring Framework Algorithmic Denial of Service via SpEL Expressions

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-expression:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-expression: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41849: Spring Framework Denial of Service via Integer Overflow in SpEL Expressions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41849](https://github.com/advisories/GHSA-775g-4xr8-78h8): Spring Framework Denial of Service via Integer Overflow in SpEL Expressions

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-expression:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-expression: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41846: Spring Framework Cross-site Scripting via JSP Form Tags
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41846](https://github.com/advisories/GHSA-957g-f97v-vppc): Spring Framework Cross-site Scripting via JSP Form Tags

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41843: Spring Framework Path Traversal via Versioned Static Resources in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41843](https://github.com/advisories/GHSA-72pg-x5f8-j25j): Spring Framework Path Traversal via Versioned Static Resources in Spring MVC and WebFlux

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41844: Spring Framework Open Redirect in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41844](https://github.com/advisories/GHSA-h3qp-gqrc-q736): Spring Framework Open Redirect in Spring MVC and WebFlux

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41845: Spring Framework Cross-site Scripting via JavaScriptUtils
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41845](https://github.com/advisories/GHSA-3chg-m5w7-qfv5): Spring Framework Cross-site Scripting via JavaScriptUtils

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41841: Spring Framework Information Disclosure via Static Resource Cache in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41841](https://github.com/advisories/GHSA-mq64-j8f9-9gcj): Spring Framework Information Disclosure via Static Resource Cache in Spring MVC and WebFlux

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41842: Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41842](https://github.com/advisories/GHSA-x23c-287f-qqv5): Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41284: Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41284](https://github.com/advisories/GHSA-gx5v-xp9w-j4cg): Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 9.0.118

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.118 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-43512: Apache Tomcat - Digest authenticator will authenticate any unknown user
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43512](https://github.com/advisories/GHSA-h6fc-48rj-7qqh): Apache Tomcat - Digest authenticator will authenticate any unknown user

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 9.0.118

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.118 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-43513: Apache Tomcat: LockOutRealm treats user names as case-sensitive
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43513](https://github.com/advisories/GHSA-5mp6-jrq3-r938): Apache Tomcat: LockOutRealm treats user names as case-sensitive

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 9.0.118

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.118 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-43515: Apache Tomcat - Security constraints not correctly applied
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-43515](https://github.com/advisories/GHSA-5m62-pw8w-7w9f): Apache Tomcat - Security constraints not correctly applied

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 9.0.118

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.118 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41293: Apache Tomcat - HTTP/2 request headers not validated
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-41293](https://github.com/advisories/GHSA-r29c-68gh-xp6x): Apache Tomcat - HTTP/2 request headers not validated

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 8.5.0, < 9.0.118

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.118 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-42498: Apache Tomcat - WebSocket authentication header exposure
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-42498](https://github.com/advisories/GHSA-fv25-8xcx-gqjc): Apache Tomcat - WebSocket authentication header exposure

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 9.0.118

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.118 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41901: Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-41901](https://github.com/advisories/GHSA-c9ph-gxww-7744): Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns

Severity: CRITICAL

Affected dependencies:
  - org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-thymeleaf at pom.xml:40); affected range: <= 3.1.4.RELEASE
  - org.thymeleaf:thymeleaf:3.0.15.RELEASE (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-thymeleaf at pom.xml:40); affected range: <= 3.1.4.RELEASE

Recommended fix:
  - org.thymeleaf:thymeleaf-spring5: upgrade to 3.1.5.RELEASE (advisory patched versions; select a compatible branch and verify all advisories)
  - org.thymeleaf:thymeleaf: upgrade to 3.1.5.RELEASE (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-22745: Spring MVC and WebFlux applications are vulnerable to Denial of Service attacks when resolving static resources
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-22745](https://github.com/advisories/GHSA-6p4f-wcwh-5vvm): Spring MVC and WebFlux applications are vulnerable to Denial of Service attacks when resolving static resources

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.47

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-40478: Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-40478](https://github.com/advisories/GHSA-xjw8-8c5c-9r79): Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf

Severity: CRITICAL

Affected dependencies:
  - org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-thymeleaf at pom.xml:40); affected range: <= 3.1.3.RELEASE
  - org.thymeleaf:thymeleaf:3.0.15.RELEASE (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-thymeleaf at pom.xml:40); affected range: <= 3.1.3.RELEASE

Recommended fix:
  - org.thymeleaf:thymeleaf-spring5: upgrade to 3.1.4.RELEASE (advisory patched versions; select a compatible branch and verify all advisories)
  - org.thymeleaf:thymeleaf: upgrade to 3.1.4.RELEASE (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-40477: Improper restriction of the scope of accessible objects in Thymeleaf expressions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

[CVE-2026-40477](https://github.com/advisories/GHSA-r4v4-5mwr-2fwr): Improper restriction of the scope of accessible objects in Thymeleaf expressions

Severity: CRITICAL

Affected dependencies:
  - org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-thymeleaf at pom.xml:40); affected range: <= 3.1.3.RELEASE
  - org.thymeleaf:thymeleaf:3.0.15.RELEASE (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-thymeleaf at pom.xml:40); affected range: <= 3.1.3.RELEASE

Recommended fix:
  - org.thymeleaf:thymeleaf-spring5: upgrade to 3.1.4.RELEASE (advisory patched versions; select a compatible branch and verify all advisories)
  - org.thymeleaf:thymeleaf: upgrade to 3.1.4.RELEASE (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-34483: Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-34483](https://github.com/advisories/GHSA-rv64-5gf8-9qq8): Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.40, < 9.0.116

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.116 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-34487: Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-34487](https://github.com/advisories/GHSA-x4m4-345f-5h5g): Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.13, < 9.0.117

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.117 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-25854: Apache Tomcat has an Open Redirect vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-25854](https://github.com/advisories/GHSA-9m3c-qcxr-9x87): Apache Tomcat has an Open Redirect vulnerability

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 8.5.30, < 9.0.116

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.116 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-24880: Apache Tomcat has an HTTP Request/Response Smuggling vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-24880](https://github.com/advisories/GHSA-563x-q5rq-57qp): Apache Tomcat has an HTTP Request/Response Smuggling vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 7.0.0, < 9.0.116

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.116 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-22737: Spring Framework Improper Path Limitation with Script View Templates
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-22737](https://github.com/advisories/GHSA-4773-3jfm-qmx3): Spring Framework Improper Path Limitation with Script View Templates

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 5.3.0, <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-24734: Apache Tomcat has an Improper Input Validation vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2026-24734](https://github.com/advisories/GHSA-mgp5-rv84-w37q): Apache Tomcat has an Improper Input Validation vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.83, < 9.0.115

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.115 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-66614: Apache Tomcat - Client certificate verification bypass
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-66614](https://github.com/advisories/GHSA-fpj8-gq4v-p354): Apache Tomcat - Client certificate verification bypass

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0-M1, < 9.0.113

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.113 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-55752: Apache Tomcat Vulnerable to Relative Path Traversal
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-55752](https://github.com/advisories/GHSA-wmwf-9ccg-fff5): Apache Tomcat Vulnerable to Relative Path Traversal

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0-M11, < 9.0.109

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.109 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-11226: QOS.CH logback-core is vulnerable to Arbitrary Code Execution through file processing
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-11226](https://github.com/advisories/GHSA-25qh-j22f-pwp8): QOS.CH logback-core is vulnerable to Arbitrary Code Execution through file processing

Severity: MEDIUM

Affected dependencies:
  - ch.qos.logback:logback-core:1.2.12 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.3.16

Recommended fix:
  - ch.qos.logback:logback-core: upgrade to 1.3.16 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-41242: Spring Framework MVC Applications Path Traversal Vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-41242](https://github.com/advisories/GHSA-r936-gwx5-v52f): Spring Framework MVC Applications Path Traversal Vulnerability

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 5.3.0, <= 5.3.43

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-48989: Apache Tomcat Improper Resource Shutdown or Release vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-48989](https://github.com/advisories/GHSA-gqp3-2cvr-x8m3): Apache Tomcat Improper Resource Shutdown or Release vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.108

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.108 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-55668: Apache Tomcat Session Fixation vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-55668](https://github.com/advisories/GHSA-23hv-mwm6-g8jf): Apache Tomcat Session Fixation vulnerability

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.106

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.106 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-53506: Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-53506](https://github.com/advisories/GHSA-25xr-qj8w-c4vf): Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.107

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.107 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-52520: Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-52520](https://github.com/advisories/GHSA-wr62-c79q-cv37): Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.107

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.107 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-52434: Apache Tomcat is vulnerable to resource exhaustion when using the APR/Native connector
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-52434](https://github.com/advisories/GHSA-4j3c-42xv-3f84): Apache Tomcat is vulnerable to resource exhaustion when using the APR/Native connector

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.107

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.107 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-49124: Apache Tomcat installer for Windows has an untrusted search path vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-49124](https://github.com/advisories/GHSA-42wg-hm62-jcwg): Apache Tomcat installer for Windows has an untrusted search path vulnerability

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.23, < 9.0.106

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.106 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-49125: Apache Tomcat - Security constraint bypass for pre/post-resources
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-49125](https://github.com/advisories/GHSA-wc4r-xq3c-5cf3): Apache Tomcat - Security constraint bypass for pre/post-resources

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, <= 9.0.105

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.106 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-48988: Apache Tomcat - DoS in multipart upload
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-48988](https://github.com/advisories/GHSA-h3gc-qfqq-6h8f): Apache Tomcat - DoS in multipart upload

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, <= 9.0.105

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.106 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-31650: Apache Tomcat Denial of Service via invalid HTTP priority header
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-31650](https://github.com/advisories/GHSA-3p2h-wqq4-wf4h): Apache Tomcat Denial of Service via invalid HTTP priority header

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.76, <= 9.0.102

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.104 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-24813: Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2025-24813](https://github.com/advisories/GHSA-83qj-6fr2-vhqg): Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT

Severity: CRITICAL

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.99

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.99 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-56337: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-56337](https://github.com/advisories/GHSA-27hp-xhwr-wr2m): Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.98

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.98 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38819: Spring Framework Path Traversal vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38819](https://github.com/advisories/GHSA-g5vr-rgqm-vf78): Spring Framework Path Traversal vulnerability

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.40

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-12798: QOS.CH logback-core Expression Language Injection vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-12798](https://github.com/advisories/GHSA-pr98-23f8-jwxv): QOS.CH logback-core Expression Language Injection vulnerability

Severity: MEDIUM

Affected dependencies:
  - ch.qos.logback:logback-core:1.2.12 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.3.15

Recommended fix:
  - ch.qos.logback:logback-core: upgrade to 1.3.15 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-50379: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-50379](https://github.com/advisories/GHSA-5j33-cvvr-w245): Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0.M1, < 9.0.98

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.98 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38828: Spring MVC controller vulnerable to a DoS attack
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38828](https://github.com/advisories/GHSA-w3c8-7r8f-9jp8): Spring MVC controller vulnerable to a DoS attack

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 5.3.0, < 5.3.42

Recommended fix:
  - org.springframework:spring-webmvc: upgrade to 5.3.42 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38286: Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38286](https://github.com/advisories/GHSA-7jqf-v358-p8g7): Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.13, < 9.0.90

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.90 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38820: Spring Framework DataBinder Case Sensitive Match Exception
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38820](https://github.com/advisories/GHSA-4gc7-5j7h-4qph): Spring Framework DataBinder Case Sensitive Match Exception

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.40
  - org.springframework:spring-context:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 5.3.40

Recommended fix:
  - org.springframework:spring-web: no patched version listed for the matched affected range; migrate to a maintained release
  - org.springframework:spring-context: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38809: Spring Framework DoS via conditional HTTP request
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38809](https://github.com/advisories/GHSA-2rmj-mq67-h97g): Spring Framework DoS via conditional HTTP request

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 5.3.38

Recommended fix:
  - org.springframework:spring-web: upgrade to 5.3.38 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38816: Path traversal vulnerability in functional web frameworks
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38816](https://github.com/advisories/GHSA-cx7f-g6mp-7hqm): Path traversal vulnerability in functional web frameworks

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-webmvc:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 5.3.0, <= 5.3.39

Recommended fix:
  - org.springframework:spring-webmvc: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38808: Spring Framework vulnerable to Denial of Service
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-38808](https://github.com/advisories/GHSA-9cmq-m9j5-mvww): Spring Framework vulnerable to Denial of Service

Severity: MEDIUM

Affected dependencies:
  - org.springframework:spring-expression:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 5.3.39

Recommended fix:
  - org.springframework:spring-expression: upgrade to 5.3.39 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-34750: Apache Tomcat - Denial of Service
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-34750](https://github.com/advisories/GHSA-wm9w-rjj3-j356): Apache Tomcat - Denial of Service

Severity: HIGH

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0-M1, < 9.0.90

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.90 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-22262: Spring Framework URL Parsing with Host Validation
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22262](https://github.com/advisories/GHSA-2wrp-6fg6-hmc5): Spring Framework URL Parsing with Host Validation

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 5.3.34

Recommended fix:
  - org.springframework:spring-web: upgrade to 5.3.34 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-22259: Spring Framework URL Parsing with Host Validation Vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22259](https://github.com/advisories/GHSA-hgjh-9rj2-g67j): Spring Framework URL Parsing with Host Validation Vulnerability

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 5.3.33

Recommended fix:
  - org.springframework:spring-web: upgrade to 5.3.33 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-23672: Denial of Service via incomplete cleanup vulnerability in Apache Tomcat
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-23672](https://github.com/advisories/GHSA-v682-8vv8-vpwr): Denial of Service via incomplete cleanup vulnerability in Apache Tomcat

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-websocket:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0-M1, <= 9.0.85

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-websocket: upgrade to 9.0.86 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-24549: Apache Tomcat Denial of Service due to improper input validation vulnerability for HTTP/2 requests
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-24549](https://github.com/advisories/GHSA-7w75-32cg-r6g2): Apache Tomcat Denial of Service due to improper input validation vulnerability for HTTP/2 requests

Severity: MEDIUM

Affected dependencies:
  - org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 9.0.0-M1, <= 9.0.85

Recommended fix:
  - org.apache.tomcat.embed:tomcat-embed-core: upgrade to 9.0.86 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-22243: Spring Web vulnerable to Open Redirect or Server Side Request Forgery
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2024-22243](https://github.com/advisories/GHSA-ccgv-vj62-xf9h): Spring Web vulnerable to Open Redirect or Server Side Request Forgery

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: >= 5.3.0, < 5.3.32

Recommended fix:
  - org.springframework:spring-web: upgrade to 5.3.32 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2023-6481: Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2023-6481](https://github.com/advisories/GHSA-gm62-rw4g-vrc4): Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data

Severity: HIGH

Affected dependencies:
  - ch.qos.logback:logback-core:1.2.12 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: = 1.2.12

Recommended fix:
  - ch.qos.logback:logback-core: upgrade to 1.2.13 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2023-6378: logback serialization vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2023-6378](https://github.com/advisories/GHSA-vmq6-5m68-f53m): logback serialization vulnerability

Severity: HIGH

Affected dependencies:
  - ch.qos.logback:logback-classic:1.2.12 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.2.13
  - ch.qos.logback:logback-core:1.2.12 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.2.13

Recommended fix:
  - ch.qos.logback:logback-classic: upgrade to 1.2.13 (advisory patched versions; select a compatible branch and verify all advisories)
  - ch.qos.logback:logback-core: upgrade to 1.2.13 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-1471: SnakeYaml Constructor Deserialization Remote Code Execution
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-1471](https://github.com/advisories/GHSA-mjmj-j48q-9wg2): SnakeYaml Constructor Deserialization Remote Code Execution

Severity: HIGH

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: <= 1.33

Recommended fix:
  - org.yaml:snakeyaml: upgrade to 2.0 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-41854: Snakeyaml vulnerable to Stack overflow leading to denial of service
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-41854](https://github.com/advisories/GHSA-w37g-rhq8-7m4j): Snakeyaml vulnerable to Stack overflow leading to denial of service

Severity: MEDIUM

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.32

Recommended fix:
  - org.yaml:snakeyaml: upgrade to 1.32 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-38751: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38751](https://github.com/advisories/GHSA-98wm-3w3q-mw94): snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.31

Recommended fix:
  - org.yaml:snakeyaml: upgrade to 1.31 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-38750: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38750](https://github.com/advisories/GHSA-hhhw-99gj-p3c3): snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.31

Recommended fix:
  - org.yaml:snakeyaml: upgrade to 1.31 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-38749: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38749](https://github.com/advisories/GHSA-c4r9-r8fh-9vj2): snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.31

Recommended fix:
  - org.yaml:snakeyaml: upgrade to 1.31 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-38752: snakeYAML before 1.32 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-38752](https://github.com/advisories/GHSA-9w3m-gqgf-c4p9): snakeYAML before 1.32 vulnerable to Denial of Service due to Out-of-bounds Write

Severity: MEDIUM

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.32

Recommended fix:
  - org.yaml:snakeyaml: upgrade to 1.32 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-25857: Uncontrolled Resource Consumption in snakeyaml
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2022-25857](https://github.com/advisories/GHSA-3mc7-4q67-w48m): Uncontrolled Resource Consumption in snakeyaml

Severity: HIGH

Affected dependencies:
  - org.yaml:snakeyaml:1.30 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 1.31

Recommended fix:
  - org.yaml:snakeyaml: upgrade to 1.31 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2016-1000027: Pivotal Spring Framework contains unsafe Java deserialization methods
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

[CVE-2016-1000027](https://github.com/advisories/GHSA-4wrc-f8pq-fpqp): Pivotal Spring Framework contains unsafe Java deserialization methods

Severity: CRITICAL

Affected dependencies:
  - org.springframework:spring-web:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-web at pom.xml:34); affected range: < 6.0.0

Recommended fix:
  - org.springframework:spring-web: upgrade to 6.0.0 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-47838: Spring Security Vulnerable to Unauthorized User Impersonation when Using X.509 Client Certificates
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2026-47838](https://github.com/advisories/GHSA-293q-567p-wmwq): Spring Security Vulnerable to Unauthorized User Impersonation when Using X.509 Client Certificates

Severity: MEDIUM

Affected dependencies:
  - org.springframework.security:spring-security-web:5.7.11 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-security at pom.xml:65); affected range: <= 5.7.14

Recommended fix:
  - org.springframework.security:spring-security-web: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41721: Spring Data Commons: Denial of Service via excessive memory allocation in projection binding
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:46

[CVE-2026-41721](https://github.com/advisories/GHSA-5m4m-73w9-8433): Spring Data Commons: Denial of Service via excessive memory allocation in projection binding

Severity: MEDIUM

Affected dependencies:
  - org.springframework.data:spring-data-commons:2.7.18 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-data-jpa at pom.xml:46); affected range: <= 2.7.19

Recommended fix:
  - org.springframework.data:spring-data-commons: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41711: Spring Data Commons: StackOverflowException when parsing Sort parameters (DoS)
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:46

[CVE-2026-41711](https://github.com/advisories/GHSA-5vpf-xvv7-c8vh): Spring Data Commons: StackOverflowException when parsing Sort parameters (DoS)

Severity: MEDIUM

Affected dependencies:
  - org.springframework.data:spring-data-commons:2.7.18 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-data-jpa at pom.xml:46); affected range: <= 2.7.19

Recommended fix:
  - org.springframework.data:spring-data-commons: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41706: Spring Security: Open Redirect via Unvalidated Post-Login Redirect URL Stored in CookieRequestCache
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2026-41706](https://github.com/advisories/GHSA-x2r2-rvhq-2mqv): Spring Security: Open Redirect via Unvalidated Post-Login Redirect URL Stored in CookieRequestCache

Severity: MEDIUM

Affected dependencies:
  - org.springframework.security:spring-security-web:5.7.11 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-security at pom.xml:65); affected range: <= 5.7.23

Recommended fix:
  - org.springframework.security:spring-security-web: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41716: Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:46

[CVE-2026-41716](https://github.com/advisories/GHSA-9fw2-h3hf-293r): Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys

Severity: HIGH

Affected dependencies:
  - org.springframework.data:spring-data-commons:2.7.18 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-data-jpa at pom.xml:46); affected range: <= 2.7.19

Recommended fix:
  - org.springframework.data:spring-data-commons: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-22732: Spring Security HTTP Headers Are not Written Under Some Conditions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2026-22732](https://github.com/advisories/GHSA-mf92-479x-3373): Spring Security HTTP Headers Are not Written Under Some Conditions

Severity: CRITICAL

Affected dependencies:
  - org.springframework.security:spring-security-web:5.7.11 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-security at pom.xml:65); affected range: <= 5.7.14

Recommended fix:
  - org.springframework.security:spring-security-web: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-22228: Spring Security Does Not Enforce Password Length
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2025-22228](https://github.com/advisories/GHSA-mg83-c7gq-rv5c): Spring Security Does Not Enforce Password Length

Severity: HIGH

Affected dependencies:
  - org.springframework.security:spring-security-crypto:5.7.11 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-security at pom.xml:65); affected range: <= 5.7.15

Recommended fix:
  - org.springframework.security:spring-security-crypto: upgrade to 5.7.16 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38827: Spring Framework has Authorization Bypass for Case Sensitive Comparisons
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-38827](https://github.com/advisories/GHSA-q3v6-hm2v-pw99): Spring Framework has Authorization Bypass for Case Sensitive Comparisons

Severity: MEDIUM

Affected dependencies:
  - org.springframework.security:spring-security-core:5.7.11 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-security at pom.xml:65); affected range: < 5.7.14

Recommended fix:
  - org.springframework.security:spring-security-core: upgrade to 5.7.14 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-38821: Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-38821](https://github.com/advisories/GHSA-c4q5-6c82-3qpw): Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications

Severity: CRITICAL

Affected dependencies:
  - org.springframework.security:spring-security-web:5.7.11 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-security at pom.xml:65); affected range: >= 5.0.0, < 5.7.13

Recommended fix:
  - org.springframework.security:spring-security-web: upgrade to 5.7.13 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-22257: Erroneous authentication pass in Spring Security
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

[CVE-2024-22257](https://github.com/advisories/GHSA-f3jh-qvm4-mg39): Erroneous authentication pass in Spring Security

Severity: HIGH

Affected dependencies:
  - org.springframework.security:spring-security-core:5.7.11 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-security at pom.xml:65); affected range: < 5.7.12

Recommended fix:
  - org.springframework.security:spring-security-core: upgrade to 5.7.12 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-89425: jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-89425](https://github.com/advisories/GHSA-7hhh-6rmp-j9qf): jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-core:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.8.0, <= 2.18.10

Recommended fix:
  - com.fasterxml.jackson.core:jackson-core: upgrade to 2.18.11 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-91777: jackson-databind quadratic forward-reference completion 
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-91777](https://github.com/advisories/GHSA-cxp5-3px4-pw24): jackson-databind quadratic forward-reference completion 

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.5.0, <= 2.18.10

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.11 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-91776: jackson-databind retains every unknown raw type ID 
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-91776](https://github.com/advisories/GHSA-wv8q-qhhj-9h54): jackson-databind retains every unknown raw type ID 

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.0.0, <= 2.18.10

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.11 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-83557: jackson-databind: Comparable missing from DefaultBaseTypeLimitingValidator's unsafe base types (incomplete PolymorphicTypeValidator denylist)
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-83557](https://github.com/advisories/GHSA-gx83-3vf8-gh7j): jackson-databind: Comparable missing from DefaultBaseTypeLimitingValidator's unsafe base types (incomplete PolymorphicTypeValidator denylist)

Severity: MEDIUM

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.11.0, < 2.18.10

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.10 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-19032: jackson-databind: Path Deserialization Missing Scheme Allowlist for FileSystemProvider Resolution
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-19032](https://github.com/advisories/GHSA-wjgm-6hv5-3cvf): jackson-databind: Path Deserialization Missing Scheme Allowlist for FileSystemProvider Resolution

Severity: MEDIUM

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.8.0, < 2.18.10

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.10 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-77310: jackson-databind: Incomplete fix for CVE-2026-54514: eager DNS resolution (SSRF) still present in InetAddress deserialization
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-77310](https://github.com/advisories/GHSA-vvgp-rfg2-7rr6): jackson-databind: Incomplete fix for CVE-2026-54514: eager DNS resolution (SSRF) still present in InetAddress deserialization

Severity: MEDIUM

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.0.0, < 2.18.9

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.9 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-59889: jackson-databind: @JsonView bypassed for @JsonUnwrapped container properties on deserialization
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-59889](https://github.com/advisories/GHSA-5gvw-p9qm-jgwh): jackson-databind: @JsonView bypassed for @JsonUnwrapped container properties on deserialization

Severity: MEDIUM

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.0.0-RC1, < 2.18.9

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.9 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-68494: jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-68494](https://github.com/advisories/GHSA-r7wm-3cxj-wff9): jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-core:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: < 2.18.8

Recommended fix:
  - com.fasterxml.jackson.core:jackson-core: upgrade to 2.18.8 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-54515: jackson-databind has case-insensitive deserialization bypasses per-property @JsonIgnoreProperties
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54515](https://github.com/advisories/GHSA-5jmj-h7xm-6q6v): jackson-databind has case-insensitive deserialization bypasses per-property @JsonIgnoreProperties

Severity: MEDIUM

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.8.0, < 2.18.9

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.9 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-54514: jackson-databind: InetSocketAddress deserialization triggers eager DNS resolution (SSRF)
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54514](https://github.com/advisories/GHSA-hgj6-7826-r7m5): jackson-databind: InetSocketAddress deserialization triggers eager DNS resolution (SSRF)

Severity: MEDIUM

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.0.0, < 2.18.8

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.8 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-54513: jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54513](https://github.com/advisories/GHSA-rmj7-2vxq-3g9f): jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.10.0, < 2.18.8

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.8 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-54512: jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-54512](https://github.com/advisories/GHSA-j3rv-43j4-c7qm): jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.10.0, <= 2.18.7

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.18.8 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-50193: jackson-databind: Deeply nested JsonNode throws StackOverflowError for toString()
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2026-50193](https://github.com/advisories/GHSA-3wrr-7qpf-2prh): jackson-databind: Deeply nested JsonNode throws StackOverflowError for toString()

Severity: MEDIUM

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-databind:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: >= 2.10.0, <= 2.13.5

Recommended fix:
  - com.fasterxml.jackson.core:jackson-databind: upgrade to 2.14.0 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-24400: AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2026-24400](https://github.com/advisories/GHSA-rqfh-9r24-8c9r): AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion

Severity: HIGH

Affected dependencies:
  - org.assertj:assertj-core:3.22.0 (test; transitive, pulled by org.springframework.boot:spring-boot-starter-test at pom.xml:84); affected range: >= 1.4.0, <= 3.27.6

Recommended fix:
  - org.assertj:assertj-core: upgrade to 3.27.7 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-52999: jackson-core can throw a StackoverflowError when processing deeply nested data
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

[CVE-2025-52999](https://github.com/advisories/GHSA-h46c-h94j-95f3): jackson-core can throw a StackoverflowError when processing deeply nested data

Severity: HIGH

Affected dependencies:
  - com.fasterxml.jackson.core:jackson-core:2.13.5 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-json at pom.xml:78); affected range: < 2.15.0

Recommended fix:
  - com.fasterxml.jackson.core:jackson-core: upgrade to 2.15.0 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2024-47554: Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:71

[CVE-2024-47554](https://github.com/advisories/GHSA-78wr-2p64-hpwj): Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader

Severity: HIGH

Affected dependencies:
  - commons-io:commons-io:2.11.0 (compile; direct at pom.xml:71); affected range: >= 2.0, < 2.14.0

Recommended fix:
  - commons-io:commons-io: upgrade to 2.14.0 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2023-51074: json-path Out-of-bounds Write vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2023-51074](https://github.com/advisories/GHSA-pfh2-hfmq-phg5): json-path Out-of-bounds Write vulnerability

Severity: MEDIUM

Affected dependencies:
  - com.jayway.jsonpath:json-path:2.7.0 (test; transitive, pulled by org.springframework.boot:spring-boot-starter-test at pom.xml:84); affected range: >= 2.2.0, < 2.9.0

Recommended fix:
  - com.jayway.jsonpath:json-path: upgrade to 2.9.0 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-41001: Spring Boot: Predictable Temp Directory in Artemis Auto-configuration
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-41001](https://github.com/advisories/GHSA-ggg2-9786-hwc8): Spring Boot: Predictable Temp Directory in Artemis Auto-configuration

Severity: MEDIUM

Affected dependencies:
  - org.springframework.boot:spring-boot-autoconfigure:2.7.18 (compile; transitive, pulled by org.springframework.boot:spring-boot-devtools at pom.xml:98); affected range: >= 2.7.0, <= 2.7.33

Recommended fix:
  - org.springframework.boot:spring-boot-autoconfigure: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-40973: Spring Boot accepts predictable temp directory without ownership verification
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-40973](https://github.com/advisories/GHSA-wwpq-f5c3-7hvx): Spring Boot accepts predictable temp directory without ownership verification

Severity: HIGH

Affected dependencies:
  - org.springframework.boot:spring-boot:2.7.18 (compile; transitive, pulled by org.springframework.boot:spring-boot-devtools at pom.xml:98); affected range: <= 2.7.32

Recommended fix:
  - org.springframework.boot:spring-boot: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2026-40972: Spring Boot DevTools remote secret comparison is vulnerable to timing attacks
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2026-40972](https://github.com/advisories/GHSA-56v8-86gj-66jp): Spring Boot DevTools remote secret comparison is vulnerable to timing attacks

Severity: HIGH

Affected dependencies:
  - org.springframework.boot:spring-boot-devtools:2.7.18 (compile; direct at pom.xml:98); affected range: <= 2.7.32

Recommended fix:
  - org.springframework.boot:spring-boot-devtools: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-41249: Spring Framework annotation detection mechanism may result in improper authorization
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

[CVE-2025-41249](https://github.com/advisories/GHSA-jmp9-x22r-554x): Spring Framework annotation detection mechanism may result in improper authorization

Severity: HIGH

Affected dependencies:
  - org.springframework:spring-core:5.3.31 (compile; transitive, pulled by org.springframework.boot:spring-boot-starter-test at pom.xml:84); affected range: >= 5.3.0, <= 5.3.44

Recommended fix:
  - org.springframework:spring-core: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2025-22235: Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

[CVE-2025-22235](https://github.com/advisories/GHSA-rc42-6c7j-7h5r): Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed

Severity: HIGH

Affected dependencies:
  - org.springframework.boot:spring-boot:2.7.18 (compile; transitive, pulled by org.springframework.boot:spring-boot-devtools at pom.xml:98); affected range: <= 2.7.24.2

Recommended fix:
  - org.springframework.boot:spring-boot: no patched version listed for the matched affected range; migrate to a maintained release

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

### CVE-2022-45868: Password exposure in H2 Database 
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:91

[CVE-2022-45868](https://github.com/advisories/GHSA-22wj-vf5f-wrvj): Password exposure in H2 Database 

Severity: HIGH

Affected dependencies:
  - com.h2database:h2:2.1.214 (test; direct at pom.xml:91); affected range: >= 1.4.198, < 2.2.220

Recommended fix:
  - com.h2database:h2: upgrade to 2.2.220 (advisory patched versions; select a compatible branch and verify all advisories)

Version-based advisory match, not proof that application-specific exploit preconditions are reachable.

## CWE Findings (Code-Level Vulnerabilities)

### CWE-606: Unchecked Input for Loop Condition
- **Category:** Code Quality
- **Severity:** potential
- **Story Points:** 3
- **Files:** src/main/java/com/photoalbum/controller/HomeController.java, src/main/resources/application.properties

HomeController.uploadPhotos:62-69 checks only whether the externally supplied files list is null or empty, then iterates every multipart entry. The app.file-upload.max-files-per-upload=10 setting at application.properties:30 is never read or enforced. A caller authorized to upload can submit many tiny files within the 50MB byte limit, triggering repeated image parsing and database writes beyond the intended ten-file limit. This is excessive bounded-request work, not an infinite loop or an assertion of unauthenticated upload access.

### CWE-789: Memory Allocation with Excessive Size Value
- **Category:** Code Quality
- **Severity:** potential
- **Story Points:** 5
- **Files:** src/main/java/com/photoalbum/controller/HomeController.java, src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java, src/main/java/com/photoalbum/repository/PhotoRepository.java, src/main/java/com/photoalbum/model/Photo.java

HomeController.index:40 invokes getAllPhotos, PhotoServiceImpl:55-57 invokes findAllOrderByUploadedAtDesc, and PhotoRepository:22-27 selects every PHOTO_DATA BLOB without a row/total-byte limit. Photo.photoData:39-41 is a default eagerly fetched @Lob byte[] and the query materializes a List<Photo>. Upload callers control the cumulatively stored image volume; each public gallery request therefore allocates heap proportional to all stored BLOB bytes despite only needing metadata. Per-upload byte limits do not bound aggregate gallery allocation. No heap exhaustion test was run.

### CWE-778: Insufficient Logging
- **Category:** Credentials & Secrets
- **Severity:** potential
- **Story Points:** 3
- **Files:** src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java, src/main/java/com/photoalbum/controller/DetailController.java

PhotoServiceImpl.uploadPhoto:179-180 and deletePhoto:212 log successful security-critical mutations with only filename/photo ID. DetailController.deletePhoto:69 similarly logs only the photo ID. None includes the authenticated principal or audit correlation identifying who performed the mutation, and no application audit listener is configured. Consequently application mutation logs cannot attribute an upload/deletion to its authenticated actor. This finding concerns omitted actor details in application logs; external proxy/security audit capabilities were not assessed.

### CWE-434: Unrestricted Upload of File with Dangerous Type
- **Category:** File & Path Security
- **Severity:** mandatory
- **Story Points:** 8
- **Files:** src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java

PhotoServiceImpl.uploadPhoto validates only the client-supplied MIME label at lines 87-94. At lines 130-149, an unrecognized file (no ImageIO reader) is not rejected; arbitrary bytes labeled image/jpeg are saved at lines 160-174. Non-IOException decoder failures also continue at lines 155-157. Thus non-image/dangerous content can pass the image-only upload restriction and is fed to image header processors. This establishes unrestricted content acceptance, not server-side code execution; serving uses the supplied image MIME label.

### CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')
- **Category:** Injection Attacks
- **Severity:** optional
- **Story Points:** 8
- **Files:** src/main/resources/static/js/upload.js, src/main/java/com/photoalbum/controller/HomeController.java

HomeController.uploadPhotos returns the client-supplied original filename as originalFileName (lines 75-78). upload.js createPhotoCard interpolates it without HTML or attribute escaping at lines 185-189 and displayNewPhotos passes the constructed string to insertAdjacentHTML at line 157. A filename containing markup or an attribute delimiter can introduce executable DOM content in the uploading browser. This is a confirmed DOM-XSS sink/source chain; cross-user delivery was not demonstrated. First confirmed match reported; no executable payload was run.

## Coverage and Limitations

See [scan coverage](security-scan-coverage.json) and [dependency coverage](cve-scan-coverage.json) for scope, sequential execution, and limitations. NOT_FOUND is not proof of absence.
