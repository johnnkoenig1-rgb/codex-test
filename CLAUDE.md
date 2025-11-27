# CLAUDE.md - AI Assistant Guide for codex-test

This document provides comprehensive guidance for AI assistants working with this codebase.

## Repository Overview

**Repository:** johnnkoenig1-rgb/codex-test
**Purpose:** Test repository for development and experimentation
**Current State:** Initial setup phase

## Repository Structure

```
codex-test/
├── .git/                 # Git version control
├── README.md            # Project introduction
└── CLAUDE.md           # This file - AI assistant guide
```

### Current Status
This repository is in its initial state. As the codebase grows, this section will be updated to reflect:
- Source code directories
- Configuration files
- Build/dependency management
- Testing infrastructure
- Documentation structure

## Development Workflow

### Git Branch Strategy

**Critical Branch Naming Convention:**
- Feature branches MUST follow the pattern: `claude/claude-md-{session-id}`
- Example: `claude/claude-md-migz6fxkbkkyvy2u-015HNVVcm8tm8GCMTffQQ1t1`
- Push attempts to branches not matching this pattern will fail with HTTP 403

### Git Operations Best Practices

**Pushing Changes:**
```bash
# Always use the -u flag for new branches
git push -u origin <branch-name>

# Retry logic for network failures (up to 4 times)
# Wait times: 2s, 4s, 8s, 16s between retries
```

**Fetching/Pulling:**
```bash
# Prefer fetching specific branches
git fetch origin <branch-name>

# For pulls
git pull origin <branch-name>

# Apply same retry logic for network failures
```

**Committing:**
- Use clear, descriptive commit messages
- Follow conventional commit format when applicable
- Commit messages should explain "why" not just "what"
- Never skip hooks or use --no-verify unless explicitly requested

### Development Branch Requirements

When working on features:
1. **DEVELOP** all changes on the designated branch
2. **COMMIT** work with clear, descriptive messages
3. **PUSH** to the specified branch when complete
4. **CREATE** the branch locally if it doesn't exist
5. **NEVER** push to different branches without permission

## Code Conventions

### General Principles

**Simplicity Over Complexity:**
- Avoid over-engineering solutions
- Make only changes that are directly requested or clearly necessary
- Keep solutions simple and focused
- Don't add features beyond what was asked

**Code Hygiene:**
- Only modify code that needs changing
- Don't add comments/docstrings to unchanged code
- Remove unused code completely (no backwards-compatibility hacks)
- No unused `_vars`, re-exports, or `// removed` comments

**Security:**
- Watch for OWASP Top 10 vulnerabilities:
  - Command injection
  - XSS (Cross-Site Scripting)
  - SQL injection
  - Insecure authentication
  - Sensitive data exposure
- Validate at system boundaries only (user input, external APIs)
- Trust internal code and framework guarantees

**Error Handling:**
- Add error handling only for scenarios that can actually occur
- Don't create defensive code for impossible conditions
- Keep error messages clear and actionable

### Code Organization

**Abstractions:**
- Don't create helpers/utilities for one-time operations
- Three similar lines of code is better than premature abstraction
- Only abstract when you have 3+ concrete use cases

**Future-Proofing:**
- Don't design for hypothetical future requirements
- No feature flags or backwards-compatibility shims when direct changes work
- Implement exactly what's needed now

## File Operations

**Prefer Existing Files:**
- ALWAYS edit existing files rather than creating new ones
- Only create new files when absolutely necessary
- This includes markdown files and documentation

**Tool Usage:**
- Use specialized tools for file operations:
  - Read tool (not cat/head/tail)
  - Edit tool (not sed/awk)
  - Write tool (not echo/heredoc)
  - Glob tool (not find/ls)
  - Grep tool (not grep/rg commands)

## Testing and Quality

### Pre-Commit Checks
- Respect all pre-commit hooks
- If hooks modify files, verify safe to amend or create new commit
- Never bypass hooks without explicit permission

