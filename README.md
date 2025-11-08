# Finance Tracker Web

A web application for tracking personal finances. Manage transactions, create budgets, and generate financial reports to better understand your spending patterns.

## Tech Stack

- **Frontend**: Angular 18 + TypeScript
- **State Management**: NgRx
- **Styling**: Tailwind CSS
- **Testing**: Jasmine + Karma
- **HTTP Client**: Angular HttpClient
- **Backend API**: REST API with PostgreSQL database

## Getting Started

### Prerequisites

- Node.js (v18 or higher)
- Yarn package manager

### Installation

```bash
# Install dependencies
yarn install
```

### Development

```bash
# Start development server
yarn start
```

The application will run on <http://localhost:4200>

### Building

```bash
# Build for production
yarn build
```

Production files will be generated in the `dist/` directory.

### Testing

```bash
# Run unit tests
yarn test

# Run unit tests with coverage
yarn test --code-coverage

# Run e2e tests
yarn run e2e
```

**Test Coverage Requirements:**

- Services: 100%
- Pipes: 100%
- Guards/Interceptors: 100%
- Components: Focus on business logic

### Code Quality

```bash
# Run linter
yarn lint
```

## Git Commit Convention

This project uses **semantic commit messages** to maintain a clear and readable git history. All commits MUST follow this format:

### Format

```text
<type>: <short description>

[optional body for detailed explanation]

[optional footer with issue references]
```

### Commit Types

- **feat**: New feature (e.g., `feat: add transaction filtering by category`)
- **fix**: Bug fix (e.g., `fix: correct budget calculation logic`)
- **docs**: Documentation only changes (e.g., `docs: update API integration guide`)
- **style**: Code formatting, missing semicolons, etc. (no logic changes)
- **refactor**: Code change that neither fixes a bug nor adds a feature
- **test**: Adding or updating tests (e.g., `test: add unit tests for transaction service`)
- **chore**: Changes to build process, dependencies, or tooling (e.g., `chore: update angular to v18`)
- **perf**: Performance improvements (e.g., `perf: optimize transaction list rendering`)

### Examples

**Good commits:**

```text
feat: add monthly budget overview dashboard

Implement dashboard component with NgRx integration to display
monthly budget summaries and spending trends.

Closes #42
```

```text
fix: resolve incorrect total in budget calculation

Previous logic didn't account for pending transactions.
Now includes all transaction statuses in the calculation.
```

```text
test: add unit tests for budget service
```

**Bad commits:**

```text
updated stuff
fix bug
WIP
changes
```

### Rules

- Keep the subject line under 72 characters
- Use imperative mood ("add" not "added" or "adds")
- Don't end the subject line with a period
- Separate subject from body with a blank line
- Use the body to explain *what* and *why*, not *how*

### Breaking Changes

For changes that break backward compatibility (used for automated versioning), add a `BREAKING CHANGE:` footer:

**Format:**

```text
<type>: <short description>

<body explaining the change>

BREAKING CHANGE: <description of what breaks and how to migrate>
```

**Examples:**

```text
feat: change transaction API response structure

Update transaction endpoint to return normalized data with embedded
relationships for better performance.

BREAKING CHANGE: Transaction API now returns data in format
{ id, attributes: {...}, relationships: {...} } instead of flat object.
Update all components using TransactionService to access data via
transaction.attributes.amount instead of transaction.amount.
```

```text
refactor: remove deprecated budget export methods

BREAKING CHANGE: Removed exportToCSV() and exportToJSON() methods
from BudgetService. Use the new unified export(format: ExportFormat)
method instead. Replace budgetService.exportToCSV() with
budgetService.export('csv').
```

**Impact on versioning:**

- `fix:` → Patch version (1.0.0 → 1.0.1)
- `feat:` → Minor version (1.0.0 → 1.1.0)
- `BREAKING CHANGE:` footer → Major version (1.0.0 → 2.0.0)

**When writing breaking changes:**

- Always explain what breaks and why
- Provide clear migration path for developers
- Include before/after code examples when helpful
- Use the `BREAKING CHANGE:` footer for automated versioning

## API Integration

The application consumes a REST API with the following conventions:

### HTTP Status Codes

- **200**: Success
- **400**: Bad request format
- **401**: Not authenticated
- **403**: Not authorized
- **404**: Resource not found
- **422**: Business logic error
- **500**: Server error

### Resource Naming

- Resources use plural names: `/transactions`, `/budgets`
- Multi-word resources use kebab-case: `/scheduled-events`

### Environment Configuration

API base URLs and other environment-specific settings are configured in:

- `src/environments/environment.ts` (development)
- `src/environments/environment.prod.ts` (production)

## Development Guidelines

For code standards, architecture patterns, and contribution guidelines, see [Copilot Instructions](.github/copilot-instructions.md).

## Status

This project is in active development.
