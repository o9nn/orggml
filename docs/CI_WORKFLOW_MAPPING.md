# CI Workflow Mapping: OpenCog → ORGGML

This document provides a detailed mapping between OpenCog's `oc.yml` workflow and ORGGML's `orggml.yml` workflow, demonstrating the analogous architecture.

## Workflow Comparison Overview

### Structural Similarities

Both workflows follow the same overall pattern:
1. **Environment Setup**: Container-based build environment
2. **Dependency Installation**: Install build tools and libraries
3. **Sequential Component Builds**: Build components in dependency order
4. **Testing**: Run tests for each component
5. **Packaging**: Create distribution packages (optional)
6. **Artifact Collection**: Upload build artifacts

### Key Differences

| Feature | OpenCog oc.yml | ORGGML orggml.yml |
|---------|----------------|-------------------|
| **Component Count** | 20 components | 3 core cognitive modules |
| **Base Container** | `opencog/opencog-deps` | `ubuntu:22.04` |
| **Primary Language** | C++, Python, Scheme (Guile) | C++, Python |
| **Database Requirements** | PostgreSQL service | None (currently) |
| **Build System** | CMake (uniform) | CMake/Make (flexible) |
| **Architecture Philosophy** | Modular components | Cognitive functions |

## Component Mapping

### OpenCog Foundation Layer → ASML

**OpenCog Components:**
- `cogutil` - Utility library
- `atomspace` - Core knowledge representation
- `atomspace-storage` - Storage abstraction
- `atomspace-rocks` - RocksDB backend
- `atomspace-restful` - REST API

**ORGGML Equivalent:**
- `asml/` - AtomSpace Machine Learning
  - Combines foundation utilities with knowledge representation
  - Uses tensor operations instead of graph-based atoms
  - Single unified component vs. multiple specialized ones

**Rationale:** ASML consolidates the foundation layer by using ggml's tensor operations as the universal knowledge representation substrate. This simplifies the architecture while maintaining the "AtomSpace" concept of a foundational knowledge store.

### OpenCog Cognitive Processing → Learn.Cog

**OpenCog Components:**
- `unify` - Unification for pattern matching
- `ure` - Unified Rule Engine
- `pln` - Probabilistic Logic Networks
- `moses` - Meta-Optimizing Semantic Evolutionary Search
- `asmoses` - AtomSpace MOSES integration
- `miner` - Pattern mining
- `learn` - Language learning
- `lg-atomese` - Link Grammar integration

**ORGGML Equivalent:**
- `learn.cog/` - Learning and Language Cognition
  - LLM-based reasoning and learning
  - Subsumes multiple OpenCog reasoning systems
  - Neural approach vs. symbolic logic

**Rationale:** Modern LLMs (via llama.cpp) provide pattern matching, reasoning, language understanding, and learning in a unified neural architecture. This consolidates what OpenCog achieves through multiple specialized symbolic AI systems.

### OpenCog Perception → Sensation

**OpenCog Components:**
- `vision` - Vision processing
- (Implied) Sensation modules for sensory input

**ORGGML Equivalent:**
- `sensation/` - Sensory Input Processing
  - Speech-to-text via Whisper
  - Extensible to other modalities

**Rationale:** Focuses on audio perception initially (whisper.cpp), with architecture supporting expansion to vision and other modalities. OpenCog's vision module is more developed, while ORGGML starts with audio as primary sensory input.

### OpenCog Infrastructure → CI + Tools

**OpenCog Components:**
- `cogserver` - Network server for cognitive operations
- CI/CD infrastructure

**ORGGML Equivalent:**
- `ci/` - Continuous integration
- `tools/` - Development tools and integrations

**Rationale:** Similar infrastructure concerns but adapted for a monorepo structure. ORGGML's tools focus more on developer productivity (editor plugins, code completion) while OpenCog's cogserver focuses on runtime cognitive architecture management.

### OpenCog Specialized Modules → Future Extensions

**OpenCog Components:**
- `attention` - Attention allocation
- `spacetime` - Spatiotemporal reasoning
- `pattern-index` - Pattern indexing

**ORGGML Status:**
- Not yet implemented
- Planned as extensions in ARCHITECTURE.md
- Can be added while maintaining cognitive architecture

**Rationale:** ORGGML starts with core cognitive functions (knowledge, reasoning, perception) and can extend to specialized modules following the same architectural principles.

## Build Process Comparison

### OpenCog Build Pattern

