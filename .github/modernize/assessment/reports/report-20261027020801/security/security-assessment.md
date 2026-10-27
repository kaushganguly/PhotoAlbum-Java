# Security Assessment Report

**Generated:** 2026-10-27T02:17:41.874777+00:00

**Minimum CVE severity:** medium

## Scope and limitations

- CVE findings are GitHub advisory matches against resolved dependency versions, not confirmed application-level exploits.
- Dependency coverage includes direct and transitive dependencies, development dependencies, and test scope; test scope is not production exposure.
- Feature/configuration prerequisites and denial-of-service-only impacts require separate triage.
- Maven resolved 101 dependency entries. All four unauthenticated HTTPS GitHub advisory batches succeeded; authenticated gh access was unavailable.
- CWE review was static and used a high-confidence exploitability threshold. NOT_FOUND does not guarantee absence; no dynamic penetration testing was performed.
- Unescaped filename DOM sinks exist in the uploader, but no remote cross-user exploit was established; persisted gallery/detail values use Thymeleaf escaping.

## Summary

| Metric | Count |
|--------|-------|
| Total Findings | 104 |
| CVE Vulnerabilities (inventory matches) | 104 |
| Confirmed CWE Vulnerabilities | 0 |
| Total Rules Assessed | 59 |
| Rules Passed (no confirmed finding) | 59 |

### By Severity

| Severity | Count |
|----------|-------|
| mandatory | 60 |
| optional | 44 |
| potential | 0 |

## CVE Findings (Dependency Vulnerabilities)

### CVE-2026-47884: Spring Framework Improper Path Limitation in XsltView
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-pc63-qcmh-9cmg; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-65905: Apache Tomcat's DIGEST authenticator has an Authentication Bypass by Capture-replay vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-9xv2-5v5q-p794; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.121.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-65182: Apache Tomcat has an Improper Access Control, Incorrect Authorization vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-gcx9-497g-6cp6; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.121.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-68525: Apache Tomcat's FORM authentication process has an Incorrect Authorization vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-h3x4-894j-xpx5; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.121.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-49844: Apache Log4j API: Improper encoding of non-finite floating-point values during MapMessage JSON serialization
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-qv9r-c865-cp47; org.apache.logging.log4j:log4j-api:2.17.2, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 2.25.5.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41853: Spring Framework Multipart Request Smuggling in Spring MVC and WebFlux
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-cjpg-rgq5-fr37; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41851: Spring Framework Denial of Service via Unbounded Cache in SpEL
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-wxpp-56q6-5pcg; org.springframework:spring-expression:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41850: Spring Framework Algorithmic Denial of Service via SpEL Expressions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-r5w3-xv2f-j59q; org.springframework:spring-expression:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41849: Spring Framework Denial of Service via Integer Overflow in SpEL Expressions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-775g-4xr8-78h8; org.springframework:spring-expression:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41846: Spring Framework Cross-site Scripting via JSP Form Tags
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-957g-f97v-vppc; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41843: Spring Framework Path Traversal via Versioned Static Resources in Spring MVC and WebFlux
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-72pg-x5f8-j25j; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41844: Spring Framework Open Redirect in Spring MVC and WebFlux
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-h3qp-gqrc-q736; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41845: Spring Framework Cross-site Scripting via JavaScriptUtils
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-3chg-m5w7-qfv5; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41841: Spring Framework Information Disclosure via Static Resource Cache in Spring MVC and WebFlux
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-mq64-j8f9-9gcj; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41842: Spring Framework Denial of Service via Versioned Resources in Spring MVC and WebFlux
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-x23c-287f-qqv5; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41284: Apache Tomcat: Unbounded read in WebDAV LOCK and  PROPFIND handling
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-gx5v-xp9w-j4cg; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.118. Inventory match only; WebDAV is not configured in application source.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-43512: Apache Tomcat - Digest authenticator will authenticate any unknown user
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-h6fc-48rj-7qqh; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.118. Application uses Spring HTTP Basic, not configured Tomcat Digest.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-43513: Apache Tomcat: LockOutRealm treats user names as case-sensitive
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-5mp6-jrq3-r938; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.118.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-43515: Apache Tomcat - Security constraints not correctly applied
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-5m62-pw8w-7w9f; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.118.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41293: Apache Tomcat - HTTP/2 request headers not validated
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-r29c-68gh-xp6x; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.118.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-42498: Apache Tomcat - WebSocket authentication header exposure
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-fv25-8xcx-gqjc; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.118.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41901: Sandboxed Thymeleaf expressions vulnerable to improper recognition of unauthorized syntax patterns
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

