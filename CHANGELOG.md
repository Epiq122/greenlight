# Changelog

All notable changes to the Greenlight project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v0.1.0] - 2025-08-25

### Added
- Initial project structure with Go modules
- HTTP server setup with configurable port and environment
- RESTful API routing using httprouter
- Health check endpoint (`GET /v1/healthcheck`) with status, environment, and version info
- Movie API endpoints structure:
  - `POST /v1/movies` - Create movie handler (stub implementation)
  - `GET /v1/movies/:id` - Show movie handler (stub implementation)
- URL parameter parsing and validation helper (`readIDParam`)
- Structured logging with Go's slog package
- Command-line flag configuration for port and environment
- HTTP server with proper timeout configurations:
  - Idle timeout: 1 minute
  - Read timeout: 5 seconds
  - Write timeout: 10 seconds
- Error handling for invalid movie ID parameters
- Clean project structure with separated concerns

### Technical Details
- Go version: 1.25.0
- Dependencies: httprouter v1.3.0
- Architecture: Clean separation between main, routes, handlers, and helpers
- Logging: Text-based structured logging to stdout
- Error handling: HTTP 404 responses for invalid requests
