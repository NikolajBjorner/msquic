# Daily Status Workflow

This workflow provides automated daily status reports for the MsQuic repository.

## Overview

The Daily Status workflow runs automatically every day at 9:00 AM UTC and generates a comprehensive status report that includes:

- **File Statistics**: Count of C/C++ files, PowerShell scripts, and CMake files
- **Recent Commit Activity**: Commits from the last 24 hours
- **Branch Information**: Current branch and total branch count
- **Latest Commit**: Details about the most recent commit
- **Recent Workflow Status**: Status of the last 10 workflow runs on the main branch
- **Open Issues and Pull Requests**: Current count of open issues and PRs
- **Recently Updated Issues**: Issues updated in the last 7 days

## How It Works

1. **Scheduled Execution**: The workflow runs daily via GitHub Actions cron schedule
2. **Report Generation**: Uses the `scripts/generate-daily-status.sh` script to collect repository metrics
3. **Workflow Status**: Queries the GitHub API to get recent workflow run statuses
4. **Issue Tracking**: Fetches open issues and PRs from the GitHub API
5. **Issue Creation**: Creates a new GitHub issue with the report or updates the existing one for the day
6. **Artifact Upload**: Saves the report as an artifact for 30 days

## Manual Execution

You can manually trigger the workflow in two ways:

### Via GitHub Actions UI
1. Go to the Actions tab in the repository
2. Select "Daily Status Report" from the workflows list
3. Click "Run workflow" and select the branch

### Via GitHub CLI
```bash
gh workflow run daily-status.yml
```

## Local Testing

You can generate a status report locally using the script:

```bash
cd /path/to/msquic
./scripts/generate-daily-status.sh output_report.md
```

This will create a basic status report without the GitHub-specific information (workflow runs, issues, PRs).

### Validating the Workflow

To validate the workflow file syntax:

```bash
# Check YAML syntax
python3 -c "import yaml; yaml.safe_load(open('.github/workflows/daily-status.yml'))"

# Or use yamllint if available
yamllint .github/workflows/daily-status.yml
```

Note: The workflow file uses `on:` as a trigger keyword, which YAML parsers may interpret as a boolean. This is expected and GitHub Actions handles it correctly.

## Permissions

The workflow requires the following permissions:
- `contents: read` - To checkout the repository
- `issues: write` - To create and update status report issues
- `actions: read` - To query workflow run status

## Output

The workflow produces two outputs:
1. **GitHub Issue**: A daily issue with the status report (labeled as "daily-status")
2. **Artifact**: A markdown file uploaded as a workflow artifact (retained for 30 days)

## Files

- `.github/workflows/daily-status.yml` - The GitHub Actions workflow definition
- `scripts/generate-daily-status.sh` - Shell script to generate the basic status report

## Customization

You can customize the workflow by:
- Changing the schedule in the workflow file (cron expression)
- Modifying the report sections in `scripts/generate-daily-status.sh`
- Adding additional metrics or checks in the workflow steps
- Changing the retention period for artifacts (default: 30 days)

## Troubleshooting

If the workflow fails:
1. Check the workflow run logs in the Actions tab
2. Verify that the repository has the required permissions
3. Ensure the GitHub API is accessible
4. Test the `generate-daily-status.sh` script locally

## Future Enhancements

Potential improvements for the workflow:
- Add code coverage metrics
- Include test results summary
- Track release information
- Monitor security alerts
- Send notifications via Slack/email
- Generate trend charts over time
