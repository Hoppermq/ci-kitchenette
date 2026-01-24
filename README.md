# ci-kitchenette
ci repository for workflows

## Go Linter Workflow

### Features
- Automatic cache management with cleanup to prevent "File exists" errors
- Configurable golangci-lint version (default: v1.52.2)
- Verbose logging for better debugging
- Cross-OS cache support with smart restore keys
- Flexible working directory and custom flags support

### Usage Example

```yaml
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: Hoppermq/ci-kitchenette/golang/linter@main
        with:
          go-version: '1.21'
          golangci-lint-version: 'v1.52.2'
          working-directory: '.'
          flags: '--timeout=5m'
```

### Inputs
- `go-version`: Go version to use (default: "1.21")
- `golangci-lint-version`: golangci-lint version to use (default: "v1.52.2")
- `working-directory`: Working directory (default: ".")
- `flags`: Additional linter flags (default: "")

### Improvements
- **Cache Cleanup**: Automatically removes existing cache directories before restoration to prevent tar errors
- **Version Pinning**: Supports explicit version specification for compatibility with `.golangci.yml`
- **Smart Caching**: Uses runner.os, version, and Go file hashes for optimal cache key strategy
- **Verbose Mode**: Includes `-v` flag for detailed linter output and better debugging