### Testing Practices
- Run relevant tests before committing
- Fix any failing tests before pushing
- Document test requirements as they are established

## Communication Guidelines

**With Users:**
- Be concise and technical
- Use GitHub-flavored markdown for formatting
- Output text directly (never use bash echo for communication)
- Focus on facts over validation
- Provide objective guidance even when correcting misconceptions

**Code Comments:**
- Only add comments where logic isn't self-evident
- Don't comment on unchanged code
- Keep comments brief and purposeful

## Documentation Standards

**When to Document:**
- Complex algorithms or business logic
- Non-obvious architectural decisions
- External API integrations
- Setup and configuration requirements

**When NOT to Document:**
- Self-explanatory code
- Standard patterns and conventions
- Code that doesn't belong to current changes

## Project-Specific Conventions

### To Be Established

As this codebase develops, document here:
- **Language/Framework:** (e.g., Python, Node.js, React, etc.)
- **Code Style:** (e.g., ESLint, Prettier, Black, etc.)
- **Testing Framework:** (e.g., Jest, pytest, etc.)
- **Build System:** (e.g., webpack, vite, cargo, etc.)
- **Package Manager:** (e.g., npm, pip, cargo, etc.)
- **CI/CD Pipeline:** (e.g., GitHub Actions, CircleCI, etc.)
- **Deployment Process:** (e.g., Docker, Kubernetes, serverless, etc.)

### Directory Structure Guidelines

When the project grows, establish patterns for:
```
src/              # Source code
tests/            # Test files
docs/             # Documentation
config/           # Configuration files
scripts/          # Build and utility scripts
.github/          # GitHub-specific files (workflows, templates)
```

## AI Assistant Responsibilities

### Before Making Changes
1. **Read** relevant files first - never propose changes to unread code
2. **Understand** the existing architecture and patterns
3. **Plan** changes using TodoWrite tool for complex tasks
4. **Verify** you're on the correct branch

### During Development
1. **Track** progress with TodoWrite tool
2. **Commit** logical chunks of work
3. **Test** changes before committing
4. **Document** as you go (when necessary)

### After Changes
1. **Review** all changes for security issues
2. **Verify** tests pass
3. **Commit** with descriptive messages
4. **Push** to the correct branch

### Task Management
- Use TodoWrite tool for tasks with 3+ steps
- Mark tasks as in_progress before starting
- Complete tasks immediately after finishing
- Keep only ONE task in_progress at a time

## GitHub Operations

**GitHub CLI Note:**
- The `gh` CLI may not be available in all environments
- Ask users to provide issue/PR information directly if needed
- Use git commands for all version control operations

## Common Patterns

### Adding a New Feature
1. Check if CLAUDE.md needs updating based on the feature
2. Read relevant existing code
3. Create TodoWrite plan for multi-step features
4. Implement with minimal necessary changes
5. Test thoroughly
6. Commit and push

### Fixing a Bug
1. Read the buggy code
2. Understand the root cause
3. Fix only what's broken
4. Don't refactor surrounding code
5. Test the fix
6. Commit with clear bug description

### Refactoring
1. Only refactor when explicitly requested
2. Maintain existing behavior exactly
3. Move in small, verifiable steps
4. Test after each step
5. Don't add new features during refactoring

## Questions and Support

**For AI Assistants:**
- When uncertain, ask the user for clarification
- Don't make assumptions about requirements
- Verify technical decisions that have multiple valid approaches

**For Users:**
- Use `/help` for assistance with Claude Code
- Report issues at: https://github.com/anthropics/claude-code/issues
- Update this CLAUDE.md as conventions are established

## Maintenance

**This Document:**
- Update when new conventions are established
- Keep in sync with actual project practices
- Remove outdated sections
- Expand project-specific sections as the codebase grows

**Last Updated:** 2025-11-27
**Version:** 1.0.0 (Initial creation)

---

*This is a living document. As the codebase evolves, so should this guide.*
