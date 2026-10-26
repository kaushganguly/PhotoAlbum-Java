# Security Assessment Report

**Generated:** 2026-10-26T05:12:09.060072Z

## Scope and limitations

- Assessment is static; browser exploitation, deployed services and database behavior were not dynamically tested.
- NOT_FOUND means no qualifying vulnerability was confirmed by this assessment, not proof of absence.
- Denial-of-service-only, resource-exhaustion-only and low-impact code-quality patterns were excluded from confirmed CWE findings.
- Dependency advisory matches establish affected package versions, not application exploitability.
- GitHub CLI authentication was unavailable. Unauthenticated GitHub REST API requests succeeded without batch errors.
- CVE scan covers all 101 resolved direct and transitive dependencies, including test scope. Of 120 unique matched advisories, 104 meet the medium threshold; 16 low-severity advisories are retained only in the raw CVE results.
- Assessment reports findings only; no application or dependency remediation was performed.
- The core source analyzer reported that dependency output was unavailable; the separate Maven-resolved CVE scan supplies dependency coverage.

## Summary

| Metric | Count |
|---|---|
| TotalFindings | 105 |
| CveCount | 104 |
| CweCount | 1 |
| TotalRulesAssessed | 59 |
| RulesPassed | 58 |

### By Severity

| Severity | Count |
|---|---|
| mandatory | 60 |
| optional | 45 |
| potential | 0 |

## CVE Findings (Dependency Vulnerabilities)

