## TASK 2 — Custom IAM Policy (S3 Read-Only)

1 - Create customer-managed policy

```bash
aws iam create-policy \
  --policy-name S3ReadOnlyCustom \
  --policy-document file://policy-examples/s3-readonly-custom-policy.json
```
verify:
```bash
aws iam list-policies --scope Local
```
2 - Detach AWS-managed ReadOnlyAccess from ReadOnly group
```bash
aws iam detach-group-policy \
  --group-name ReadOnly \
  --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess
```
  3 - Attach custom policy to ReadOnly group
```bash
  aws iam attach-group-policy \
  --group-name ReadOnly \
  --policy-arn arn:aws:iam::<ACCOUNT_ID>:policy/S3ReadOnlyCustom
```
  verify
  ```bash
aws iam list-attached-group-policies --group-name ReadOnly
```
  
