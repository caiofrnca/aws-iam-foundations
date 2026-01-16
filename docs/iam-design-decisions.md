### TASK 1 - User Authentication & Identity

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








