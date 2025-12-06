# CI (Continuous Integration)

**Origin**: `ci` and related tools from https://github.com/ggml-org/ci

## Purpose

CI provides continuous integration, testing, and build automation for the entire monorepo, ensuring quality and consistency across all cognitive modules.

## OpenCog Mapping

While not directly mapped to a cognitive component, CI serves as the infrastructure layer ensuring system reliability and coherence, similar to OpenCog's development and testing infrastructure.

The ORGGML CI workflow is intentionally analogous to OpenCog's `oc.yml` workflow, adapted for ORGGML's cognitive architecture. See [CI Workflow Mapping](../docs/CI_WORKFLOW_MAPPING.md) for detailed comparison.

## Active Workflows

- **ORGGML Build** (`../.github/workflows/orggml.yml`) - Main build and test workflow
  - Builds ASML (foundation)
  - Builds Learn.Cog (cognition)
  - Builds Sensation (perception)
  - Runs tests for all components
  - Creates packages and uploads artifacts

See [workflows/README.md](./workflows/README.md) for detailed workflow documentation.

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
- Cognitive architecture-aligned build order

## Tools Included

- `free-disk-space`: Disk management for CI jobs
- `ccache-action`: Compilation caching for faster builds
- `action-create-release`: Automated release management

## Documentation

- [Workflow Documentation](./workflows/README.md) - Detailed workflow guide
- [CI Workflow Mapping](../docs/CI_WORKFLOW_MAPPING.md) - OpenCog to ORGGML mapping
