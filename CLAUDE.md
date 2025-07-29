# CLAUDE.md - User Memory and Working Principles

## Core Development Principles

### 1. Version Control Best Practices
- **Always create commits after completing each step or todo list item**
- Commit messages should be clear and descriptive
- Small, atomic commits are preferred over large, monolithic ones

### 2. Code Formatting Standards
- **Always use proper line break '\' symbol for longer bash commands**
- Example:
  ```bash
  docker build \
    --build-arg VERSION=1.0.0 \
    --tag myapp:latest \
    --file Dockerfile .
  ```

### 3. Codebase Analysis and Documentation
- **Always create project diagrams of each component when analyzing a codebase**
- Use tools like Mermaid or ASCII diagrams to visualize architecture
- Create visual representations of:
  - System architecture
  - Data flow
  - Component relationships
  - API structure

### 4. File Documentation Standards
- **Create a detailed breakdown markdown overview of the purpose of each component/file**
- **Add this summary on top of each file as formatted long comments**
- Example for Python:
  ```python
  """
  Module: user_authentication.py
  Purpose: Handles user authentication and session management
  
  Components:
  - authenticate_user(): Validates user credentials
  - create_session(): Generates secure session tokens
  - validate_token(): Verifies JWT tokens
  
  Dependencies:
  - jwt: For token generation
  - bcrypt: For password hashing
  """
  ```

### 5. Documentation Maintenance
- **Every time the codebase is updated, always remember to update relevant information**
- Keep documentation in sync with code changes
- Update:
  - README files
  - API documentation
  - Component overviews
  - Dependency lists

### 6. File Organization Standards
- **Manage documents in a dedicated docs/ directory**
- **Put adhoc documents in a docs/temp/ directory**
- **For other adhoc files, put them in a temp/ folder**
- Directory structure:
  ```
  project/
  ├── docs/
  │   ├── architecture/
  │   ├── api/
  │   ├── guides/
  │   └── temp/         # Temporary documentation
  ├── temp/             # Temporary files
  └── src/
  ```

