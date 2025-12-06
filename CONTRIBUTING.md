# Contributing to ORGGML

Thank you for your interest in contributing to ORGGML! This guide will help you understand the project structure and how to contribute effectively.

## Understanding the Architecture

ORGGML reorganizes the ggml-org ecosystem according to OpenCog-inspired cognitive architecture principles. Before contributing, please read:

1. **[README.md](./README.md)** - Project overview and quick start
2. **[ARCHITECTURE.md](./ARCHITECTURE.md)** - Detailed architectural design and philosophy
3. **[MAPPING.md](./MAPPING.md)** - Repository mapping from ggml-org to ORGGML

## Project Structure

The monorepo is organized by **cognitive function**, not technical implementation:

```
orggml/
├── asml/           # Knowledge representation (tensor operations)
├── learn.cog/      # Learning and language cognition
├── sensation/      # Sensory input processing
├── ci/             # Continuous integration
└── tools/          # Development tools
```

## Contribution Guidelines

### 1. Cognitive-First Organization

When adding or modifying code:
- **Think cognitively**: What cognitive function does this serve?
- **Place appropriately**: Put code in the module that matches its cognitive role
- **Maintain separation**: Keep clear boundaries between cognitive modules

### 2. No Submodules Policy

ORGGML is a true monorepo:
- ✅ **DO**: Integrate code directly into the repository
- ❌ **DON'T**: Add git submodules or external dependencies via git
- All code should be directly committed to the monorepo

### 3. Naming Conventions

Follow cognitive function naming:
- Use descriptive names that reflect cognitive purpose
- Prefer `learn.cog` over `llama-cpp` style names
- Emphasize "what it does" over "how it works"

### 4. Documentation Requirements

Every contribution should include:
- **Code comments**: Explain cognitive purpose, not just mechanics
- **README updates**: If adding new components or changing structure
- **Examples**: Show practical usage in cognitive context

### 5. Cross-Module Dependencies

When creating dependencies:
- **ASML foundation**: All modules can depend on ASML (tensor operations)
- **Minimize coupling**: Keep modules as independent as possible
- **Explicit interfaces**: Define clear APIs between modules
- **Document dependencies**: Make relationships explicit

## Development Workflow

### Setting Up

```bash
git clone https://github.com/o9nn/orggml.git
cd orggml

# Each module can be built independently
cd asml
# Follow build instructions in module README
```

### Making Changes

1. **Create a branch**:
   ```bash
   git checkout -b feature/your-cognitive-feature
   ```

2. **Make changes** following the guidelines above

3. **Test thoroughly**:
   - Unit tests for individual functions
   - Integration tests across modules
   - Verify cognitive coherence

4. **Document changes**:
   - Update relevant READMEs
   - Add/update examples
   - Update ARCHITECTURE.md if structural changes

5. **Submit pull request**:
   - Clear description of cognitive function
   - Reference related issues
   - Include test results

## Module-Specific Guidelines

### ASML (asml/)
- Low-level tensor operations
- Hardware abstraction
- Performance-critical code
- Foundation for all other modules

### Learn.Cog (learn.cog/)
- Language model inference
- Learning algorithms
- Cognitive reasoning
- Natural language processing

### Sensation (sensation/)
- Sensory input processing
- Currently: speech-to-text
- Future: vision, touch, etc.
- Multimodal integration

### CI (ci/)
- Build automation
- Testing infrastructure
- Release management
- Quality assurance

### Tools (tools/)
- Developer integrations
- Editor plugins
- Deployment utilities
- Human-AI collaboration tools

## Code Quality

### Standards
- Follow existing code style in each module
- Use meaningful variable names
- Comment complex cognitive logic
- Write self-documenting code when possible

### Testing
- Add tests for all new functionality
- Maintain or improve test coverage
- Test cognitive behavior, not just implementation
- Include edge cases

### Performance
- ORGGML targets resource-constrained deployment
- Profile performance-critical code
- Use quantization where appropriate
- Document performance characteristics

## Integrating ggml-org Code

When integrating code from ggml-org repositories:

1. **Identify cognitive function**: Determine which module it belongs to
2. **Remove .git directories**: No submodules
3. **Update paths**: Adjust include paths for monorepo structure
4. **Preserve licenses**: Keep original license information
5. **Update documentation**: Add to MAPPING.md and module README

## Communication

- **Issues**: Use GitHub issues for bugs, features, and discussions
- **Pull Requests**: Clear, focused PRs with good descriptions
- **Documentation**: When in doubt, document your thinking

## Questions?

If you're unsure about:
- Where code should go → Read ARCHITECTURE.md and ask in an issue
- How to structure a contribution → Look at existing code patterns
- Cognitive mapping → Refer to MAPPING.md or ask for guidance

## License

By contributing, you agree that your contributions will be licensed under the same licenses as the components you're modifying (typically MIT). See individual module directories for specific license information.

## Recognition

Contributors are recognized in commit messages and releases. Thank you for helping build a cognitively-organized AGI framework!
