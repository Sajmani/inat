# Gemini Code Assistant Context

## Project: iNaturalist Go Client

This project is a Go client library for the iNaturalist API. The client is generated from an OpenAPI specification using the `oapi-codegen` tool.

### Key Technologies

*   **Go:** The programming language used for the client library.
*   **oapi-codegen:** A tool for generating Go client and server code from OpenAPI 3 specifications.
*   **iNaturalist API:** The API for which the client is generated.

### Project Structure

*   `api.json`: The OpenAPI 3 specification for the iNaturalist API. This file is downloaded from the iNaturalist API documentation and may require manual modifications as described in the `README.md`.
*   `cfg.yaml`: The configuration file for `oapi-codegen`. It specifies the output package, file, and generation options.
*   `generate.go`: Contains the `go:generate` directive to run `oapi-codegen` and generate the client.
*   `client.gen.go`: The generated Go client code. This file should not be manually edited.
*   `go.mod`, `go.sum`: Go module files that manage project dependencies.
*   `README.md`: Provides an overview of the project and instructions for generating the client.

### Building and Running

To regenerate the Go client, you will need to have `oapi-codegen` installed. You can then run the following command:

```bash
go generate
```

This will execute the `oapi-codegen` command as specified in `generate.go` and `cfg.yaml`, updating the `client.gen.go` file.

There are no other build or run commands specified. This project is a library, so it is intended to be used as a dependency in other Go projects.

### Development Conventions

*   The primary development workflow is to update the `api.json` file from the iNaturalist API documentation, apply any necessary manual fixes as documented in the `README.md`, and then run `go generate` to update the client.
*   The generated code in `client.gen.go` should not be modified directly. All changes should be made by modifying the `api.json` or the `cfg.yaml` and then regenerating the client.
