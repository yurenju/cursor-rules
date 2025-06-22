---
description:
globs:
alwaysApply: false
---

# Rule: Generating a Task List from a PRD

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list in Markdown format based on an existing Product Requirements Document (PRD). The task list should guide a developer through TDD (Test-Driven Development) implementation.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/tasks/`
- **Filename:** `tasks-[prd-file-name].md` (e.g., `tasks-prd-user-profile-editing.md`)

## Process

1.  **Receive PRD Reference:** The user points the AI to a specific PRD file
2.  **Analyze PRD:** The AI reads and analyzes the functional requirements, user stories, and other sections of the specified PRD.
3.  **Write Gherkin Acceptance Criteria:** Use Cucumber's Gherkin syntax to write high-level acceptance criteria for the entire PRD. These acceptance criteria will be used for subsequent direct observation of output through MCP to ensure implementation truly achieves its purpose. Should include main Features, Scenarios, and Given-When-Then steps, covering core functionality and key user flows.
4.  **Phase 1: Generate Parent Tasks:** Based on the PRD analysis and Gherkin acceptance criteria, create the file and generate the main, high-level tasks required to implement the feature following TDD methodology. Use your judgement on how many high-level tasks to use. It's likely to be about 5. Present these tasks to the user in the specified format (without sub-tasks yet). Inform the user: "I have generated the high-level tasks based on the PRD using TDD methodology. Ready to generate the detailed sub-tasks? Respond with 'Go' to proceed."
5.  **Wait for Confirmation:** Pause and wait for the user to respond with "Go".
6.  **Phase 2: Generate Sub-Tasks:** Once the user confirms, break down each parent task into smaller, actionable sub-tasks following the TDD development flow. Ensure sub-tasks logically follow the 5-phase TDD process and cover the implementation details implied by the PRD.
7.  **Identify Relevant Files:** Based on the tasks and PRD, identify potential files that will need to be created or modified. List these under the `Relevant Files` section, including corresponding test files.
8.  **Generate Final Output:** Combine the parent tasks, sub-tasks, relevant files, acceptance criteria, PRD reference, and notes into the final Markdown structure.
9.  **Save Task List:** Save the generated document in the `/tasks/` directory with the filename `tasks-[prd-file-name].md`, where `[prd-file-name]` matches the base name of the input PRD file.

## TDD Development Flow

The generated tasks should follow this granular, class/file-based TDD methodology:

### Per-Class/File TDD Cycle

Each class or file should go through a complete TDD cycle before moving to the next:

1. **Define Structure for Single Class/File**

   - Define the basic structure for one specific class/file (can be TypeScript interfaces, empty classes, or stub functions)
   - For classes: Create empty class with method signatures that throw "Not implemented" errors
   - For functions: Create function signatures with parameters that throw "Not implemented" errors
   - For TypeScript interfaces: Only define when multiple classes need to implement the same contract
   - Establish basic structure and determine function signatures and return types for this component only

2. **Write Test Structure for This Class/File**

   - Write only `describe` and `it` statement declarations for this specific class/file
   - Do NOT implement any test logic or assertions inside the `it` blocks
   - **Focus on core functionality and main error scenarios** - prioritize essential test coverage over comprehensive edge case testing
   - Leave the `it` block bodies empty - this allows user to confirm the testing approach and scope before implementation
   - Focus only on the current component being developed
   - The purpose is to get user approval on what aspects will be tested before writing actual test code

3. **Implement Test Logic (Red Phase)**

   - Write complete test code with assertions for this class/file
   - **Tests should expect the correct behavior/return values, NOT "Not implemented" errors**
   - Tests should validate actual functionality (return values, side effects, proper error types)
   - Run tests to ensure ALL tests fail because functionality is not yet implemented
   - Verify that tests fail for the right reasons (missing implementation, not syntax errors)
   - Adjust interface design based on test feedback if needed

4. **Implement Feature Logic (Green Phase)**

   - Start with minimal implementation to make first test pass
   - Gradually implement more functionality to make additional tests pass
   - Refine implementation iteratively until ALL tests pass
   - Complete this component before moving to next

5. **Move to Next Class/File**
   - Repeat the entire cycle for the next component
   - Build incrementally, one component at a time

### Implementation Order

Tasks should be organized by dependency order, implementing foundational components first:

- Utility functions and helpers
- Core service classes
- API integration classes
- React hooks
- UI components and demo pages

### Key Principles

- **One component at a time**: Complete the full TDD cycle for each class/file before proceeding
- **Developer confirmation**: Get approval after each component's test structure before implementing
- **Incremental building**: Each component builds upon previously completed, tested components
- **Immediate feedback**: Test and validate each component individually
- **Red Phase validation**: ALL tests must fail initially to ensure test validity
- **Green Phase progression**: Gradually implement functionality to make tests pass one by one

## Output Format

The generated task list _must_ follow this structure:

```markdown
## PRD Reference

**Source Document**: [Link to the original PRD file that this task list is based on]

This task list implements the features specified in the above PRD. Please refer to the PRD for detailed context, requirements, and user stories.

## Root Problem

[Brief description of the core problem being solved based on PRD analysis]

## Gherkin Acceptance Criteria

High-level acceptance criteria defined using Cucumber's Gherkin syntax, used for direct observation and verification of implementation results through MCP:

