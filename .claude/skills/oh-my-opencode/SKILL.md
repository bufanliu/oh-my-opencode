---
name: oh-my-opencode-conventions
description: Development conventions and patterns for oh-my-opencode. TypeScript project with conventional commits.
---

# Oh My Opencode Conventions

> Generated from [bufanliu/oh-my-opencode](https://github.com/bufanliu/oh-my-opencode) on 2026-03-20

## Overview

This skill teaches Claude the development patterns and conventions used in oh-my-opencode.

## Tech Stack

- **Primary Language**: TypeScript
- **Architecture**: type-based module organization
- **Test Location**: colocated
- **Test Framework**: jest

## When to Use This Skill

Activate this skill when:
- Making changes to this repository
- Adding new features following established patterns
- Writing tests that match project conventions
- Creating commits with proper message format

## Commit Conventions

Follow these commit message conventions based on 200 analyzed commits.

### Commit Style: Conventional Commits

### Prefixes Used

- `fix`
- `feat`
- `chore`
- `docs`

### Message Guidelines

- Average message length: ~69 characters
- Keep first line concise and descriptive
- Use imperative mood ("Add feature" not "Added feature")


*Commit message example*

```text
feat(hooks/todo-continuation-enforcer): enhance continuation message with skeptical verification guidance
```

*Commit message example*

```text
fix(cli/run): set OPENCODE_CLIENT to 'run' to exclude question tool from registry
```

*Commit message example*

```text
docs(skills/github-triage): fix Phase 1 JSON parsing and large repo handling
```

*Commit message example*

```text
chore: remove console.* debug logging from non-CLI source files
```

*Commit message example*

```text
revert(todo-continuation): remove [TODO-DIAG] console.error debug logging
```

*Commit message example*

```text
@nguyentamdat has signed the CLA in code-yeongyu/oh-my-openagent#2718
```

*Commit message example*

```text
@tonymfer has signed the CLA in code-yeongyu/oh-my-openagent#2701
```

*Commit message example*

```text
@trafgals has signed the CLA in code-yeongyu/oh-my-openagent#2690
```

## Architecture

### Project Structure: Monorepo

This project uses **type-based** module organization.

### Source Layout

```
src/
├── agents/
├── cli/
├── config/
├── features/
├── hooks/
├── mcp/
├── openclaw/
├── plugin-handlers/
├── plugin/
├── shared/
```

### Entry Points

- `src/index.ts`

### Configuration Files

- `.github/workflows/ci.yml`
- `.github/workflows/cla.yml`
- `.github/workflows/lint-workflows.yml`
- `.github/workflows/publish-platform.yml`
- `.github/workflows/publish.yml`
- `.github/workflows/sisyphus-agent.yml`
- `package.json`
- `packages/darwin-arm64/package.json`
- `packages/darwin-x64-baseline/package.json`
- `packages/darwin-x64/package.json`
- `packages/linux-arm64-musl/package.json`
- `packages/linux-arm64/package.json`
- `packages/linux-x64-baseline/package.json`
- `packages/linux-x64-musl-baseline/package.json`
- `packages/linux-x64-musl/package.json`
- `packages/linux-x64/package.json`
- `packages/windows-x64-baseline/package.json`
- `packages/windows-x64/package.json`
- `src/hooks/atlas/tsconfig.json`
- `tests/hashline/package.json`
- `tsconfig.json`

### Guidelines

- Group code by type (components, services, utils)
- Keep related functionality in the same type folder
- Avoid circular dependencies between type folders

## Code Style

### Language: TypeScript

### Naming Conventions

| Element | Convention |
|---------|------------|
| Files | kebab-case |
| Functions | camelCase |
| Classes | PascalCase |
| Constants | SCREAMING_SNAKE_CASE |

### Import Style: Relative Imports

### Export Style: Named Exports


*Preferred import style*

```typescript
// Use relative imports
import { Button } from '../components/Button'
import { useAuth } from './hooks/useAuth'
```

*Preferred export style*

```typescript
// Use named exports
export function calculateTotal() { ... }
export const TAX_RATE = 0.1
export interface Order { ... }
```

## Testing

### Test Framework: jest

### File Pattern: `*.test.ts`

### Test Types

- **Unit tests**: Test individual functions and components in isolation
- **Integration tests**: Test interactions between multiple components/services


*Test file structure*

```typescript
import { describe, it, expect } from 'jest'

describe('MyFunction', () => {
  it('should return expected result', () => {
    const result = myFunction(input)
    expect(result).toBe(expected)
  })
})
```

## Error Handling

### Error Handling Style: Try-Catch Blocks


*Standard error handling pattern*

```typescript
try {
  const result = await riskyOperation()
  return result
} catch (error) {
  console.error('Operation failed:', error)
  throw new Error('User-friendly message')
}
```

## Common Workflows

These workflows were detected from analyzing commit patterns.

### Database Migration

Database schema changes with migration files

**Frequency**: ~2 times per month

**Steps**:
1. Create migration file
2. Update schema definitions
3. Generate/update types

**Files typically involved**:
- `**/schema.*`
- `**/types.ts`
- `migrations/*`

**Example commit sequence**:
```
chore: regenerate JSON schema with circuitBreaker.enabled field
@tad-hq has signed the CLA in code-yeongyu/oh-my-openagent#2655
@ogormans-deptstack has signed the CLA in code-yeongyu/oh-my-openagent#2656
```

### Feature Development

Standard feature implementation workflow

**Frequency**: ~8 times per month

**Steps**:
1. Add feature implementation
2. Add tests for feature
3. Update documentation

**Files typically involved**:
- `src/config/schema/*`
- `src/features/background-agent/*`
- `src/features/builtin-commands/templates/*`
- `**/*.test.*`

**Example commit sequence**:
```
fix(release): add oh-my-openagent dual-publish to platform and main workflows
Merge pull request #2650 from code-yeongyu/fix/openagent-platform-publish
fix(release): set version when publishing oh-my-openagent
```

### Add Or Enhance Hook

Add a new hook or enhance an existing hook, including implementation, tests, and registration.

**Frequency**: ~3 times per month

**Steps**:
1. Create or modify hook implementation files under src/hooks/{hook-name}/
2. Update or add corresponding test files under src/hooks/{hook-name}/
3. Update src/hooks/index.ts to register the hook (for new hooks)
4. Optionally update src/config/schema/hooks.ts or related schema/config files
5. Optionally update plugin hooks or interface files

**Files typically involved**:
- `src/hooks/{hook-name}/index.ts`
- `src/hooks/{hook-name}/*.ts`
- `src/hooks/{hook-name}/*.test.ts`
- `src/hooks/index.ts`
- `src/config/schema/hooks.ts`
- `src/plugin/hooks/*.ts`
- `src/plugin-interface.ts`

**Example commit sequence**:
```
Create or modify hook implementation files under src/hooks/{hook-name}/
Update or add corresponding test files under src/hooks/{hook-name}/
Update src/hooks/index.ts to register the hook (for new hooks)
Optionally update src/config/schema/hooks.ts or related schema/config files
Optionally update plugin hooks or interface files
```

### Feature Or Bugfix With Tests

Implement a feature or bugfix and add/modify corresponding tests.

**Frequency**: ~10 times per month

**Steps**:
1. Modify implementation files (often in src/hooks/, src/features/, src/shared/, etc.)
2. Update or add test files with the same base name and .test.ts extension
3. Commit both implementation and test changes together

**Files typically involved**:
- `src/hooks/**/*.ts`
- `src/hooks/**/*.test.ts`
- `src/features/**/*.ts`
- `src/features/**/*.test.ts`
- `src/shared/**/*.ts`
- `src/shared/**/*.test.ts`

**Example commit sequence**:
```
Modify implementation files (often in src/hooks/, src/features/, src/shared/, etc.)
Update or add test files with the same base name and .test.ts extension
Commit both implementation and test changes together
```

### Documentation Sync Or Update

Update documentation files to reflect code or feature changes, often across multiple related docs.

**Frequency**: ~4 times per month

**Steps**:
1. Edit documentation files (README.md, AGENTS.md, docs/reference/*.md, etc.)
2. Optionally update related config or schema files if documentation references them
3. Commit documentation changes, sometimes with code changes

**Files typically involved**:
- `README.md`
- `AGENTS.md`
- `src/AGENTS.md`
- `src/plugin/AGENTS.md`
- `src/config/AGENTS.md`
- `src/hooks/AGENTS.md`
- `docs/reference/*.md`
- `docs/guide/*.md`

**Example commit sequence**:
```
Edit documentation files (README.md, AGENTS.md, docs/reference/*.md, etc.)
Optionally update related config or schema files if documentation references them
Commit documentation changes, sometimes with code changes
```

### Cli Or Workflow Pipeline Update

Update CI/CD workflow files or CLI scripts, often to fix publishing or build issues.

**Frequency**: ~2 times per month

**Steps**:
1. Edit workflow YAML files under .github/workflows/
2. Edit CLI scripts or related files under src/cli/ or script/
3. Commit changes, sometimes referencing a publishing or build bug

**Files typically involved**:
- `.github/workflows/*.yml`
- `src/cli/**/*.ts`
- `script/*.ts`

**Example commit sequence**:
```
Edit workflow YAML files under .github/workflows/
Edit CLI scripts or related files under src/cli/ or script/
Commit changes, sometimes referencing a publishing or build bug
```

### Background Agent Circuit Breaker Enhancement

Enhance or fix the background agent's circuit breaker and loop detection logic, including config, implementation, and tests.

**Frequency**: ~3 times per month

**Steps**:
1. Edit src/features/background-agent/*.ts implementation files
2. Edit or add corresponding test files (*.test.ts)
3. Edit schema/config files for background tasks
4. Optionally update assets/oh-my-opencode.schema.json

**Files typically involved**:
- `src/features/background-agent/*.ts`
- `src/features/background-agent/*.test.ts`
- `src/config/schema/background-task.ts`
- `assets/oh-my-opencode.schema.json`

**Example commit sequence**:
```
Edit src/features/background-agent/*.ts implementation files
Edit or add corresponding test files (*.test.ts)
Edit schema/config files for background tasks
Optionally update assets/oh-my-opencode.schema.json
```

### Cla Signature Update

Add a new entry to the CLA signatures file when a contributor signs the CLA.

**Frequency**: ~4 times per month

**Steps**:
1. Add or update signatures/cla.json with the new contributor's signature

**Files typically involved**:
- `signatures/cla.json`

**Example commit sequence**:
```
Add or update signatures/cla.json with the new contributor's signature
```


## Best Practices

Based on analysis of the codebase, follow these practices:

### Do

- Use conventional commit format (feat:, fix:, etc.)
- Write tests using jest
- Follow *.test.ts naming pattern
- Use kebab-case for file names
- Prefer named exports

### Don't

- Don't write vague commit messages
- Don't skip tests for new features
- Don't deviate from established patterns without discussion

---

*This skill was auto-generated by [ECC Tools](https://ecc.tools). Review and customize as needed for your team.*
