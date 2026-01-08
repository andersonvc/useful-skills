# Software Design Spec Skill for Claude Code

This skill helps Claude create comprehensive software design specifications following proven patterns.

## Installation

1. Copy this entire `software-design-spec` folder to your Claude Code skills directory:

```bash
cp -r software-design-spec ~/.claude/skills/
```

2. Verify installation:

```bash
ls ~/.claude/skills/software-design-spec/SKILL.md
```

3. The skill will be automatically available the next time you start Claude Code.

## Usage

The skill activates automatically when you ask Claude to create specifications:

- "Create a software spec for..."
- "Write a design doc for..."
- "I need a technical specification for..."
- "Generate a SPEC.md for..."

## Output

Generates **two documents**:

### 1. `TECH-SPEC.md`

- Functional and non-functional requirements
- System architecture and component design
- Database schemas
- API specifications
- Configuration examples
- CLI/UI design

### 2. `ANALYSIS-TECH-SPEC.md`

After creating the spec, a self-review analysis is **always** generated:

- Summary of findings (critical/major/minor)
- Security concerns
- Architecture issues
- Performance risks
- Data design gaps
- Technical consistency checklist

## Workflow

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

## What This Skill Provides

- Standard spec structure following industry best practices
- Guidelines for writing clear, testable requirements
- Patterns for different project types (web apps, CLI tools, libraries, etc.)
- Code example formatting best practices
- Elicitation questions to gather complete requirements
- **Iterative refinement** with technical analysis at each pass

## Updating

To update the skill, simply edit the SKILL.md file:

```bash
code ~/.claude/skills/software-design-spec/SKILL.md
```

Changes take effect the next time you restart Claude Code.
