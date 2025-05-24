# AGENTS.md - Vue.js Project Contributor Guide

Welcome to this Vue.js project repository. This file contains the main points for new contributors and AI assistants working with Vue.js 3/Composition API/TypeScript projects.

## Repository overview
- **Source code**: `src/` contains components, composables, stores, and utilities.
- **Components**: `src/components/` with base and feature-specific directories.
- **Composables**: `src/composables/` for reusable Composition API logic.
- **Stores**: `src/stores/` for Pinia state management.
- **Router**: `src/router/` for Vue Router configuration and guards.
- **Services**: `src/services/` for API communication and external integrations.
- **Tests**: `tests/` with unit and e2e test directories.

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
   npm run lint              # ESLint with Vue-specific rules
   npm run type-check        # TypeScript checking
   ```

3. Run the tests:
   ```bash
   npm test                  # Run all tests
   npm run test:unit         # Unit tests only
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
Use Vitest with Vue Test Utils for component testing:
```bash
npm run test:watch          # Watch mode for development
npm run test:ui             # Visual test interface
npm run test:coverage       # Coverage with threshold checking
```
- Test components using user-centric approaches with Testing Library
- Test composables in isolation from components
- Test Pinia stores with proper mocking
- Include tests for reactive behavior and lifecycle
- Test router navigation and guards

## Style notes
- Use Composition API with `<script setup>` syntax for all components.
- Prefer composables for reusable logic over mixins.
- Use proper ref/reactive for state management.
- Follow Vue Style Guide conventions for component organization.
- Use TypeScript with proper typing for props, emits, and template refs.

## Commit message format
Use conventional commit format:
```
type(scope): description

Examples:
feat(auth): implement user login with Pinia store
fix(router): resolve navigation guard timing issue
perf(components): optimize UserList with virtual scrolling
refactor(composables): extract common API logic to useApi
test(stores): add comprehensive user store tests
style(components): update design system spacing
```

## Pull request expectations
PRs should include:
- **Summary**: Clear description of functionality and user impact
- **Reactivity impact**: How changes affect Vue's reactivity system
- **Performance considerations**: Impact on component re-rendering and reactivity
- **Screenshots/Videos**: Visual proof of UI changes and interactions
- **Accessibility**: Keyboard navigation and screen reader compatibility

Before submitting, ensure:
- [ ] All tests pass (`npm test`)
- [ ] TypeScript compilation succeeds (`npm run type-check`)
- [ ] ESLint passes (`npm run lint`)
- [ ] Vue DevTools shows proper component structure
- [ ] Reactivity works as expected in all scenarios
- [ ] Components are properly accessible
- [ ] No memory leaks in reactive references

## What reviewers look for
- **Composition API usage**: Proper use of ref, reactive, computed, and watch.
- **Component design**: Single File Component structure and organization.
- **Reactivity patterns**: Efficient reactive data management and avoiding common pitfalls.
- **Store management**: Proper Pinia store design and state management.
- **Performance**: Optimized rendering and appropriate use of Vue 3 features.
- **Type safety**: Comprehensive TypeScript integration with Vue components.

## Vue 3 Composition API best practices
- Use `<script setup>` syntax for cleaner component code.
- Apply ref() for primitive values, reactive() for objects.
- Use computed() for derived state, avoid unnecessary calculations.
- Implement proper cleanup in composables and watchers.
- Use defineProps and defineEmits with TypeScript for type safety.
- Apply toRefs() when destructuring reactive objects.

## Reactivity system guidelines
- Understand ref vs reactive and use appropriately.
- Use readonly() for immutable reactive data.
- Apply unref() to safely access ref values.
- Implement proper reactive transformations with toRef/toRefs.
- Avoid losing reactivity through destructuring.
- Use watchEffect vs watch based on dependency tracking needs.

## Composables best practices
- Create reusable logic with clear interfaces.
- Return reactive objects or refs consistently.
- Implement proper lifecycle management (cleanup).
- Use dependency injection pattern for flexibility.
- Document composable APIs clearly.
- Test composables independently of components.

## Pinia state management
- Design stores with clear responsibilities.
- Use getters for computed store values.
- Implement actions for state mutations and async operations.
- Apply store composition for complex state relationships.
- Use store subscription for reactive side effects.
- Test stores with proper mocking strategies.

## Vue Router integration
- Use named routes for better maintainability.
- Implement navigation guards for authentication and authorization.
- Use route meta fields for configuration.
- Apply dynamic route matching appropriately.
- Implement proper error handling for route failures.
- Use router composition API in components.

## Component architecture
- Follow Single File Component conventions.
- Use slots for flexible component composition.
- Implement proper prop validation with TypeScript.
- Use custom events for parent-child communication.
- Apply provide/inject for deep component trees.
- Create reusable components with clear APIs.

## Performance optimization
- Use v-memo for expensive list rendering.
- Implement KeepAlive for component state preservation.
- Apply async components with defineAsyncComponent.
- Use shallow reactive objects when appropriate.
- Optimize computed properties to avoid unnecessary calculations.
- Monitor reactivity performance with Vue DevTools.

## TypeScript integration
- Define proper interfaces for component props and emits.
- Use generic types for flexible component APIs.
- Implement proper typing for template refs.
- Apply type assertions carefully and sparingly.
- Use Vue's built-in TypeScript utilities.
- Test TypeScript integration thoroughly.

## Accessibility guidelines
- Use semantic HTML in component templates.
- Implement proper ARIA attributes for complex components.
- Ensure keyboard navigation works for all interactive elements.
- Test with screen readers and assistive technologies.
- Maintain proper focus management in single-page navigation.
- Use Vue's built-in accessibility helpers appropriately.

## Security considerations
- Validate all user inputs and sanitize data display.
- Use proper authentication state management.
- Implement CSRF protection for form submissions.
- Avoid using v-html with untrusted content.
- Secure API endpoints and validate responses.
- Use environment variables for sensitive configuration.
