# Agent Working Memory

> **Note**: This is a template for `memory/README.md` in your project. Replace placeholders like `[Project]`, `[component]`, and `[module]` with your project-specific terms.

---

## Purpose

This directory contains detailed design documents, implementation plans, and benchmarks that agents use as working memory across sessions.

**For stable core knowledge**, see `/CLAUDE.md`.
**For module-specific information**, see module READMEs (e.g., `src/[module]/README.md`).

## Directory Structure

### memory/design/
Design documents and architectural decisions affecting multiple modules.

- **`[doc_name].md`** - [Description of what this design document covers]
- **`[doc_name].md`** - [Description of what this design document covers]

### memory/testing/
Critical tests and testing documentation.

- **`README.md`** - Testing philosophy and critical test overview
- **`[test_doc].md`** - [Description of test documentation]

### memory/benchmarks/
Performance analysis and optimization plans.

- **`[benchmark_doc].md`** - [Description of benchmark results and plans]

### memory/plans/
Active implementation plans spanning multiple modules. Archive when completed.

- **`[plan_name].md`** - [Status]: [Brief description of the plan]

**Note**: [Any notes about exploratory/brainstorming files in this directory]

### memory/archive/
Completed plans, superseded designs, and historical benchmark results.

- `memory/archive/completed/` - Finished implementation plans
  - `[plan_name].md` - [Brief description] ([date], see [relevant docs])
- `memory/archive/deprecated/` - Superseded design documents and implementation notes
  - `[doc_name].md` - [Brief description and why deprecated]
- `memory/archive/old_benchmarks/` - Historical performance results

## Agent Documentation Protocol

### How agents should behave (applies to all locations)

#### Situation 1: User gives clear direction
**Examples:**
- "Add this to memory/design/"
- "Update the benchmark results"
- "Document this in CLAUDE.md"
- Working from existing plans in memory/plans/

**Agent behavior:** Execute directly

#### Situation 2: User implies documentation
**Examples:**
- "Remember that [component] uses [approach]"
- "Keep in mind the [formula] is..."
- "Note that we decided to use [choice] instead of [alternative]"

**Agent behavior:** Present plan with content preview
```
"I'll document this in memory/design/[doc_name].md:
- Add section on [topic]
- Content: [actual content you'll write]
Should I proceed?"
```

#### Situation 3: Agent discovers something worth documenting
**Examples:**
- Found important design pattern while coding
- Completed benchmark with interesting results
- Realized a convention is being used consistently

**Agent behavior:** Present plan with justification
```
"I found that [finding]. I can update memory/[location]/[doc].md with:
- [Content item 1]
- [Content item 2]
- [Content item 3]
Should I make this update?"
```

## Content Criteria (what belongs where)

**Note:** These are content standards, not permission levels. The behavioral protocol above applies regardless of destination.

### CLAUDE.md (Highest content bar)

**Only add when:**
- Information must be known by ALL future agents
- Convention or principle is stable and permanent
- Content is concise and fundamental
- Examples: [Project-specific examples]

**Not for:**
- Detailed explanations (use memory/)
- Module-specific info (use module READMEs)
- Temporary decisions or explorations

### memory/ (Working knowledge)

**Add memory/design/ document when:**
- After finishing design features that affect multiple modules
- After making architectural decisions with project-wide implications
- Documenting design rationale for future agents

**Add memory/benchmarks/ document when:**
- Recording performance analysis results
- Documenting optimization plans and speedup results

**Add memory/plans/ document when:**
- Planning refactoring spanning multiple modules
- Designing complex features requiring multiple steps
- Brainstorming design decisions
- Coordinating changes across codebase

### Module READMEs (Module-specific)

**Use module README (e.g., `src/[module]/README.md`) when:**
- Documenting architecture of a single module
- Explaining module-specific APIs
- Providing usage examples for the module
- Describing module file organization

**Can edit more freely when:**
- Making code changes to that module
- Updating API documentation after refactoring
- Adding usage examples for new features

## Examples

| Information | Correct Location | Reason |
|-------------|------------------|--------|
| "High-level: What is [Project]?" | CLAUDE.md | Core conceptual knowledge |
| "Detailed: [Specifications/formulas]" | memory/design/[topic].md | Cross-cutting system specifications |
| "Why we chose [approach] over [alternative]" | memory/design/ | Design rationale, may evolve |
| "[Component] class API and logic" | src/[module]/README.md | Module-specific architecture |
| "Benchmark shows [results], plan to optimize" | memory/benchmarks/ | Active performance work |
| "How to run [tool] with custom configs" | [component]/README.md | Module-specific usage |
| "Plan to refactor [component]" | memory/plans/ | Active cross-module work |

## Maintenance

### Archive Protocol

**When you complete a plan:**
- Identify design decisions and rationale worth preserving
- Present a proposal to:
  1. Extract design decisions to relevant `memory/design/` document
  2. Move performance findings to `memory/benchmarks/` if applicable
  3. Archive the plan itself to `memory/archive/completed/`
- Note: Plans often contain valuable insights beyond just implementation steps

**When you notice inactive/abandoned plans:**
- Evaluate if plan contains useful design decisions or learnings
- Present a proposal to extract valuable content before archiving
- Archive to `memory/archive/abandoned/` with note about why it was discontinued

**When a design becomes outdated:**
- Identify what superseded it and document the evolution
- Present a proposal to archive with deprecation note
- Check if CLAUDE.md needs updates to reflect new approach

**When benchmarks age:**
- Consider if historical data is useful for trend analysis
- Present a proposal to move to `memory/archive/old_benchmarks/` with date context

### README Maintenance

**After any memory update:**
- Check if `memory/README.md` directory index needs updating
- Update file listings when adding/moving/archiving documents
- Keep the index synchronized with actual directory structure
