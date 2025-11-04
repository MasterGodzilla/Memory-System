# Claude Memory System

A three-tier documentation system for organizing project knowledge across AI agent sessions.

## 🚀 Quick Start (2 minutes)

Open Claude Code in your project directory and paste this:

```
Please set up the memory system from https://github.com/MasterGodzilla/Memory-System
by following the MEMORY_SYSTEM_INTEGRATION.md guide
```

Claude Code will fetch the integration guide and handle everything automatically:
- Read your existing CLAUDE.md to understand your project
- Create the memory/ directory structure
- Adapt templates with your project's terminology
- Set up the complete three-tier system
- Optionally discover and migrate scattered .md files into the memory structure

## Overview

This repository provides templates for implementing a memory system that helps Claude agents maintain context and knowledge across multiple sessions. The system is particularly valuable for long-running projects where agents need to understand:

- Core project concepts and conventions
- Design decisions and their rationale
- Active implementation plans
- Bug investigations and debugging workflows

## The Three-Tier System

**Tier 1: CLAUDE.md (Agent Core Memory)**
- Stable, fundamental knowledge ALL future agents need
- Notation, conventions, core implementation principles
- Must remain concise; updated rarely

**Tier 2: memory/ (Agent Working Memory)**
- Detailed design docs, implementation plans, and debugging investigations
- Evolves frequently during active development
- Can be verbose and detailed

```
memory/
├── design/           # Architectural decisions
├── plans/            # Active implementation plans
├── testing/          # Test documentation and rationale
├── debugging/        # Bug investigations
└── archive/
    ├── completed/    # Finished plans
    └── deprecated/   # Outdated designs
```

**Tier 3: Module READMEs (Module-Specific Docs)**
- Architecture and API of a single module
- Usage examples and setup instructions
- Read by both agents and humans

## Files in This Repository

### [CLAUDE_MEMORY_TEMPLATE.md](CLAUDE_MEMORY_TEMPLATE.md)
Template for the memory management section to add to your project's `CLAUDE.md` file. This establishes the three-tier system, explains what content belongs where, and defines update protocols.

### [memory-readme.md](memory-readme.md)
Template for creating `memory/README.md` in your project. This provides:
- Directory structure documentation
- Agent behavior protocols for different situations
- Content criteria for each tier
- Maintenance and archiving guidelines

### [MEMORY_SYSTEM_INTEGRATION.md](MEMORY_SYSTEM_INTEGRATION.md)
Integration plan for Claude Code agents to execute. This is what Claude Code follows when you ask it to set up the memory system.



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

## How It Works

Claude Code reads your existing `CLAUDE.md` to understand your project's structure and terminology, then automatically adapts the memory system templates to match your project's conventions and organization.

## Origin

This system was extracted from a production ML research project where it successfully managed complex agent interactions across months of development, including:
- Multi-module refactorings
- Performance optimization campaigns
- Design decision tracking
- Bug discovery and fix documentation

## Notes
- This system is still in early development. Please report any issues or feedback to the repository.
- We only tested this system with Claude Code using Sonnet 4.5. It may not work with other models.