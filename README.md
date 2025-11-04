# Claude Memory System

A three-tier documentation system for organizing project knowledge across AI agent sessions.

## Overview

This repository provides templates for implementing a memory system that helps Claude agents maintain context and knowledge across multiple sessions. The system is particularly valuable for long-running projects where agents need to understand:

- Core project concepts and conventions
- Design decisions and their rationale
- Active implementation plans
- Performance characteristics and benchmarks

## The Three-Tier System

**Tier 1: CLAUDE.md (Agent Core Memory)**
- Stable, fundamental knowledge ALL future agents need
- Notation, conventions, core implementation principles
- Must remain concise; updated rarely

**Tier 2: memory/ (Agent Working Memory)**
- Detailed design docs, implementation plans, benchmarks
- Evolves frequently during active development
- Can be verbose and detailed

**Tier 3: Module READMEs (Module-Specific Docs)**
- Architecture and API of a single module
- Usage examples and setup instructions
- Read by both agents and humans

## Files in This Repository

### [CLAUDE_MEMORY_TEMPLATE.md](CLAUDE_MEMORY_TEMPLATE.md)
Template for the memory management section to add to your project's `CLAUDE.md` file. This establishes the three-tier system, explains what content belongs where, and defines update protocols.

### [MEMORY_README_TEMPLATE.md](MEMORY_README_TEMPLATE.md)
Template for creating `memory/README.md` in your project. This provides:
- Directory structure documentation
- Agent behavior protocols for different situations
- Content criteria for each tier
- Maintenance and archiving guidelines

### [MEMORY_SYSTEM_INTEGRATION.md](MEMORY_SYSTEM_INTEGRATION.md)
Step-by-step guide for integrating the memory system into your project. Read this first if you're adopting the system.

## Quick Start

1. Read [MEMORY_SYSTEM_INTEGRATION.md](MEMORY_SYSTEM_INTEGRATION.md) for integration instructions
2. Adapt [CLAUDE_MEMORY_TEMPLATE.md](CLAUDE_MEMORY_TEMPLATE.md) to your project and add to your `CLAUDE.md`
3. Create a `memory/` directory in your project root
4. Adapt [MEMORY_README_TEMPLATE.md](MEMORY_README_TEMPLATE.md) and save as `memory/README.md`
5. Create subdirectories: `memory/design/`, `memory/plans/`, `memory/benchmarks/`, `memory/testing/`, `memory/archive/`

## Why Use This System?

### For Projects
- **Consistency**: Agents follow established conventions across sessions
- **Knowledge preservation**: Design rationale isn't lost when implementation is complete
- **Reduced context**: Agents can reference memory docs instead of re-reading entire codebase
- **Better decisions**: Historical context helps avoid repeating past mistakes

### For Agents
- **Clear boundaries**: Know what information goes where
- **Explicit protocols**: Understand when to document vs. when to ask
- **Structured exploration**: Navigate project knowledge systematically
- **Reduced hallucination**: Reference concrete documentation instead of guessing

## Customization

The templates use placeholders like `[Project]`, `[component]`, and `[module]` that you should replace with your project-specific terms. See [MEMORY_SYSTEM_INTEGRATION.md](MEMORY_SYSTEM_INTEGRATION.md) for detailed customization instructions.

## Origin

This system was extracted from a production ML research project where it successfully managed complex agent interactions across months of development, including:
- Multi-module refactorings
- Performance optimization campaigns
- Design decision tracking
- Bug discovery and fix documentation

## License

MIT License - feel free to adapt this system to your needs.
