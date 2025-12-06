# OpenCog Component Mapping for ORGGML

## Overview

This document provides an enriched mapping between ORGGML components and OpenCog cognitive architecture components. It extends the basic repository mappings (see [MAPPING.md](../MAPPING.md)) with detailed cognitive component groupings that align with OpenCog's architectural principles.

## Mapping Philosophy

ORGGML reorganizes ggml-org repositories according to OpenCog-inspired cognitive architecture principles. While the basic structure maps repositories to cognitive functions (ASML → AtomSpace, Learn.Cog → Cognitive Modules, Sensation → Perception), this document provides more granular mappings showing how ORGGML components correspond to specific OpenCog subsystems.

## Component Grouping Architecture

### High-Level Structure

```
ORGGML Cognitive Architecture
│
├── orggml-core          (Foundation & Orchestration)
├── orggml-perception    (Sensory Processing)
├── orggml-knowledge     (Knowledge Representation & Reasoning)
├── orggml-planning      (Goal-Directed Behavior)
├── orggml-learning      (Adaptive Evolution)
├── orggml-communication (Language & Multi-Agent)
├── orggml-memory        (Persistent State & Attention)
└── orggml-tools         (External Integration)
```

---

## Detailed Component Mappings

### 1. orggml-core: Main Orchestration Engine

**Purpose**: Provides the foundational infrastructure for cognitive processing, similar to OpenCog's core utilities and orchestration systems.

**OpenCog Components**:
- **cogutil** - Core utilities and base data structures
- **atomspace** - Central knowledge representation hypergraph
- **cogserver** - Network server for distributed cognition

**ORGGML Mapping**:
```
orggml-core/
├── asml/           # AtomSpace analog - tensor-based knowledge representation
│   ├── core/       # Core tensor operations (cogutil analog)
│   ├── context/    # Computational graph management (AtomSpace analog)
│   └── backend/    # Hardware abstraction (distributed processing)
├── orchestrator/   # Main coordination engine (cogserver analog)
│   ├── scheduler/  # Task scheduling and resource allocation
│   ├── agent/      # Cognitive agent management
│   └── network/    # Inter-agent communication
└── common/         # Shared utilities and base classes
```

**Key Responsibilities**:
- Tensor graph construction and management (knowledge representation)
- Cognitive agent lifecycle management
- Resource scheduling and allocation
- Inter-component communication
- Hardware abstraction and backend management

**OpenCog Analogy**:
- `cogutil` provides base utilities → `asml/core/` provides tensor utilities
- `atomspace` manages hypergraph → `asml/context/` manages computational graphs
- `cogserver` orchestrates agents → `orchestrator/` manages cognitive cycles

---

### 2. orggml-perception: Multi-Modal Sensory Processing

**Purpose**: Handles sensory input processing across multiple modalities, converting raw sensory data into structured representations for cognitive processing.

**OpenCog Components**:
- **sensory** - Generic sensory processing interface
- **vision** - Visual perception and processing
- **perception** - Multi-modal perception integration

**ORGGML Mapping**:
```
orggml-perception/
├── sensation/           # Speech and audio processing
│   ├── whisper/         # Whisper model integration
│   ├── audio/           # Audio preprocessing
│   └── transcription/   # Speech-to-text conversion
├── vision/              # Visual processing (future)
│   ├── image/           # Image preprocessing
│   ├── object/          # Object detection
│   └── scene/           # Scene understanding
└── integration/         # Multi-modal fusion
    ├── attention/       # Cross-modal attention
    └── alignment/       # Temporal and spatial alignment
```

**Key Responsibilities**:
- Audio signal processing and speech recognition
- Visual input processing (planned)
- Cross-modal sensory integration
- Perceptual attention mechanisms
- Feature extraction for cognitive processing

**OpenCog Analogy**:
- `sensory` interface → `sensation/` audio processing
- `vision` processing → `vision/` visual processing (planned)
- `perception` fusion → `integration/` multi-modal fusion

**Current Status**:
- ✅ Audio/speech processing implemented (sensation/)
- 📋 Visual processing planned
- 📋 Multi-modal fusion planned

---

### 3. orggml-knowledge: Knowledge Representation & Reasoning

**Purpose**: Implements knowledge storage, representation, and reasoning capabilities using tensor-based structures analogous to OpenCog's symbolic reasoning systems.

**OpenCog Components**:
- **atomspace** - Hypergraph knowledge representation
- **pln** - Probabilistic Logic Networks for uncertain reasoning
- **ure** - Unified Rule Engine for inference
- **miner** - Pattern mining and discovery

