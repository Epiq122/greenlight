# Greenlight

A modern REST API for movie management built with Go, featuring clean architecture and comprehensive error handling.

## Version
**v0.1.0**

## Features
- ✅ RESTful API endpoints for movie operations
- ✅ Health check endpoint with environment status
- ✅ Clean HTTP routing with httprouter
- ✅ Structured logging with slog
- ✅ Configurable server settings (port, environment)
- ✅ URL parameter parsing and validation
- ✅ HTTP server with proper timeouts
- ✅ Command-line flag configuration

## Tech Stack
- **Language:** Go 1.25.0
- **Router:** httprouter v1.3.0
- **Logging:** Built-in slog package
- **HTTP Server:** Go's standard net/http package

## Installation

### Prerequisites
- Go 1.25.0 or higher
- Git

### Setup
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd greenlight
   ```

2. Install dependencies:
   ```bash
   go mod download
   ```

3. Build the application:
   ```bash
   go build -o bin/api ./cmd/api
   ```

## Usage

### Running the Server
```bash
# Run with default settings (port 4000, development environment)
./bin/api

# Run with custom port and environment
./bin/api -port=8080 -env=production
```

### API Endpoints
- `GET /v1/healthcheck` - Check API health and status
- `POST /v1/movies` - Create a new movie (stub)
- `GET /v1/movies/:id` - Get movie details by ID (stub)

### Example Requests
```bash
# Health check
curl http://localhost:4000/v1/healthcheck

# Get movie by ID
curl http://localhost:4000/v1/movies/123
```

## Project Structure
```
greenlight/
├── cmd/api/              # Application entrypoint and HTTP handlers
├── internal/             # Private application code
├── migrations/           # Database migration files
├── remote/              # Deployment configuration
├── bin/                 # Compiled binaries
├── go.mod               # Go module definition
└── Makefile            # Build automation
```

## Roadmap

### Upcoming Features
- [ ] Complete movie CRUD operations
- [ ] Database integration and migrations
- [ ] Data validation and sanitization
- [ ] Authentication and authorization
- [ ] Rate limiting
- [ ] API versioning
- [ ] Comprehensive error handling
- [ ] Unit and integration tests
- [ ] Docker containerization
- [ ] CI/CD pipeline

### Future Enhancements
- [ ] Search and filtering capabilities
- [ ] Pagination for large datasets
- [ ] Caching layer
- [ ] Metrics and monitoring
- [ ] API documentation with OpenAPI/Swagger

## Development

### Local Development
1. Start the development server:
   ```bash
   go run ./cmd/api -port=4000 -env=development
   ```

2. The API will be available at `http://localhost:4000`

### Building for Production
```bash
make build
```

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
