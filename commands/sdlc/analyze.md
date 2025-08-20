 ---
description: "SDLC Analysis Phase: Transform feature requirements into
detailed technical specifications through iterative analysis and critique"
  ---

# Feature Analysis Agent

## Purpose
Analyze and document feature requirements for "{{-f}}" to create comprehensive
technical specifications.

## Feature Description
{{-d}}

## Required Steps (All Mandatory)

### Step 0: Display Execution Plan
- Show all steps (1-6) at the beginning
- Confirm you will execute each step in sequence
- No steps are optional

### Step 1: Create Feature Workspace
- Create directory: `.feature/{{-f}}/`
- Ensure clean workspace for analysis artifacts

### Step 2: Document Requirements
- Create `Requirements.md` in `.feature/{{-f}}/`
- Include:
   - Feature name: "{{-f}}"
   - Feature description: "{{-d}}"
   - Clear requirements structure

### Step 3: Run Analysis
- Launch `analyst` subagent with `Requirements.md` as input
- Analyst must deliver comprehensive technical analysis

### Step 4: Save Analysis Results
- Save analyst output to `Analysis.md` in `.feature/{{-f}}/`
- Ensure complete capture of analysis results
- Verify file creation and content

### Step 5: Critical Review
- Launch `solution-critic` subagent
- Input: Both `Requirements.md` AND `Analysis.md`
- Save critique to `Criticism.md` in `.feature/{{-f}}/`
- Categorize issues as: Critical, Major, or Minor

### Step 6: Quality Gate
- **IF** any Critical or Major issues exist in latest `Criticism.md`:
   - Return to Step 3
   - Provide ONLY the latest criticism to analyst (not previous versions) and initial requirements
   - Re-run analysis with improvements
   - Continue to Step 5 for fresh critique
   - Repeat until NO Critical/Major issues remain
- **ONLY** proceed when all issues are Minor or resolved

## Success Criteria
- All steps completed in sequence
- No Critical or Major issues in final `Criticism.md`
- Complete documentation in `.feature/{{-f}}/` folder
- Analysis meets project architectural standards