**ORGGML Mapping**:
```
orggml-knowledge/
├── representation/      # Knowledge representation layer
│   ├── asml/            # Tensor-based knowledge atoms
│   ├── graphs/          # Knowledge graph structures
│   └── embeddings/      # Semantic embeddings
├── reasoning/           # Inference and reasoning engines
│   ├── inference/       # Forward/backward chaining (URE analog)
│   ├── probabilistic/   # Uncertainty handling (PLN analog)
│   └── logical/         # Logical reasoning
├── patterns/            # Pattern recognition and mining
│   ├── discovery/       # Pattern discovery (miner analog)
│   ├── matching/        # Pattern matching
│   └── recognition/     # Pattern recognition
└── storage/             # Persistent knowledge storage
    ├── cache/           # In-memory caching
    └── persistence/     # Disk-based storage
```

**Key Responsibilities**:
- Tensor-based knowledge representation (symbolic + subsymbolic)
- Probabilistic reasoning under uncertainty
- Rule-based inference and deduction
- Pattern mining from knowledge structures
- Persistent knowledge storage

**OpenCog Analogy**:
- `atomspace` hypergraph → `representation/asml/` tensor graphs
- `pln` probabilistic reasoning → `reasoning/probabilistic/` tensor-based uncertainty
- `ure` rule engine → `reasoning/inference/` tensor inference
- `miner` pattern mining → `patterns/discovery/` tensor pattern recognition

**Implementation Notes**:
- Knowledge represented as computational tensor graphs
- Embeddings enable semantic reasoning over continuous spaces
- Combines symbolic logic (OpenCog) with subsymbolic learning (neural)

---

### 4. orggml-planning: Hierarchical Planning & Goals

**Purpose**: Implements goal-directed behavior and hierarchical planning capabilities, enabling agents to reason about actions and future states.

**OpenCog Components**:
- **spacetime** - Spatial and temporal reasoning
- **cogserver** - Agent coordination and goal management

**ORGGML Mapping**:
```
orggml-planning/
├── goals/               # Goal representation and management
│   ├── representation/  # Goal structures
│   ├── prioritization/  # Goal priority and selection
│   └── tracking/        # Goal state tracking
├── planning/            # Planning algorithms
│   ├── hierarchical/    # Hierarchical task decomposition
│   ├── temporal/        # Temporal planning (spacetime analog)
│   └── search/          # Plan search strategies
├── execution/           # Plan execution engine
│   ├── monitor/         # Execution monitoring
│   ├── adapt/           # Runtime plan adaptation
│   └── recovery/        # Failure recovery
└── coordination/        # Multi-agent coordination
    ├── negotiation/     # Agent negotiation
    └── synchronization/ # Action synchronization
```

**Key Responsibilities**:
- Goal representation and prioritization
- Hierarchical task decomposition
- Temporal and spatial reasoning for planning
- Plan generation and optimization
- Multi-agent coordination and negotiation
- Runtime plan monitoring and adaptation

**OpenCog Analogy**:
- `spacetime` reasoning → `planning/temporal/` and `planning/hierarchical/`
- `cogserver` coordination → `coordination/` multi-agent planning

**Implementation Strategy**:
- Use language model reasoning for high-level planning
- Combine with tensor-based search for plan optimization
- Leverage working memory for context-aware planning

---

### 5. orggml-learning: Continuous Learning & Adaptation

**Purpose**: Enables continuous learning, adaptation, and evolutionary improvement of cognitive capabilities.

**OpenCog Components**:
- **moses** - Meta-Optimizing Semantic Evolutionary Search
- **asmoses** - AtomSpace integration for MOSES
- **learn** - Unsupervised language learning

**ORGGML Mapping**:
```
orggml-learning/
├── evolutionary/        # Evolutionary optimization
│   ├── genetic/         # Genetic algorithms (MOSES analog)
│   ├── search/          # Meta-optimization search
│   └── fitness/         # Fitness evaluation
├── language/            # Language learning and adaptation
│   ├── learn.cog/       # LLM-based learning
│   ├── unsupervised/    # Unsupervised learning (learn analog)
│   └── fine-tuning/     # Model fine-tuning and adaptation
├── reinforcement/       # Reinforcement learning
│   ├── policy/          # Policy learning
│   ├── value/           # Value estimation
│   └── reward/          # Reward modeling
└── transfer/            # Transfer learning
    ├── knowledge/       # Knowledge transfer
    └── adaptation/      # Domain adaptation
```

