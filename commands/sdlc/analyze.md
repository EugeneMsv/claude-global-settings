 ---
description: "SDLC Analysis Phase: Transform feature requirements into
detailed business specifications through iterative analysis and critique"
  ---


## Purpose
Analyze and document feature requirements for "{{-f}}" to create comprehensive business specifications.

## Feature Description
{{-d}}

You must not read or write to the code, you are only working with initial input and subagents

## Required Steps (All Mandatory and sequential)

### Step 1: Create Feature Workspace
- Create directory: `.feature/{{-f}}/`
- Ensure clean workspace for analysis artifacts

### Step 2: Document Requirements
- Create `.feature/{{-f}}/Ask.md`
- Include ONLY:
   - Feature name: "{{-f}}"
   - Feature description: "{{-d}}"

### Step 3: Run Analysis
- Launch `analyst` subagent with `.feature/{{-f}}/Ask.md` as input
- Save analyst output to `.feature/{{-f}}/Analysis-<iteration-number>.md`

### Step 4: Critical Review
- Launch `analyst-critic` subagent
- Input: Both `Ask.md` AND `Analysis-<iteration-number>.md`
- Save critique to `.feature/{{-f}}/Criticism-<iteration-number>.md`

### Step 5: Quality Gate
- **IF** any Critical or Major issues exist in the latest `.feature/{{-f}}/Criticism-<iteration-number>.md`:
    - Return to Step 3
    - Provide ONLY the latest criticism to analyst (from the latest iteration) and initial ask
    - Re-run analysis with improvements
    - Continue to Step 5 for fresh critique
    - Repeat until NO Critical/Major issues remain
- **ONLY** proceed when all issues are Minor or resolved
- When issues are resolved the latest `Analysis-<iteration-number>.md` in `.feature/{{-f}}/` must be renamed to 
  `Analysis.md`


## Success Criteria
- All steps completed in sequence
- No Critical or Major issues in final `.feature/{{-f}}/Criticism-<iteration-number>.md`
- The `Analysis.md` exists `.feature/{{-f}}/` folder
- The `Ask.md` exists `.feature/{{-f}}/` folder
