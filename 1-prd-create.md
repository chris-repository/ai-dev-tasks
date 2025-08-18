# Rule: Generating a Product Requirements Document (PRD)

## Goal

To guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format, based on an initial user prompt. The PRD should be clear, actionable, and suitable for a junior developer to understand and implement the feature.

## Process

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Ask Clarifying Questions:** Before writing the PRD, the AI _must_ ask clarifying questions to gather sufficient detail. The goal is to understand the "what" and "why" of the feature, not necessarily the "how" (which the developer will figure out). Make sure to provide options in letter/number lists so I can respond easily with my selections.
3.  **Generate PRD:** Based on the initial prompt and the user's answers to the clarifying questions, generate a PRD using the structure outlined below.
4.  **Save PRD:** Save the generated document as `prd-[incremental-number]-[feature-name].md` (e.g., `prd-001-new-feature.md`) inside the `/tasks` directory.

## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

- **Problem/Goal:** "What problem does this feature solve for the user?" or "What is the main goal we want to achieve with this feature?"
- **Target User:** "Who is the primary user of this feature?"
- **Core Functionality:** "Can you describe the key actions a user should be able to perform with this feature?"
- **User Stories:** "Could you provide a few user stories? (e.g., As a [type of user], I want to [perform an action] so that [benefit].)"
- **Acceptance Criteria:** "How will we know when this feature is successfully implemented? What are the key success criteria?"
- **Scope/Boundaries:** "Are there any specific things this feature _should not_ do (non-goals)?"
- **Data Requirements:** "What kind of data does this feature need to display or manipulate?"
- **Design/UI:** "Are there any existing design mockups or UI guidelines to follow?" or "Can you describe the desired look and feel?"
- **Edge Cases:** "Are there any potential edge cases or error conditions we should consider?"

## PRD Structure

The generated PRD should include the following sections:

1.  **Introduction/Overview:** Briefly describe the feature and the problem it solves. State the goal.
2.  **Goals:** List the specific, measurable objectives for this feature.
3.  **User Stories:** Detail the user narratives describing feature usage and benefits.
4.  **Functional Requirements:** List the specific functionalities the feature must have. Use clear, concise language (e.g., "The system must allow users to upload a profile picture."). Number these requirements.
5.  **Non-Goals (Out of Scope):** Clearly state what this feature will _not_ include to manage scope.
6.  **Design Considerations (Optional):** Link to mockups, describe UI/UX requirements, or mention relevant components/styles if applicable.
7.  **Technical Considerations (Optional):** Mention any known technical constraints, dependencies, or suggestions (e.g., "Should integrate with the existing Auth module").
8.  **Success Metrics:** How will the success of this feature be measured? (e.g., "Increase user engagement by 10%", "Reduce support tickets related to X").
9.  **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the PRD is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the feature's purpose and core logic, dialogue with me PT-BR and code in US-EN.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/tasks/`
- **Filename:**
  - Standard: `prd-[incremental-number]-new-[feature-name].md` (e.g., `prd-001-new-feature.md`)
  - Emergency fixes: `prd-[incremental-number]-fix-[feature-name].md` (e.g., `prd-001-fix-mobile-hook-error.md`)

- **Memory File:**
  - If `memory.md` does not exist in `/tasks/`, the system must create it with this template:

    ```markdown
    # PROJECT MEMORY

    ## Current Context

    - **Project**: [Name]
    - **Tech Stack**: [List]
    - **Known Issues**:
      - [Issue 1]
      - [Issue 2]

    ## Active Tasks

    - `prd-[ID]-[feature].md` (Status: In Progress)

    ## Changelog

    - [YYYY-MM-DD HH:MM]: [Action] (e.g., "PRD-001 created for image upload feature")
    ```
  2. **Auto-Update Rules**:
  - After generating a PRD/bug fix, append to `## Changelog`:
    ```markdown
    - {date}: {PRD/task filename} created for {purpose}.
    ```
  - For critical changes (e.g., bug resolutions), add under `## Known Issues`:
    ```markdown
    - [x] {Issue} (Fixed in {PRD-filename})
    ```
  3. **Manual Overrides**:
  - Users may edit `memory.md` directly to:
    - Adjust priorities.
    - Add non-automated notes.

## Final instructions

### Standard Feature Development

1. Do NOT start implementing the PRD
2. Make sure to ask the user clarifying questions
3. Take the user's answers to the clarifying questions and improve the PRD

### Emergency Bug Fixes (Critical Errors)

**When to use:** For critical errors that block system functionality (e.g., TypeError, runtime errors that prevent pages from loading).

**Process:**

1. Create a simplified PRD immediately without asking clarifying questions
2. Use the filename format: `prd-[incremental-number]-[feature-name].md` (e.g., `prd-001-fix-mobile-hook-error.md`)
3. Include essential sections only: Problem Description, Solution Approach, Files to Modify, Success Criteria
4. Proceed immediately to task generation and implementation
5. Document the decision in the PRD: "Emergency fix - critical error blocking system functionality"

**File Numbering:**

- Use incremental numbering starting from 001
- Check existing files in `/tasks` directory to determine next number
- Apply same numbering to task files: `tasks-[incremental-number]-[feature-name].md`
