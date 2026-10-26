# API and Service Contracts

The application exposes HTTP endpoints only; it has no outbound service calls other than the Oracle database.

| Method | Path | Auth | Description |
|---|---|---|---|
| GET | `/` | Public | Gallery page (all photos, newest first) |
| POST | `/upload` | HTTP Basic (ADMIN) | Multipart `files` (list); JSON response `{success, uploadedPhotos[], failedUploads[]}` |
| GET | `/detail/{id}` | Public | Photo detail page with previous/next navigation |
| POST | `/detail/{id}/delete` | HTTP Basic (ADMIN) | Deletes photo, redirects to `/` with flash message |
| GET | `/photo/{id}` | Public | Streams photo bytes with stored MIME type, no-cache headers, `X-Photo-*` headers |

Upload validation: allowed MIME types `image/jpeg,image/png,image/gif,image/webp`; max 10 MB per file; max 50 MB per request; max 40M pixels.

```mermaid
sequenceDiagram
    participant B as Browser
    participant C as HomeController
    participant S as PhotoServiceImpl
    participant R as PhotoRepository
    participant D as Oracle DB
    B->>C: POST /upload (multipart, Basic auth)
    C->>S: uploadPhoto(file)
    S->>S: validate type, size, dimensions
    S->>R: save(Photo with BLOB)
    R->>D: INSERT INTO PHOTOS
    C-->>B: JSON result
    B->>C: GET /photo/{id}
    C->>S: getPhotoById
    S->>R: findById
    R->>D: SELECT
    C-->>B: image bytes
```
