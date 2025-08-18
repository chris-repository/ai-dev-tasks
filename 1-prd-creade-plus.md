# Rule: Generating a Product Requirements Document (PRD)

## 1. Goal

To guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format, based on an initial user prompt. The PRD should be clear, actionable, and suitable for a junior developer to implement the feature.

---

## 2. Process

### Standard Feature Development

1. **Receive Initial Prompt**: User provides a brief feature description.
2. **Ask Clarifying Questions**: Must gather details before proceeding (see [Section 3](#3-clarifying-questions)).
3. **Generate PRD**: Follow the structure in [Section 4](#4-prd-structure)).
4. **Save File**: Use format `/tasks/prd-[ID]-[feature].md` (see [Section 6](#6-output-rules)).

### Emergency Bug Fixes

1. **Skip Clarifying Questions**: Immediate action for critical errors.
2. **Generate Minimal PRD**: Include only:
   - Problem Description
   - Solution Approach
   - Files to Modify
   - Success Criteria
3. **Save File**: Use format `/tasks/prd-[ID]-fix-[feature].md`.
4. **Document**: Add "Emergency fix - critical error blocking functionality" to PRD.

---

## 3. Clarifying Questions

_Required for Standard Process only._ Examples:

- **Problem/Goal**: "What problem does this feature solve for the user?"
- **User Stories**: "As a [type of user], I want to [action] so that [benefit]."
- **Acceptance Criteria**: "How will we know this feature is successful?"
- **Non-Goals**: "What should this feature _not_ do?"

---

## 4. PRD Structure

### Required Sections

1. **Introduction/Overview**: Brief feature description and goal.
2. **Goals**: Specific, measurable objectives.
3. **User Stories**: Narratives from user perspectives.
4. **Functional Requirements**: Numbered list of actions (e.g., "The system must allow X").
5. **Non-Goals**: Explicit out-of-scope items.
6. **Success Metrics**: How success will be measured (e.g., "Increase engagement by 10%").

### Optional Sections

- **Design Considerations**: UI/UX notes or mockup links.
- **Technical Considerations**: Dependencies or constraints.
- **Open Questions**: Unresolved topics needing clarification.

---

## 5. Target Audience

- **Primary Reader**: Junior developers.
- **Requirements**:
  - Use explicit, unambiguous language.
  - Avoid jargon unless defined.
  - Provide enough context for feature logic.

---

## 6. Output Rules

### Filenames

- **Standard Feature**: `prd-[ID]-new-[feature].md` (e.g., `prd-001-new-image-upload.md`).
- **Emergency Fix**: `prd-[ID]-fix-[feature].md` (e.g., `prd-002-fix-login-error.md`).

### File Numbering

- Start at `001`.
- Check `/tasks` directory for the next available number.

### Memory File (`memory.md`)

- **Template**:

  ```markdown
  # PROJECT MEMORY

  ### Current Context

  - **Project**: [Name]
  - **Tech Stack**: [List]
  - **Known Issues**:
    - [Issue 1]
    - [x] [Fixed Issue] (e.g., "Fixed in prd-002-fix-login-error.md")

  ### Changelog

  - YYYY-MM-DD HH:MM: [Action] (e.g., "PRD-001 created for image upload feature")
  ```