### CVE-2026-47884: Spring Framework Improper Path Limitation in XsltView
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-47884](https://github.com/advisories/GHSA-pc63-qcmh-9cmg)

Severity: CRITICAL

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 5.3.0, <= 5.3.49; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-65905: Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-65905](https://github.com/advisories/GHSA-9xv2-5v5q-p794)

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.121; first patched version for this range: 9.0.121

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-65182: Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-65182](https://github.com/advisories/GHSA-gcx9-497g-6cp6)

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0-M1, < 9.0.121; first patched version for this range: 9.0.121

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-68525: Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-68525](https://github.com/advisories/GHSA-h3x4-894j-xpx5)

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0-M1, < 9.0.121; first patched version for this range: 9.0.121

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-49844: Apache Log4j API: Improper encoding of non-finite floating-point values during MapMessage JSON serialization
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-49844](https://github.com/advisories/GHSA-qv9r-c865-cp47)

Severity: MEDIUM

- org.apache.logging.log4j:log4j-api:2.17.2 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 2.13.1, < 2.25.5; first patched version for this range: 2.25.5

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41853: Spring Framework Multipart Request Smuggling in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41853](https://github.com/advisories/GHSA-cjpg-rgq5-fr37)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41851: Spring Framework Denial of Service via Unbounded Cache in SpEL
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41851](https://github.com/advisories/GHSA-wxpp-56q6-5pcg)

Severity: MEDIUM

- org.springframework:spring-expression:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41850: Spring Framework Algorithmic Denial of Service via SpEL Expressions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41850](https://github.com/advisories/GHSA-r5w3-xv2f-j59q)

Severity: HIGH

- org.springframework:spring-expression:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41849: Spring Framework Denial of Service via Integer Overflow in SpEL Expressions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41849](https://github.com/advisories/GHSA-775g-4xr8-78h8)

Severity: HIGH

- org.springframework:spring-expression:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41846: Spring Framework Cross-site Scripting via JSP Form Tags
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41846](https://github.com/advisories/GHSA-957g-f97v-vppc)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41843: Spring Framework Path Traversal via Versioned Static Resources in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41843](https://github.com/advisories/GHSA-72pg-x5f8-j25j)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41844: Spring Framework Open Redirect in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41844](https://github.com/advisories/GHSA-h3qp-gqrc-q736)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41845: Spring Framework Cross-site Scripting via JavaScriptUtils
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41845](https://github.com/advisories/GHSA-3chg-m5w7-qfv5)

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41841: Spring Framework Information Disclosure via Static Resource Cache in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41841](https://github.com/advisories/GHSA-mq64-j8f9-9gcj)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41842: Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41842](https://github.com/advisories/GHSA-x23c-287f-qqv5)

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41284: Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41284](https://github.com/advisories/GHSA-gx5v-xp9w-j4cg)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 9.0.118; first patched version for this range: 9.0.118

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-43512: Apache Tomcat - Digest authenticator will authenticate any unknown user
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-43512](https://github.com/advisories/GHSA-h6fc-48rj-7qqh)

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 9.0.118; first patched version for this range: 9.0.118

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-43513: Apache Tomcat: LockOutRealm treats user names as case-sensitive
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-43513](https://github.com/advisories/GHSA-5mp6-jrq3-r938)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 9.0.118; first patched version for this range: 9.0.118

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-43515: Apache Tomcat - Security constraints not correctly applied
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-43515](https://github.com/advisories/GHSA-5m62-pw8w-7w9f)

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 9.0.118; first patched version for this range: 9.0.118

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41293: Apache Tomcat - HTTP/2 request headers not validated
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-41293](https://github.com/advisories/GHSA-r29c-68gh-xp6x)

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 8.5.0, < 9.0.118; first patched version for this range: 9.0.118

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-42498: Apache Tomcat - WebSocket authentication header exposure
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-42498](https://github.com/advisories/GHSA-fv25-8xcx-gqjc)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 9.0.118; first patched version for this range: 9.0.118

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41901: Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:38

[CVE-2026-41901](https://github.com/advisories/GHSA-c9ph-gxww-7744)

Severity: CRITICAL

- org.thymeleaf:thymeleaf:3.0.15.RELEASE (transitive via org.springframework.boot:spring-boot-starter-thymeleaf; Maven scope: compile); affected range: <= 3.1.4.RELEASE; first patched version for this range: 3.1.5.RELEASE
- org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (transitive via org.springframework.boot:spring-boot-starter-thymeleaf; Maven scope: compile); affected range: <= 3.1.4.RELEASE; first patched version for this range: 3.1.5.RELEASE

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-22745: Spring MVC and WebFlux applications are vulnerable to Denial of Service attacks when resolving static resources
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-22745](https://github.com/advisories/GHSA-6p4f-wcwh-5vvm)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.47; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-40478: Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:38

[CVE-2026-40478](https://github.com/advisories/GHSA-xjw8-8c5c-9r79)

Severity: CRITICAL

- org.thymeleaf:thymeleaf:3.0.15.RELEASE (transitive via org.springframework.boot:spring-boot-starter-thymeleaf; Maven scope: compile); affected range: <= 3.1.3.RELEASE; first patched version for this range: 3.1.4.RELEASE
- org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (transitive via org.springframework.boot:spring-boot-starter-thymeleaf; Maven scope: compile); affected range: <= 3.1.3.RELEASE; first patched version for this range: 3.1.4.RELEASE

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-40477: Improper restriction of the scope of accessible objects in Thymeleaf expressions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:38

[CVE-2026-40477](https://github.com/advisories/GHSA-r4v4-5mwr-2fwr)

Severity: CRITICAL

- org.thymeleaf:thymeleaf:3.0.15.RELEASE (transitive via org.springframework.boot:spring-boot-starter-thymeleaf; Maven scope: compile); affected range: <= 3.1.3.RELEASE; first patched version for this range: 3.1.4.RELEASE
- org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE (transitive via org.springframework.boot:spring-boot-starter-thymeleaf; Maven scope: compile); affected range: <= 3.1.3.RELEASE; first patched version for this range: 3.1.4.RELEASE

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-34483: Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-34483](https://github.com/advisories/GHSA-rv64-5gf8-9qq8)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.40, < 9.0.116; first patched version for this range: 9.0.116

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-34487: Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-34487](https://github.com/advisories/GHSA-x4m4-345f-5h5g)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.13, < 9.0.117; first patched version for this range: 9.0.117

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-25854: Apache Tomcat has an Open Redirect vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-25854](https://github.com/advisories/GHSA-9m3c-qcxr-9x87)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 8.5.30, < 9.0.116; first patched version for this range: 9.0.116

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-24880: Apache Tomcat has an HTTP Request/Response Smuggling vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-24880](https://github.com/advisories/GHSA-563x-q5rq-57qp)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 7.0.0, < 9.0.116; first patched version for this range: 9.0.116

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-22737: Spring Framework Improper Path Limitation with Script View Templates
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-22737](https://github.com/advisories/GHSA-4773-3jfm-qmx3)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 5.3.0, <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-24734: Apache Tomcat has an Improper Input Validation vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2026-24734](https://github.com/advisories/GHSA-mgp5-rv84-w37q)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.83, < 9.0.115; first patched version for this range: 9.0.115

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-66614: Apache Tomcat - Client certificate verification bypass
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-66614](https://github.com/advisories/GHSA-fpj8-gq4v-p354)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0-M1, < 9.0.113; first patched version for this range: 9.0.113

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-55752: Apache Tomcat Vulnerable to Relative Path Traversal
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-55752](https://github.com/advisories/GHSA-wmwf-9ccg-fff5)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0-M11, < 9.0.109; first patched version for this range: 9.0.109

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-11226: QOS.CH logback-core is vulnerable to Arbitrary Code Execution through file processing
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-11226](https://github.com/advisories/GHSA-25qh-j22f-pwp8)

Severity: MEDIUM

- ch.qos.logback:logback-core:1.2.12 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.3.16; first patched version for this range: 1.3.16

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-41242: Spring Framework MVC Applications Path Traversal Vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-41242](https://github.com/advisories/GHSA-r936-gwx5-v52f)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 5.3.0, <= 5.3.43; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-48989: Apache Tomcat Improper Resource Shutdown or Release vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-48989](https://github.com/advisories/GHSA-gqp3-2cvr-x8m3)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.108; first patched version for this range: 9.0.108

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-55668: Apache Tomcat Session Fixation vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-55668](https://github.com/advisories/GHSA-23hv-mwm6-g8jf)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.106; first patched version for this range: 9.0.106

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-53506: Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-53506](https://github.com/advisories/GHSA-25xr-qj8w-c4vf)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.107; first patched version for this range: 9.0.107

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-52520: Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-52520](https://github.com/advisories/GHSA-wr62-c79q-cv37)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.107; first patched version for this range: 9.0.107

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-52434: Apache Tomcat is vulnerable to resource exhaustion when using the APR/Native connector
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-52434](https://github.com/advisories/GHSA-4j3c-42xv-3f84)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.107; first patched version for this range: 9.0.107

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-49124: Apache Tomcat installer for Windows has an untrusted search path vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-49124](https://github.com/advisories/GHSA-42wg-hm62-jcwg)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.23, < 9.0.106; first patched version for this range: 9.0.106

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-49125: Apache Tomcat - Security constraint bypass for pre/post-resources
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-49125](https://github.com/advisories/GHSA-wc4r-xq3c-5cf3)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, <= 9.0.105; first patched version for this range: 9.0.106

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-48988: Apache Tomcat - DoS in multipart upload
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-48988](https://github.com/advisories/GHSA-h3gc-qfqq-6h8f)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, <= 9.0.105; first patched version for this range: 9.0.106

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-31650: Apache Tomcat Denial of Service via invalid HTTP priority header
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-31650](https://github.com/advisories/GHSA-3p2h-wqq4-wf4h)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.76, <= 9.0.102; first patched version for this range: 9.0.104

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-24813: Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2025-24813](https://github.com/advisories/GHSA-83qj-6fr2-vhqg)

Severity: CRITICAL

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.99; first patched version for this range: 9.0.99

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-56337: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-56337](https://github.com/advisories/GHSA-27hp-xhwr-wr2m)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.98; first patched version for this range: 9.0.98

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38819: Spring Framework Path Traversal vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-38819](https://github.com/advisories/GHSA-g5vr-rgqm-vf78)

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.40; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-12798: QOS.CH logback-core Expression Language Injection vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-12798](https://github.com/advisories/GHSA-pr98-23f8-jwxv)

Severity: MEDIUM

- ch.qos.logback:logback-core:1.2.12 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.3.15; first patched version for this range: 1.3.15

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-50379: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-50379](https://github.com/advisories/GHSA-5j33-cvvr-w245)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0.M1, < 9.0.98; first patched version for this range: 9.0.98

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38828: Spring MVC controller vulnerable to a DoS attack
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-38828](https://github.com/advisories/GHSA-w3c8-7r8f-9jp8)

Severity: MEDIUM

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 5.3.0, < 5.3.42; first patched version for this range: 5.3.42

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38286: Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-38286](https://github.com/advisories/GHSA-7jqf-v358-p8g7)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.13, < 9.0.90; first patched version for this range: 9.0.90

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38820: Spring Framework DataBinder Case Sensitive Match Exception
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-38820](https://github.com/advisories/GHSA-4gc7-5j7h-4qph)

Severity: MEDIUM

- org.springframework:spring-context:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.40; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.
- org.springframework:spring-web:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 5.3.40; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38809: Spring Framework DoS via conditional HTTP request
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-38809](https://github.com/advisories/GHSA-2rmj-mq67-h97g)

Severity: MEDIUM

- org.springframework:spring-web:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 5.3.38; first patched version for this range: 5.3.38

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38816: Path traversal vulnerability in functional web frameworks
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-38816](https://github.com/advisories/GHSA-cx7f-g6mp-7hqm)

Severity: HIGH

- org.springframework:spring-webmvc:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 5.3.0, <= 5.3.39; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38808: Spring Framework vulnerable to Denial of Service
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-38808](https://github.com/advisories/GHSA-9cmq-m9j5-mvww)

Severity: MEDIUM

- org.springframework:spring-expression:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 5.3.39; first patched version for this range: 5.3.39

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-34750: Apache Tomcat - Denial of Service
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-34750](https://github.com/advisories/GHSA-wm9w-rjj3-j356)

Severity: HIGH

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0-M1, < 9.0.90; first patched version for this range: 9.0.90

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-22262: Spring Framework URL Parsing with Host Validation
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-22262](https://github.com/advisories/GHSA-2wrp-6fg6-hmc5)

Severity: HIGH

- org.springframework:spring-web:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 5.3.34; first patched version for this range: 5.3.34

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-22259: Spring Framework URL Parsing with Host Validation Vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-22259](https://github.com/advisories/GHSA-hgjh-9rj2-g67j)

Severity: HIGH

- org.springframework:spring-web:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 5.3.33; first patched version for this range: 5.3.33

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-23672: Denial of Service via incomplete cleanup vulnerability in Apache Tomcat
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-23672](https://github.com/advisories/GHSA-v682-8vv8-vpwr)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-websocket:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0-M1, <= 9.0.85; first patched version for this range: 9.0.86

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-24549: Apache Tomcat Denial of Service due to improper input validation vulnerability for HTTP/2 requests
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-24549](https://github.com/advisories/GHSA-7w75-32cg-r6g2)

Severity: MEDIUM

- org.apache.tomcat.embed:tomcat-embed-core:9.0.83 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 9.0.0-M1, <= 9.0.85; first patched version for this range: 9.0.86

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-22243: Spring Web vulnerable to Open Redirect or Server Side Request Forgery
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2024-22243](https://github.com/advisories/GHSA-ccgv-vj62-xf9h)

Severity: HIGH

- org.springframework:spring-web:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: >= 5.3.0, < 5.3.32; first patched version for this range: 5.3.32

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2023-6481: Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2023-6481](https://github.com/advisories/GHSA-gm62-rw4g-vrc4)

Severity: HIGH

- ch.qos.logback:logback-core:1.2.12 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: = 1.2.12; first patched version for this range: 1.2.13

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2023-6378: logback serialization vulnerability
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2023-6378](https://github.com/advisories/GHSA-vmq6-5m68-f53m)

Severity: HIGH

- ch.qos.logback:logback-core:1.2.12 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.2.13; first patched version for this range: 1.2.13
- ch.qos.logback:logback-classic:1.2.12 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.2.13; first patched version for this range: 1.2.13

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-1471: SnakeYaml Constructor Deserialization Remote Code Execution
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2022-1471](https://github.com/advisories/GHSA-mjmj-j48q-9wg2)

Severity: HIGH

- org.yaml:snakeyaml:1.30 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: <= 1.33; first patched version for this range: 2.0

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-41854: Snakeyaml vulnerable to Stack overflow leading to denial of service
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2022-41854](https://github.com/advisories/GHSA-w37g-rhq8-7m4j)

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.32; first patched version for this range: 1.32

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-38751: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2022-38751](https://github.com/advisories/GHSA-98wm-3w3q-mw94)

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.31; first patched version for this range: 1.31

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-38750: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2022-38750](https://github.com/advisories/GHSA-hhhw-99gj-p3c3)

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.31; first patched version for this range: 1.31

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-38749: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2022-38749](https://github.com/advisories/GHSA-c4r9-r8fh-9vj2)

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.31; first patched version for this range: 1.31

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-38752: snakeYAML before 1.32 vulnerable to Denial of Service due to Out-of-bounds Write
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2022-38752](https://github.com/advisories/GHSA-9w3m-gqgf-c4p9)

Severity: MEDIUM

- org.yaml:snakeyaml:1.30 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.32; first patched version for this range: 1.32

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-25857: Uncontrolled Resource Consumption in snakeyaml
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2022-25857](https://github.com/advisories/GHSA-3mc7-4q67-w48m)

Severity: HIGH

- org.yaml:snakeyaml:1.30 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 1.31; first patched version for this range: 1.31

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2016-1000027: Pivotal Spring Framework contains unsafe Java deserialization methods
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:32

[CVE-2016-1000027](https://github.com/advisories/GHSA-4wrc-f8pq-fpqp)

Severity: CRITICAL

- org.springframework:spring-web:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-web; Maven scope: compile); affected range: < 6.0.0; first patched version for this range: 6.0.0

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-47838: Spring Security Vulnerable to Unauthorized User Impersonation when Using X.509 Client Certificates
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:63

[CVE-2026-47838](https://github.com/advisories/GHSA-293q-567p-wmwq)

Severity: MEDIUM

- org.springframework.security:spring-security-web:5.7.11 (transitive via org.springframework.boot:spring-boot-starter-security; Maven scope: compile); affected range: <= 5.7.14; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41721: Spring Data Commons: Denial of Service via excessive memory allocation in projection binding
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:44

[CVE-2026-41721](https://github.com/advisories/GHSA-5m4m-73w9-8433)

Severity: MEDIUM

- org.springframework.data:spring-data-commons:2.7.18 (transitive via org.springframework.boot:spring-boot-starter-data-jpa; Maven scope: compile); affected range: <= 2.7.19; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41711: Spring Data Commons: StackOverflowException when parsing Sort parameters (DoS)
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:44

[CVE-2026-41711](https://github.com/advisories/GHSA-5vpf-xvv7-c8vh)

Severity: MEDIUM

- org.springframework.data:spring-data-commons:2.7.18 (transitive via org.springframework.boot:spring-boot-starter-data-jpa; Maven scope: compile); affected range: <= 2.7.19; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41706: Spring Security: Open Redirect via Unvalidated Post-Login Redirect URL Stored in CookieRequestCache
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:63

[CVE-2026-41706](https://github.com/advisories/GHSA-x2r2-rvhq-2mqv)

Severity: MEDIUM

- org.springframework.security:spring-security-web:5.7.11 (transitive via org.springframework.boot:spring-boot-starter-security; Maven scope: compile); affected range: <= 5.7.23; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41716: Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:44

[CVE-2026-41716](https://github.com/advisories/GHSA-9fw2-h3hf-293r)

Severity: HIGH

- org.springframework.data:spring-data-commons:2.7.18 (transitive via org.springframework.boot:spring-boot-starter-data-jpa; Maven scope: compile); affected range: <= 2.7.19; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-22732: Spring Security HTTP Headers Are not Written Under Some Conditions
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:63

[CVE-2026-22732](https://github.com/advisories/GHSA-mf92-479x-3373)

Severity: CRITICAL

- org.springframework.security:spring-security-web:5.7.11 (transitive via org.springframework.boot:spring-boot-starter-security; Maven scope: compile); affected range: <= 5.7.14; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-22228: Spring Security Does Not Enforce Password Length
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:63

[CVE-2025-22228](https://github.com/advisories/GHSA-mg83-c7gq-rv5c)

Severity: HIGH

- org.springframework.security:spring-security-crypto:5.7.11 (transitive via org.springframework.boot:spring-boot-starter-security; Maven scope: compile); affected range: <= 5.7.15; first patched version for this range: 5.7.16

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38827: Spring Framework has Authorization Bypass for Case Sensitive Comparisons
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:63

[CVE-2024-38827](https://github.com/advisories/GHSA-q3v6-hm2v-pw99)

Severity: MEDIUM

- org.springframework.security:spring-security-core:5.7.11 (transitive via org.springframework.boot:spring-boot-starter-security; Maven scope: compile); affected range: < 5.7.14; first patched version for this range: 5.7.14

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-38821: Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:63

[CVE-2024-38821](https://github.com/advisories/GHSA-c4q5-6c82-3qpw)

Severity: CRITICAL

- org.springframework.security:spring-security-web:5.7.11 (transitive via org.springframework.boot:spring-boot-starter-security; Maven scope: compile); affected range: >= 5.0.0, < 5.7.13; first patched version for this range: 5.7.13

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-22257: Erroneous authentication pass in Spring Security
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:63

[CVE-2024-22257](https://github.com/advisories/GHSA-f3jh-qvm4-mg39)

Severity: HIGH

- org.springframework.security:spring-security-core:5.7.11 (transitive via org.springframework.boot:spring-boot-starter-security; Maven scope: compile); affected range: < 5.7.12; first patched version for this range: 5.7.12

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-89425: jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-89425](https://github.com/advisories/GHSA-7hhh-6rmp-j9qf)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-core:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.8.0, <= 2.18.10; first patched version for this range: 2.18.11

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-91777: jackson-databind quadratic forward-reference completion 
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-91777](https://github.com/advisories/GHSA-cxp5-3px4-pw24)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.5.0, <= 2.18.10; first patched version for this range: 2.18.11

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-91776: jackson-databind retains every unknown raw type ID 
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-91776](https://github.com/advisories/GHSA-wv8q-qhhj-9h54)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.0.0, <= 2.18.10; first patched version for this range: 2.18.11

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-83557: jackson-databind: Comparable missing from DefaultBaseTypeLimitingValidator's unsafe base types (incomplete PolymorphicTypeValidator denylist)
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-83557](https://github.com/advisories/GHSA-gx83-3vf8-gh7j)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.11.0, < 2.18.10; first patched version for this range: 2.18.10

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-19032: jackson-databind: Path Deserialization Missing Scheme Allowlist for FileSystemProvider Resolution
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-19032](https://github.com/advisories/GHSA-wjgm-6hv5-3cvf)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.8.0, < 2.18.10; first patched version for this range: 2.18.10

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-77310: jackson-databind: Incomplete fix for CVE-2026-54514: eager DNS resolution (SSRF) still present in InetAddress deserialization
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-77310](https://github.com/advisories/GHSA-vvgp-rfg2-7rr6)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.0.0, < 2.18.9; first patched version for this range: 2.18.9

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-59889: jackson-databind: @JsonView bypassed for @JsonUnwrapped container properties on deserialization
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-59889](https://github.com/advisories/GHSA-5gvw-p9qm-jgwh)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.0.0-RC1, < 2.18.9; first patched version for this range: 2.18.9

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-68494: jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-68494](https://github.com/advisories/GHSA-r7wm-3cxj-wff9)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-core:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: < 2.18.8; first patched version for this range: 2.18.8

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-54515: jackson-databind has case-insensitive deserialization bypasses per-property @JsonIgnoreProperties
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-54515](https://github.com/advisories/GHSA-5jmj-h7xm-6q6v)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.8.0, < 2.18.9; first patched version for this range: 2.18.9

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-54514: jackson-databind: InetSocketAddress deserialization triggers eager DNS resolution (SSRF)
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-54514](https://github.com/advisories/GHSA-hgj6-7826-r7m5)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.0.0, < 2.18.8; first patched version for this range: 2.18.8

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-54513: jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-54513](https://github.com/advisories/GHSA-rmj7-2vxq-3g9f)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.10.0, < 2.18.8; first patched version for this range: 2.18.8

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-54512: jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-54512](https://github.com/advisories/GHSA-j3rv-43j4-c7qm)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.10.0, <= 2.18.7; first patched version for this range: 2.18.8

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-50193: jackson-databind: Deeply nested JsonNode throws StackOverflowError for toString()
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2026-50193](https://github.com/advisories/GHSA-3wrr-7qpf-2prh)

Severity: MEDIUM

- com.fasterxml.jackson.core:jackson-databind:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: >= 2.10.0, <= 2.13.5; first patched version for this range: 2.14.0

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-24400: AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:82

[CVE-2026-24400](https://github.com/advisories/GHSA-rqfh-9r24-8c9r)

Severity: HIGH

- org.assertj:assertj-core:3.22.0 (transitive via org.springframework.boot:spring-boot-starter-test; Maven scope: test); affected range: >= 1.4.0, <= 3.27.6; first patched version for this range: 3.27.7

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-52999: jackson-core can throw a StackoverflowError when processing deeply nested data
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:76

[CVE-2025-52999](https://github.com/advisories/GHSA-h46c-h94j-95f3)

Severity: HIGH

- com.fasterxml.jackson.core:jackson-core:2.13.5 (transitive via org.springframework.boot:spring-boot-starter-json; Maven scope: compile); affected range: < 2.15.0; first patched version for this range: 2.15.0

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2024-47554: Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:69

[CVE-2024-47554](https://github.com/advisories/GHSA-78wr-2p64-hpwj)

Severity: HIGH

- commons-io:commons-io:2.11.0 (direct; Maven scope: compile); affected range: >= 2.0, < 2.14.0; first patched version for this range: 2.14.0

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2023-51074: json-path Out-of-bounds Write vulnerability
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:82

[CVE-2023-51074](https://github.com/advisories/GHSA-pfh2-hfmq-phg5)

Severity: MEDIUM

- com.jayway.jsonpath:json-path:2.7.0 (transitive via org.springframework.boot:spring-boot-starter-test; Maven scope: test); affected range: >= 2.2.0, < 2.9.0; first patched version for this range: 2.9.0

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-41001: Spring Boot: Predictable Temp Directory in Artemis Auto-configuration
- **Category:** CVE
- **Severity:** optional
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:96

[CVE-2026-41001](https://github.com/advisories/GHSA-ggg2-9786-hwc8)

Severity: MEDIUM

- org.springframework.boot:spring-boot-autoconfigure:2.7.18 (transitive via org.springframework.boot:spring-boot-devtools; Maven scope: compile); affected range: >= 2.7.0, <= 2.7.33; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-40973: Spring Boot accepts predictable temp directory without ownership verification
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:96

[CVE-2026-40973](https://github.com/advisories/GHSA-wwpq-f5c3-7hvx)

Severity: HIGH

- org.springframework.boot:spring-boot:2.7.18 (transitive via org.springframework.boot:spring-boot-devtools; Maven scope: compile); affected range: <= 2.7.32; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2026-40972: Spring Boot DevTools remote secret comparison is vulnerable to timing attacks
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:96

[CVE-2026-40972](https://github.com/advisories/GHSA-56v8-86gj-66jp)

Severity: HIGH

- org.springframework.boot:spring-boot-devtools:2.7.18 (direct; Maven scope: compile); affected range: <= 2.7.32; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-41249: Spring Framework annotation detection mechanism may result in improper authorization
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:82

[CVE-2025-41249](https://github.com/advisories/GHSA-jmp9-x22r-554x)

Severity: HIGH

- org.springframework:spring-core:5.3.31 (transitive via org.springframework.boot:spring-boot-starter-test; Maven scope: compile); affected range: >= 5.3.0, <= 5.3.44; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2025-22235: Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:96

[CVE-2025-22235](https://github.com/advisories/GHSA-rc42-6c7j-7h5r)

Severity: HIGH

- org.springframework.boot:spring-boot:2.7.18 (transitive via org.springframework.boot:spring-boot-devtools; Maven scope: compile); affected range: <= 2.7.24.2; first patched version for this range: No patched version listed for this affected release range; migrate to a supported fixed release.

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.

### CVE-2022-45868: Password exposure in H2 Database 
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/pom.xml:89

[CVE-2022-45868](https://github.com/advisories/GHSA-22wj-vf5f-wrvj)

Severity: HIGH

- com.h2database:h2:2.1.214 (direct; Maven scope: test); affected range: >= 1.4.198, < 2.2.220; first patched version for this range: 2.2.220

Dependency-version match only; application exploitability and advisory-specific prerequisites have not been dynamically verified. Test-scoped dependencies are not production runtime dependencies. Optional development tooling requires separate deployment review. Upgrade through a compatible maintained framework/dependency release; a patched version from another release branch is not necessarily a drop-in replacement.


## CWE Findings (Code-Level Vulnerabilities)

### CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')
- **Category:** Injection Attacks
- **Severity:** optional
- **Story Points:** 8
- **Files:** /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/static/js/upload.js:73, /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/static/js/upload.js:215, /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/resources/static/js/upload.js:185, /home/runner/work/PhotoAlbum-Java/PhotoAlbum-Java/src/main/java/com/photoalbum/controller/HomeController.java:77

DOM-based XSS through attacker-supplied filenames; security severity MEDIUM, confidence 9/10. handleFiles interpolates file.name into validation-error strings at lines 73-75; showErrors at lines 215-218 inserts these strings using innerHTML without escaping. A file named '<img src=x onerror=alert(1)>.txt' triggers the unsupported-type error and is parsed as HTML, causing its event handler to run in the application's origin. An attacker must persuade a victim to select or drop an attacker-named file; exploitation does not require successful upload or backend authentication. Separately, upload response originalFileName values are interpolated into attributes and HTML text at lines 185-189, then parsed by insertAdjacentHTML at line 157. HomeController.uploadPhotos returns the original multipart filename at line 77. No escaping guard or CSP configuration was identified for these DOM sinks. The client-validation path demonstrates the vulnerability without assuming that another visitor's server-rendered gallery executes stored filenames; server-rendered Thymeleaf text is escaped.