### 7. Software Design Principles
- **Always create maintainable, readable, modular codebase design**
- **Design for extensibility and future expansion**
- **Maximize code reuse through:**
  - DRY (Don't Repeat Yourself) principle
  - Creating reusable functions and modules
  - Abstracting common patterns
  - Using composition over inheritance
- **Make only the necessary changes**
  - Focus on the specific task at hand
  - Avoid scope creep
  - Do not over-reach beyond the assigned task
- **Modular Design Guidelines:**
  - Single Responsibility Principle (SRP)
  - Loose coupling between modules
  - High cohesion within modules
  - Clear interfaces and contracts
  - Dependency injection where appropriate

## AI Agent-Specific Principles

### 8. Context Management
- Always use `Grep` and `Glob` tools before making changes to understand existing patterns
- Read related files in parallel to build comprehensive context
- Check imports and dependencies before adding new ones
- Verify file exists before attempting edits

### 9. Tool Usage Optimization
- Batch multiple read operations in single messages for efficiency
- Use `Task` tool for complex searches instead of multiple sequential operations
- Prefer `MultiEdit` over multiple `Edit` calls for the same file
- Check `package.json`, `requirements.txt`, etc. before assuming libraries exist

### 10. Code Generation Discipline
- Mirror existing code style exactly (spacing, naming, patterns)
- Never add comments unless explicitly requested
- Generate minimal code that solves the specific problem
- Always preserve existing functionality when refactoring

### 11. Change Management
- Run lint/type-check commands after every code change
- Commit after each completed todo item (with descriptive messages)
- Update relevant documentation immediately after code changes
- Never commit unless explicitly asked by user

### 12. Error Prevention
- Always check if commands exist before running (`which <command>`)
- Verify paths are absolute when required by tools
- Test for file existence before operations
- Use proper escaping for bash commands

### 13. Search Strategy
- Start broad with `Glob`, then narrow with `Grep`
- Search for multiple related terms in parallel
- Look for usage examples before implementing new patterns
- Check test files to understand expected behavior

### 14. Communication Efficiency
- Keep responses under 4 lines unless detail requested
- Show file paths with line numbers (file.py:42)
- State actions concisely without explanation
- Let code changes speak for themselves

### 15. Project Awareness
- Always check README and CLAUDE.md first
- Respect .gitignore patterns
- Follow existing directory structure
- Maintain consistent import patterns

### 16. Safe Operations
- Never delete without explicit instruction
- Preserve all existing functionality
- Make backups mentally before large refactors
- Validate file operations before executing

### 17. Learning from Codebase
- Identify and reuse existing utility functions
- Follow established error handling patterns
- Use same testing framework and patterns
- Respect existing architectural decisions

## macOS Development Environment

### 18. File System Awareness
- Understand case-insensitive but case-preserving filesystem (APFS/HFS+)
- Be aware of `.DS_Store` files (add to .gitignore)
- Use `/usr/bin/open` to open files/URLs when needed
- Respect macOS hidden files (starting with .)

### 19. Command Differences
- Use `pbcopy`/`pbpaste` for clipboard operations
- `sed -i ''` requires empty string for in-place editing on macOS
- Use `brew list` to check installed packages
- Prefer `ggrep` (GNU grep) when available over BSD grep

### 20. Development Tools
- Check for tools in `/opt/homebrew/bin` (Apple Silicon) or `/usr/local/bin` (Intel)
- Use `xcrun` for Xcode command line tools
- Be aware of Python versions: system Python vs brew Python
- Handle both `python3` and `python` commands appropriately

### 21. Path Considerations
- Include Homebrew paths in tool checks
- Handle spaces in paths (common in macOS: `/Users/name/My Documents/`)
- Use `~/Library/` for app-specific data
- Respect macOS security (may need permissions for certain directories)

### 22. Process Management
- Use `launchctl` for service management instead of systemd
- `ps aux` for process listing (BSD style)
- Activity Monitor equivalent: `top` or `htop`

## General Development Principles

### 23. Error Handling & Resilience
- Always implement proper error handling with meaningful error messages
- Use early returns and guard clauses
- Log errors with appropriate context for debugging
- Implement retry mechanisms for transient failures
- Never expose sensitive information in error messages

### 24. Testing Philosophy
- Write tests first when fixing bugs (regression tests)
- Aim for meaningful test coverage, not just high percentages
- Test edge cases and error conditions
- Keep tests simple, readable, and maintainable
- Use descriptive test names that explain what and why

### 25. Security First
- Never commit secrets, keys, or credentials
- Validate all inputs (API, user, file)
- Use parameterized queries for databases
- Follow principle of least privilege
- Keep dependencies updated for security patches

### 26. Performance Awareness
- Optimize only when necessary (profile first)
- Consider algorithmic complexity (O notation)
- Use appropriate data structures
- Implement caching strategically
- Monitor resource usage (memory, CPU, network)

### 27. API Design Principles
- Use consistent naming conventions
- Version APIs appropriately
- Return meaningful HTTP status codes
- Implement proper pagination for large datasets
- Document all endpoints with examples

### 28. Dependency Management
- Minimize external dependencies
- Pin versions for reproducibility
- Regularly audit and update dependencies
- Document why each dependency is needed
- Consider the maintenance burden of each dependency

### 29. Observability & Debugging
- Add meaningful log statements at key points
- Use structured logging formats
- Implement health checks and monitoring
- Include correlation IDs for request tracing
- Make systems debuggable in production

### 30. Database Best Practices
- Use migrations for schema changes
- Never modify production data directly
- Implement proper indexing strategies
- Use transactions for data consistency
- Regular backups and restore testing

### 31. Continuous Improvement
- Regular refactoring of problematic areas
- Technical debt tracking and management
- Post-mortem analysis for incidents
- Knowledge sharing through documentation
- Automate repetitive tasks

## Additional Guidelines

### Documentation Structure
- Keep documentation close to the code it describes
- Use consistent formatting across all documentation
- Include examples whenever possible

### Commit Workflow
1. Complete a task or todo item
2. Review changes
3. Create descriptive commit
4. Push to repository

### Code Review Checklist
- [ ] Code is properly documented
- [ ] Long commands use line breaks
- [ ] Architecture diagrams are updated
- [ ] File headers include purpose overview
- [ ] Documentation reflects current state
- [ ] Files are in appropriate directories
- [ ] Code is modular and reusable
- [ ] Changes are minimal and focused
- [ ] Design allows for future extension
- [ ] No unnecessary complexity added
- [ ] Error handling is implemented properly
- [ ] Tests cover the changes made
- [ ] Security best practices followed
- [ ] Performance impact considered
- [ ] Dependencies properly managed