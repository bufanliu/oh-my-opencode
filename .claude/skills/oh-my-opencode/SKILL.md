# oh-my-opencode Development Patterns

> Auto-generated skill from repository analysis

## Overview

oh-my-opencode is a TypeScript-based tool that appears to be a code analysis and development assistant platform. The codebase follows consistent patterns for fixing implementation bugs, managing CI/CD workflows, handling model configurations, and maintaining various plugin handlers. The project emphasizes test-driven development with comprehensive Jest testing and follows semantic commit conventions.

## Coding Conventions

### File Naming
- Use **kebab-case** for all files: `config-handler.ts`, `model-requirements.ts`, `ralph-loop.test.ts`

### Import/Export Style
```typescript
// Use relative imports
import { ConfigHandler } from './config-handler';
import { ModelProvider } from '../shared/model-provider';

// Use named exports
export { ConfigManager };
export const defaultConfig = {};
```

### Commit Messages
- Follow semantic commit format: `type: description`
- Common prefixes: `fix:`, `feat:`, `refactor:`
- Keep messages around 69 characters
- Examples:
  ```
  fix: resolve ralph-loop completion detection issue
  feat: add new model provider configuration
  refactor: improve config handler error handling
  ```

## Workflows

### Fix with Tests
**Trigger:** When fixing bugs or issues in existing features
**Command:** `/fix-with-tests`

1. Identify the bug in the main implementation file
2. Create or modify the corresponding test file to reproduce the issue
3. Fix the implementation in the source file
4. Verify the test passes and covers the fix
5. Run the full test suite to ensure no regressions

```typescript
// Example test structure
describe('ConfigHandler', () => {
  it('should handle missing config gracefully', () => {
    const handler = new ConfigHandler();
    expect(() => handler.load()).not.toThrow();
  });
});
```

### CLA Signature Management
**Trigger:** When a new contributor signs the CLA in a pull request
**Command:** `/sign-cla`

1. Contributor submits pull request and signs CLA
2. Update `signatures/cla.json` with contributor information
3. Include contributor name, email, and timestamp
4. Commit changes with message: `feat: add CLA signature for [contributor]`

### CI Workflow Fixes
**Trigger:** When CI builds fail or need improvements
**Command:** `/fix-ci`

1. Identify the failing CI step or configuration issue
2. Modify the appropriate GitHub workflow YAML file in `.github/workflows/`
3. Test the workflow changes locally if possible
4. Commit with descriptive message about the CI fix
5. Monitor the next CI run to verify the fix

### Ralph Loop Maintenance
**Trigger:** When ralph-loop has bugs or needs feature updates
**Command:** `/fix-ralph-loop`

1. Update completion detection logic in `src/hooks/ralph-loop/`
2. Modify loop state management components
3. Update event handlers and their configurations
4. Adjust storage mechanisms and TypeScript types
5. Add or update corresponding test files
6. Ensure all ralph-loop tests pass

```typescript
// Example ralph-loop pattern
export const useRalphLoop = (config: LoopConfig) => {
  const [state, setState] = useState(LoopState.IDLE);
  
  const handleCompletion = useCallback(() => {
    setState(LoopState.COMPLETED);
  }, []);
};
```

### Model Configuration Updates
**Trigger:** When model providers change or new models are added
**Command:** `/update-models`

1. Update model requirements in `src/shared/model-*.ts` files
2. Modify provider configurations and API settings
3. Update test snapshots in `src/**/__snapshots__/*.snap`
4. Adjust fallback logic for model failures
5. Update agent configurations to use new models
6. Run tests and update snapshots as needed

### Pull Request Merging
**Trigger:** When a pull request is ready to be merged
**Command:** `/merge-pr`

1. Review all PR changes and ensure they meet coding standards
2. Verify all CI checks pass
3. Confirm tests are adequate and passing
4. Merge the pull request using appropriate merge strategy
5. Update any affected documentation or configuration files

### Platform Binary Management
**Trigger:** When releasing new versions or adding platform support
**Command:** `/update-platforms`

1. Update the main `package.json` with new version
2. Update all platform-specific `packages/*/package.json` files
3. Modify CI workflows to handle new platforms or versions
4. Update platform detection logic in `bin/*.js` files
5. Test binary generation for all supported platforms

### Configuration Handler Fixes
**Trigger:** When configuration management has issues or needs improvements
**Command:** `/fix-config`

1. Identify the specific configuration issue
2. Update config handler logic in `src/plugin-handlers/config-handler*.ts`
3. Modify CLI config manager files in `src/cli/config-manager/`
4. Add or update tests to cover the configuration scenarios
5. Ensure existing user configurations are preserved during updates

```typescript
// Example config handler pattern
export class ConfigHandler {
  async load(): Promise<Config> {
    try {
      const config = await this.readConfig();
      return this.validateConfig(config);
    } catch (error) {
      return this.getDefaultConfig();
    }
  }
}
```

## Testing Patterns

### Test File Structure
- Test files follow pattern: `*.test.ts`
- Place test files alongside source files
- Use Jest framework with comprehensive coverage

```typescript
describe('ComponentName', () => {
  beforeEach(() => {
    // Setup
  });

  it('should handle expected behavior', () => {
    // Arrange
    const input = {};
    
    // Act
    const result = someFunction(input);
    
    // Assert
    expect(result).toBeDefined();
  });
});
```

### Snapshot Testing
- Update snapshots when model configurations change
- Use snapshots for complex configuration objects
- Review snapshot changes carefully during PR reviews

## Commands

| Command | Purpose |
|---------|---------|
| `/fix-with-tests` | Fix bugs by updating implementation and corresponding tests |
| `/sign-cla` | Add contributor license agreement signature |
| `/fix-ci` | Resolve CI/CD pipeline issues |
| `/fix-ralph-loop` | Maintain ralph-loop hook functionality |
| `/update-models` | Update model configurations and providers |
| `/merge-pr` | Merge ready pull requests |
| `/update-platforms` | Manage platform-specific binaries and versions |
| `/fix-config` | Fix configuration handling issues |