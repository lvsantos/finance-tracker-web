# Finance Tracker Web

Personal finance tracking application.

## Tech Stack

- State Management: NgRx
- Styling: Tailwind CSS
- Testing: Jasmine + Karma
- Package Manager: yarn
- HTTP Client: Angular HttpClient (never axios or fetch)

## Architecture

### Folder Structure

```
src/
├── app/
│   ├── core/          # Singleton services, guards, interceptors
│   ├── shared/        # Shared components, directives, pipes
│   ├── features/      # Feature modules (transactions, budgets, reports)
│   └── models/        # TypeScript interfaces and types
├── assets/            # Static files
└── environments/      # Environment configurations
```

### Module Organization

- Each feature has its own module under `features/`
- Core services are provided in root and located in `core/`
- Shared components are standalone or in SharedModule
- Use lazy loading for feature modules

### Component Structure

- Smart components in feature folders handle state and logic
- Dumb components in shared/ receive data via @Input and emit via @Output
- Keep components under 300 lines
- One component per file

## Code Standards

### Naming Conventions

- Components: PascalCase files with `.component.ts` suffix (e.g., `TransactionList.component.ts`)
- Services: PascalCase files with `.service.ts` suffix (e.g., `TransactionService.service.ts`)
- Interfaces: PascalCase with `I` prefix (e.g., `ITransaction`)
- Observables: suffix with `$` (e.g., `transactions$`)
- Methods/variables: camelCase, methods start with verbs
- Constants: UPPER_SNAKE_CASE
- Folders/files: kebab-case

### TypeScript Rules

- Never use `any` - create proper interfaces for all data structures
- Use `const` over `let` where possible
- Declare class properties as `private` or `readonly` by default
- Keep methods under 50 lines
- Use early returns instead of nested if/else (max 2 levels)
- Declare variables close to where they're used
- No flag parameters - create separate methods instead
- Max 4 parameters per method - use objects for more

### Angular Specific

- Use OnPush change detection strategy where possible
- Unsubscribe from observables using `takeUntil` pattern or async pipe
- Use reactive forms over template-driven forms
- Implement OnDestroy for cleanup
- Use dependency injection, avoid direct instantiation
- Services should be provided in root or feature module, not component level
- Use Angular HttpClient for API calls, never axios or fetch
- Implement error handling with HttpInterceptor

### RxJS Patterns

- Prefer async pipe in templates over manual subscription
- Use operators: map, filter, switchMap, catchError
- Avoid nested subscriptions - use higher-order operators
- Keep subscriptions in smart components only

## Testing Strategy

### Unit Tests (Jasmine/Karma)

- Test files located alongside source files with `.spec.ts` extension
- Test all services, pipes, and utility functions
- Test smart component logic (mock dependencies)
- Use TestBed for Angular-specific testing
- Mock HttpClient with HttpClientTestingModule
- Follow Arrange-Act-Assert pattern
- One behavior per test
- Mock Date objects for time-dependent tests

### What to Test

- Services: all public methods, error handling
- Components: data transformation, event handlers, lifecycle hooks (not template rendering)
- Pipes: all transformation scenarios
- Guards: all authorization scenarios

## API Integration

- Use Angular HttpClient service (never axios or fetch)
- Implement interceptors for authentication tokens
- Handle errors globally with HttpInterceptor
- Resource paths in plural: `/transactions`, `/budgets`
- Use kebab-case for multi-word resources: `/scheduled-events`
- Create interfaces for all API responses
- Handle loading states with observables
- Implement retry logic for failed requests
- Use environment files for API base URLs

## State Management (NgRx)

- Actions: verb-based names (e.g., `loadTransactions`, `addTransaction`)
- Effects: handle side effects (API calls, navigation)
- Selectors: memoized queries for derived state
- Keep state normalized
- Never mutate state directly

## Git Commit Convention

After completing any task, generate a semantic commit message following this format:

### Format

```
<type>: <short description>

[optional body explaining changes]
```

### Commit Types

- **feat**: New feature or functionality
- **fix**: Bug fix
- **docs**: Documentation changes only
- **style**: Code formatting, no logic changes
- **refactor**: Code restructuring without changing behavior
- **test**: Adding or updating tests
- **chore**: Build process, dependencies, tooling
- **perf**: Performance improvements

### Rules for AI

- Always use imperative mood: "add" not "added" or "adds"
- Keep subject line under 72 characters
- No period at end of subject line
### Rules for AI

- Always use imperative mood: "add" not "added" or "adds"
- Keep subject line under 72 characters
- No period at end of subject line
- Choose the most specific type that applies
- Include body for complex changes explaining what and why
- Reference issue numbers in footer if applicable
- For breaking changes, add `BREAKING CHANGE:` footer

### Breaking Changes

For changes that break backward compatibility (impacts automated versioning):

**Format:**

```
<type>: <short description>

<body>

BREAKING CHANGE: <what breaks and migration instructions>
```

**When to mark as breaking:**

- API response/request format changes
- Interface or type definition changes that require code updates
- Removed or renamed public methods/properties
- Changed method signatures (parameters, return types)
- Database schema changes affecting existing data
- Configuration format changes

**Breaking change requirements:**

- Always include clear description of what breaks
- Provide migration path or instructions for developers
- Explain why the breaking change was necessary
- Include before/after examples when applicable

### Examples

```
feat: implement transaction filtering component

Add TransactionFilter component with date range and category
selection using reactive forms and NgRx state management.
```

```
fix: correct budget limit validation logic

Previous implementation allowed negative values. Updated
validation to enforce positive numbers only.
```

```
test: add unit tests for transaction service
```

```
refactor: simplify budget calculation method
```

## Review Checklist

Before completing any task:

- Run tests: `yarn test` - all must pass
- Run linter: `yarn lint` - no errors
- Check for unused imports/variables
- Verify no hardcoded values (use environment files)
- Ensure no console.log statements remain
- Verify proper TypeScript typing (no `any`)
- Check component templates use async pipe where possible
- Verify observables are properly unsubscribed
- Generate semantic commit message following convention above
