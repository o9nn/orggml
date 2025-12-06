# ORGGML Architecture

## Overview

ORGGML is a monorepo that reorganizes the ggml-org ecosystem according to OpenCog-inspired cognitive architecture principles. This creates a cohesive framework for artificial general intelligence (AGI) research by mapping machine learning inference tools to cognitive system components.

## OpenCog-Inspired Architecture

OpenCog is a framework for AGI research with a modular architecture consisting of:

1. **AtomSpace**: Core knowledge representation and storage
2. **Cognitive Modules**: Specialized processing units (sensation, action, language, etc.)
3. **Mind Agents**: Concurrent processes for reasoning, learning, and inference
4. **Scheduler**: Resource management and attention allocation

ORGGML adapts these principles by mapping ggml-org projects to equivalent cognitive components.

## Repository Structure and Mapping

### Core Components

| Directory | Origin Repo | OpenCog Analogy | Purpose |
|-----------|-------------|-----------------|---------|
| `asml/` | [ggml](https://github.com/ggml-org/ggml) | **AtomSpace** | Tensor library for knowledge representation and computation |
| `learn.cog/` | [llama.cpp](https://github.com/ggml-org/llama.cpp) | **Language/Cognitive Modules** | LLM inference for learning and language understanding |
| `sensation/` | [whisper.cpp](https://github.com/ggml-org/whisper.cpp) | **Sensation Module** | Speech-to-text for sensory input processing |
| `ci/` | [ci](https://github.com/ggml-org/ci) | **Infrastructure** | Continuous integration and testing |
| `tools/` | Editor plugins & utilities | **Development Tools** | Developer integrations and utilities |

### Enriched Component Architecture

ORGGML organizes components into eight cognitive functional groups that map to OpenCog subsystems. For detailed documentation of these mappings, see:

**[OpenCog Component Mapping](./docs/OPENCOG_COMPONENT_MAPPING.md)**

The eight component groups are:
1. **orggml-core** - Main orchestration engine (cogutil, atomspace, cogserver)
2. **orggml-perception** - Multi-modal sensory processing (sensory, vision, perception)
3. **orggml-knowledge** - Knowledge representation & reasoning (atomspace, pln, ure, miner)
4. **orggml-planning** - Hierarchical planning & goals (spacetime, cogserver)
5. **orggml-learning** - Continuous learning & adaptation (moses, asmoses, learn)
6. **orggml-communication** - NLP & multi-agent communication (lg-atomese, opencog)
7. **orggml-memory** - Memory & context management (atomspace-rocks, attention)
8. **orggml-tools** - External tool integration (external-tools, ros-behavior-scripting)

### Detailed Mapping

#### ASML (AtomSpace Machine Learning)
**From**: `ggml` (https://github.com/ggml-org/ggml)

ASML serves as the foundational layer, analogous to OpenCog's AtomSpace:
- Provides tensor operations as "knowledge atoms"
- Implements efficient quantization for practical AGI
- Hardware-agnostic computational primitives
- Foundation for all cognitive processing

**Key Philosophy**: Just as AtomSpace represents knowledge as graphs of atoms, ASML represents computational knowledge as tensor operations and transformations.

#### Learn.Cog (Learning and Cognition)
**From**: `llama.cpp` (https://github.com/ggml-org/llama.cpp)

Learn.Cog implements cognitive processing, mapping to multiple OpenCog modules:
- **Language Module**: Natural language understanding and generation
- **Focused Cognition**: Goal-driven reasoning with LLMs
- **General Cognition**: Associative pattern recognition
- **Learning**: Continuous adaptation through language model inference

**Key Philosophy**: Large language models serve as both knowledge repositories and reasoning engines, similar to how OpenCog's cognitive modules process and learn from information.

#### Sensation (Sensory Processing)
**From**: `whisper.cpp` (https://github.com/ggml-org/whisper.cpp)

Sensation handles multimodal input, specifically audio:
- Speech recognition and transcription
- Converts sensory data to structured representations
- Provides input pipeline for cognitive processing
- Edge-device capable for embodied AI

**Key Philosophy**: AGI requires multimodal understanding. Sensation bridges the gap between raw sensory input and symbolic/subsymbolic cognitive processing.

#### CI (Continuous Integration)
**From**: `ci` and related tools (https://github.com/ggml-org/ci)

Infrastructure for maintaining system coherence:
- Cross-platform build automation
- Automated testing and validation
- Performance monitoring
- Integration verification

#### Tools (Development Ecosystem)
**From**: Various ggml-org projects
- `llama.vim`, `llama.vscode`, `llama.qtcreator`: Editor integrations
- `LlamaBarn`: macOS/iOS deployment
- `p1`: Code completion engine

Tools enable human-AI collaboration and practical AGI applications.

## Design Principles

### 1. Cognitive Modularity
Each component maps to a distinct cognitive function, enabling:
- Independent development and optimization
- Parallel processing of different cognitive tasks
- Clear separation of concerns
- Reusable components across applications

### 2. Knowledge Integration
Components share knowledge through ASML's tensor representation:
- Learn.Cog generates language-based knowledge
- Sensation provides perceptual knowledge
- All stored and processed via ASML primitives

### 3. Practical AGI
Focus on deployable, efficient systems:
- Quantization for resource-constrained deployment
- Cross-platform support (CPU, GPU, edge devices)
- Minimal dependencies for wide applicability
- Real-world integration via Tools

### 4. Symbolic-Subsymbolic Bridge
Combines symbolic reasoning with subsymbolic learning:
- Neural networks (subsymbolic) in Learn.Cog and Sensation
- Tensor operations (mathematical/symbolic) in ASML
- Natural integration point for hybrid AI architectures

## Monorepo Benefits

### No Submodules
- All code directly integrated (no `.git` subdirectories)
- Simplified dependency management
- Atomic commits across components
- Easier refactoring and cross-component changes

### Unified Development
- Single build system across all modules
- Consistent coding standards and practices
- Integrated testing and CI/CD
- Shared utilities and common code

### Cognitive Coherence
- Clear architectural vision
- Explicit component relationships
- Facilitates AGI research by making cognitive structure explicit

## Future Extensions

The architecture naturally extends to additional OpenCog-inspired components:

- **Action Module**: Motor control and environmental interaction
- **Attention Module**: Dynamic resource allocation (Scheduler equivalent)
- **Memory Systems**: Episodic and procedural memory
- **Reasoning Engines**: Logic, probabilistic inference, pattern mining
- **Social Modeling**: Theory of mind, multi-agent coordination

## Getting Started

Each component directory contains:
- `README.md`: Component overview and purpose
- Source code organized by function
- Tests and benchmarks
- Integration examples

See individual module README files for detailed information:
- [ASML Documentation](./asml/README.md)
- [Learn.Cog Documentation](./learn.cog/README.md)
- [Sensation Documentation](./sensation/README.md)
- [CI Documentation](./ci/README.md)
- [Tools Documentation](./tools/README.md)

## References

- **ggml-org**: https://github.com/ggml-org
- **OpenCog**: https://opencog.org/
- **OpenCog Wiki**: https://wiki.opencog.org/
- **OpenCog GitHub**: https://github.com/opencog

## License

This project inherits licenses from the original ggml-org repositories. See individual component directories for specific license information.
