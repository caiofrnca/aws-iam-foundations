# TASK 1 - IAM Foundations — CLI Commands

Obj:
- Separate users for administrative, developer, and read-only access
- Group-based permission management
- Explicit avoidance of user-attached permissions where possible

Prerequisites:
Confirm AWS identity and CLI access:
  ```bash
  aws sts get-caller-identity
  aws iam get-account-summary

1 - Create Groups:
  ```bash
  aws iam create-group --group-name Admins
  aws iam create-group --group-name Developers
  aws iam create-group --group-name ReadOnly

To verify:
  ```bash
  aws iam list-groups

2 - Attach AWS-managed(pre-built) policies to groups:
  ```bash
  aws iam attach-group-policy \
    --group-name Admins \
    --policy-arn arn:aws:iam::aws:policy/AdministratorAccess
  
  aws iam attach-group-policy \
    --group-name Developers \
    --policy-arn arn:aws:iam::aws:policy/PowerUserAccess
  
  aws iam attach-group-policy \
    --group-name ReadOnly \
    --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess

To verify attached policies:
  ```bash
  aws iam list-attached-group-policies --group-name Admins
  aws iam list-attached-group-policies --group-name Developers
  aws iam list-attached-group-policies --group-name ReadOnly
  
3 - Create users (with no access keys):
  ```bash
  aws iam create-user --user-name admin-user
  aws iam create-user --user-name dev-user
  aws iam create-user --user-name readonly-user

To verify users:
  ```bash
  aws iam list-users

4 - Add users to groups:
  ```bash
  aws iam add-user-to-group --group-name Admins --user-name admin-user
  aws iam add-user-to-group --group-name Developers --user-name dev-user
  aws iam add-user-to-group --group-name ReadOnly --user-name readonly-user

To verify membership:
  ```bash
  aws iam get-group --group-name Admins
  aws iam get-group --group-name Developers
  aws iam get-group --group-name ReadOnly

