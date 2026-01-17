### TASK 1 - User Authentication & Identity - Notes

First question: Who is the user, and how they authenticate?
 * Before granting any permissions, it was important to define clear identity boundaries and access patterns.

Why permissions are attached to groups, not users?
  * Permissions are assigned to groups instead of individual users to keep access management scalable and consistent. As environments grow, group-based access helps avoid permission drift and makes it easier to change a user’s role without reconfiguring policies one by one.

Why no access keys for human users?
  * Long-lived access keys increase risk and are easy to misuse or leak. For AWS services and workloads, IAM roles are the preferred mechanism. For human users, console access combined with MFA provides stronger security and better visibility. In more mature environments, this would typically evolve toward centralized access using AWS SSO.

AWS Identity and Access Management (IAM)

Use when:
 * Authenticating AWS users, services, and workloads
 * Granting fine-grained permissions to AWS resources
 * Managing roles for EC2, Lambda, ECS, EKS
 * Enforcing least privilege inside AWS

Typical scenarios
 * EC2 instance needs S3 access → IAM Role
 * Lambda needs DynamoDB → IAM Role
 * Admins managing AWS console → IAM Users / Roles

Do NOT use IAM for:
 * End-user sign-up/login
 * Mobile or web application users

Exam signal:
“AWS internal authentication and authorization” → IAM

---

### TASK 2 - IAM Policies and Permission Evaluation

To better understand how IAM evaluates permissions, the AWS-managed `ReadOnlyAccess` policy was replaced with a created policy (`S3ReadOnlyCustom`) limited to Amazon S3 read-only actions.

Using a narrower policy makes allowed actions explicit and helps with troubleshooting and security reviews.

Managed vs customer-managed policies
* AWS-managed policies simplify policy management but are generally over-permissive. In contrast, customer-managed policies provide tighter, least-privilege access and better match practical access patterns.

Policy evaluation logic
* IAM evaluates permissions based on explicit allows, explicit denies, and implicit denies.  
* In this policy, only specific S3 read actions are explicitly allowed; all other actions are implicitly denied.
* Ex:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowListAndReadS3Objects",
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "s3:ListBucket",
        "s3:GetObject"
      ],
      "Resource": "*"
    }
  ]
}
```












