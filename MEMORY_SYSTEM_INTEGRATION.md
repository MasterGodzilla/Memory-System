# Memory System Integration Plan

This document is an execution plan for coding agents. When a user references this repository and asks to integrate the memory system, follow these phases.

Agent-specific core memory file:
- If you are Claude Code, use `CLAUDE.md`
- If you are Codex, use `AGENTS.md`

## Important Guidelines

1. **Only modify markdown files and create directories** - Do not touch code files, configs, or any non-.md files
2. **Always present plan before write operations** - Show user what you'll create/modify and get approval before writing any files. You don't need to reshow the plan that was already specified in the integration plan.
3. **Respect existing documentation** - When appending to the core memory file, preserve existing content; when merging with existing memory/, keep user's files

## Phase 1: Load Memory System Templates

First, fetch and read the template files to understand what you'll be integrating.

Fetch the memory system templates from the repository (https://github.com/MasterGodzilla/Memory-System):
- Use WebFetch to read:
  - `CLAUDE_MEMORY_TEMPLATE.md` from the repository
  - `memory-readme.md` from the repository

Read both files completely to understand the three-tier documentation system before proceeding to Phase 2.

## Phase 2: Understand Existing Project

Read the project's core memory file to understand the current project's structure, terminology, and conventions.

### Check for Existing Core Memory File

Verify the project has the appropriate core memory file with project context:

```bash
ls CLAUDE.md
# or
ls AGENTS.md
```

**If the appropriate core memory file doesn't exist:**
- If you are Claude Code, stop and tell the user: "This project needs a `CLAUDE.md` file first. Please run `/init` in Claude Code to scan your codebase and create project context. After that, come back and we can integrate the memory system."
- If you are Codex, stop and tell the user: "This project needs an `AGENTS.md` file first. Please create it with the project's core context before integrating the memory system. After that, come back and we can integrate the memory system."

**If the appropriate core memory file exists:**
- Continue to check for existing memory/ directory

### Check for Existing memory/ Directory

```bash
ls -d memory/
```

**If memory/ directory already exists:**
- Analyze the existing structure
- Present a conflict resolution plan to the user with options (merge, rename, use different name, etc.)
- Wait for user approval before proceeding

**If memory/ does not exist:**
- Proceed to Phase 3


## Phase 3: Present Integration Plan

Show the user what you will create. Present this plan:

```
I will integrate the three-tier memory system into [ProjectName]:

1. Create memory/ directory structure:
   - memory/design/          (architectural decisions across modules)
   - memory/plans/           (active multi-step implementation plans)
   - memory/debugging/       (bug investigations and root cause analysis)
   - memory/archive/         (completed and deprecated documents)
     - archive/completed/
     - archive/deprecated/

2. Append memory management section to the core memory file (`CLAUDE.md` or `AGENTS.md`):
   - Three-tier system explanation
   - "What Goes Where" decision table
   - Agent documentation protocols
   (Adapted with your project's terminology)

3. Create memory/README.md:
   - Directory structure guide
   - Agent behavior protocols
   - Content criteria for each tier
   - Archive and maintenance guidelines
   (Adapted with your project's terminology)

Preview of adapted content:
[Show a few key sections with actual project terminology filled in]

Proceed with integration?
```

Wait for user approval before continuing.

## Phase 4: Execute Integration

After user approves:

### 4.1 Create Directory Structure

Execute these commands:

```bash
mkdir -p memory/design
mkdir -p memory/plans
mkdir -p memory/debugging
mkdir -p memory/archive/completed
mkdir -p memory/archive/deprecated
```

### 4.2 Adapt and Append to the Core Memory File

Adapt `CLAUDE_MEMORY_TEMPLATE.md` with project-specific terminology and examples, then append to the end of the project's core memory file (`CLAUDE.md` for Claude Code, `AGENTS.md` for Codex).

### 4.3 Create memory/README.md

Adapt `memory-readme.md` template with project-specific terms and write to `memory/README.md`.

## Phase 5: Validate and Report

Verify the integration:

```bash
ls -la memory/
cat CLAUDE.md | grep -A 5 "Memory Management"
# or
cat AGENTS.md | grep -A 5 "Memory Management"
ls memory/README.md
```

Report to user:

```
✓ Memory system integrated successfully!

Created:
- memory/ directory with design/, plans/, debugging/, archive/
- Memory management section in the core memory file (`CLAUDE.md` or `AGENTS.md`)
- memory/README.md with documentation protocols

The three-tier system is now active:
- Tier 1: core memory file (`CLAUDE.md` or `AGENTS.md`) (core knowledge, rarely updated)
- Tier 2: memory/ (working memory, updated frequently)
- Tier 3: Module READMEs (module-specific docs)

To get started, try:
- "Document this design decision in memory"
- "Create a plan for [feature/refactoring]"
- "What's currently in memory/design/?"
```

Ask user if they want to migrate existing scattered documentation into the memory system. If yes, proceed to Phase 6. If no, integration is complete.

## Phase 6: Discover and Migrate Existing Documentation

Explore the codebase to find scattered .md files that might be memory/documentation created by previous agent sessions.

### Search for candidate files

Look for .md files outside of standard locations (ignore node_modules/, .git/, etc.):
- Design documents
- Plan documents
- Notes or decisions files
- Any files that look like agent-generated memory

### Present Migration Plan

Show the user what you found and present a refactoring plan:

```
Found potential memory documents to migrate:

[List files with brief description of content]

Suggested migration:
- {file1} → memory/design/ (architectural decision)
- {file2} → memory/plans/ (implementation plan)
- {file3} → memory/archive/completed/ (completed work)
- {file4} → keep in place (module-specific, belongs in module README)

Should I proceed with this migration?
```

Wait for user approval, then execute the migration if approved.

After the migration, report to the user the final state of the memory system.
