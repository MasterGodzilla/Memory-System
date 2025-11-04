# Memory System Integration Guide

This guide walks you through integrating the Claude Memory System into your project.

## Overview

The memory system consists of three documentation tiers that work together:
1. **CLAUDE.md** - Core memory that all agents read (add memory section from template)
2. **memory/** directory - Working memory with detailed docs (use template to create structure)
3. **Module READMEs** - Module-specific documentation (already common practice)

## Prerequisites

Before integrating, ensure your project has:
- A `CLAUDE.md` file (or similar agent instruction file)
- A clear project structure with modules/components
- Some form of agent-assisted development workflow

## Step-by-Step Integration

### Step 1: Understand Your Project's Terminology

Identify your project-specific terms to replace template placeholders:

| Placeholder | Example Values | Your Project |
|-------------|----------------|--------------|
| `[Project]` | "GEC", "TaskFlow", "DataPipeline" | __________ |
| `[component]` | "models", "kernels", "services" | __________ |
| `[module]` | "router", "optimizer", "database" | __________ |
| `[notation/formulas/specs]` | "MoE notation", "API specs" | __________ |
| `[test_dir]` | "benchmark", "tests", "specs" | __________ |

### Step 2: Create Memory Directory Structure

In your project root, create:

```bash
mkdir -p memory/design
mkdir -p memory/plans
mkdir -p memory/benchmarks
mkdir -p memory/testing
mkdir -p memory/archive/completed
mkdir -p memory/archive/deprecated
mkdir -p memory/archive/old_benchmarks
```

Optional subdirectories based on your needs:
- `memory/archive/abandoned/` - For discontinued plans
- `memory/experiments/` - For experimental designs
- Any domain-specific categories

### Step 3: Adapt CLAUDE_MEMORY_TEMPLATE.md

1. Open `CLAUDE_MEMORY_TEMPLATE.md` from this repository
2. Replace all placeholders with your project-specific terms:
   - `[Project]` → Your project name
   - `[component]`, `[module]` → Your directory names
   - `[notation/formulas/specs]` → What documentation you need
   - `[test_dir]`, `[method]` → Your testing approach
3. Customize the "What Goes Where?" table with concrete examples from your project
4. Add this adapted section to your project's `CLAUDE.md` file

**Example customization:**
```markdown
# Before (template)
| High-level: What is [Project]? | CLAUDE.md | Core conceptual knowledge |

# After (adapted)
| High-level: What is TaskFlow? | CLAUDE.md | Core conceptual knowledge |
```

### Step 4: Adapt MEMORY_README_TEMPLATE.md

1. Open `MEMORY_README_TEMPLATE.md` from this repository
2. Replace all placeholders with your terms (same as Step 3)
3. In the "Directory Structure" section, list your initial documents:
   - If you have design docs, list them under `memory/design/`
   - If you have active plans, list them under `memory/plans/`
   - If you have benchmarks, list them under `memory/benchmarks/`
4. Customize examples to match your project's actual use cases
5. Save as `memory/README.md` in your project

### Step 5: Migrate Existing Documentation (Optional)

If you already have design docs, move them into the new structure:

**Design documents** → `memory/design/`
- Architecture decisions
- System specifications
- Cross-module rationale

**Plans and TODOs** → `memory/plans/`
- Refactoring plans
- Feature implementations
- Multi-step initiatives

**Performance analysis** → `memory/benchmarks/`
- Benchmark results
- Optimization findings
- Speedup measurements

**Test documentation** → `memory/testing/`
- Critical test rationale
- Bug discoveries
- Test methodology

**Old documents** → `memory/archive/`
- Completed plans → `memory/archive/completed/`
- Superseded designs → `memory/archive/deprecated/`
- Historical benchmarks → `memory/archive/old_benchmarks/`

### Step 6: Initialize With First Documents

Create your first memory documents to establish patterns:

**Example: memory/design/notation.md**
```markdown
# [Project] Notation System

[Document your project's notation, terminology, or key concepts]
```

**Example: memory/testing/README.md**
```markdown
# Testing Strategy

## Critical Tests
- `test_[name].py` - [Why this test is critical]

## Test Philosophy
[Your testing approach]
```

### Step 7: Train Your Agents

Add a note to your project's `CLAUDE.md` that instructs agents:

```markdown
## Memory Management

Whenever user asks you to do anything with memory, you should first check
the CLAUDE.md and memory/README.md to understand how memory is organized.
```

This is already included in the CLAUDE_MEMORY_TEMPLATE.md, so if you completed Step 3, you're done!

### Step 8: Start Using the System

Begin using the three-tier system:
- **New core conventions** → Add to CLAUDE.md (sparingly)
- **Design decisions** → Document in memory/design/
- **Active work** → Track in memory/plans/
- **Module changes** → Update module READMEs

## Customization Checklist

Use this checklist to ensure you've adapted everything:

- [ ] Created `memory/` directory structure
- [ ] Replaced all `[Project]` placeholders with project name
- [ ] Replaced all `[component]`/`[module]` placeholders with actual directory names
- [ ] Replaced all `[notation/formulas/specs]` placeholders with relevant concepts
- [ ] Customized "What Goes Where?" table with project-specific examples
- [ ] Listed initial documents in memory/README.md directory structure
- [ ] Added memory management section to CLAUDE.md
- [ ] Migrated existing docs to appropriate memory/ subdirectories (if any)
- [ ] Created at least one initial document in memory/design/ or memory/testing/
- [ ] Updated examples in memory/README.md to match your project's domain

## Validation

After integration, test that agents understand the system:

**Test 1: Ask about memory structure**
```
User: "Where should I document the API design decision?"
Expected: Agent references memory/design/ and explains why
```

**Test 2: Implied documentation**
```
User: "Remember that we use approach X for feature Y"
Expected: Agent offers to document in memory/design/ with content preview
```

**Test 3: Discovery**
```
User: [Agent completes a benchmark]
Expected: Agent offers to update memory/benchmarks/ with results
```

## Common Customizations

### For ML/AI Projects
- Add `memory/experiments/` for experimental architectures
- Add `memory/results/` for training run analysis
- Include model architecture under `src/models/README.md`

### For Backend Services
- Add `memory/api/` for API design decisions
- Add `memory/migrations/` for database migration rationale
- Document service architecture in `memory/design/architecture.md`

### For Frontend Projects
- Add `memory/ux/` for UX design decisions
- Add `memory/components/` for component library design
- Document state management in `memory/design/state.md`

### For Research Projects
- Add `memory/papers/` for paper summaries and related work
- Add `memory/hypotheses/` for experimental hypotheses
- Document methodology in `memory/design/methodology.md`

## Maintenance

### Weekly
- Review memory/plans/ for completed items → archive
- Update memory/README.md if new docs were added

### Monthly
- Review memory/design/ for outdated content → archive deprecated designs
- Review memory/archive/completed/ for extractable patterns → update design docs

### Quarterly
- Audit CLAUDE.md for content that could move to memory/
- Review entire memory/ structure for reorganization opportunities

## Troubleshooting

**Problem**: Agent ignores memory system
**Solution**: Ensure CLAUDE.md includes the memory management section and references memory/README.md

**Problem**: Agent over-documents trivial details
**Solution**: Strengthen the "Content Criteria" section in memory/README.md with project-specific examples

**Problem**: Memory documents become stale
**Solution**: Set up regular archive reviews and add dates to document headers

**Problem**: Directory structure feels wrong
**Solution**: Customize subdirectories based on your project's needs - the template is a starting point

## Getting Help

- Review the original templates for clarification on design decisions
- Check the main README.md for system overview
- Adapt the system to your needs - it's a template, not a rigid framework

## Next Steps

After integration:
1. Create your first design document
2. Start a plan for your next feature
3. Document a critical test
4. Let agents work with the system and refine based on their usage

The system improves as you use it - don't aim for perfection on day one!