CRITICAL https://github.com/advisories/GHSA-c9ph-gxww-7744; org.thymeleaf:thymeleaf:3.0.15.RELEASE and org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE, compile, transitive via spring-boot-starter-thymeleaf. Upgrade to applicable patched release 3.1.5.RELEASE; verify framework compatibility. No attacker-controlled template expression source was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-22745: Spring MVC and WebFlux applications are vulnerable to Denial of Service attacks when resolving static resources
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-6p4f-wcwh-5vvm; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-40478: Improper neutralization of specific syntax patterns for unauthorized expressions in Thymeleaf
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

CRITICAL https://github.com/advisories/GHSA-xjw8-8c5c-9r79; org.thymeleaf:thymeleaf:3.0.15.RELEASE and org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE, compile, transitive via spring-boot-starter-thymeleaf. Upgrade to applicable patched release 3.1.4.RELEASE; verify framework compatibility.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-40477: Improper restriction of the scope of accessible objects in Thymeleaf expressions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:40

CRITICAL https://github.com/advisories/GHSA-r4v4-5mwr-2fwr; org.thymeleaf:thymeleaf:3.0.15.RELEASE and org.thymeleaf:thymeleaf-spring5:3.0.15.RELEASE, compile, transitive via spring-boot-starter-thymeleaf. Upgrade to applicable patched release 3.1.4.RELEASE; verify framework compatibility.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-34483: Apache Tomcat has an Improper Encoding or Escaping of Output vulnerability in the JsonAccessLogValve
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-rv64-5gf8-9qq8; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.116.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-34487: Apache Tomcat vulnerable to Insertion of Sensitive Information into Log File
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-x4m4-345f-5h5g; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.117.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-25854: Apache Tomcat has an Open Redirect vulnerability
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-9m3c-qcxr-9x87; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.116.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-24880: Apache Tomcat has an HTTP Request/Response Smuggling vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-563x-q5rq-57qp; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.116.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-22737: Spring Framework Improper Path Limitation with Script View Templates
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-4773-3jfm-qmx3; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-24734: Apache Tomcat has an Improper Input Validation vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-mgp5-rv84-w37q; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.115.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-66614: Apache Tomcat - Client certificate verification bypass
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-fpj8-gq4v-p354; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.113.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-55752: Apache Tomcat Vulnerable to Relative Path Traversal
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-wmwf-9ccg-fff5; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.109.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-11226: QOS.CH logback-core is vulnerable to Arbitrary Code Execution through file processing
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-25qh-j22f-pwp8; ch.qos.logback:logback-core:1.2.12, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 1.3.16; verify compatibility.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-41242: Spring Framework MVC Applications Path Traversal Vulnerability
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-r936-gwx5-v52f; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-48989: Apache Tomcat Improper Resource Shutdown or Release vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-gqp3-2cvr-x8m3; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.108.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-55668: Apache Tomcat Session Fixation vulnerability
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-23hv-mwm6-g8jf; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.106. Application security config uses stateless sessions.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-53506: Apache Tomcat Coyote vulnerable to Denial of Service via excessive HTTP/2 streams
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-25xr-qj8w-c4vf; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.107.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-52520: Apache Tomcat Catalina is vulnerable to DoS attack through bypassing of size limits
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-wr62-c79q-cv37; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.107.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-52434: Apache Tomcat is vulnerable to resource exhaustion when using the APR/Native connector
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-4j3c-42xv-3f84; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only resource-exhaustion advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.107.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-49124: Apache Tomcat installer for Windows has an untrusted search path vulnerability
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-42wg-hm62-jcwg; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.106. Windows-installer exposure is not established for this embedded Linux deployment.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-49125: Apache Tomcat - Security constraint bypass for pre/post-resources
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-wc4r-xq3c-5cf3; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.106.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-48988: Apache Tomcat - DoS in multipart upload
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-h3gc-qfqq-6h8f; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.106.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-31650: Apache Tomcat Denial of Service via invalid HTTP priority header
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-3p2h-wqq4-wf4h; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.104.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-24813: Apache Tomcat: Potential RCE and/or information disclosure and/or information corruption with partial PUT
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-83qj-6fr2-vhqg; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.99. Writable DefaultServlet and related exploitation prerequisites were not established.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-56337: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-27hp-xhwr-wr2m; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.98 and follow advisory JVM/filesystem requirements. Application exploitability not established.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38819: Spring Framework Path Traversal vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-g5vr-rgqm-vf78; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed. Functional resource routing prerequisites were not identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-12798: QOS.CH logback-core Expression Language Injection vulnerability
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-pr98-23f8-jwxv; ch.qos.logback:logback-core:1.2.12, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 1.3.15; verify compatibility.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-50379: Apache Tomcat Time-of-check Time-of-use (TOCTOU) Race Condition vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-5j33-cvvr-w245; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 9.0.98 and follow related advisory requirements. Application exploitability not established.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38828: Spring MVC controller vulnerable to a DoS attack
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-w3c8-7r8f-9jp8; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 5.3.42.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38286: Apache Tomcat Allocation of Resources Without Limits or Throttling vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-7jqf-v358-p8g7; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only resource-exhaustion advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.90.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38820: Spring Framework DataBinder Case Sensitive Match Exception
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-4gc7-5j7h-4qph; org.springframework:spring-context:5.3.31 and org.springframework:spring-web:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38809: Spring Framework DoS via conditional HTTP request
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-2rmj-mq67-h97g; org.springframework:spring-web:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 5.3.38.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38816: Path traversal vulnerability in functional web frameworks
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-cx7f-g6mp-7hqm; org.springframework:spring-webmvc:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to a vendor-supported fixed release; no applicable patch listed. Functional resource routing prerequisites were not identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38808: Spring Framework vulnerable to Denial of Service
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-9cmq-m9j5-mvww; org.springframework:spring-expression:5.3.31, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 5.3.39.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-34750: Apache Tomcat - Denial of Service
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-wm9w-rjj3-j356; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.90.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-22262: Spring Framework URL Parsing with Host Validation
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-2wrp-6fg6-hmc5; org.springframework:spring-web:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 5.3.34.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-22259: Spring Framework URL Parsing with Host Validation Vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-hgjh-9rj2-g67j; org.springframework:spring-web:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 5.3.33.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-23672: Denial of Service via incomplete cleanup vulnerability in Apache Tomcat
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-v682-8vv8-vpwr; org.apache.tomcat.embed:tomcat-embed-websocket:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.86.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-24549: Apache Tomcat Denial of Service due to improper input validation vulnerability for HTTP/2 requests
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-7w75-32cg-r6g2; org.apache.tomcat.embed:tomcat-embed-core:9.0.83, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 9.0.86.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-22243: Spring Web vulnerable to Open Redirect or Server Side Request Forgery
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-ccgv-vj62-xf9h; org.springframework:spring-web:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 5.3.32.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2023-6481: Logback is vulnerable to an attacker mounting a Denial-Of-Service attack by sending poisoned data
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-gm62-rw4g-vrc4; ch.qos.logback:logback-core:1.2.12, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 1.2.13.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2023-6378: logback serialization vulnerability
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-vmq6-5m68-f53m; ch.qos.logback:logback-core:1.2.12 and ch.qos.logback:logback-classic:1.2.12, compile, transitive via spring-boot-starter-web. Upgrade both to applicable patched release 1.2.13.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-1471: SnakeYaml Constructor Deserialization Remote Code Execution
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-mjmj-j48q-9wg2; org.yaml:snakeyaml:1.30, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 2.0; verify framework compatibility. No application parsing of attacker-controlled YAML was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-41854: Snakeyaml vulnerable to Stack overflow leading to denial of service
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-w37g-rhq8-7m4j; org.yaml:snakeyaml:1.30, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 1.32.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-38751: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-98wm-3w3q-mw94; org.yaml:snakeyaml:1.30, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 1.31.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-38750: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-hhhw-99gj-p3c3; org.yaml:snakeyaml:1.30, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 1.31.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-38749: snakeYAML before 1.31 vulnerable to Denial of Service due to Out-of-bounds Write
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-c4r9-r8fh-9vj2; org.yaml:snakeyaml:1.30, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 1.31.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-38752: snakeYAML before 1.32 vulnerable to Denial of Service due to Out-of-bounds Write
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:34

