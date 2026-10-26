# Dependency Map

```mermaid
graph LR
    App["photo-album 1.0.0"] --> Parent["spring-boot-starter-parent 2.7.18"]
    App --> Web["spring-boot-starter-web"]
    App --> Thy["spring-boot-starter-thymeleaf"]
    App --> JPA["spring-boot-starter-data-jpa"]
    App --> Val["spring-boot-starter-validation"]
    App --> Sec["spring-boot-starter-security"]
    App --> Json["spring-boot-starter-json"]
    App --> IO["commons-io 2.11.0"]
    App --> Ojdbc["ojdbc8 (runtime)"]
    App --> Dev["spring-boot-devtools (optional)"]
    App -.test.-> Test["spring-boot-starter-test"]
    App -.test.-> H2["h2"]
    Web --> Tomcat["tomcat-embed-core 9.0.83"]
    Web --> SWeb["spring-web 5.3.31"]
    JPA --> Hib["hibernate-core 5.6.15"]
    Sec --> SSec["spring-security 5.7.x"]
```

| Dependency | Version | Scope | Notes |
|------------|---------|-------|-------|
| Spring Boot parent | 2.7.18 | - | End of OSS support; Java 8 baseline |
| commons-io | 2.11.0 | compile | Declared explicitly; CVE-2024-47554 fixed in 2.14.0 |
| ojdbc8 | managed | runtime | Oracle JDBC driver |
| h2 | managed | test | In-memory DB for tests |
| spring-boot-devtools | managed | optional | Development only |

Build tool: Maven. Java source/target: 8.
