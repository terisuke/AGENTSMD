# AGENTS.md - React Project Contributor Guide

Welcome to this React project repository. This file contains the main points for new contributors and AI assistants working with React/TypeScript projects.

## Repository overview
- **Source code**: `src/` contains components, hooks, services, and utilities.
- **Components**: `src/components/` with ui and feature-specific directories.
- **Hooks**: `src/hooks/` for custom React hooks and reusable logic.
- **Services**: `src/services/` for API communication and external integrations.
- **State**: `src/store/` for global state management (Zustand/Redux).
- **Tests**: `tests/` with component, integration, and e2e test files.
- **Types**: `src/types/` for TypeScript type definitions.

## Local workflow
1. Install dependencies and set up environment:
   ```bash
   npm install               # Install dependencies
   cp .env.example .env      # Set up environment variables
   npm run dev               # Start development server
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
   npm run test:watch        # Watch mode for development
   npm run test:ui           # Vitest UI interface
   npm run test:e2e          # End-to-end tests with Playwright
   npm run coverage          # Generate coverage report
   ```

4. Build and analyze:
   ```bash
   npm run build             # Production build
   npm run preview           # Preview production build
   npm run analyze           # Bundle size analysis
   ```

## Testing guidelines
Use Vitest with React Testing Library for component testing:
```bash
npm run test:watch          # Interactive watch mode
npm run test:coverage       # Coverage report with thresholds
npm run test:ui             # Visual test interface
```
- Test user interactions rather than implementation details
- Use MSW (Mock Service Worker) for API mocking
- Write tests for custom hooks in isolation
- Include accessibility tests with testing-library/jest-dom
- Test error boundaries and loading states

## Style notes
- Use functional components with hooks exclusively.
- Prefer custom hooks for complex stateful logic.
- Use destructuring for props and state access.
- Implement proper key props for list items.
- Use TypeScript strictly with minimal `any` usage.
- Follow React naming conventions: PascalCase for components, camelCase for functions.

## Commit message format
Use conventional commit format:
```
type(scope): description

Examples:
feat(auth): add user authentication with context
fix(ui): resolve button hover state accessibility issue
perf(components): optimize UserList rendering performance
refactor(hooks): extract common API logic to useApi hook
test(auth): add comprehensive login form validation tests
style(components): update design system spacing tokens
```

## Pull request expectations
PRs should include:
- **Summary**: Clear description of functionality and user impact
- **Screenshots/Videos**: Visual proof of UI changes (before/after)
- **Performance impact**: Bundle size changes and runtime performance
- **Accessibility**: Keyboard navigation and screen reader compatibility
- **Responsive design**: Mobile and desktop compatibility verification

Before submitting, ensure:
- [ ] All tests pass (`npm test`)
- [ ] TypeScript compilation succeeds (`npm run type-check`)
- [ ] ESLint passes with no warnings (`npm run lint`)
- [ ] Components are accessible (keyboard navigation, ARIA attributes)
- [ ] Responsive design works on different screen sizes
- [ ] No console errors or warnings in browser
- [ ] Performance is not significantly degraded

## What reviewers look for
- **Component design**: Proper separation of concerns and reusability.
- **Hook usage**: Correct implementation of React hooks and dependencies.
- **Performance**: Efficient rendering with proper memoization strategies.
- **Accessibility**: WCAG compliance and keyboard navigation.
- **User experience**: Intuitive interactions and error handling.
- **Type safety**: Comprehensive TypeScript usage with proper prop types.

## React best practices
- Use functional components with hooks exclusively.
- Implement proper dependency arrays for useEffect, useMemo, useCallback.
- Avoid prop drilling by using Context API or state management libraries.
- Use React.memo for expensive components to prevent unnecessary re-renders.
- Implement proper error boundaries for error handling.
- Use Suspense for loading states with lazy-loaded components.

## State management guidelines
- Prefer local state (useState) for component-specific data.
- Use useReducer for complex state logic.
- Apply Context API for moderately shared state.
- Use Zustand or Redux for complex global state.
- Implement React Query/SWR for server state management.
- Keep state as close to where it's used as possible.

## Performance optimization
- Use React.memo to prevent unnecessary re-renders.
- Implement useMemo and useCallback judiciously (not everywhere).
- Use lazy loading with React.lazy for route-based code splitting.
- Optimize images with proper formats and lazy loading.
- Implement virtual scrolling for large lists.
- Monitor bundle size and remove unused dependencies.

## Accessibility guidelines
- Use semantic HTML elements (button, nav, main, etc.).
- Implement proper ARIA attributes for complex components.
- Ensure keyboard navigation works for all interactive elements.
- Maintain proper color contrast ratios (4.5:1 minimum).
- Provide alternative text for images and icons.
- Test with screen readers and keyboard-only navigation.

## Custom hooks best practices
- Extract reusable logic into custom hooks.
- Use proper hook naming convention (useXxx).
- Return objects for multiple values, arrays for related values.
- Handle cleanup in useEffect return functions.
- Implement proper error handling within hooks.
- Test custom hooks in isolation.

## Component organization
- Create reusable UI components in `components/ui/`.
- Organize feature-specific components in `components/features/`.
- Use composition patterns over inheritance.
- Implement proper prop interfaces with TypeScript.
- Keep components focused on a single responsibility.
- Extract complex logic to custom hooks or utility functions.

## Security considerations
- Validate all user inputs and sanitize data display.
- Use proper authentication context and route guards.
- Implement proper CORS configuration for API calls.
- Avoid storing sensitive data in local storage.
- Use HTTPS in production and implement proper CSP headers.
- Validate environment variables and API responses.