MEDIUM https://github.com/advisories/GHSA-9w3m-gqgf-c4p9; org.yaml:snakeyaml:1.30, compile, transitive via spring-boot-starter-web. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 1.32.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-25857: Uncontrolled Resource Consumption in snakeyaml
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

HIGH https://github.com/advisories/GHSA-3mc7-4q67-w48m; org.yaml:snakeyaml:1.30, compile, transitive via spring-boot-starter-web. Inventory-only resource-exhaustion advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 1.31.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2016-1000027: Pivotal Spring Framework contains unsafe Java deserialization methods
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:34

CRITICAL https://github.com/advisories/GHSA-4wrc-f8pq-fpqp; org.springframework:spring-web:5.3.31, compile, transitive via spring-boot-starter-web. Upgrade to applicable patched release 6.0.0; requires coordinated framework/runtime upgrade. No exposed HTTP Invoker deserialization endpoint was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-47838: Spring Security Vulnerable to Unauthorized User Impersonation when Using X.509 Client Certificates
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

MEDIUM https://github.com/advisories/GHSA-293q-567p-wmwq; org.springframework.security:spring-security-web:5.7.11, compile, transitive via spring-boot-starter-security. Upgrade to a vendor-supported fixed release; no applicable patch listed. Application uses HTTP Basic rather than X.509 authentication.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41721: Spring Data Commons: Denial of Service via excessive memory allocation in projection binding
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:46

