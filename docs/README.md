# Greenlight API Documentation

## Overview
Greenlight is a REST API for movie management built with Go. It provides endpoints for creating, retrieving, and managing movie data with a clean, scalable architecture.

## Architecture

### Project Structure
```
greenlight/
├── cmd/api/              # Application entrypoint and HTTP layer
│   ├── main.go          # Server setup and configuration
│   ├── routes.go        # HTTP route definitions
│   ├── movies.go        # Movie-related handlers
│   ├── healthcheck.go   # Health check endpoint
│   └── helpers.go       # Utility functions for HTTP handling
├── internal/            # Private application code (future models, services)
├── migrations/          # Database migration files
├── remote/             # Deployment and infrastructure configuration
├── bin/                # Compiled binaries
└── docs/               # Project documentation
```

### Design Principles
- **Separation of Concerns**: Clean separation between HTTP layer, business logic, and data layer
- **Configuration**: Environment-based configuration using command-line flags
- **Error Handling**: Consistent error responses and logging
- **Scalability**: Structured to support future database integration and business logic

## Configuration

### Application Structure
```go
type config struct {
    port int    // Server port (default: 4000)
    env  string // Environment (development|staging|production)
}

type application struct {
    config config
    logger *slog.Logger
}
```

### Command-Line Flags
- `-port`: Set server port (default: 4000)
- `-env`: Set environment (default: development)

### Server Configuration
- **Idle Timeout**: 1 minute
- **Read Timeout**: 5 seconds
- **Write Timeout**: 10 seconds
- **Logging Level**: Error logs are captured and structured

## Local Development

### Prerequisites
- Go 1.25.0+
- Git

### Setup Steps
1. Clone the repository
2. Navigate to project directory
3. Install dependencies: `go mod download`
4. Run the server: `go run ./cmd/api`

### Development Commands
```bash
# Run with custom settings
go run ./cmd/api -port=8080 -env=development

# Build for production
go build -o bin/api ./cmd/api

# Run built binary
./bin/api -port=4000 -env=production
```

## Deployment

### Building
```bash
# Build binary
go build -o bin/api ./cmd/api

# Cross-compile for Linux
GOOS=linux GOARCH=amd64 go build -o bin/api-linux ./cmd/api
```

### Environment Variables
Currently configured via command-line flags. Future versions may support environment variables.

### Production Considerations
- Set `-env=production` for production deployments
- Configure appropriate port based on infrastructure
- Ensure proper logging aggregation
- Set up health check monitoring on `/v1/healthcheck`

## Troubleshooting

### Common Issues
1. **Port Already in Use**: Change port with `-port` flag
2. **Invalid Movie ID**: API returns 404 for non-numeric or negative IDs
3. **Server Won't Start**: Check port availability and Go version compatibility

### Logging
All server activity is logged to stdout using structured logging. Key log messages include:
- Server startup with address and environment
- HTTP errors and invalid requests
- Application errors and panics
