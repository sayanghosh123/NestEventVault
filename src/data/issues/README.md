# Issue Import Schema

This directory contains issue definition files that can be automatically imported into the repository using the GitHub Actions workflow.

## Supported Formats

### YAML Format

```yaml
issues:
  - title: "Issue Title"
    body: |
      Issue description with multiple lines
      supported using YAML multiline syntax
    labels:
      - "enhancement"
      - "bug"
    assignees:
      - "username1"
      - "username2"
    milestone: "v1.0"
    imported: false
    url: null
    issue_no: null
```

### CSV Format

```csv
title,body,labels,assignees,milestone,imported,url,issue_no
"Issue Title","Issue description","label1,label2","user1,user2","v1.0",false,,
```

## Schema Fields

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| `title` | string | Yes | - | The issue title |
| `body` | string | No | "" | The issue description/body |
| `labels` | array/string | No | [] | Labels to apply (comma-separated in CSV) |
| `assignees` | array/string | No | [] | Users to assign (comma-separated in CSV) |
| `milestone` | string | No | null | Milestone name or number |
| `imported` | boolean | No | false | Whether the issue has been imported |
| `url` | string | No | null | URL of the created issue (populated after import) |
| `issue_no` | number | No | null | Issue number (populated after import) |

## Workflow

When files in this directory are modified and pushed to the main branch, the GitHub Actions workflow will:

1. Process all issue definition files
2. Create GitHub issues for any entries with `imported: false`
3. Update the definition files with the created issue URLs and numbers
4. Set `imported: true` for successfully created issues
5. Commit the updated files back to the repository

## Usage

1. Add your issue definitions to files in this directory (`.yml`, `.yaml`, or `.csv` format)
2. Commit and push the changes to the main branch
3. The workflow will automatically process the files and create the issues
4. Check the updated files to see the populated `url` and `issue_no` fields

## Examples

- `example-issues.yml` - YAML format with multiple issues
- `additional-issues.csv` - CSV format example