MEDIUM https://github.com/advisories/GHSA-5m4m-73w9-8433; org.springframework.data:spring-data-commons:2.7.18, compile, transitive via spring-boot-starter-data-jpa. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41711: Spring Data Commons: StackOverflowException when parsing Sort parameters (DoS)
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:46

MEDIUM https://github.com/advisories/GHSA-5vpf-xvv7-c8vh; org.springframework.data:spring-data-commons:2.7.18, compile, transitive via spring-boot-starter-data-jpa. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41706: Spring Security: Open Redirect via Unvalidated Post-Login Redirect URL Stored in CookieRequestCache
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

MEDIUM https://github.com/advisories/GHSA-x2r2-rvhq-2mqv; org.springframework.security:spring-security-web:5.7.11, compile, transitive via spring-boot-starter-security. Upgrade to a vendor-supported fixed release; no applicable patch listed. CookieRequestCache was not configured in application source.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41716: Spring Data Commons: Heap exhaustion from unbounded property-lookup cache retaining crafted string keys
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:46

HIGH https://github.com/advisories/GHSA-9fw2-h3hf-293r; org.springframework.data:spring-data-commons:2.7.18, compile, transitive via spring-boot-starter-data-jpa. Inventory-only heap-exhaustion advisory, excluded from confirmed exploit findings. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-22732: Spring Security HTTP Headers Are not Written Under Some Conditions
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

CRITICAL https://github.com/advisories/GHSA-mf92-479x-3373; org.springframework.security:spring-security-web:5.7.11, compile, transitive via spring-boot-starter-security. Upgrade to a vendor-supported fixed release; no applicable patch listed. Header-bypass exploitation conditions were not verified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-22228: Spring Security Does Not Enforce Password Length
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

HIGH https://github.com/advisories/GHSA-mg83-c7gq-rv5c; org.springframework.security:spring-security-crypto:5.7.11, compile, transitive via spring-boot-starter-security. Upgrade to applicable patched release 5.7.16. BCrypt is used, but exploitation depends on administrator password characteristics not inspected.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38827: Spring Framework has Authorization Bypass for Case Sensitive Comparisons
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:65

MEDIUM https://github.com/advisories/GHSA-q3v6-hm2v-pw99; org.springframework.security:spring-security-core:5.7.11, compile, transitive via spring-boot-starter-security. Upgrade to applicable patched release 5.7.14.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-38821: Spring Security vulnerable to Authorization Bypass of Static Resources in WebFlux Applications
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

