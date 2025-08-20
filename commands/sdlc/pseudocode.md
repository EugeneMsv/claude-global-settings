---
description: "Pseudocode part of the SDLC process which includes: The sequence
and the phases are: Analysis, Architecture, Pseudocode, Development, Quality
Testing, Performance Testing (optional)"
---

# Pseudocode feature: {{-f}}

## Purpose

Create detailed algorithmic pseudocode for `{{-f}}` based on comprehensive
architectural designs from the architecture phase to translate system
blueprints into step-by-step implementation logic.

## Required Steps (All Mandatory)

### Step 0: Display Execution Plan
- Show all steps (1-6) at the beginning
- Confirm you will execute each step in sequence
- No steps are optional

### Step 1: Validate Prerequisites
- Verify `.feature/{{-f}}/Analysis.md` exists and is not empty
- Verify `.feature/{{-f}}/Architecture.md` exists and is not empty
- FAIL FAST if missing - suggest running analysis and architecture phases
  first
- Confirm architecture contains sufficient design specifications

### Step 2: Prepare Pseudocode Input
- Read and validate `Analysis.md` and `Architecture.md` content
- Ensure architecture provides adequate foundation for algorithmic design
- Document any gaps or assumptions

### Step 3: Run Pseudocode Generation
- Launch `pseudocoder` subagent with `Analysis.md` and `Architecture.md` as input
- Pseudocoder must deliver comprehensive step-by-step algorithmic logic

### Step 4: Save Pseudocode Results
- Save `pseudocoder` output to `Pseudocode.md` in `.feature/{{-f}}/`
- Ensure complete capture of algorithmic specifications
- Verify file creation and content completeness

### Step 5: Critical Review
- Launch `solution-critic` subagent
- Input and tell to focus only on Pseudocode criticism: `Analysis.md, Architecture.md AND 
Pseudocode.md`
- Save critique to `Pseudocode-Criticism.md` in `.feature/{{-f}}/`
- Categorize issues as: Critical, Major, or Minor

### Step 6: Quality Gate
- IF any Critical or Major issues exist in latest `Pseudocode-Criticism.md`:
    - Return to Step 3
    - Provide ONLY the latest criticism to pseudocoder (not previous versions)
      and original analysis/architecture
    - Re-run pseudocode with improvements
    - Continue to Step 5 for fresh critique
    - Repeat until NO Critical/Major issues remain
- ONLY proceed when all issues are Minor or resolved

## Success Criteria
- All steps completed in sequence
- No Critical or Major issues in final `Pseudocode-Criticism.md`
- Complete algorithmic documentation in `.feature/{{-f}}/` folder
- Pseudocode follows project's established patterns and architectural
  decisions
- Clear step-by-step implementation logic ready for development phase

## Usage
/pseudocode -f="user-authentication"