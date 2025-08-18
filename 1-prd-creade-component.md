# Rule: Generating a Product Requirements Document (PRD) for Component Creation

## 1. Goal

Guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format for a reusable UI component, based on a user prompt describing the component. The PRD must be clear, actionable, and suitable for a junior developer to implement, using explicit language in EN-US for technical content and Brazilian Portuguese (PT-BR) for all user interactions.

---

## 2. Process

1. **Receive Initial Prompt**: User provides a brief description of the component (e.g., "Create a reusable button component").
2. **Ask Clarifying Questions**: Present 3-5 questions in PT-BR to gather details (see [Section 3](#3-clarifying-questions)). Wait for user responses.
3. **Incorporate Responses**: Update the PRD with user-provided details. If ambiguities remain, ask follow-up questions in PT-BR.
4. **Generate PRD**: Follow the structure in [Section 4](#4-prd-structure).
5. **Save File**: Use format `/tasks/prd-[ID]-component-[component-slug].md` (see [Section 5](#5-output-rules)).
6. **Update Memory**: Append to `memory.md` with the new entry.

---

## 3. Clarifying Questions

Present questions as a numbered list in PT-BR, tailored to the component's purpose. Examples:

1. "Qual é a função principal do componente (ex.: botão primário para ações principais)?"

---

## 4. PRD Structure

Use Markdown with headings, lists, and tables. Write all sections in EN-US for developer clarity, except where specified.

### Required Sections

1. **Introduction/Overview**: Brief description of the component and its purpose (1-2 paragraphs).
2. **Goals**: Specific objectives of the component. Use a table:

   | Goal | Description | Priority |
   |------|-------------|----------|
   | Example: Reusability | Ensure button works across multiple pages | High |

3. **Functional Requirements**: Numbered list of must-have features (e.g., "1. The button must support a loading state.").
4. **Non-Functional Requirements**: Accessibility, performance, or compatibility needs (e.g., "Must meet WCAG 2.1 AA standards.").
5. **Success Metrics**: Measurable outcomes. Use a table:

   | Metric | Target | Measurement Method |
   |--------|--------|---------------------|
   | Example: Reusability | Used in 3+ pages | Codebase audit |

### Optional Sections

- **Technical Considerations**: Framework, dependencies, or pseudocode. Code must be in EN-US with PT-BR comments. Example:

   ```javascript
   // Renderiza um botão com suporte a estados
   function Button({ label, isLoading, disabled }) {
       // Verifica estado de loading para exibir spinner
       return isLoading ? <Spinner /> : <button disabled={disabled}>{label}</button>;
   }