CRITICAL https://github.com/advisories/GHSA-c4q5-6c82-3qpw; org.springframework.security:spring-security-web:5.7.11, compile, transitive via spring-boot-starter-security. Upgrade to applicable patched release 5.7.13. This project uses MVC, not an identified WebFlux application; production exploitability not established.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-22257: Erroneous authentication pass in Spring Security
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:65

HIGH https://github.com/advisories/GHSA-f3jh-qvm4-mg39; org.springframework.security:spring-security-core:5.7.11, compile, transitive via spring-boot-starter-security. Upgrade to applicable patched release 5.7.12.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-89425: jackson-core: UTF8DataInputJsonParser._reportInvalidToken() missing maxErrorTokenLength limit -> unbounded StringBuilder growth (DoS)
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

HIGH https://github.com/advisories/GHSA-7hhh-6rmp-j9qf; com.fasterxml.jackson.core:jackson-core:2.13.5, compile, transitive via spring-boot-starter-json. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 2.18.11.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-91777: jackson-databind quadratic forward-reference completion 
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

HIGH https://github.com/advisories/GHSA-cxp5-3px4-pw24; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.11. Resource-consumption-only impact is excluded from confirmed exploit findings.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-91776: jackson-databind retains every unknown raw type ID 
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

HIGH https://github.com/advisories/GHSA-wv8q-qhhj-9h54; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.11. Resource-consumption-only impact is excluded from confirmed exploit findings.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-83557: jackson-databind: Comparable missing from DefaultBaseTypeLimitingValidator's unsafe base types (incomplete PolymorphicTypeValidator denylist)
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

MEDIUM https://github.com/advisories/GHSA-gx83-3vf8-gh7j; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.10. No application polymorphic-deserialization configuration was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-19032: jackson-databind: Path Deserialization Missing Scheme Allowlist for FileSystemProvider Resolution
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

MEDIUM https://github.com/advisories/GHSA-wjgm-6hv5-3cvf; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.10. No attacker-controlled Path binding was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-77310: jackson-databind: Incomplete fix for CVE-2026-54514: eager DNS resolution (SSRF) still present in InetAddress deserialization
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

MEDIUM https://github.com/advisories/GHSA-vvgp-rfg2-7rr6; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.9. No application InetAddress binding was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-59889: jackson-databind: @JsonView bypassed for @JsonUnwrapped container properties on deserialization
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

MEDIUM https://github.com/advisories/GHSA-5gvw-p9qm-jgwh; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.9.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-68494: jackson-core: Async parser maxNumberLength bypass via chunked digit accumulation (incomplete fix for GHSA-72hv-8253-57qq)
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

HIGH https://github.com/advisories/GHSA-r7wm-3cxj-wff9; com.fasterxml.jackson.core:jackson-core:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.8. Resource-exhaustion-only impact is excluded from confirmed exploit findings.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-54515: jackson-databind has case-insensitive deserialization bypasses per-property @JsonIgnoreProperties
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

MEDIUM https://github.com/advisories/GHSA-5jmj-h7xm-6q6v; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.9.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-54514: jackson-databind: InetSocketAddress deserialization triggers eager DNS resolution (SSRF)
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

MEDIUM https://github.com/advisories/GHSA-hgj6-7826-r7m5; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.8. No application InetSocketAddress binding was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-54513: jackson-databind has an array subtype allowlist bypass in BasicPolymorphicTypeValidator (allowIfSubTypeIsArray)
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

HIGH https://github.com/advisories/GHSA-rmj7-2vxq-3g9f; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.8. No application polymorphic-deserialization configuration was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-54512: jackson-databind has a PolymorphicTypeValidator bypass via generic type parameters that allows arbitrary class instantiation
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

HIGH https://github.com/advisories/GHSA-j3rv-43j4-c7qm; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Upgrade to applicable patched release 2.18.8. No application polymorphic-deserialization configuration was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-50193: jackson-databind: Deeply nested JsonNode throws StackOverflowError for toString()
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:78