**Key Responsibilities**:
- Evolutionary program synthesis and optimization
- Continuous language model improvement
- Reinforcement learning from interaction
- Transfer learning across domains
- Meta-learning for rapid adaptation

**OpenCog Analogy**:
- `moses` evolutionary search → `evolutionary/genetic/` genetic optimization
- `asmoses` AtomSpace integration → integration with `orggml-knowledge`
- `learn` language learning → `language/unsupervised/` and `language/learn.cog/`

**Implementation Strategy**:
- Leverage pre-trained language models as starting point
- Use evolutionary algorithms for architecture search
- Enable continuous learning from interaction data
- Support model fine-tuning and parameter optimization

---

### 6. orggml-communication: NLP & Multi-Agent Communication

**Purpose**: Enables natural language processing, understanding, and multi-agent communication capabilities.

**OpenCog Components**:
- **lg-atomese** - Link Grammar integration for NLP
- **opencog** - Final integration and communication layer

**ORGGML Mapping**:
```
orggml-communication/
├── nlp/                 # Natural language processing
│   ├── parsing/         # Language parsing (LG analog)
│   ├── generation/      # Language generation
│   └── understanding/   # Semantic understanding
├── dialogue/            # Dialogue management
│   ├── context/         # Dialogue context tracking
│   ├── state/           # Dialogue state management
│   └── policy/          # Dialogue policy
├── multi-agent/         # Multi-agent communication
│   ├── protocols/       # Communication protocols
│   ├── coordination/    # Agent coordination
│   └── negotiation/     # Multi-agent negotiation
└── integration/         # System integration (opencog analog)
    ├── api/             # External API interfaces
    └── bridges/         # Cross-component bridges
```

**Key Responsibilities**:
- Natural language parsing and generation
- Dialogue management and context tracking
- Multi-agent communication protocols
- System-wide integration and coordination
- External system interfacing

**OpenCog Analogy**:
- `lg-atomese` Link Grammar → `nlp/parsing/` language parsing via LLMs
- `opencog` integration → `integration/` system-wide coordination

**Implementation Strategy**:
- Use language models for NLP (replacing traditional parsers)
- Implement dialogue state tracking with tensor-based context
- Enable agent-to-agent communication via natural language
- Provide API bridges for external system integration

---

### 7. orggml-memory: Memory & Context Management

**Purpose**: Manages persistent memory, working memory, attention allocation, and context for cognitive processing.

**OpenCog Components**:
- **atomspace-rocks** - RocksDB-based persistent storage
- **attention** - Economic Attention Networks (ECAN)

**ORGGML Mapping**:
```
orggml-memory/
├── working/             # Working memory
│   ├── context/         # Context window management
│   ├── cache/           # Fast access cache
│   └── operations/      # Working memory operations
├── episodic/            # Episodic memory
│   ├── events/          # Event recording
│   ├── retrieval/       # Memory retrieval
│   └── consolidation/   # Memory consolidation
├── semantic/            # Semantic memory
│   ├── knowledge/       # Long-term knowledge storage
│   ├── embeddings/      # Semantic embeddings
│   └── associations/    # Associative memory
├── attention/           # Attention mechanisms
│   ├── allocation/      # Attention allocation (ECAN analog)
│   ├── spread/          # Attention spreading
│   └── focus/           # Focus management
└── persistence/         # Persistent storage
    ├── storage/         # Database backend (RocksDB analog)
    └── serialization/   # Data serialization
```

**Key Responsibilities**:
- Working memory and context window management
- Episodic memory for experience recording
- Semantic memory for long-term knowledge
- Attention allocation and resource management
- Persistent storage and retrieval

**OpenCog Analogy**:
- `atomspace-rocks` persistence → `persistence/storage/` database backends
- `attention` ECAN → `attention/allocation/` attention mechanisms

**Implementation Strategy**:
- Use tensor-based context windows for working memory
- Implement episodic memory as sequence of events
- Store semantic knowledge as embeddings and graphs
- Economic attention allocation for cognitive resources
- Support multiple storage backends (memory, disk, distributed)

---

### 8. orggml-tools: External Tool Integration

**Purpose**: Provides integration with external tools, robotics platforms, and behavior scripting systems.

**OpenCog Components**:
- **external-tools** - Integration with external systems
- **ros-behavior-scripting** - ROS robotics integration

