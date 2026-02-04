Use the @tech-spec-writer agent to create a comprehensive technical specification for the feature.

## Input

**Feature Slug**: `$ARGUMENTS`

## Process

1. **Create Feature Folder** (if it doesn't exist):
   - Create directory: `docs/tasks/$ARGUMENTS/`

2. **Gather Context**:
   - Check if `docs/tasks/$ARGUMENTS/prd.md` exists for product requirements
   - Review any existing documentation or code related to the feature
   - Ask clarifying questions if the requirements are unclear

3. **Generate Tech Spec**:
   - Use the template at `docs/templates/techspec.md`
   - Fill in all applicable sections based on the feature requirements
   - Output to: `docs/tasks/$ARGUMENTS/techspec.md`

4. **Validation**:
   - Ensure all mandatory sections are completed:
     - Overview (Goal, Scope, Owner, Status, Target Apps)
     - Requirements (Functional + Non-Functional)
     - Technical Approach
     - API/Interface Contracts (if applicable)
     - Data Model (if applicable)
     - Testing Strategy
   - Mark optional sections as "N/A" if not applicable

## Output

- **Tech Spec**: `docs/tasks/$ARGUMENTS/techspec.md`

## Next Steps

After the tech spec is created and reviewed, use the `create-task` command to generate the task breakdown:

```
/create-task $ARGUMENTS
```