# Work Review Rules

When preparing code for review or before pushing to a branch:

## Pre-Push Validation (Mandatory)

1. **Run all checks locally** - Tests, linters, type checking must all pass
2. **Build the whole project** - Ensure complete project builds without errors
3. **Never dismiss warnings** - Fix or explicitly document suppression with reason
4. **Validate integration points** - Test with dependent services/modules

## File Management

- **Include only necessary files** - Source code, tests, documentation
- **Exclude build artifacts** - No dist/, node_modules/, __pycache__, .venv/
- **No personal configs** - No .vscode/, .idea/, or personal settings
- **Update .gitignore** - Ensure artifacts are properly excluded

## Testing Requirements

```
Before requesting review:
[ ] All unit tests pass
[ ] Integration tests pass  
[ ] Project builds successfully
[ ] No linter errors
[ ] Coverage threshold met
[ ] Manual verification done
```

## Tool Warnings

- **Blocking errors** - Must fix: compilation, type errors, failed tests
- **Critical warnings** - Fix or document: linter errors, security issues
- **Advisory warnings** - Address or create tech debt ticket

## Ownership

- **You build it, you test it** - Comprehensive test coverage required
- **You ship it, you support it** - Be ready to fix issues in production
- **Whole project works** - Verify no regressions across the system

## Code Review

- Self-review before requesting review
- Clear PR description with context
- Respond to feedback constructively
- Re-test after addressing comments

## Documentation Quality

- Professional tone and clarity
- No emojis in documentation or code comments
- English language for all documentation
- Self-documenting code preferred over excessive comments

**For detailed methodology:** Use `/work-review` skill