MEDIUM https://github.com/advisories/GHSA-3wrr-7qpf-2prh; com.fasterxml.jackson.core:jackson-databind:2.13.5, compile, transitive via spring-boot-starter-json. Inventory-only stack-exhaustion advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 2.14.0.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-24400: AssertJ has XML External Entity (XXE) vulnerability when parsing untrusted XML via isXmlEqualTo assertion
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

HIGH https://github.com/advisories/GHSA-rqfh-9r24-8c9r; org.assertj:assertj-core:3.22.0, test, transitive via spring-boot-starter-test. Upgrade to applicable patched release 3.27.7. Test-only dependency; not established production exposure.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-52999: jackson-core can throw a StackoverflowError when processing deeply nested data
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:78

HIGH https://github.com/advisories/GHSA-h46c-h94j-95f3; com.fasterxml.jackson.core:jackson-core:2.13.5, compile, transitive via spring-boot-starter-json. Inventory-only stack-exhaustion advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 2.15.0.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2024-47554: Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:71

HIGH https://github.com/advisories/GHSA-78wr-2p64-hpwj; commons-io:commons-io:2.11.0, compile, direct dependency. Inventory-only DoS advisory, excluded from confirmed exploit findings. Upgrade to applicable patched release 2.14.0.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2023-51074: json-path Out-of-bounds Write vulnerability
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:84

MEDIUM https://github.com/advisories/GHSA-pfh2-hfmq-phg5; com.jayway.jsonpath:json-path:2.7.0, test, transitive via spring-boot-starter-test. Upgrade to applicable patched release 2.9.0. Test-only dependency; not established production exposure.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-41001: Spring Boot: Predictable Temp Directory in Artemis Auto-configuration
- **Severity:** optional
- **Story Points:** 1
- **Files:** pom.xml:98

MEDIUM https://github.com/advisories/GHSA-ggg2-9786-hwc8; org.springframework.boot:spring-boot-autoconfigure:2.7.18, compile, transitive via spring-boot-devtools in resolved tree. Upgrade to a vendor-supported fixed release; no applicable patch listed. No Artemis application configuration was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-40973: Spring Boot accepts predictable temp directory without ownership verification
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

HIGH https://github.com/advisories/GHSA-wwpq-f5c3-7hvx; org.springframework.boot:spring-boot:2.7.18, compile, transitive via spring-boot-devtools in resolved tree. Upgrade to a vendor-supported fixed release; no applicable patch listed. Application-level local-attacker prerequisites were not verified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2026-40972: Spring Boot DevTools remote secret comparison is vulnerable to timing attacks
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

HIGH https://github.com/advisories/GHSA-56v8-86gj-66jp; org.springframework.boot:spring-boot-devtools:2.7.18, compile, direct optional development dependency. Upgrade to a vendor-supported fixed release; no applicable patch listed. Remote DevTools enablement and packaged runtime inclusion were not established.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-41249: Spring Framework annotation detection mechanism may result in improper authorization
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:84

HIGH https://github.com/advisories/GHSA-jmp9-x22r-554x; org.springframework:spring-core:5.3.31, effective scope compile, transitive via spring-boot-starter-test in Maven's deduplicated tree; not test-only. Upgrade to a vendor-supported fixed release; no applicable patch listed.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2025-22235: Spring Boot EndpointRequest.to() creates wrong matcher if actuator endpoint is not exposed
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:98

HIGH https://github.com/advisories/GHSA-rc42-6c7j-7h5r; org.springframework.boot:spring-boot:2.7.18, compile, transitive via spring-boot-devtools in resolved tree. Upgrade to a vendor-supported fixed release; no applicable patch listed. No Actuator EndpointRequest security matcher was identified.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

### CVE-2022-45868: Password exposure in H2 Database 
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:91

HIGH https://github.com/advisories/GHSA-22wj-vf5f-wrvj; com.h2database:h2:2.1.214, test, direct dependency. Upgrade to applicable patched release 2.2.220. Test-only dependency; not established production exposure.

Dependency inventory match only; application-level exploitability was not established. Results include transitive, development, and test dependencies. Test scope is not production exposure; feature/configuration prerequisites and denial-of-service-only impacts require separate triage.

## CWE Findings (Code-Level Vulnerabilities)

No confirmed findings across the 59 assessed rules. See the scope and limitations above and the six category result files for assessment coverage.
