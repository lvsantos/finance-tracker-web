# Prompt Template for Finance Tracker Web

> **Note:** This project follows strict coding standards defined in `.github/copilot-instructions.md`. All those rules are automatically applied. This template focuses on task-specific context.

---

## How to Use This Template

1. Copy this template
2. Fill in the `<Task>`, `<Context>`, `<Constraints>`, and other sections
3. Remove placeholder text and examples
4. Submit to LLM

---

## Execution Flow

**Before implementing, you MUST follow this workflow:**

1. **Clarification Phase:** Read the entire prompt and ask concise questions about anything unclear or missing. Wait for developer responses.

2. **Planning Phase:** Create a detailed execution plan with specific steps and file changes. Wait for developer approval.

3. **Implementation Phase:** Only after approval, proceed with implementation.

---

<Task>

[Describe what needs to be accomplished in 1-2 sentences using imperative mood]

Example: Implement a transaction filtering component that allows users to filter transactions by date range, category, and amount.

</Task>

---

<Context>

**Context** = Everything the LLM needs to know about the current state of the project to understand this task. This is WHAT EXISTS NOW.

**What already exists:**

- [Features, components, or services already implemented that relate to this task]
- [Example: Transaction list component displays all transactions in `src/app/features/transactions/transaction-list/`]
- [Example: TransactionService provides `getTransactions()` method that returns Observable<ITransaction[]>]

**Dependencies:**

- [Code that this task will use or integrate with]
- [Example: ITransaction interface in `src/app/models/transaction.model.ts` defines transaction structure]
- [Example: TransactionActions in store already has `loadTransactions` and `addTransaction` actions]

</Context>

---

<Constraints>

**Constraints** = Limitations, restrictions, or special conditions that apply ONLY to this specific task. This is WHAT YOU CANNOT DO or MUST WORK AROUND.

- [Task-specific limitations that affect implementation]
- [Example: Backend API endpoint `/api/transactions/filter` is not ready yet - mock the HTTP response in the service]
- [Example: Filter must support maximum 100 transactions per page due to performance requirements]
- [Example: Date picker library is not available - use native HTML input type="date"]

</Constraints>

---

## Requirements

**Requirements** = WHAT the implementation must include or achieve. Focus on features, functionality, and user-facing behavior.

- [Feature or functionality that must be implemented]
- [Example: Create a filter form with fields for date range (start/end), category dropdown, and amount range (min/max)]
- [Example: Add "Apply Filter" button that triggers filtering and "Clear" button that resets all fields]
- [Example: Display filtered results immediately after applying filter without page reload]
- [Example: Show loading indicator while fetching filtered data]

## Technical Specifications

**Technical Specifications** = HOW to implement the requirements. Specify architecture, components, data structures, and integration points.

**Example:** If creating a transaction filter feature, specify: NgRx actions (`applyFilter`, `clearFilter`), API endpoint (GET `/api/transactions?category=X`), components (`TransactionFilterComponent` in shared/ as dumb component), and interface (`ITransactionFilter` with date range and category fields).

**NgRx Store (if needed):**

- Actions: [action names with payloads]
- Effects: [which effects handle which actions and call what services]
- Selectors: [selector names and what they return]

**API (if needed):**

- Endpoints: [HTTP method and path with parameters]
- Request: [body structure for POST/PUT/PATCH]
- Response: [expected response structure]

**Components:**

- [Component name, location (path), type (smart/dumb), and responsibility]

**Interfaces:**

- [Interface name, location (path), and key properties with types]

## Acceptance Criteria

**Acceptance Criteria** = Testable conditions that prove the task is complete and working correctly. These should be specific, measurable, and verifiable.

1. [Specific user action produces expected result]
   - [Example: When user selects start date "2024-01-01", end date "2024-01-31", category "food" and clicks "Apply", only transactions matching those criteria are displayed]

2. [System handles normal operations correctly]
   - [Example: Filtered transactions load within 2 seconds and display in descending date order]

3. [Edge cases are properly handled]
   - [Example: When no transactions match filters, display "No transactions found" message instead of empty list]
   - [Example: When end date is before start date, show validation error and disable "Apply" button]

4. [Error scenarios are managed gracefully]
   - [Example: When API returns error, show user-friendly message "Failed to load transactions. Please try again." and keep previous results visible]

---

<Output>

## Expected Deliverables

### Files to Create

- [ ] `path/to/new-file.ts` - [purpose]
- [ ] `path/to/new-file.spec.ts` - [test coverage]

### Files to Modify

- [ ] `path/to/existing-file.ts` - [what changes]

</Output>

---

## AI Instructions

**You must follow this workflow before implementing:**

### Step 1: Clarification

Read the entire prompt carefully. If anything is unclear, ambiguous, or missing, ask concise questions to clarify:

- Missing technical details
- Unclear requirements
- Ambiguous acceptance criteria
- Unknown dependencies or constraints

**Wait for the developer to answer all questions before proceeding.**

### Step 2: Execution Plan

Create a detailed execution plan including:

- Step-by-step implementation approach
- Files to create with their purpose
- Files to modify with specific changes
- Testing strategy
- Potential risks or considerations

**Wait for the developer's approval before proceeding.**

### Step 3: Implementation

Only after receiving approval, proceed with the implementation following the project's coding standards.
