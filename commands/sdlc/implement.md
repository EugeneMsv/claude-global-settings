---
description: "Development part of the SDLC process which includes: The
sequence and the phases are: Analysis, Architecture, Pseudocode, Development,
Quality Testing, Performance Testing (optional)"
---

# Development feature: {{-f}}

## Purpose

Implement production-ready code for `{{-f}}` based on comprehensive
architectural designs and detailed pseudocode from previous phases to create
fully functional, tested software components.

## Required Steps (All Mandatory)

### Step 0: Display Execution Plan
- Show all steps (1-6) at the beginning
- Confirm you will execute each step in sequence
- No steps are optional

### Step 1: Validate Prerequisites
- Verify `.feature/{{-f}}/Analysis.md` exists and is not empty
- Verify `.feature/{{-f}}/Architecture.md` exists and is not empty
- Verify `.feature/{{-f}}/Pseudocode.md` exists and is not empty
- FAIL FAST if missing - suggest running analysis, architecture, and
  pseudocode phases first
- Confirm pseudocode contains sufficient implementation specifications

### Step 2: Prepare Implementation Input
- Read and validate Analysis.md, Architecture.md, and Pseudocode.md content
- Ensure pseudocode provides adequate foundation for code implementation
- Document any gaps or assumptions

### Step 3: Run Code Implementation
- Launch `developer` subagent with `Architecture.md` and `Pseudocode.md` as input
- Include comprehensive unit tests and documentation

### Step 4: Save Implementation Results
- Save `developer` high-level summary to `Implementation.md` in
  `.feature/{{-f}}/`
- Ensure complete capture of implementation decisions and changes made
- Verify file creation and content completeness

### Step 5: Critical Review
- Launch `solution-critic` subagent
- Input: `Architecture.md, Pseudocode.md, Implementation.md AND actual
  implemented code`
- Save critique to `Implementation-Criticism.md` in `.feature/{{-f}}/`
- Categorize issues as: Critical, Major, or Minor

### Step 6: Quality Gate
- IF any Critical or Major issues exist in latest
  `Implementation-Criticism.md`:
    - Return to Step 3
    - Provide ONLY the latest criticism to developer (not previous versions)
      and original architecture/pseudocode
    - Re-implement with improvements
    - Continue to Step 5 for fresh critique
    - Repeat until NO Critical/Major issues remain
- ONLY proceed when all issues are Minor or resolved

## Success Criteria
- All steps completed in sequence
- No Critical or Major issues in final Implementation-Criticism.md
- Complete implementation documentation in .feature/{{-f}}/ folder
- Code follows project's established patterns and architectural decisions
- Production-ready implementation with comprehensive test coverage
- All code includes proper documentation

## Usage
/implement -f="user-authentication"