**ORGGML Mapping**:
```
orggml-tools/
├── editors/             # Editor integrations
│   ├── vim/             # Vim integration (llama.vim)
│   ├── vscode/          # VSCode integration (llama.vscode)
│   └── qtcreator/       # Qt Creator integration
├── deployment/          # Deployment tools
│   ├── llamabarn/       # macOS/iOS deployment
│   ├── containers/      # Container deployment
│   └── cloud/           # Cloud deployment
├── completion/          # Code completion
│   └── p1/              # P1 completion engine
├── robotics/            # Robotics integration (future)
│   ├── ros/             # ROS integration
│   ├── behavior/        # Behavior scripting
│   └── sensors/         # Sensor integration
└── external/            # External tool integration
    ├── apis/            # API integrations
    ├── databases/       # Database connectors
    └── services/        # External services
```

**Key Responsibilities**:
- IDE and editor integration for development
- Model deployment across platforms
- Code completion and assistance
- Robotics and embodiment integration (planned)
- External API and service integration

**OpenCog Analogy**:
- `external-tools` → `external/` API and service integration
- `ros-behavior-scripting` → `robotics/` ROS integration (planned)

**Current Status**:
- ✅ Editor integrations planned
- ✅ Deployment tools planned
- 📋 Robotics integration planned
- 📋 External tool bridges planned

---

## Integration Architecture

### Dependency Graph

```
                    ┌─────────────────┐
                    │  orggml-core    │
                    │  (Foundation)   │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
         ┌────▼────┐   ┌─────▼──────┐  ┌───▼────┐
         │ orggml- │   │  orggml-   │  │orggml- │
         │knowledge│   │ perception │  │ memory │
         └────┬────┘   └─────┬──────┘  └───┬────┘
              │              │              │
              └──────┬───────┴──────┬───────┘
                     │              │
              ┌──────▼───────┐ ┌───▼──────────┐
              │   orggml-    │ │   orggml-    │
              │communication │ │   planning   │
              └──────┬───────┘ └───┬──────────┘
                     │              │
                     └──────┬───────┘
                            │
                     ┌──────▼───────┐
                     │   orggml-    │
                     │   learning   │
                     └──────┬───────┘
                            │
                     ┌──────▼───────┐
                     │   orggml-    │
                     │    tools     │
                     └──────────────┘
```

### Cross-Component Integration

1. **Core → All Components**: Foundation layer provides tensor operations and orchestration
2. **Knowledge ↔ Memory**: Knowledge representation interfaces with memory systems
3. **Perception → Knowledge**: Sensory input feeds into knowledge representation
4. **Planning ↔ Learning**: Planning uses learned models, learning optimizes planning
5. **Communication ↔ All**: Communication layer enables inter-component coordination
6. **Tools → External Systems**: Tools integrate ORGGML with external platforms

---

## Comparison with OpenCog Architecture

### Similarities

1. **Modular Design**: Both use cognitive component decomposition
2. **Hypergraph Foundation**: AtomSpace ≈ ASML tensor graphs
3. **Attention Mechanisms**: Both implement cognitive resource allocation
4. **Multi-Agent Support**: Both enable distributed cognition
5. **Reasoning Capabilities**: Both support inference and pattern mining

### Key Differences

1. **Implementation**:
   - OpenCog: Symbolic hypergraph with Scheme/C++
   - ORGGML: Tensor-based with C/C++ and neural models

2. **Learning**:
   - OpenCog: Evolutionary (MOSES) + rule learning
   - ORGGML: Neural language models + evolutionary optimization

3. **Knowledge Representation**:
   - OpenCog: Discrete atoms and links
   - ORGGML: Continuous tensors and embeddings

4. **Language Processing**:
   - OpenCog: Link Grammar + symbolic parsing
   - ORGGML: Pre-trained language models (transformer-based)

5. **Deployment**:
   - OpenCog: Research-focused, requires full stack
   - ORGGML: Production-ready, quantized, edge-deployable

---

## Implementation Roadmap

### Phase 1: Foundation (Current)
- [x] Core ASML tensor library (orggml-core foundation)
- [x] Basic perception (orggml-perception audio)
- [x] Initial documentation structure
- [ ] Memory foundations (orggml-memory working memory)

### Phase 2: Knowledge & Reasoning
- [ ] Knowledge representation layer (orggml-knowledge)
- [ ] Tensor-based inference (reasoning)
- [ ] Pattern mining capabilities
- [ ] Persistent storage backends

### Phase 3: Planning & Learning
- [ ] Goal representation and planning (orggml-planning)
- [ ] Evolutionary optimization (orggml-learning)
- [ ] Reinforcement learning integration
- [ ] Continuous adaptation mechanisms

### Phase 4: Communication & Tools
- [ ] Multi-agent communication (orggml-communication)
- [ ] External tool integration (orggml-tools)
- [ ] Robotics platform support
- [ ] Advanced deployment capabilities