```yaml
- name: Build and Install <component>
  run: |
    mkdir -p <component>/build && cd <component>/build
    cmake -DCMAKE_BUILD_TYPE=Release ..
    make -j$(nproc)
    sudo make install
    sudo ldconfig
    cd ../..
```

**Characteristics:**
- Uniform CMake-based builds
- All components follow identical pattern
- Sequential execution required due to dependencies
- Requires sudo for installation

### ORGGML Build Pattern

```yaml
- name: Build and Install <component>
  run: |
    if [ -f <component>/CMakeLists.txt ] || [ -f <component>/Makefile ]; then
      # Build logic with CMake or Make
      make install
      ldconfig
    else
      echo "<component> source not yet integrated - skipping build"
    fi
```

**Characteristics:**
- Flexible build system detection (CMake or Make)
- Graceful handling of missing components
- No sudo needed (running as root in container)
- Supports incremental integration from ggml-org

## Test Strategy Comparison

### OpenCog Testing
- Tests implicit in build process
- No explicit test steps in workflow
- Assumed to be part of `make` or handled separately

### ORGGML Testing
```yaml
- name: Test <component>
  run: |
    if [ -d <component>/build ]; then
      cd <component>/build
      ctest --output-on-failure || echo "Tests not configured yet"
    fi
```

**Characteristics:**
- Explicit test steps after each component
- Uses CTest for CMake-based projects
- Graceful handling of missing tests
- Fails gracefully vs. failing entire build

## Database and Service Dependencies

### OpenCog Requirements
```yaml
services:
  opencog-postgres:
    image: opencog/postgres
    env:
      POSTGRES_USER: root
      POSTGRES_PASSWORD: cheese
      POSTGRES_DB: atomspace_db
```

**Purpose:** AtomSpace persistence via PostgreSQL

### ORGGML Requirements
- Currently: None
- Future: May add vector databases for knowledge storage
- Tensor-based representation typically in-memory or file-based

## Environment Variables

### Common Settings (Both)
```yaml
env:
  CCACHE_DIR: /ws/ccache
  MAKEFLAGS: -j$(nproc)
```

Both workflows use:
- `ccache` for compilation caching
- Parallel builds via `nproc`

## Packaging and Artifacts

### OpenCog Packaging
```yaml
- name: Package Components
  run: |
    cd <component>/build
    make package || echo "<component> package target not defined."
```

Creates packages for each of 20 components.

### ORGGML Packaging
```yaml
- name: Package Components
  run: |
    # Package only 3 core components
    cd asml/build && make package || echo "not defined"
    cd learn.cog/build && make package || echo "not defined"
    cd sensation/build && make package || echo "not defined"
```

Simplified to 3 core cognitive modules.

### Artifact Upload
Both workflows upload build artifacts for debugging:
```yaml
- name: Upload Build Artifacts
  if: always()
  uses: actions/upload-artifact@v4
```

## Evolution Path

### OpenCog Evolution
- Started with core AtomSpace
- Gradually added cognitive modules
- Grew to 20+ components over years
- Maintains backward compatibility

### ORGGML Evolution (Planned)
1. **Phase 1 (Current)**: Structure and documentation
2. **Phase 2**: Integrate core components (ASML, Learn.Cog, Sensation)
3. **Phase 3**: Add CI/CD and development tools
4. **Phase 4**: Extend with additional cognitive modules
5. **Phase 5**: Advanced AGI research features

## Architectural Philosophy

### OpenCog Approach
- **Symbolic AI**: Logic, rules, pattern matching
- **Modular**: Many specialized components
- **Graph-based**: AtomSpace as hypergraph
- **Explicit reasoning**: Defined inference rules

### ORGGML Approach
- **Hybrid AI**: Neural networks + tensor operations
- **Cognitive functions**: Fewer, broader components
- **Tensor-based**: ASML as computational substrate
- **Implicit reasoning**: LLM-based inference

Both approaches aim for AGI but take different paths:
- OpenCog: Build AGI from symbolic reasoning primitives
- ORGGML: Build AGI from neural inference + cognitive organization

## Conclusion

The ORGGML workflow is intentionally analogous to OpenCog's workflow:
- Same container-based CI approach
- Similar build and test patterns
- Comparable artifact collection
- Parallel cognitive architecture mapping

However, ORGGML achieves a simpler workflow through:
- **Consolidation**: 3 cognitive modules vs 20 components
- **Modern ML**: Neural networks vs symbolic AI
- **Monorepo**: Direct integration vs submodules
- **Pragmatic**: Flexible build system vs uniform CMake

This makes ORGGML easier to understand, build, and extend while maintaining the cognitive architecture principles that make OpenCog powerful for AGI research.
