# ORGGML - OpenCog-Inspired Machine Learning Monorepo

ORGGML reorganizes the [ggml-org](https://github.com/ggml-org) ecosystem into a cohesive monorepo structured according to OpenCog cognitive architecture principles. This creates an integrated framework for artificial general intelligence (AGI) research and practical AI applications.

## Quick Overview

ORGGML maps machine learning inference tools to cognitive system components:

- **ASML** (`asml/`) ← ggml: Tensor library as knowledge representation (AtomSpace equivalent)
- **Learn.Cog** (`learn.cog/`) ← llama.cpp: Language model inference for cognition
- **Sensation** (`sensation/`) ← whisper.cpp: Speech processing for sensory input
- **CI** (`ci/`) ← ggml-org/ci: Continuous integration infrastructure
- **Tools** (`tools/`) ← Editor plugins & utilities: Development ecosystem

## Key Features

- 🧠 **Cognitive Architecture**: Organized by cognitive function (learning, sensation, action)
- 🔗 **Monorepo**: No submodules, all code directly integrated
- ⚡ **Efficient**: Quantization and hardware abstraction for deployment
- 🌐 **Cross-platform**: CPU, GPU, edge devices
- 🎯 **Practical AGI**: Real-world applications with theoretical grounding

## Documentation

- **[ARCHITECTURE.md](./ARCHITECTURE.md)** - Detailed architectural overview and OpenCog mapping
- **[MAPPING.md](./MAPPING.md)** - Complete repository mapping from ggml-org to ORGGML
- **[OpenCog Component Mapping](./docs/OPENCOG_COMPONENT_MAPPING.md)** - Enriched mappings of ORGGML component groups to OpenCog subsystems

### Component Documentation
- [ASML (AtomSpace-ML)](./asml/README.md) - Tensor operations and knowledge representation
- [Learn.Cog](./learn.cog/README.md) - Language understanding and learning
- [Sensation](./sensation/README.md) - Sensory input processing (speech)
- [CI](./ci/README.md) - Continuous integration and testing
- [Tools](./tools/README.md) - Development tools and editor integrations

## Why ORGGML?

Traditional machine learning projects organize code by technical concerns (models, training, inference). ORGGML organizes by **cognitive function**, inspired by OpenCog's AGI architecture:

1. **Knowledge Representation** (ASML) - How information is stored and computed
2. **Cognition** (Learn.Cog) - How the system thinks and learns
3. **Perception** (Sensation) - How the system perceives the world
4. **Tools** - How humans interact with the system

This organization makes the path from narrow AI to AGI more explicit and tractable.

## Getting Started

```bash
# Clone the repository
git clone https://github.com/o9nn/orggml.git
cd orggml

# Each module can be built independently
cd asml
# Build instructions in component README

cd ../learn.cog
# Build instructions in component README
```

## Project Status

🚧 **In Progress**: Repository structure and documentation being established. Source code integration from ggml-org repositories will follow.

## Contributing

ORGGML integrates and extends work from the ggml-org community. Contributions should maintain the cognitive architecture organization and OpenCog-inspired design principles.

## Related Projects

- **ggml-org**: https://github.com/ggml-org - Original source repositories
- **OpenCog**: https://opencog.org/ - Cognitive architecture inspiration
- **llama.cpp**: https://github.com/ggml-org/llama.cpp - LLM inference
- **ggml**: https://github.com/ggml-org/ggml - Tensor library

## License

Components inherit their original licenses from ggml-org repositories (primarily MIT). See individual component directories for specific license information.