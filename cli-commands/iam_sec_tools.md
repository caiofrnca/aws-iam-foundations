## TASK 5 — IAM Security tools

#### Objectives:
Use AWS IAM security tools to identify overly permissive access, unused credentials, and potential misconfigurations.

1 - Create IAM Access Analyzer
```bash
aws accessanalyzer create-analyzer --analyzer-name iam-foundations-analyzer --type ACCOUNT
```
Verify:
```bash
aws accessanalyzer list-analyzers
```
Check findings:
```bash
aws accessanalyzer list-findings --analyzer-name iam-foundations-analyzer
```

2 - Generate report:
(Helps identify users whithout MFA, unused passwords, old access keys, inactive accounts)

```bash
aws iam generate-credential-report
```
Then, retrieve it:
```bash
aws iam get-credential-report --query Content --output text
```

Decode and save locally:
```bash
aws iam get-credential-report --query Content --output text | Out-File credential-report.b64
```
decode & view on Powershell:
```bash
$decoded = [System.Text.Encoding]::UTF8.GetString(
  [System.Convert]::FromBase64String(
    (aws iam get-credential-report --query Content --output text)
  )
)

$decoded
```
decode & view as csv:
```bash
aws iam get-credential-report `
  --query Content `
  --output text | `
  ForEach-Object {
    [System.Text.Encoding]::UTF8.GetString(
      [System.Convert]::FromBase64String($_)
    )
  } | Out-File credential-report.csv
```