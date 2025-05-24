# AGENTS.md - Python Project Contributor Guide

Welcome to this Python project repository. This file contains the main points for new contributors and AI assistants working with Python/Flask projects.

## Repository overview
- **Source code**: `src/your_package_name/` contains the main implementation.
- **Tests**: `tests/` with unit, integration, and fixture directories.
- **Migrations**: `migrations/` for database schema changes.
- **Documentation**: API documentation and setup guides.
- **Configuration**: `pyproject.toml`, `requirements.txt` for dependencies.
- **Environment**: `.env.example` template for environment variables.

## Local workflow
1. Set up environment and install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   pip install -e .          # Install in development mode
   ```

2. Format, lint and type-check your changes:
   ```bash
   black .                   # Format code
   isort .                   # Sort imports
   flake8 .                  # Lint code
   mypy src/                 # Type checking
   ```

3. Run the tests:
   ```bash
   pytest                    # Run all tests
   pytest --cov=src         # With coverage
   pytest -k test_name      # Run specific test
   ```

4. Run the application:
   ```bash
   flask run                 # Development server
   flask db migrate          # Create migration
   flask db upgrade          # Apply migration
   ```

## Testing guidelines
Maintain 90% test coverage for new code. Use pytest with these tools:
```bash
pytest -v                   # Verbose output
pytest -x                   # Stop on first failure
pytest --cov=src --cov-report=html  # Generate HTML coverage report
```
- Test all public API methods
- Use factory_boy for test data generation
- Mock external dependencies appropriately
- Include edge cases and error scenarios

## Style notes
- Follow PEP 8 and use Black formatter with 88-character line limit.
- Use type hints for all function parameters and return values.
- Write docstrings in Google style for all public functions and classes.
- Prefer `Optional[Type]` over `Type | None` for compatibility.
- Use snake_case for functions/variables, PascalCase for classes, UPPER_SNAKE_CASE for constants.

## Commit message format
Use conventional commit format:
```
type(scope): description

Examples:
feat(auth): implement JWT authentication system
fix(models): resolve user relationship cascade issue
refactor(services): optimize database query performance
test(auth): add comprehensive login flow tests
docs(api): update endpoint documentation
```

## Pull request expectations
PRs should include:
- **Summary**: Clear description of changes and motivation
- **Database changes**: Note any migration files or schema changes
- **Breaking changes**: Document any API or configuration changes
- **Test plan**: How to verify the changes work correctly

Before submitting, ensure:
- [ ] All tests pass (`pytest`)
- [ ] Type checking passes (`mypy src/`)
- [ ] Code is formatted (`black .` and `isort .`)
- [ ] Database migrations are included if needed
- [ ] Documentation is updated for public API changes
- [ ] Environment variables are documented in `.env.example`

## What reviewers look for
- **Test coverage**: Comprehensive tests for business logic and edge cases.
- **Type safety**: Proper type hints and mypy compliance.
- **Database design**: Efficient queries, proper relationships, and migration safety.
- **Security**: Input validation, SQL injection prevention, and secure password handling.
- **Error handling**: Proper exception handling and user-friendly error messages.
- **Flask patterns**: Proper use of Blueprints, Application Factory pattern, and middleware.

## Architecture guidelines
- Use Flask Application Factory pattern for app initialization.
- Organize code with Blueprints for feature separation.
- Implement Repository pattern for data access abstraction.
- Use Service layer for business logic separation.
- Apply dependency injection where appropriate.

## Database best practices (SQLAlchemy)
- Define models in `models/` directory with proper relationships.
- Use database migrations for all schema changes.
- Implement proper indexing for performance optimization.
- Handle transactions appropriately with context managers.
- Avoid N+1 query problems with eager loading.

## Security considerations
- Use Flask-Login for user session management.
- Implement CSRF protection for forms.
- Hash passwords with bcrypt or similar strong algorithms.
- Validate all user inputs with proper sanitization.
- Store sensitive configuration in environment variables.
- Use parameterized queries (ORM handles this automatically).

## Performance guidelines
- Optimize database queries and use appropriate indexes.
- Implement caching strategies with Flask-Caching where beneficial.
- Use pagination for large datasets.
- Consider async processing with Celery for heavy tasks.
- Profile code performance for critical paths.
- Monitor memory usage and prevent leaks.
