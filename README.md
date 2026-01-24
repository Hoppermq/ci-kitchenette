# ci-kitchenette
ci repository for workflows

## Go Linter Workflow

### Features
- Uses official `golangci/golangci-lint-action` for reliable linting
- Automatic cache management built into the official action
- Configurable golangci-lint version (default: v1.52.2)
- Verbose logging for better debugging
- Flexible working directory and custom arguments support

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
          args: '--timeout=5m'
```

### Inputs
- `go-version`: Go version to use (default: "1.21")
- `golangci-lint-version`: golangci-lint version to use (default: "v1.52.2")
- `working-directory`: Working directory (default: ".")
- `args`: Additional golangci-lint arguments (default: "")

### Benefits
- **Official Action**: Uses `golangci/golangci-lint-action@v6` which handles all cache management automatically
- **Version Pinning**: Supports explicit version specification for compatibility with `.golangci.yml`
- **Verbose Mode**: Includes `-v` flag for detailed linter output and better debugging
- **Simplified**: No manual cache management needed - the official action handles it properly
