## TASK 3 - IAM Role for EC2 (S3 Read-Only)

1 - Create IAM role with EC2 trust policy

```bash
aws iam create-role \
  --role-name EC2S3ReadOnlyRole \
  --assume-role-policy-document file://policy-examples/ec2-trust-policy.json
```
to verify:
```bash
aws iam get-role --role-name EC2S3ReadOnlyRole
```
2 - Create permission policy for the role:
```bash
aws iam create-policy \
  --policy-name EC2S3ReadOnlyPolicy \
  --policy-document file://policy-examples/ec2-s3-readonly-policy.json
```
Verify:
```bash
aws iam list-policies --scope Local
```
3 - Attach permission policy to the role:
```bash
aws iam attach-role-policy \
  --role-name EC2S3ReadOnlyRole \
  --policy-arn arn:aws:iam::<ACCOUNT_ID>:policy/EC2S3ReadOnlyPolicy
```
Verify:
```bash
aws iam list-attached-role-policies --role-name EC2S3ReadOnlyRole
```
4 - Attach Role to EC2

To attach the new role to an already created EC2 instance:

```bash
aws ec2 associate-iam-instance-profile \
  --instance-id <INSTANCE_ID> \
  --iam-instance-profile Name=EC2S3ReadOnlyRole
```
