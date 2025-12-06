# ASML (AtomSpace Machine Learning)

**Origin**: `ggml` from https://github.com/ggml-org/ggml

## Purpose

ASML serves as the foundational tensor library and knowledge representation layer, analogous to OpenCog's AtomSpace. This module provides:

- Low-level tensor operations for machine learning
- Efficient quantization and hardware abstraction
- Knowledge representation through mathematical structures
- Cross-platform computational primitives (CPU, GPU, etc.)

## OpenCog Mapping

In OpenCog architecture, the **AtomSpace** is the core graph database for knowledge storage and retrieval. ASML adapts this concept by providing:

- Tensor-based knowledge representation
- Efficient computation primitives
- Universal machine learning operations
- Foundation for all cognitive modules

## Key Features

- Minimal dependencies
- Hardware-agnostic tensor operations
- Quantization support for efficient inference
- Foundation for symbolic and subsymbolic processing

## Integration

ASML is used by all other cognitive modules (learn.cog, sensation, etc.) as the computational backbone, similar to how AtomSpace underpins all OpenCog operations.
