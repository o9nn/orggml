# ORGGML CI/CD Workflow Documentation

## Overview

The ORGGML workflow (`.github/workflows/orggml.yml`) implements a continuous integration pipeline analogous to OpenCog's `oc.yml` workflow, adapted for ORGGML's cognitive architecture.

## Active Workflows

- **ORGGML** (`../../.github/workflows/orggml.yml`) - Main build and test workflow
  - ✅ **Implemented** - Builds and tests all cognitive components

## Architecture Comparison

### OpenCog Workflow Structure
The OpenCog `oc.yml` workflow builds components in dependency order:
1. **cogutil** - Utility library (foundation)
2. **atomspace** - Core knowledge representation
3. **atomspace-storage** - Persistence layer
4. **atomspace-rocks** - RocksDB storage backend
5. **atomspace-restful** - RESTful API
6. **cogserver** - Network server
7. **unify** - Unification library
8. **ure** - Unified Rule Engine
9. **spacetime** - Spatiotemporal reasoning
10. **attention** - Attention allocation
11. **miner** - Pattern mining
12. **pln** - Probabilistic Logic Networks
13. **moses** - Program learning
14. **asmoses** - AtomSpace MOSES integration
15. **lg-atomese** - Link Grammar integration
16. **learn** - Language learning
17. **pattern-index** - Pattern indexing
18. **vision** - Vision processing
19. **opencog** - Main integration package

### ORGGML Workflow Structure
The ORGGML workflow builds components in cognitive function order:
1. **ASML (asml/)** - AtomSpace Machine Learning
   - Foundation tensor library
   - Analogous to cogutil + atomspace
   - Provides knowledge representation through tensors
   
2. **Learn.Cog (learn.cog/)** - Learning and Language Cognition
   - LLM inference and language processing
   - Analogous to learn + pln + ure (cognitive processing)
   - Depends on ASML for tensor operations
   
3. **Sensation (sensation/)** - Sensory Input Processing
   - Speech-to-text processing
   - Analogous to vision + sensation modules
   - Depends on ASML for neural network inference

## Design Principles

### 1. Cognitive Architecture Alignment
The build order reflects the cognitive architecture:
- **Foundation**: ASML provides the computational substrate
- **Cognition**: Learn.Cog implements reasoning and language
- **Perception**: Sensation handles sensory input

This mirrors how OpenCog builds from AtomSpace → Cognitive Modules → Integration.

### 2. Dependency Management
Each component explicitly depends on its predecessors:
```
ASML (foundation)
  ↓
Learn.Cog (cognition)
  ↓
Sensation (perception)
```

### 3. Flexibility for Integration
The workflow uses conditional logic to handle:
- Components not yet integrated from ggml-org
- Different build systems (CMake vs Makefile)
- Optional features and tests

### 4. Testing Strategy
Tests run after each component builds:
- Unit tests via CTest or make test
- Integration tests across components
- Performance benchmarks (planned)

## Workflow Features

### Container Environment
- Uses Ubuntu 22.04 as base (vs OpenCog's opencog-deps)
- Installs standard ML build dependencies
- Configurable ccache for faster rebuilds

### Build Process
Each component follows a standard pattern:
1. Check if source code exists (CMakeLists.txt or Makefile)
2. Configure with CMake or Make
3. Build with parallel jobs (`-j$(nproc)`)
4. Install to system directories
5. Update library cache (`ldconfig`)

### Error Handling
- Gracefully handles missing source code
- Continues on test failures (reports but doesn't fail build)
- Provides clear error messages for debugging

### Artifact Collection
- Uploads build directories for all components
- Enabled on all runs (success or failure)
- Useful for debugging build issues

## Planned Workflows

Future workflow additions:
- **Multi-platform**: Cross-platform builds (Linux, macOS, Windows)
- **Lint**: Code quality and style checks
- **Performance**: Benchmark regression detection
- **Release**: Automated release creation and deployment

## Usage

### Triggering Builds
- **Automatic**: Runs on push to `main` or pull requests
- **Manual**: Can be triggered via GitHub Actions UI

### Monitoring
- Check Actions tab for build status
- Download artifacts for failed builds
- Review logs for each component

### Local Testing
Before pushing, test builds locally:
```bash
# Build ASML
cd asml && mkdir -p build && cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)

# Build Learn.Cog
cd ../../learn.cog && mkdir -p build && cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)

# Build Sensation
cd ../../sensation && mkdir -p build && cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)
```

## Comparison with OpenCog

| Aspect | OpenCog oc.yml | ORGGML orggml.yml |
|--------|---------------|-------------------|
| Components | 20 sequential builds | 3 core cognitive modules |
| Base Image | opencog/opencog-deps | ubuntu:22.04 |
| Dependencies | PostgreSQL, RocksDB, OctoMap | Standard ML libraries |
| Build Time | ~30-60 minutes | ~10-20 minutes (estimated) |
| Architecture | Traditional modular | Cognitive function-based |
| Integration | Git submodules | Monorepo (no submodules) |

## Contributing

When adding new cognitive modules:
1. Follow the cognitive architecture principles
2. Update this workflow to build in dependency order
3. Add appropriate tests
4. Document the OpenCog mapping in ARCHITECTURE.md

## References

- OpenCog CI: https://github.com/opencog/pycog0/.github/workflows/oc.yml
- ggml-org CI: https://github.com/ggml-org/ci
- ORGGML Architecture: [../../ARCHITECTURE.md](../../ARCHITECTURE.md)
- Component Mapping: [../../MAPPING.md](../../MAPPING.md)
