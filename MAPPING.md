# Repository Mapping: ggml-org → ORGGML

This document provides a complete mapping of repositories from the ggml-org GitHub organization to the ORGGML monorepo structure.

## Mapping Table

| ggml-org Repository | ORGGML Location | OpenCog Component | Status |
|---------------------|-----------------|-------------------|--------|
| [ggml](https://github.com/ggml-org/ggml) | `asml/` | AtomSpace | 📋 Planned |
| [llama.cpp](https://github.com/ggml-org/llama.cpp) | `learn.cog/` | Language/Cognitive Modules | 📋 Planned |
| [whisper.cpp](https://github.com/ggml-org/whisper.cpp) | `sensation/` | Sensation Module | 📋 Planned |
| [ci](https://github.com/ggml-org/ci) | `ci/` | Infrastructure | 📋 Planned |
| [llama.vim](https://github.com/ggml-org/llama.vim) | `tools/editors/vim/` | Development Tools | 📋 Planned |
| [llama.vscode](https://github.com/ggml-org/llama.vscode) | `tools/editors/vscode/` | Development Tools | 📋 Planned |
| [llama.qtcreator](https://github.com/ggml-org/llama.qtcreator) | `tools/editors/qtcreator/` | Development Tools | 📋 Planned |
| [LlamaBarn](https://github.com/ggml-org/LlamaBarn) | `tools/deployment/llamabarn/` | Development Tools | 📋 Planned |
| [p1](https://github.com/ggml-org/p1) | `tools/completion/p1/` | Development Tools | 📋 Planned |
| [free-disk-space](https://github.com/ggml-org/free-disk-space) | `ci/actions/free-disk-space/` | CI Utilities | 📋 Planned |
| [ccache-action](https://github.com/ggml-org/ccache-action) | `ci/actions/ccache/` | CI Utilities | 📋 Planned |
| [action-create-release](https://github.com/ggml-org/action-create-release) | `ci/actions/create-release/` | CI Utilities | 📋 Planned |
| [ggml-org.github.io](https://github.com/ggml-org/ggml-org.github.io) | `docs/website/` | Documentation | 📋 Planned |
| [media](https://github.com/ggml-org/media) | `docs/media/` | Documentation | 📋 Planned |

## Directory Structure

```
orggml/
├── asml/                          # AtomSpace Machine Learning (from ggml)
│   ├── README.md
│   ├── src/                       # Core tensor library
│   ├── include/                   # Public headers
│   ├── examples/                  # Usage examples
│   └── tests/                     # Unit tests
│
├── learn.cog/                     # Learning & Cognition (from llama.cpp)
│   ├── README.md
│   ├── src/                       # LLM inference engine
│   ├── models/                    # Model architectures
│   ├── examples/                  # Example applications
│   └── tests/                     # Unit tests
│
├── sensation/                     # Sensory Processing (from whisper.cpp)
│   ├── README.md
│   ├── src/                       # Speech-to-text engine
│   ├── models/                    # Whisper model variants
│   ├── examples/                  # Usage examples
│   └── tests/                     # Unit tests
│
├── ci/                           # Continuous Integration
│   ├── README.md
│   ├── workflows/                # GitHub Actions workflows
│   ├── actions/                  # Custom actions
│   │   ├── free-disk-space/
│   │   ├── ccache/
│   │   └── create-release/
│   └── scripts/                  # Build and test scripts
│
├── tools/                        # Development Tools
│   ├── README.md
│   ├── editors/                  # Editor integrations
│   │   ├── vim/                  # llama.vim
│   │   ├── vscode/               # llama.vscode
│   │   └── qtcreator/            # llama.qtcreator
│   ├── deployment/               # Deployment tools
│   │   └── llamabarn/            # LlamaBarn for macOS/iOS
│   └── completion/               # Code completion
│       └── p1/                   # P1 completion engine
│
├── docs/                         # Documentation
│   ├── website/                  # ggml-org.github.io content
│   └── media/                    # Media assets
│
├── ARCHITECTURE.md               # Architecture documentation
├── MAPPING.md                    # This file
├── README.md                     # Main README
├── LICENSE                       # License information
└── .gitignore                    # Git ignore patterns
```

## Integration Strategy

### Phase 1: Structure ✅ (Current)
- [x] Create directory structure
- [x] Add README documentation for each component
- [x] Create ARCHITECTURE.md explaining the cognitive organization
- [x] Create MAPPING.md documenting the repository correspondence

### Phase 2: Core Integration (Next)
- [ ] Clone ggml source code into `asml/`
- [ ] Clone llama.cpp source code into `learn.cog/`
- [ ] Clone whisper.cpp source code into `sensation/`
- [ ] Remove `.git` directories (no submodules)
- [ ] Resolve any path dependencies between components
- [ ] Update build systems for monorepo structure

### Phase 3: CI and Tools
- [ ] Integrate CI workflows and actions into `ci/`
- [ ] Add editor plugins to `tools/editors/`
- [ ] Add deployment tools to `tools/deployment/`
- [ ] Add completion engines to `tools/completion/`
- [ ] Set up unified build and test systems

### Phase 4: Documentation
- [ ] Migrate website content to `docs/website/`
- [ ] Move media assets to `docs/media/`
- [ ] Create unified API documentation
- [ ] Add integration examples
- [ ] Document cognitive architecture patterns

### Phase 5: Refinement
- [ ] Optimize cross-component dependencies
- [ ] Implement shared utilities library
- [ ] Create integration tests across modules
- [ ] Performance optimization
- [ ] Add advanced AGI research examples

## Naming Conventions

### Component Names
- **asml**: AtomSpace Machine Learning (not GGML) - emphasizes cognitive role
- **learn.cog**: Learning and Cognition - explicit cognitive function
- **sensation**: Sensory processing - OpenCog-inspired naming

### Design Philosophy
The naming emphasizes **cognitive function** over technical implementation, making the AGI architecture explicit. This helps researchers and developers understand how components contribute to the larger cognitive system.

## Dependency Graph

```
              ┌──────────────┐
              │     ASML     │  (Foundation - Tensor Operations)
              │   (ggml)     │
              └──────┬───────┘
                     │
         ┌───────────┴───────────┐
         │                       │
    ┌────▼────────┐      ┌──────▼─────┐
    │  Learn.Cog  │      │  Sensation │
    │ (llama.cpp) │      │(whisper.cpp)│
    └─────────────┘      └────────────┘
              │                  │
              └────────┬─────────┘
                       │
                  ┌────▼────┐
                  │  Tools  │  (Editor Plugins, Deployment)
                  └─────────┘
```

All cognitive modules depend on ASML for tensor operations. Tools can leverage any cognitive module for their functionality.

## License Inheritance

Each component maintains its original license from ggml-org:
- **ggml**: MIT License
- **llama.cpp**: MIT License
- **whisper.cpp**: MIT License
- **CI and tools**: Various (see individual component licenses)

The monorepo structure does not change licensing, only organization.

## Migration Notes

### Submodule Removal
Original ggml-org repositories use git submodules. In ORGGML:
- All code is directly integrated (no `.git` subdirectories)
- Dependencies are explicit in the directory structure
- Simplifies atomic commits and refactoring

### Build System Updates
- Cmake/Make files updated to reflect new directory structure
- Paths adjusted for monorepo organization
- Cross-component dependencies explicitly declared

### Import Path Changes
Code using these libraries may need import path updates:
- `#include "ggml.h"` → `#include "asml/ggml.h"`
- `#include "llama.h"` → `#include "learn.cog/llama.h"`
- `#include "whisper.h"` → `#include "sensation/whisper.h"`

## Contributing to the Mapping

If additional ggml-org repositories are created or discovered:

1. Identify the cognitive function it serves
2. Map to appropriate OpenCog-inspired component
3. Add to the mapping table above
4. Update ARCHITECTURE.md if needed
5. Place in the corresponding directory

## References

- **ggml-org repositories**: https://github.com/orgs/ggml-org/repositories
- **OpenCog architecture**: https://wiki.opencog.org/w/OpenCogPrime:Cognitive_Architecture
- **ORGGML architecture**: [ARCHITECTURE.md](./ARCHITECTURE.md)

## Questions?

For questions about the mapping or suggestions for improvements, please open an issue in the repository.
