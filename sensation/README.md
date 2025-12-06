# Sensation (Sensory Input Processing)

**Origin**: `whisper.cpp` from https://github.com/ggml-org/whisper.cpp

## Purpose

Sensation handles sensory input processing, specifically speech-to-text transcription. Analogous to OpenCog's **Sensation Module** for handling multimodal inputs.

## OpenCog Mapping

Maps to OpenCog's **Sensation Module**:
- Processes input data from various sensory modalities
- Converts raw audio to structured text representation
- Provides interface between external world and cognitive system

## Key Features

- OpenAI Whisper model C/C++ implementation
- Real-time speech recognition
- Edge device deployment capability
- Efficient audio processing via ASML

## Dependencies

- **ASML**: For tensor operations and model inference
- Transformer-based speech recognition models

## Integration

Sensation provides the input pipeline for multimodal cognitive processing, converting speech to text that can be processed by Learn.Cog and other cognitive modules.
