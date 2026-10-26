# Data Architecture

Single relational store: Oracle Database (Free 23ai in docker-compose), accessed through Spring Data JPA/Hibernate. `spring.jpa.hibernate.ddl-auto=create` recreates the schema on every start. Tests use H2.

```mermaid
erDiagram
    PHOTOS {
        VARCHAR2_36 id PK
        VARCHAR2_255 original_file_name
        BLOB photo_data
        VARCHAR2_255 stored_file_name
        VARCHAR2_500 file_path
        NUMBER_19 file_size
        VARCHAR2_50 mime_type
        TIMESTAMP uploaded_at
        NUMBER width
        NUMBER height
    }
```

- Entity: `com.photoalbum.model.Photo` (UUID string id, index `idx_photos_uploaded_at`).
- Image binaries are stored in the `photo_data` BLOB column; `file_path` is retained for compatibility only. A legacy file exists under `src/main/resources/static/uploads/`.
- Repository uses Oracle-specific native SQL (`ROWNUM`, `NVL`, `TO_CHAR`), which couples the data layer to Oracle.
- Init scripts in `oracle-init/` create the application user.
