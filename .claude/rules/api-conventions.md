# API Conventions

## Endpoint Patterns
- Use nouns, not verbs: `/users` not `/getUsers`
- Plural for collections: `/users`, `/posts`
- Nested for relationships: `/users/{id}/posts`
- Use kebab-case: `/user-settings`

## HTTP Methods
- `GET`: Read (idempotent)
- `POST`: Create
- `PUT`: Full update (idempotent)
- `PATCH`: Partial update
- `DELETE`: Remove (idempotent)

## Response Format
```json
{
  "data": {},
  "meta": {
    "timestamp": "ISO-8601",
    "requestId": "uuid"
  }
}
```

## Error Format
```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable message",
    "details": {}
  }
}
```

## Status Codes
- `200`: Success
- `201`: Created
- `204`: No content (successful delete)
- `400`: Bad request (client error)
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not found
- `422`: Validation error
- `500`: Server error

## Pagination
- Use `page` and `limit` query params
- Include `total`, `page`, `limit` in response meta
- Default limit: 20, max: 100

## Versioning
- Version in URL: `/api/v1/users`
- Support n-1 version minimum
