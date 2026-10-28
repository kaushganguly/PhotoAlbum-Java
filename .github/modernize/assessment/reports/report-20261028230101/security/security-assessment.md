# Security Assessment Report

**Generated:** 2026-10-28T23:10:10.033857Z

## Scope and limitations

- CVE threshold: **medium**. All 11 resolved direct Maven dependencies, including test and optional dependencies, were assessed.
- The configured `cveScanScope=direct` excludes 90 resolved transitive dependencies; parent POMs, build plugins, and non-Maven assets are not advisory-scanned.
- CVE matches establish affected dependency versions, not reachable exploitation. Finding details describe prerequisites and test-only exposure.
- All 59 rules in the six requested CWE categories were assessed statically. `NOT_FOUND` means no finding identified within this review, not proof of absence.
- No application build, test suite, deployment, or exploit test was performed. See `cve-coverage.json` and individual result files for evidence.

## Summary

| Metric | Count |
|--------|-------|
| Total Findings | 9 |
| CVE Vulnerabilities | 3 |
| CWE Vulnerabilities | 6 |
| Total Rules Assessed | 59 |
| Rules Passed (no finding identified) | 53 |

### By Severity

| Severity | Count |
|----------|-------|
| mandatory | 5 |
| optional | 1 |
| potential | 3 |

## CVE Findings (Dependency Vulnerabilities)

### CVE-2022-45868: Password exposure in H2 Database
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:89

