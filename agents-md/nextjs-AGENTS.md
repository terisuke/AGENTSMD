# AGENTS.md - Next.js Project Contributor Guide

Welcome to this Next.js project repository. This file contains the main points for new contributors and AI assistants working with Next.js/TypeScript projects.

## Repository overview
- **App directory**: `app/` contains pages, layouts, and API routes (App Router).
- **Components**: `components/` with ui and feature-specific directories.
- **Library**: `lib/` for utilities, validations, and configuration.
- **Public assets**: `public/` for static files, images, and icons.
- **Types**: `types/` for TypeScript type definitions.
- **Configuration**: `next.config.js`, `tailwind.config.js`, and environment files.

## Local workflow
1. Install dependencies and set up environment:
   ```bash
   npm install               # Install dependencies
   cp .env.example .env.local # Set up environment variables
   npm run dev               # Start development server
   ```

2. Format, lint and type-check your changes:
   ```bash
   npm run format            # Prettier formatting
   npm run lint              # ESLint with Next.js rules
   npm run type-check        # TypeScript checking
   ```

3. Run the tests:
   ```bash
   npm test                  # Run all tests
   npm run test:watch        # Watch mode for development
   npm run test:e2e          # End-to-end tests with Playwright
   npm run coverage          # Generate coverage report
   ```

4. Build and analyze:
   ```bash
   npm run build             # Production build with optimization
   npm run start             # Start production server
   npm run analyze           # Bundle analyzer for optimization
   ```

## Testing guidelines
Use Jest with Testing Library for component testing:
```bash
npm run test:watch          # Interactive development mode
npm run test:e2e            # Full application flow testing
npm run lighthouse          # Performance and accessibility audit
```
- Test pages and components with realistic data scenarios
- Use MSW for API route mocking in tests
- Test both client and server components appropriately
- Include SEO and accessibility in critical path tests
- Test responsive behavior across different viewport sizes

## Style notes
- Use Server Components by default, Client Components only when necessary.
- Implement proper TypeScript types for all props and API responses.
- Use Next.js Image component for all images for automatic optimization.
- Follow file-based routing conventions with proper naming.
- Prefer async/await for server-side data fetching.

## Commit message format
Use conventional commit format:
```
type(scope): description

Examples:
feat(auth): implement OAuth login with NextAuth
fix(seo): resolve missing metadata for product pages
perf(images): optimize hero section image loading
refactor(api): migrate to App Router API routes
test(pages): add comprehensive home page functionality tests
style(ui): update design system with new brand colors
```

## Pull request expectations
PRs should include:
- **Summary**: Clear description of functionality and user experience impact
- **Performance impact**: Core Web Vitals changes and lighthouse scores
- **SEO considerations**: Metadata, structured data, and accessibility improvements
- **Screenshots**: Visual verification across different devices and browsers
- **API changes**: Documentation of any new or modified API routes

Before submitting, ensure:
- [ ] All tests pass (`npm test`)
- [ ] Build succeeds without errors (`npm run build`)
- [ ] TypeScript compilation passes (`npm run type-check`)
- [ ] Lighthouse scores are acceptable (90+ recommended)
- [ ] Pages are responsive and work across major browsers
- [ ] API routes are properly typed and tested
- [ ] Environment variables are documented in `.env.example`

## What reviewers look for
- **Next.js patterns**: Proper use of App Router, Server/Client Components, and routing.
- **Performance**: Core Web Vitals optimization and efficient data fetching.
- **SEO**: Proper metadata, structured data, and accessibility implementation.
- **Security**: Proper authentication, input validation, and API security.
- **User experience**: Responsive design, loading states, and error handling.
- **Type safety**: Comprehensive TypeScript usage with minimal `any` types.

## Next.js App Router best practices
- Use Server Components by default for better performance.
- Implement `'use client'` directive only when necessary (interactivity, hooks).
- Use proper loading.tsx and error.tsx files for better UX.
- Implement proper metadata generation for SEO.
- Use Suspense boundaries for optimal loading experiences.
- Leverage parallel and intercepting routes for advanced patterns.

## Data fetching strategies
- Use Server Components for initial data loading.
- Implement proper caching strategies with fetch options.
- Use React Query/SWR for client-side data management.
- Apply proper error handling for both server and client fetching.
- Implement optimistic updates for better user experience.
- Cache expensive operations appropriately.

## Performance optimization
- Optimize Core Web Vitals (LCP, FID, CLS).
- Use Next.js Image component with proper sizing and formats.
- Implement code splitting with dynamic imports.
- Optimize fonts with next/font for performance.
- Use proper caching headers for static assets.
- Monitor and optimize bundle size regularly.

## SEO and accessibility
- Implement comprehensive metadata for all pages.
- Use proper heading hierarchy (h1, h2, h3, etc.).
- Add structured data (JSON-LD) for rich snippets.
- Ensure keyboard navigation and screen reader compatibility.
- Implement proper Open Graph and Twitter Card meta tags.
- Use semantic HTML and ARIA attributes where needed.

## API routes best practices
- Use proper HTTP methods and status codes.
- Implement comprehensive input validation.
- Add proper error handling and logging.
- Use middleware for cross-cutting concerns (auth, CORS).
- Implement rate limiting for protection.
- Document API endpoints with proper TypeScript types.

## Authentication and security
- Use NextAuth.js for authentication when applicable.
- Implement proper CSRF protection.
- Validate all inputs on both client and server sides.
- Use proper session management and JWT handling.
- Implement role-based access control where needed.
- Secure API routes with proper middleware.

## Styling and UI guidelines
- Use Tailwind CSS with consistent utility classes.
- Implement responsive design with mobile-first approach.
- Use CSS modules or styled-components for component-specific styles.
- Maintain design system consistency across components.
- Implement proper dark mode support if required.
- Optimize for both performance and maintainability.

## Environment and deployment
- Use proper environment variable naming (NEXT_PUBLIC_ for client-side).
- Implement different configurations for development/staging/production.
- Use proper build optimization flags.
- Implement proper monitoring and error tracking.
- Set up proper CI/CD pipelines for automated testing and deployment.
- Configure proper caching strategies for static assets.
