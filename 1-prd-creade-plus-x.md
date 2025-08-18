# Rule: Generating a Product Requirements Document (PRD)

## 1. Goal

Guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format, based on an initial user prompt describing a feature or bug fix. The PRD must be clear, actionable, and suitable for a junior developer to implement, using explicit language, defined terms, and sufficient context for logic and implementation. All interactions with the user (e.g., clarifying questions, responses) must be conducted in Brazilian Portuguese (PT-BR) to ensure clear communication.


---

## 2. Process

### Standard Feature Development

1. **Receive Initial Prompt**: User provides a brief feature description (e.g., "Add image upload functionality").
2. **Ask Clarifying Questions**: Gather essential details before generating the PRD (see [Section 3](#3-clarifying-questions)). Present questions in a numbered list and wait for user responses.
3. **Handle User Responses**: If the user provides answers, incorporate them into the PRD. If needed, ask follow-up questions for unresolved items.
4. **Generate PRD**: Follow the structure in [Section 4](#4-prd-structure).
5. **Save File**: Create the PRD file in the format `/tasks/prd-[ID]-new-[feature-slug].md` (see [Section 6](#6-output-rules) for details on ID generation and slug creation).
6. **Update Memory**: Append to `memory.md` with the new entry (see [Section 6](#6-output-rules)).

### Emergency Bug Fixes

1. **Identify Scenario**: Trigger this if the user's prompt includes urgency indicators like "critical", "bug", "error", or "fix immediately".
2. **Skip Clarifying Questions**: Proceed directly for critical issues blocking functionality.
3. **Generate Minimal PRD**: Include only the required sections listed below (adapted from [Section 4](#4-prd-structure)):
   - Introduction/Overview (include note: "Emergency fix - critical error blocking functionality").
   - Problem Description (as a subsection under Goals).
   - Functional Requirements (focus on solution approach).
   - Files to Modify (as a subsection under Technical Considerations).
   - Success Criteria (as Acceptance Criteria under Success Metrics).
4. **Save File**: Use format `/tasks/prd-[ID]-fix-[feature-slug].md`.
5. **Update Memory**: Append to `memory.md` with the new entry.

---

## 3. Clarifying Questions

_Required for Standard Process only. Present as a numbered list to the user in PT-BR. Aim for 4-6 questions based on the prompt's needs._

Examples (translated to PT-BR for user interaction):

- **Problema/Objetivo**: "Qual problema específico essa funcionalidade resolve para o usuário final?"
- **Histórias de Usuário**: "Pode fornecer histórias de usuário no formato: 'Como [tipo de usuário], quero [ação] para que [benefício]'?"
- **Critérios de Aceitação**: "Quais condições devem ser atendidas para considerar essa funcionalidade concluída (ex.: casos de borda, desempenho)?"
- **Não-Objetivos**: "Quais funcionalidades ou aspectos essa feature explicitamente _não_ deve incluir?"
- **Detalhes Técnicos**: "Há dependências, restrições de tecnologia ou arquivos/módulos existentes para integrar?"
- **Métricas**: "Como o sucesso será medido (ex.: aumento de engajamento, redução de erros)?"

If user responses raise new ambiguities, ask targeted follow-ups in PT-BR.

---

## 4. PRD Structure

Use Markdown formatting with headings, lists, and tables for clarity. Ensure all sections are filled with content derived from the user's prompt and clarifications.

### Required Sections

1. **Introduction/Overview**: Brief description of the feature and its high-level goal (1-2 paragraphs).
2. **Goals**: Specific, measurable objectives. Use a bullet list or table:

   | Goal | Description | Priority |
   |------|-------------|----------|
   | Example: Improve user retention | Allow quick image uploads to reduce drop-off | High |

3. **User Stories**: Narratives from user perspectives. Format as a numbered list (e.g., "As a [user], I want [action] so that [benefit].").
4. **Functional Requirements**: Numbered list of must-have actions (e.g., "1. The system must validate file types (JPEG, PNG).").
5. **Non-Goals**: Bullet list of explicit out-of-scope items (e.g., "- No support for video uploads.").
6. **Success Metrics**: How to measure success. Use a table:

   | Metric | Target | Measurement Method |
   |--------|--------|---------------------|
   | Example: Upload success rate | >95% | Track via logs/analytics |

### Optional Sections (Include if relevant based on clarifications)

- **Design Considerations**: UI/UX notes, wireframe links, or accessibility requirements.
- **Technical Considerations**: Dependencies, constraints, or files to modify. If code or pseudocode is included, write the code in EN-US (e.g., variable names, function names) with comments in PT-BR for documentation. Example:
   ```javascript/typescript
    // Valida o tipo de arquivo antes do upload
    function validateFileType(file) {
       // Tipos permitidos: JPEG, PNG
       const allowedTypes = ['image/jpeg', 'image/png'];
       return allowedTypes.includes(file.type);
    }
    ```
- **Open Questions**: Bullet list of unresolved items; flag for future clarification.
- **Acceptance Criteria**: Detailed tests for each requirement (e.g., "If upload fails, display error message X.").

### Example PRD Snippet (for Reference)

For a hypothetical prompt: "Add login with Google."

```markdown
# PRD-001-New-Google-Login

## Introduction/Overview
This feature enables users to log in using Google accounts, simplifying authentication and reducing signup friction.

## Goals
| Goal | Description | Priority |
|------|-------------|----------|
| Simplify login | Integrate OAuth with Google | High |
| Enhance security | Use secure token exchange | Medium |

## User Stories
1. As a new user, I want to log in with Google so that I don't need to create a new password.

## Functional Requirements
1. The system must redirect to Google's OAuth page on button click.
2. The system must handle callback and store user session.

## Non-Goals
- No support for other providers like Facebook.

## Success Metrics
| Metric | Target | Measurement Method |
|--------|--------|---------------------|
| Login conversion rate | +20% | A/B testing |
```

---

## 5. Target Audience

- **Primary Reader**: Junior developers.
- **Requirements**:
  - Use explicit, unambiguous language (e.g., define terms like "OAuth" if used).
  - Avoid undefined jargon; provide explanations (e.g., "OAuth: A protocol for secure authorization").
  - Include enough context for implementation logic, such as pseudocode snippets if complex.
  - Assume basic knowledge of the project's tech stack (reference `memory.md` for details).

---

## 6. Output Rules

### Filenames

- **Slug Creation**: Convert feature name to lowercase, replace spaces with hyphens (e.g., "Image Upload" → "image-upload").
- **Standard Feature**: `prd-[ID]-new-[feature-slug].md` (e.g., `prd-001-new-image-upload.md`).
- **Emergency Fix**: `prd-[ID]-fix-[feature-slug].md` (e.g., `prd-002-fix-login-error.md`).

### File Numbering

- Start at `001`.
- To generate ID: Simulate checking `/tasks` directory by assuming sequential numbering. If previous PRDs exist (from `memory.md`), increment the highest ID by 1. If none, use `001`.

### Memory File (`memory.md`)

- **Location**: Always update or create in the root directory.
- **Template** (Append new entries; do not overwrite):

  ```markdown
  # PROJECT MEMORY

  ### Current Context
  - **Project**: [Project Name, e.g., "Web App Dashboard"]
  - **Tech Stack**: [List, e.g., "React, Node.js, MongoDB"]
  - **Known Issues**:
    - [Issue 1 description]
    - [x] [Fixed Issue] (e.g., "Fixed in prd-002-fix-login-error.md")

  ### Changelog
  - YYYY-MM-DD HH:MM: [Action] (e.g., "2025-08-14 10:00: PRD-001 created for image upload feature")
  ```

- Use current date/time for changelog entries (format: YYYY-MM-DD HH:MM).
