# API Reference

## Base URL
```
http://localhost:4000/v1
```

## Endpoints

### Health Check
Check the API status and get system information.

**Endpoint:** `GET /v1/healthcheck`

**Response:**
```
status: available
environment: development
version: 1.0.0
```

**Example:**
```bash
curl http://localhost:4000/v1/healthcheck
```

---

### Movies

#### Create Movie
Create a new movie entry.

**Endpoint:** `POST /v1/movies`

**Status:** Stub implementation - returns placeholder response

**Response:**
```
create a new movie...
```

**Example:**
```bash
curl -X POST http://localhost:4000/v1/movies
```

#### Get Movie by ID
Retrieve details of a specific movie by its ID.

**Endpoint:** `GET /v1/movies/:id`

**Parameters:**
- `id` (path parameter): Movie ID (must be a positive integer)

**Status:** Stub implementation - returns placeholder response

**Success Response:**
```
show the details of movie with ID {id}...
```

**Error Response:**
- **404 Not Found**: When ID is invalid (non-numeric, zero, or negative)

**Examples:**
```bash
# Valid request
curl http://localhost:4000/v1/movies/123

# Invalid request (returns 404)
curl http://localhost:4000/v1/movies/abc
curl http://localhost:4000/v1/movies/0
curl http://localhost:4000/v1/movies/-1
```

## Error Handling

### HTTP Status Codes
- `200 OK`: Successful request
- `404 Not Found`: Invalid movie ID or resource not found

### Error Responses
Currently, error responses are handled by Go's standard HTTP package:
- Invalid movie IDs return a standard 404 Not Found response
- Server errors are logged but may return generic error pages

## Request/Response Format

### Current Implementation
- **Content-Type**: Plain text responses
- **Character Encoding**: UTF-8

### Future Enhancements
Planned improvements include:
- JSON request/response format
- Structured error responses
- Request validation
- Content negotiation
