## TASK 3 — IAM Role for EC2 (S3 Read-Only)

### 1) Create IAM role with EC2 trust policy

```bash
aws iam create-role \
  --role-name EC2S3ReadOnlyRole \
  --assume-role-policy-document file://policy-examples/ec2-trust-policy.json
```
