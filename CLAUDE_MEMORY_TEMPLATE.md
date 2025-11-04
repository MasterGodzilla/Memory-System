# Memory Management Section

> **Note**: This is a template to add to your project's `CLAUDE.md` file. 

---

## Memory Management

Whenever user asks you to do anything with memory, you should first check the CLAUDE.md and memory/README.md to understand how memory is organized.

### Three-Tier System

**CLAUDE.md (Agent Core Memory)**
- Stable, fundamental knowledge ALL future agents need
- Notation, conventions, core implementation principles
- Must remain concise; updated rarely
- Location: `/CLAUDE.md`

**memory/ (Agent Working Memory)**
- Detailed design docs, implementation plans, and debugging investigations
- Evolves frequently during active development
- Can be verbose and detailed
- Location: `/memory/` (see memory/README.md for index)

**Module READMEs (Module-Specific Docs)**
- Architecture and API of a single module
- Usage examples and setup instructions
- Read by both agents and humans
- Location: Scattered (e.g., `src/[module]/README.md`, `[component]/README.md`)

### What Goes Where?

| Information Type | Location | Why |
|-----------------|----------|-----|
| High-level: What is this project? | CLAUDE.md | Core conceptual knowledge |
| Detailed notation/formulas/specifications | `memory/design/{topic}.md` | Cross-cutting system specifications |
| Component implementation details | `src/{component}/README.md` | Module-specific architecture |
| Design decision rationale | `memory/design/` | Cross-module design decision |
| Critical concept design | `memory/design/{concept}.md` | Cross-module design decision |
| How to run tools/tests | `{component}/README.md` | Module-specific usage |
| Component performance tests | Test directories | Component-specific testing |
| Integration/system tests | `test/` | System-level testing |
| Critical test documentation | `memory/testing/` | Test rationale and bug history |
| Bug investigation and root cause analysis | `memory/debugging/` | Cross-module debugging sessions |
| Refactoring plans | `memory/plans/` | Active cross-module work |
| Component API | `src/{component}/README.md` | Module-specific API |

### Update Protocol

**Agent behavior (see `memory/README.md` for details):**
- Explicit requests → Execute directly
- Implied documentation → Present plan with content preview
- Agent discoveries → Present plan with justification

**CLAUDE.md** - Highest content bar:
- Only for knowledge ALL future agents must know
- Stable conventions and permanent principles
- Must be concise and fundamental

**memory/** - Working knowledge:
- Cross-module designs and rationale
- Implementation plans (extract design decisions before archiving)
- Debugging investigations and root cause analysis
- See `memory/README.md` for detailed guidelines

**Module READMEs** - Module-specific:
- Architecture and APIs of that module
- Usage examples and setup instructions
- Can edit more freely when updating that module

**Archive protocol:**
- Extract design decisions from plans → `memory/design/`
- Completed plans → `memory/archive/completed/`
- Superseded designs → `memory/archive/deprecated/`
