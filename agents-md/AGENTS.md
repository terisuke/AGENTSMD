# AGENTS.md - Project Contributor Guide

Welcome to this project repository. This file contains the main points for new contributors and AI assistants.

## Repository overview
- **Source code**: `src/` contains the main implementation.
- **Tests**: `tests/` with testing guidelines and examples.
- **Examples**: `examples/` directory for usage demonstrations.
- **Documentation**: markdown files in `docs/` with configuration files.
- **Configuration**: `config/` for environment and build settings.
- **Scripts**: `scripts/` for build, deployment, and utility commands.
- **PR template**: `.github/PULL_REQUEST_TEMPLATE/` contains the required PR format.

## Local workflow
1. Format, lint and type-check your changes:
   ```bash
   npm run format     # or: black . / ruff format .
   npm run lint       # or: flake8 . / ruff check .
   npm run typecheck  # or: mypy . / tsc --noEmit
   ```

2. Run the tests:
   ```bash
   npm test          # or: pytest / go test ./...
   ```
   To run a single test, use `npm test -- --grep "<test_name>"` or `pytest -k <test_name>`.

3. Build the project (optional but recommended):
   ```bash
   npm run build     # or: python setup.py build / go build
   ```
   Generate test coverage with `npm run coverage` or `pytest --cov`.

## Testing guidelines
Tests should cover new functionality and edge cases. See `tests/README.md` for detailed guidelines:
```bash
npm run test:unit       # run unit tests
npm run test:integration # run integration tests
npm test:e2e           # run end-to-end tests
```
Maintain minimum 80% test coverage for new code.

## Style notes
- Write comments as full sentences and end them with a period.
- Use meaningful variable and function names.
- Follow the established naming conventions for the language.
- Keep functions small and focused on a single responsibility.
- Include type hints/annotations where applicable.

## Commit message format
Use conventional commit format:
```
type(scope): description

Examples:
feat(auth): add user authentication system
fix(api): resolve null pointer exception in user service
docs(readme): update installation instructions
test(utils): add unit tests for helper functions
```

## Pull request expectations
PRs should use the template in `.github/PULL_REQUEST_TEMPLATE/`. Include:
- **Summary**: Clear description of changes and motivation
- **Test plan**: How to verify the changes work correctly
- **Issue reference**: Link to related issues if applicable

Before submitting, ensure:
- [ ] New tests are added for new functionality
- [ ] Documentation is updated for public API changes
- [ ] All formatting and linting checks pass
- [ ] Full test suite passes locally
- [ ] Commit messages follow the conventional format

## What reviewers look for
- **Test coverage**: Comprehensive tests for new behavior and edge cases.
- **Code quality**: Consistent formatting, proper error handling, and clear logic.
- **Documentation**: Updated docs for any public API or behavior changes.
- **Security**: Input validation, proper authentication, and secure data handling.
- **Performance**: Efficient algorithms and appropriate data structures.
- **Maintainability**: Clean, readable code with appropriate abstractions.

## Architecture guidelines
- Follow the layered architecture pattern established in the codebase.
- Maintain separation of concerns between different modules.
- Use dependency injection where appropriate.
- Prefer composition over inheritance.
- Keep external dependencies minimal and well-justified.

## Security considerations
- Validate all user inputs at entry points.
- Use parameterized queries to prevent SQL injection.
- Implement proper authentication and authorization.
- Never commit secrets or sensitive data to version control.
- Follow secure coding practices for the target language/framework.

## Performance guidelines
- Profile code for performance-critical sections.
- Use appropriate data structures for the use case.
- Implement caching strategies where beneficial.
- Optimize database queries and minimize N+1 problems.
- Consider memory usage and potential leaks.
