# AGENTS.md - Node.js Project Contributor Guide

Welcome to this Node.js project repository. This file contains the main points for new contributors and AI assistants working with Node.js/Express/TypeScript projects.

## Repository overview
- **Source code**: `src/` contains controllers, services, repositories, and utilities.
- **Tests**: `tests/` with unit, integration, and e2e test directories.
- **Database**: `prisma/` for schema and migrations (if using Prisma).
- **Configuration**: `tsconfig.json`, `package.json`, and environment files.
- **Documentation**: API documentation and setup guides.
- **Types**: `src/types/` for TypeScript type definitions.

## Local workflow
1. Install dependencies and set up environment:
   ```bash
   npm install               # Install dependencies
   cp .env.example .env      # Set up environment variables
   npm run db:migrate        # Run database migrations
   npm run db:seed           # Seed database (optional)
   ```

2. Format, lint and type-check your changes:
   ```bash
   npm run format            # Prettier formatting
   npm run lint              # ESLint checking
   npm run type-check        # TypeScript checking
   ```

3. Run the tests:
   ```bash
   npm test                  # Run all tests
   npm run test:unit         # Unit tests only
   npm run test:integration  # Integration tests only
   npm run test:e2e          # End-to-end tests
   npm run coverage          # Generate coverage report
   ```

4. Run the application:
   ```bash
   npm run dev               # Development server with hot reload
   npm run build             # Build for production
   npm run start             # Production server
   ```

## Testing guidelines
Use Jest with Supertest for HTTP testing. Maintain high test coverage:
```bash
npm test -- --watch         # Watch mode for development
npm test -- --detectOpenHandles  # Debug hanging processes
npm run test:coverage        # Generate detailed coverage report
```
- Test all API endpoints with integration tests
- Unit test service layer business logic
- Mock external dependencies appropriately
- Test error scenarios and edge cases
- Use testcontainers for database integration tests

## Style notes
- Use strict TypeScript configuration with proper type safety.
- Follow ESLint rules and Prettier formatting.
- Use async/await for asynchronous operations, avoid callbacks.
- Implement proper error handling middleware for Express.
- Use meaningful variable names: camelCase for variables, PascalCase for classes, UPPER_SNAKE_CASE for constants.

## Commit message format
Use conventional commit format:
```
type(scope): description

Examples:
feat(auth): implement JWT refresh token mechanism
fix(api): resolve user validation middleware issue
perf(db): optimize user search query performance
security(auth): add rate limiting to login endpoint
refactor(services): extract common database operations
test(controllers): add comprehensive user CRUD tests
```

## Pull request expectations
PRs should include:
- **Summary**: Clear description of changes and API modifications
- **Database changes**: Document any Prisma schema or migration changes
- **API documentation**: Update Swagger/OpenAPI specs if applicable
- **Security impact**: Note any authentication, authorization, or validation changes
- **Performance considerations**: Document any performance implications

Before submitting, ensure:
- [ ] All tests pass (`npm test`)
- [ ] TypeScript compilation succeeds (`npm run type-check`)
- [ ] ESLint passes (`npm run lint`)
- [ ] Code is formatted (`npm run format`)
- [ ] Database migrations are included and tested
- [ ] API documentation is updated
- [ ] Environment variables are documented

## What reviewers look for
- **API design**: RESTful design patterns and appropriate HTTP status codes.
- **Type safety**: Proper TypeScript usage with minimal `any` types.
- **Error handling**: Comprehensive error middleware and proper error responses.
- **Security**: Input validation, authentication/authorization, and secure practices.
- **Database efficiency**: Optimized queries and proper transaction handling.
- **Testing quality**: Comprehensive test coverage including edge cases.

## Architecture guidelines
- Use layered architecture: Controllers → Services → Repositories.
- Implement Express Router for modular route organization.
- Apply Repository pattern for data access abstraction.
- Use dependency injection for better testability.
- Separate business logic from HTTP concerns.

## Express.js best practices
- Use middleware chain appropriately (auth, validation, error handling).
- Implement proper error handling middleware as the last middleware.
- Use helmet and cors for security headers.
- Apply rate limiting for API protection.
- Validate requests with libraries like Joi or Zod.
- Return consistent error response formats.

## Database best practices (Prisma)
- Design efficient database schemas with proper relationships.
- Use Prisma migrations for all schema changes.
- Implement connection pooling for production.
- Avoid N+1 query problems with proper includes.
- Handle transactions for data consistency.
- Index frequently queried fields.

## Security considerations
- Implement JWT-based authentication with refresh tokens.
- Use bcrypt for password hashing with appropriate rounds.
- Validate all inputs with proper sanitization.
- Implement role-based access control (RBAC).
- Add rate limiting to prevent abuse.
- Use HTTPS in production and secure headers.
- Store secrets in environment variables, never in code.

## Performance guidelines
- Implement Redis caching for frequently accessed data.
- Optimize database queries and use appropriate indexes.
- Use compression middleware for response optimization.
- Implement efficient pagination for large datasets.
- Monitor memory usage and prevent leaks.
- Use clustering or PM2 for production scalability.
