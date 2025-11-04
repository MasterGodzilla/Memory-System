# Memory Management Section

> **Note**: This is a template to add to your project's `CLAUDE.md` file. Replace placeholders like `[Project]`, `[component]`, and `[module]` with your project-specific terms.

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
- Detailed design docs, implementation plans, benchmarks
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
| High-level: What is [Project]? | CLAUDE.md | Core conceptual knowledge |
| Detailed [notation/formulas/specs] | `memory/design/[topic].md` | Cross-cutting system specifications |
| [Component] implementation details | `src/[component]/README.md` | Module-specific architecture |
| [Design decision] rationale | `memory/design/` | Cross-module design decision |
| [Critical concept] design | `memory/design/[concept].md` | Cross-module design decision |
| Benchmark results | `memory/benchmarks/` | Working analysis |
| "How to run [tools/tests]" | `[component]/README.md` | Module-specific usage |
| [Component] performance tests | `[test_dir]/` | Testing via [method] |
| Integration/system tests | `test/` | Non-[component] testing |
| Critical test documentation | `memory/testing/` | Test rationale and bug history |
| Refactoring plans | `memory/plans/` | Active cross-module work |
| [Component] API | `src/[component]/README.md` | Module-specific API |

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
- Benchmarks and performance analysis
- Implementation plans (extract design decisions before archiving)
- See `memory/README.md` for detailed guidelines

**Module READMEs** - Module-specific:
- Architecture and APIs of that module
- Usage examples and setup instructions
- Can edit more freely when updating that module

**Archive protocol:**
- Extract design decisions from plans → `memory/design/`
- Completed plans → `memory/archive/completed/`
- Superseded designs → `memory/archive/deprecated/`
- Old benchmarks → `memory/archive/old_benchmarks/`