\`\`\`gherkin
Feature: [Feature Name]
As a [User Role]
I want to [What I want to do]
So that [Expected outcome]

Scenario: [Scenario Name]
Given [Precondition]
When [Action performed]
Then [Expected result]
And [Additional verification]

Scenario: [Another Scenario Name]
Given [Precondition]
When [Action performed]
Then [Expected result]
\`\`\`

## Acceptance Criteria

- [ ] **[Feature Name]**: [Detailed acceptance criteria describing completion conditions using testable outcomes]
- [ ] **[Another Feature]**: [Another acceptance criteria with specific, measurable conditions]
- [ ] **[Integration Test]**: [End-to-end test criteria that validates the complete feature workflow]

## Relevant Files

- `path/to/potential/file1.ts` - Brief description of why this file is relevant (e.g., Contains the main service class for this feature).
- `path/to/potential/file1.test.ts` - Unit tests for `file1.ts` (co-located with implementation).
- `path/to/another/file.tsx` - Brief description (e.g., API route handler for data submission).
- `path/to/another/file.test.tsx` - Unit tests for `file.tsx` (co-located with implementation).
- `lib/utils/helpers.ts` - Brief description (e.g., Utility functions needed for calculations).
- `lib/utils/helpers.test.ts` - Unit tests for `helpers.ts` (co-located with implementation).

### TDD Implementation Rules

**Critical**: Each component must follow the TDD cycle step by step, no skipping allowed unless explicitly instructed by the user:

1. **Structure Definition Phase**:

   - Create empty classes, function stubs, or interfaces as needed
   - For functions: Create function signatures with parameters that throw "Not implemented" errors
   - For classes: Create empty classes with method signatures that throw "Not implemented" errors
   - Only define TypeScript interfaces when multiple classes need to implement the same contract

2. **Test Structure Phase**:

   - **Write ONLY `describe` and `it` declarations with NO test logic inside**
   - **Focus on core functionality and key error scenarios only** - aim for essential test coverage, not exhaustive edge cases. For example, a function or hook-provided function, including core functionality and main errors combined, should preferably not exceed five test items
   - Leave ALL `it` blocks completely empty - no assertions or test code
   - Purpose: Allow developer to confirm testing approach and scope before implementation

3. **Test Logic Phase (Red Phase)**:

   - Fill the empty `it` blocks with complete test code and assertions
   - **Tests should expect correct functional behavior and return values, not merely verify "Not implemented" error throwing**
   - Tests should validate real return values, side effects, and proper error types
   - Run tests to confirm **ALL tests fail** because implementation is missing (this is required)
   - Verify tests fail due to missing implementation, not syntax errors

4. **Feature Implementation Phase (Green Phase)**:
   - Start with minimal implementation to make first test pass
   - Gradually implement more functionality to make additional tests pass
   - Complete current component before moving to next component

### Notes

- Test files should be co-located with their implementation files in the same directory
- Use `.test.ts` or `.test.tsx` suffix for test files
- Integration tests can be placed in a separate `tests/` directory if needed, with `.integration.test.ts` suffix
- Use `npx jest [optional/path/to/test/file]` to run tests. Running without a path executes all tests found by the Jest configuration.
- **Strictly follow TDD methodology**: each sub-task should be completed one at a time with developer confirmation before proceeding to the next sub-task.

- Use Mermaid diagrams where helpful to visualize system interactions and data flow.

## Tasks

Please complete one component at a time, following the complete TDD cycle for each class/file before proceeding to the next component.

- [ ] 1.0 **[Component Name 1] - Complete TDD Cycle**

  - [ ] 1.1 Define structure (interface/class/function stubs) for [Component Name 1]
  - [ ] 1.2 Write test structure (`describe` and `it` statements) for [Component Name 1]
  - [ ] 1.3 Implement test logic and run tests (Red Phase) for [Component Name 1]
  - [ ] 1.4 Implement feature logic (Green Phase) for [Component Name 1]

- [ ] 2.0 **[Component Name 2] - Complete TDD Cycle**

  - [ ] 2.1 Define structure (interface/class/function stubs) for [Component Name 2]
  - [ ] 2.2 Write test structure (`describe` and `it` statements) for [Component Name 2]
  - [ ] 2.3 Implement test logic and run tests (Red Phase) for [Component Name 2]
  - [ ] 2.4 Implement feature logic (Green Phase) for [Component Name 2]

- [ ] 3.0 **[Component Name 3] - Complete TDD Cycle**

  - [ ] 3.1 Define structure (interface/class/function stubs) for [Component Name 3]
  - [ ] 3.2 Write test structure (`describe` and `it` statements) for [Component Name 3]
  - [ ] 3.3 Implement test logic and run tests (Red Phase) for [Component Name 3]
  - [ ] 3.4 Implement feature logic (Green Phase) for [Component Name 3]

- [ ] [Continue pattern for remaining components...]

- [ ] **Final Acceptance**: After reading the Gherkin syntax acceptance criteria, directly confirm whether acceptance can be passed through MCP or commands

### Component Implementation Order

Components should be implemented in dependency order:

1. **Utility Functions**: Helper functions and calculations
2. **Core Services**: Business logic and data processing
3. **API Integration**: External service communication
4. **React Hooks**: State management and UI logic
5. **UI Components**: Demo pages and user interface
```

## Interaction Model

The process explicitly requires:

1. **Pause after generating parent tasks** to get user confirmation ("Go") before proceeding to generate detailed sub-tasks
2. **Task-by-task completion** following TDD methodology, with developer confirmation between each major phase
3. **Test-first approach** ensuring test structure is reviewed before implementation begins

This ensures the high-level plan aligns with user expectations and follows proper TDD practices throughout development.

## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature using TDD methodology. The tasks should guide them through proper test-driven development practices while building the features specified in the PRD.
