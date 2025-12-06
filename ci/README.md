# CI (Continuous Integration)

**Origin**: `ci` and related tools from https://github.com/ggml-org/ci

## Purpose

CI provides continuous integration, testing, and build automation for the entire monorepo, ensuring quality and consistency across all cognitive modules.

## OpenCog Mapping

While not directly mapped to a cognitive component, CI serves as the infrastructure layer ensuring system reliability and coherence, similar to OpenCog's development and testing infrastructure.

## Components

- Automated build systems
- Cross-platform testing
- Performance benchmarking
- Release automation
- GitHub Actions workflows

## Key Features

- Multi-platform build support
- Automated testing for all modules
- Integration verification
- Performance regression detection

## Tools Included

- `free-disk-space`: Disk management for CI jobs
- `ccache-action`: Compilation caching for faster builds
- `action-create-release`: Automated release management
