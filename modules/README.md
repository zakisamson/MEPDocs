# Module Knowledge Documents

This directory is for incremental module detail documents referenced by the MEP System Map. Planned catalog paths do not imply files already exist.

Create details only when a PRD review, automation task, or validation needs deeper knowledge. Keep observed implementation separate from user-confirmed requirements.

## Suggested Template

```markdown
# <Module Name>

## Purpose and Scope
- Included and excluded areas.

## Pages and Routes
| Page / Feature | Route | Frontend Entry | Status |
| --- | --- | --- | --- |

## Observable Frontend Behavior
- Navigation, workflows, tabs, dialogs, and drawers.

## Inputs, Outputs, and UI States
- Inputs/actions and loading, empty, success, validation, and error states.

## Related Modules and Dependencies
| Module | Relationship | Evidence | Confidence |
| --- | --- | --- | --- |

## Relevant Source Files
- Route, page, state, service, and shared-component paths.

## Existing Tests or Automation
- Test paths and reusable automation, when known.

## Rules and Evidence
### User Confirmed
### Observed Implementation

## Known Gaps
## Review Metadata
- Last reviewed date:
- Frontend revision:
- Reviewer:
```

Use `Needs Review`, `User Confirmed`, and `Changed` for knowledge status; use `Confirmed by Source`, `Needs Review`, or `User Confirmed` for relationships.

