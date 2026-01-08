---
name: software-design-spec
description: Create comprehensive software design specifications and technical documentation. Use when users request a "spec", "design doc", "software specification", "technical spec", or "SPEC.md" for a software project, feature, or system. Also use when users need to document system architecture, functional requirements, technical requirements, or implementation details.
---

# Software Design Spec Creator

This skill guides the creation of comprehensive software design specifications following proven patterns for clarity, completeness, and maintainability.

## Core Principles

**Clarity over brevity**: Specs should be detailed enough that a competent developer unfamiliar with the project can implement the system correctly.

**Structure over prose**: Use tables, code blocks, and hierarchical sections to make information scannable and easy to reference.

**Precision in requirements**: Distinguish clearly between functional requirements (what the system does), non-functional requirements (how well it does it), and technical constraints (how it's built).

## Standard Spec Structure

### 1. Header Section
- **Document title**: Clear, descriptive title
- **Version and date**: Track document evolution (optional)
- **Overview/Introduction**: 1-3 paragraphs explaining purpose, scope, and audience

### 2. System Overview
Brief summary (2-5 paragraphs) covering:
- What the system does
- Core design principles or architectural approach
- Key technical decisions

### 3. Functional Requirements
What the system must do. Use either:

**Table format** (preferred for many discrete requirements):
```markdown
| ID | Requirement | Description |
|:---|:------------|:------------|
| FR-1 | Feature Name | Detailed description of what the system must do |
| FR-2 | Another Feature | Clear, testable requirement |
```

**Subsection format** (for complex features needing detailed explanation):
```markdown
#### 3.1 Feature Category
- **Requirement**: Specific capability
  - Details, edge cases, constraints
  - Expected behavior
```

Each requirement should be:
- **Specific**: Clearly defined, not ambiguous
- **Testable**: Can verify if implemented correctly
- **Actionable**: Developer knows what to build

### 4. Non-Functional Requirements (when relevant)
Quality attributes and constraints:

| ID | Requirement | Description |
|:---|:------------|:------------|
| NFR-1 | Performance | Response time, throughput, scalability targets |
| NFR-2 | Maintainability | Code quality, modularity expectations |
| NFR-3 | Reliability | Error handling, recovery, uptime |
| NFR-4 | Usability | User experience expectations |

### 5. System Architecture and Design
Detailed technical design covering:

**Component breakdown**:
- List major components/modules
- Describe responsibility of each
- Show relationships between components

**Key processes and workflows**:
- Step-by-step description of important flows
- Use numbered lists for sequences
- Include decision points and branching logic
- Consider using mermaid diagrams for complex flows

**Error handling**:
- How errors are detected and reported
- Recovery strategies
- When the system should fail vs. continue

### 6. Data Design (when applicable)
**Database schemas**: Full table definitions with CREATE TABLE statements or equivalent

**File formats**: Structure of configuration files, data files, or APIs

**Example configurations**: Sample YAML/JSON/etc. with inline comments explaining each field

When showing data structures:
- Use code blocks with syntax highlighting
- Include comments explaining purpose of fields
- Show realistic examples, not just placeholders
- Document constraints (required fields, valid ranges, etc.)

### 7. Technical/Implementation Requirements
Technology choices and implementation guidance:
- Programming languages and key libraries
- Required frameworks or tools
- Configuration approach (files, CLI flags, environment variables)
- Logging strategy
- Testing expectations
- Code quality standards

### 8. User Interface / Command Line Interface (when applicable)
**For CLIs**: Document all flags, arguments, and usage patterns

**For UIs**: Describe layout, user workflows, key interactions

### 9. Out of Scope (optional but valuable)
Explicitly state what the system will NOT do to prevent scope creep and set clear expectations.

## Writing Guidelines

### Requirements Writing

**Good requirement examples**:
- "The system must validate email addresses using RFC 5322 standard before storing them"
- "When a file upload fails, the system must retry up to 3 times with exponential backoff"
- "The application must support PostgreSQL 12+ and MySQL 8+"

**Poor requirement examples** (too vague):
- "The system should be fast"
- "Users should have a good experience"
- "The code should be maintainable"

### Code Examples and Specifications

**When to include code**:
- Database schemas (always include full CREATE TABLE statements)
- Configuration file formats (show complete examples with all options)
- API request/response formats
- CLI usage patterns
- Key algorithms or complex logic

**Code block best practices**:
- Always specify the language for syntax highlighting
- Include inline comments explaining non-obvious parts
- Show realistic examples, not minimal stubs
- For configuration files, document every field

### Table Usage

Use tables for:
- Lists of requirements with IDs
- Comparing multiple options
- Documenting parameters or fields
- Showing supported platforms or versions

Table formatting:
```markdown
| Column 1 | Column 2 | Column 3 |
|:---------|:---------|:---------|
| Left aligned | Left aligned | Left aligned |
```

### Hierarchical Organization

Use consistent heading levels:
- `##` for major sections
- `###` for subsections  
- `####` for detailed subsections
- `#####` rarely (indicates possible restructuring need)

## Common Patterns by Project Type

### Web Applications
Focus on:
- Frontend/backend architecture
- API specifications (endpoints, methods, request/response formats)
- Database schema
- Authentication/authorization approach
- UI component structure

### CLI Tools
Focus on:
- Command structure and flags
- Input/output formats
- Error handling and exit codes
- Configuration file format
- Installation and dependencies

### Libraries/SDKs
Focus on:
- Public API surface
- Usage examples
- Extension points
- Thread safety and concurrency
- Versioning and compatibility

### System Tools/Automation
Focus on:
- Workflow steps (detailed, numbered sequences)
- Idempotency requirements
- State management
- Error recovery
- Prerequisites and dependencies

## Elicitation Questions

When creating a spec, gather information about:

**Scope and purpose**:
- What problem does this solve?
- Who will use this and how?
- What are the must-have vs. nice-to-have features?

**Technical context**:
- Existing systems or constraints to work within?
- Technology preferences or requirements?
- Performance or scale requirements?
- Security or compliance needs?

**Data and interfaces**:
- What data does the system work with?
- What external systems does it integrate with?
- What file formats or protocols are involved?

**Quality and testing**:
- What level of reliability is needed?
- What testing is expected?
- Code quality or documentation standards?

Ask focused questions, typically 1-2 at a time, to avoid overwhelming the user. Prioritize questions that significantly impact the spec's structure or content.

## Output Format

Create the spec as a markdown file with:
- Filename: `TECH-SPEC.md`
- Clear section hierarchy with consistent heading levels
- Tables for requirements and structured data
- Code blocks for schemas, configurations, and examples
- Enough detail that a competent developer could implement the system

The spec should be comprehensive enough to guide implementation without requiring extensive follow-up questions, while remaining readable and well-organized.

## Final Step: Self-Review & Analysis

After creating the spec, **always** perform a self-review and create an analysis document.

### Analysis Document: `ANALYSIS-TECH-SPEC.md`

**Purpose:** Identify technical risks, architectural gaps, security concerns, and areas needing further clarification before implementation begins.

**Structure:**

```markdown
# Technical Spec Analysis
## [Project Name] - Technical Review

**Date:** YYYY-MM-DD
**Spec Reviewed:** TECH-SPEC.md

---

## 1. Summary

Brief overview of findings (X critical, Y major, Z minor issues).

---

## 2. Critical Issues

Issues that could cause implementation failures, security vulnerabilities, or major architectural problems.

| ID | Category | Issue | Recommendation |
|:---|:---------|:------|:---------------|
| CRIT-001 | Security | Description of the issue | How to resolve it |

---

## 3. Major Issues

Important gaps or inconsistencies that should be addressed before implementation.

| ID | Category | Issue | Recommendation |
|:---|:---------|:------|:---------------|
| MAJ-001 | Architecture | Description of the issue | How to resolve it |

---

## 4. Minor Issues

Nice-to-have improvements or clarifications.

| ID | Category | Issue | Recommendation |
|:---|:---------|:------|:---------------|
| MIN-001 | Documentation | Description of the issue | How to resolve it |

---

## 5. Questions for Stakeholder

Decisions that require user input before proceeding.

1. **Question about X?**
   - Option A: Description
   - Option B: Description
   - Recommendation: Which option and why

---

## 6. Technical Consistency Checklist

| Check | Status | Notes |
|:------|:-------|:------|
| All components have defined responsibilities | ✅/❌ | |
| All APIs have request/response formats | ✅/❌ | |
| All error conditions have handling strategies | ✅/❌ | |
| Database schema supports all requirements | ✅/❌ | |
| Authentication/authorization defined | ✅/❌ | |
| Configuration options documented | ✅/❌ | |
| Performance requirements have measurable targets | ✅/❌ | |
| External dependencies identified | ✅/❌ | |
| Testing strategy defined | ✅/❌ | |
```

### What to Look For

**Security Concerns:**
- Missing input validation
- Unclear authentication/authorization boundaries
- Secrets or credentials in configuration examples
- SQL injection or XSS vectors in API design
- Missing rate limiting or abuse prevention

**Architecture Issues:**
- Tight coupling between components
- Missing component boundaries or unclear responsibilities
- Single points of failure
- Stateful components that complicate scaling
- Circular dependencies

**Performance Risks:**
- Missing caching strategy for expensive operations
- N+1 query patterns in data access
- Unbounded queries or result sets
- Missing pagination for list endpoints
- No consideration of concurrent access

**Data Design Gaps:**
- Missing indexes for query patterns
- Normalization issues (over or under)
- No migration strategy for schema changes
- Missing constraints (foreign keys, unique, not null)
- Unclear data retention or cleanup strategy

**API Design Issues:**
- Inconsistent naming conventions
- Missing versioning strategy
- Unclear error response contracts
- Missing or incomplete request validation
- No consideration of backwards compatibility

**Completeness Gaps:**
- Requirements without corresponding design
- Endpoints without error handling
- Configuration options without defaults
- Missing logging or observability strategy
- No deployment or operational considerations

### Workflow

```
    ┌─────────────────────────────────────┐
    │                                     │
    ▼                                     │
1. Create TECH-SPEC.md                    │
          ↓                               │
2. Review spec for technical issues       │
          ↓                               │
3. Create/Update ANALYSIS-TECH-SPEC.md    │
          ↓                               │
4. Present findings to user               │
          ↓                               │
5. User provides decisions                │
          ↓                               │
6. Update TECH-SPEC.md based on decisions │
          ↓                               │
7. Ask user: "Another refinement pass?"   │
          ↓                               │
      ┌───┴───┐                           │
      │  Yes  │───────────────────────────┘
      └───┬───┘
          │ No
          ▼
8. Spec finalized, ready for implementation
```

**Important:** Always create the analysis document. Do not skip this step. The analysis often catches issues that would be expensive to fix during implementation.

Continue the refinement loop until the user is satisfied with the spec quality. Each iteration should show measurable improvement in the consistency checklist.

## Anti-Patterns to Avoid

**Premature optimization:**
- Don't specify caching before understanding access patterns
- Don't add complexity for hypothetical scale
- Don't over-engineer for flexibility that isn't needed

**Underspecification:**
- "Handle errors appropriately" (how?)
- "Use standard security practices" (which ones?)
- "The API should be RESTful" (what resources? what methods?)

**Technology-first thinking:**
- Don't choose technologies before understanding requirements
- Don't force-fit a solution to use a preferred tool
- Don't ignore simpler alternatives

**Good examples:**
- "POST /api/users returns 201 with user object on success, 400 with validation errors, 409 if email exists"
- "Cache user sessions in Redis with 24-hour TTL, refresh on activity"
- "Validate all string inputs against a 10,000 character limit to prevent memory exhaustion"
