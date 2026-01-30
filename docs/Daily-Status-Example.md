# Example Daily Status Report Output

This document shows an example of what the Daily Status Report workflow generates.

## Sample Report

```markdown
# 📊 MsQuic Daily Status Report

**Generated:** 2026-01-30 09:00 UTC
**Repository:** NikolajBjorner/msquic

---

### File Statistics

- C/C++ files: 617
- PowerShell scripts: 44
- CMake files: 39

### Recent Commit Activity (Last 24 Hours)

- Commits in last 24 hours: 3

Recent commits:
```
277871e Add workflow validation documentation
41aca05 Add daily status workflow with GitHub Actions
e757fc5 Initial plan
```

### Branch Information

- Current branch: `main`
- Total branches: 45

### Latest Commit

- **Commit:** `277871e`
- **Author:** Developer Name
- **Date:** 2 hours ago
- **Message:** Add workflow validation documentation

### Recent Workflow Status

| Workflow | Status | Date | Link |
|----------|--------|------|------|
| Build | ✅ success | 2026-01-30 08:45 | [View](https://github.com/...) |
| Test | ✅ success | 2026-01-30 08:30 | [View](https://github.com/...) |
| CodeQL | ✅ success | 2026-01-29 17:00 | [View](https://github.com/...) |
| Code Coverage | ⚠️ cancelled | 2026-01-29 15:20 | [View](https://github.com/...) |
| Docker Publish | ✅ success | 2026-01-29 12:10 | [View](https://github.com/...) |

### Open Issues and Pull Requests

- Open Issues: 87
- Open Pull Requests: 12

### Recently Updated Issues (Last 7 Days)

- [#1234](https://github.com/.../issues/1234) Fix memory leak in connection handling - open
- [#1233](https://github.com/.../issues/1233) Update documentation for API changes - closed
- [#1232](https://github.com/.../issues/1232) Performance regression in v2.3.0 - open
- [#1231](https://github.com/.../issues/1231) Add support for new TLS extensions - open
- [#1230](https://github.com/.../issues/1230) CI/CD pipeline improvements - closed

---

*This report is automatically generated daily by the [Daily Status workflow](https://github.com/NikolajBjorner/msquic/actions/workflows/daily-status.yml).*
```

## GitHub Issue Format

When the workflow runs, it creates a GitHub issue with:
- **Title**: `Daily Status Report - YYYY-MM-DD`
- **Label**: `daily-status`
- **Body**: The markdown report above

If an issue for the current date already exists, the workflow adds the updated report as a comment to the existing issue rather than creating a new one. This prevents duplicate issues and keeps all daily updates organized.

## Artifact

The workflow also uploads the report as a build artifact that can be downloaded from the GitHub Actions run page. The artifact is retained for 30 days.

## Use Cases

1. **Daily Health Check**: Quick overview of repository activity and CI/CD health
2. **Team Standup**: Reference for discussing recent changes and issues
3. **Trend Analysis**: Compare reports over time to track project evolution
4. **Onboarding**: New contributors can review recent reports to understand project activity
5. **Management Reporting**: High-level metrics for stakeholders

## Notifications

Team members can subscribe to the `daily-status` label to receive notifications when new reports are posted.
