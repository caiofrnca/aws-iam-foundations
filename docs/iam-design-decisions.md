### TASK 1 — User Authentication & Identity

First question: Who is the user, and how they authenticate?

Why permissions are attached to groups, not users?
  * Groups scale better than user-by-user permissions and reduce permission drift over time.

Why no access keys for human users?
  * Long-lived access keys increase risk. For AWS services, roles should be used; for humans, prefer console access with MFA (and later, SSO).

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