[CVE-2022-45868](https://github.com/advisories/GHSA-22wj-vf5f-wrvj) — Password exposure in H2 Database 

Severity: HIGH

Verified advisory identifiers: CVE-2022-45868; GHSA-22wj-vf5f-wrvj.

CVE reference: https://nvd.nist.gov/vuln/detail/CVE-2022-45868

Affected direct dependencies (Maven-resolved versions):

- com.h2database:h2:2.1.214 (test; declared at pom.xml:89); validated affected range: >= 1.4.198, < 2.2.220.

Recommended fix:
- Upgrade com.h2database:h2 to 2.2.220 or a later compatible release verified outside the affected range.

Applicability caveat: H2 is test-scoped, not a production runtime dependency. Exploitation requires starting the H2 web admin console with a cleartext -webAdminPassword CLI argument and local process-argument access. No such invocation or H2 console configuration was found in the repository. The vendor disputes the security classification, as documented in the advisory; this is a conditional test/tooling exposure, not a demonstrated production exploit.

Coverage: full-repository direct dependencies only (including test and optional dependencies); transitive packages are not advisory-scanned. Version presence is confirmed; exploitability is not proven. No tests or application builds were run.

### CVE-2024-47554: Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:69

[CVE-2024-47554](https://github.com/advisories/GHSA-78wr-2p64-hpwj) — Apache Commons IO: Possible denial of service attack on untrusted input to XmlStreamReader

Severity: HIGH

Verified advisory identifiers: CVE-2024-47554; GHSA-78wr-2p64-hpwj.

CVE reference: https://nvd.nist.gov/vuln/detail/CVE-2024-47554

Affected direct dependencies (Maven-resolved versions):

- commons-io:commons-io:2.11.0 (compile; declared at pom.xml:69); validated affected range: >= 2.0, < 2.14.0.

Recommended fix:
- Upgrade commons-io:commons-io to 2.14.0 or a later compatible release verified outside the affected range.

Applicability caveat: Dependency version is affected, but exploitation requires malicious input to org.apache.commons.io.input.XmlStreamReader. No XmlStreamReader or Commons IO imports were found in repository Java sources; reachable exploitation is not established by this dependency assessment.

Coverage: full-repository direct dependencies only (including test and optional dependencies); transitive packages are not advisory-scanned. Version presence is confirmed; exploitability is not proven. No tests or application builds were run.

### CVE-2026-40972: Spring Boot DevTools remote secret comparison is vulnerable to timing attacks
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** pom.xml:96

[CVE-2026-40972](https://github.com/advisories/GHSA-56v8-86gj-66jp) — Spring Boot DevTools remote secret comparison is vulnerable to timing attacks

Severity: HIGH

Verified advisory identifiers: CVE-2026-40972; GHSA-56v8-86gj-66jp.

CVE reference: https://nvd.nist.gov/vuln/detail/CVE-2026-40972

Affected direct dependencies (Maven-resolved versions):

- org.springframework.boot:spring-boot-devtools:2.7.18 (compile; declared at pom.xml:96); validated affected range: <= 2.7.32.

Recommended fix:
- GitHub lists no first patched version for the affected 2.7.x range. The advisory description names vendor fix 2.7.33, but availability/support must be verified; alternatively migrate to a supported patched Spring Boot line (e.g. 3.5.14 or 4.0.6, requiring coordinated Java/framework upgrades). Disable remote DevTools and exclude DevTools from production deployments as immediate mitigation.

Applicability caveat: Exploitation requires Spring Boot remote DevTools to be enabled and configured with a remote secret, and an attacker able to measure comparison timing over the network. No spring.devtools.remote setting was found in checked-in configuration. Optional DevTools presence alone does not establish exposure; external configuration may differ. Spring Boot repackaged archives normally exclude DevTools unless explicitly included; the deployed artifact was not built or inspected.

Coverage: full-repository direct dependencies only (including test and optional dependencies); transitive packages are not advisory-scanned. Version presence is confirmed; exploitability is not proven. No tests or application builds were run.


## CWE Findings (Code-Level Vulnerabilities)

### CWE-606: Unchecked Input for Loop Condition
- **Category:** Code Quality
- **Severity:** potential
- **Story Points:** 3
- **Files:** src/main/java/com/photoalbum/controller/HomeController.java, src/main/resources/application.properties

HomeController.uploadPhotos checks only null/empty input at lines 62-66 and iterates every caller-supplied multipart file at lines 68-91, invoking image parsing/persistence for each accepted item. The configured app.file-upload.max-files-per-upload=10 (application.properties line 30) is never read or enforced. Multipart byte limits at lines 24-25 bound request bytes, not the intended per-request item/work count; many small files can cause substantially more parsing and database operations than the configured ten. This is a missing iteration/cardinality limit, not an infinite loop; authentication is required for upload, and actual DoS was not measured.

### CWE-789: Memory Allocation with Excessive Size Value
- **Category:** Code Quality
- **Severity:** potential
- **Story Points:** 5
- **Files:** src/main/java/com/photoalbum/repository/PhotoRepository.java, src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java, src/main/java/com/photoalbum/controller/HomeController.java, src/main/java/com/photoalbum/model/Photo.java

PhotoRepository.findAllOrderByUploadedAtDesc lines 22-27 returns all rows and explicitly selects PHOTO_DATA without a row limit. Photo.photoData is a byte[] @Lob with no lazy-fetch override (Photo.java lines 36-41), so this path materializes stored image bytes along with the collection. PhotoServiceImpl.getAllPhotos lines 53-57 passes that unbounded list to the publicly accessible HomeController.index lines 37-41. Although each upload is size-limited, cumulative stored photo count/BLOB bytes are not bounded; increasing stored uploads increases heap allocations for every gallery request, potentially exhausting the configured heap. This is unbounded aggregate allocation, not an unbounded allocation from one uploaded image header; no measured exhaustion or anonymous upload capability is asserted.

### CWE-778: Insufficient Logging
- **Category:** Credentials & Secrets
- **Severity:** potential
- **Story Points:** 3
- **Files:** src/main/java/com/photoalbum/controller/DetailController.java, src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java, src/main/java/com/photoalbum/config/SecurityConfig.java

SecurityConfig.securityFilterChain lines 54-60 requires HTTP Basic authentication for uploads and deletions. Nevertheless DetailController.deletePhoto lines 64-76 logs only the photo ID and outcome; PhotoServiceImpl.deletePhoto lines 199-216 and uploadPhoto lines 173-184 likewise log object IDs/filenames without the authenticated principal, source client or audit correlation. These are security-critical mutation events, but the application logs omit attribution to the actor. This finding is insufficient audit detail, not a claim that mutations have no logging or that Spring Security never emits any diagnostic logs. The supplied in-memory user store currently contains one admin account; the logs still cannot distinguish the client responsible for an operation.

### CWE-434: Unrestricted Upload of File with Dangerous Type
- **Category:** File & Path Security
- **Severity:** mandatory
- **Story Points:** 8
- **Files:** src/main/java/com/photoalbum/service/impl/PhotoServiceImpl.java, src/main/java/com/photoalbum/controller/PhotoFileController.java, src/main/java/com/photoalbum/config/SecurityConfig.java

PhotoServiceImpl.uploadPhoto lines 87-94 trusts the multipart Content-Type allowlist rather than requiring a recognized image. At lines 130-149 no ImageReader is allowed without rejecting the upload, and lines 155-168 continue after non-IO parser failures and persist the original bytes. Thus an authenticated uploader can submit non-image or other disallowed file contents under an allowed image MIME label, which are subsequently published by PhotoFileController.servePhoto lines 74-83. This is a file-content/type validation bypass; database storage and image response MIME do not demonstrate server-side script execution or browser execution.

### CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')
- **Category:** Injection Attacks
- **Severity:** optional
- **Story Points:** 8
- **Files:** src/main/resources/static/js/upload.js, src/main/java/com/photoalbum/controller/HomeController.java

upload.js handleFiles lines 71-82 includes the selected file.name verbatim in validation errors; showErrors lines 215-218 interpolates those strings into innerHTML without escaping. A crafted filename containing HTML/event attributes is therefore parsed as markup when a user selects or drops that file, even when it fails upload validation. Separately, createPhotoCard lines 181-190 interpolates photo.originalFileName into attributes/text and displayNewPhotos inserts it with insertAdjacentHTML at lines 155-157; HomeController.uploadPhotos lines 75-83 returns the upload filename unchanged. Exploitation requires a user to select/drop the crafted filename or process a corresponding upload response; initial server-rendered Thymeleaf gallery pages escape filenames, so this is not evidence that all later gallery viewers receive stored XSS.

### CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')
- **Category:** Injection Attacks
- **Severity:** mandatory
- **Story Points:** 13
- **Files:** oracle-init/create-user.sh

create-user.sh lines 11-19 accepts APP_USER and APP_USER_PASSWORD from the container environment and only uppercases the username. The unquoted here-document at lines 22-45 substitutes APP_USER_UPPER into a quoted SQL string at line 27 and a dynamic CREATE USER statement at line 30, and substitutes APP_USER_PASSWORD into that dynamic statement without SQL escaping. Quotes or SQL syntax in those externally supplied configuration values can change SQL structure executed as SYSTEM. This is an initialization/configuration trust-boundary issue requiring control of those environment values, not SQL injection through the photo HTTP endpoints (whose repository queries use bound parameters). Credential contents are intentionally omitted.

