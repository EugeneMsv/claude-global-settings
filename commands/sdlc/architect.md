---
description: Feature Architecture Agent
---


## Purpose

Design system architecture for "{{-f}}" based on detailed technical
specifications from the analysis phase to create comprehensive architectural
blueprints.

## Required Steps (All Mandatory)


Step 1: Validate Prerequisites

- Verify `.feature/{{-f}}/Analysis.md` exists and is not empty
- FAIL FAST if missing - suggest running analysis phase first
- Confirm analysis contains sufficient technical specifications

Step 2: Prepare Architecture Input

- Read and validate `Analysis.md` content
- Ensure analysis provides adequate foundation for architectural decisions
- Document any gaps or assumptions

Step 3: Run Architecture Design

- Launch `architector` subagent with `Analysis.md` as input
- Architector must deliver comprehensive system architecture

Step 4: Save Architecture Results

- Save `architector` output to Architecture.md in `.feature/{{-f}}/`
- Ensure complete capture of architectural decisions
- Verify file creation and content completeness

Step 5: Critical Review

- Launch `solution-critic` subagent
- Input: `Both Analysis.md AND Architecture.md`
- Save critique to `Architecture-Criticism.md` in .feature/{{-f}}/
- Categorize issues as: Critical, Major, or Minor

Step 6: Quality Gate

- IF any Critical or Major issues exist in latest `Architecture-Criticism.md`:
   - Return to Step 3
   - Provide ONLY the latest criticism to architector (not previous versions)
     and original analysis
   - Re-run architecture with improvements
   - Continue to Step 5 for fresh critique
   - Repeat until NO Critical/Major issues remain
- ONLY proceed when all issues are Minor or resolved

Success Criteria

- All steps completed in sequence
- No Critical or Major issues in final Architecture-Criticism.md
- Complete architectural documentation in .feature/{{-f}}/ folder
- Architecture follows project's established patterns and standards
- Clear technology decisions with justified rationale

Usage

/architect -f="user-authentication"