### Phase 5: Integration & Optimization
- [ ] Cross-component optimization
- [ ] Performance benchmarking
- [ ] Documentation completion
- [ ] Production deployment examples

---

## Usage Examples

### Example 1: Knowledge Representation

```c
// orggml-knowledge: Create knowledge representation
struct ggml_context *ctx = ggml_init(params);

// Create concept nodes (atoms)
struct ggml_tensor *agent = asml_concept_node(ctx, "Agent_0");
struct ggml_tensor *task = asml_concept_node(ctx, "Task_Process_Audio");

// Create relationship (link)
struct ggml_tensor *executes = asml_execution_link(
    ctx, 
    agent, 
    task,
    0.95f,  // truth strength
    0.90f   // confidence
);

// Query knowledge graph
struct asml_query_result *results = asml_pattern_match(
    ctx,
    "Agent_* executes Task_*"
);
```

### Example 2: Perception to Knowledge

```c
// orggml-perception: Process audio input
struct sensation_whisper *whisper = sensation_whisper_init(model_path, &params);
struct sensation_audio *audio = sensation_audio_preprocess(samples, n_samples, 16000);
const char *text = sensation_whisper_decode(whisper, audio, &decode_params);

// orggml-knowledge: Store in knowledge base
struct ggml_tensor *perception_event = asml_event_node(ctx, text);
asml_add_temporal_link(ctx, perception_event, current_timestamp);

// orggml-memory: Add to working memory
orggml_memory_add_to_working(memory, perception_event);
```

### Example 3: Planning with Learning

```c
// orggml-planning: Define goal
struct orggml_goal *goal = orggml_goal_create(
    "Respond_to_user_query",
    priority = 0.9
);

// orggml-knowledge: Query relevant knowledge
struct asml_query_result *context = asml_retrieve_context(
    knowledge_base,
    goal->description,
    max_tokens = 2048
);

// orggml-learning: Use learned model for plan generation
struct learncog_plan *plan = learncog_generate_plan(
    model,
    goal,
    context,
    &planning_params
);

// orggml-planning: Execute plan
orggml_execute_plan(plan, &execution_context);
```

### Example 4: Multi-Agent Communication

```c
// orggml-communication: Agent 1 sends message
struct orggml_message *msg = orggml_message_create(
    sender = "Agent_0",
    receiver = "Agent_1",
    content = "Query: What is the current task status?",
    protocol = ORGGML_PROTOCOL_INFORM
);

orggml_send_message(msg);

// orggml-communication: Agent 2 processes and responds
struct orggml_message *response = orggml_process_message(
    msg,
    agent1_knowledge,
    agent1_context
);

// orggml-memory: Both agents update their memory
orggml_memory_add_interaction(agent0_memory, msg, response);
orggml_memory_add_interaction(agent1_memory, msg, response);
```

---

## References

### ORGGML Documentation
- [MAPPING.md](../MAPPING.md) - Repository mapping from ggml-org
- [ARCHITECTURE.md](../ARCHITECTURE.md) - Overall architecture documentation
- [README.md](../README.md) - Project overview

### OpenCog Documentation
- [OpenCog Wiki](https://wiki.opencog.org/) - Comprehensive documentation
- [OpenCog Architecture](https://wiki.opencog.org/w/OpenCogPrime:Cognitive_Architecture) - Cognitive architecture details
- [AtomSpace](https://wiki.opencog.org/w/AtomSpace) - Knowledge representation
- [OpenCog GitHub](https://github.com/opencog) - Source code repositories

### Related Projects
- [ggml-org](https://github.com/ggml-org) - Original source repositories
- [llama.cpp](https://github.com/ggml-org/llama.cpp) - LLM inference
- [whisper.cpp](https://github.com/ggml-org/whisper.cpp) - Speech recognition

---

## Contributing

When contributing to ORGGML component development:

1. **Identify Cognitive Function**: Determine which component group your contribution belongs to
2. **Follow OpenCog Principles**: Maintain alignment with OpenCog cognitive architecture concepts
3. **Use Tensor Operations**: Implement using ASML/GGML tensor primitives
4. **Document Mappings**: Explain how your contribution maps to OpenCog components
5. **Cross-Component Integration**: Consider integration points with other components

---

## Questions and Feedback

For questions about OpenCog component mappings or suggestions for improvements:
- Open an issue in the repository
- Reference this document and the specific component group
- Provide OpenCog architecture context if applicable

---

**Last Updated**: 2025-12-06  
**Version**: 1.0  
**Status**: Initial comprehensive mapping
