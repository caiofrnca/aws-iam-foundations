AWS IAM Foundations

This repository is part of my AWS Solutions Architect Associate (SAA-C03) "Build as I learn" journey:

This repo demonstrates practical and architectural understanding of AWS Identity and Access Management (IAM).The goal is to design and implement secure, least-privilege access patterns using users, groups, roles, and policies, aligned with AWS best practices and focuses on how AWS expects identity to be designed, not just configured.

Objectives:
  * Understand the difference between authentication and authorization
  * Implement least-privilege access using custom IAM policies
  * Use IAM roles instead of long-lived credentials
  * Apply security best practices such as MFA and access analysis

What Was Built:

  1 - IAM Users and Groups
  * Separate users for administrative, developer, and read-only access
  * Group-based permission management
  * Explicit avoidance of user-attached permissions where possible
  
  2 - IAM Policies
  * Custom JSON policy granting read-only access to S3
  * Comparison between AWS-managed and customer-managed policies
  * Policy evaluation logic (Allow, Deny, implicit deny)
  
  3 - IAM Roles
  * IAM role assumed by an EC2 instance to access AWS services
  * Trust policy configuration
  * No use of access keys for AWS services
  
  4 - Multi-Factor Authentication (MFA)
  * MFA enforced for privileged users
  * Explanation of risk reduction for compromised credentials
  
  5 - IAM Security Tools
  * IAM Access Analyzer
  * Credential reports
  * Identification of overly permissive access

Repository Structure:
```bash
aws-iam-foundations/
├── README.md
├── docs/
│ ├── iam-design-decisions.md
│ └── least-privilege-examples.md
├── policy-examples/
│ ├── s3-readonly-custom-policy.json
│ └── ec2-assume-role-trust-policy.json
├── cli-commands/
│ └── commands.md
└── evidences/screenshot
```
Key Design Decisions:
  * Roles over access keys:
      Wherever possible, IAM roles are used instead of long-lived access keys. This reduces credential exposure and limits the blast radius if something is misconfigured or compromised.
  
  * Group-based access control:
      Permissions are assigned to groups rather than individual users. This makes access management easier to scale and avoids inconsistent or duplicated permissions as more users are added.
  
  * Least privilege by default:
      Access is intentionally limited to only what is required. Even when using AWS-managed policies during early learning, the goal is to progressively move toward more tightly scoped  permissions.
  
  * Separation of human and machine identities:
      IAM users are used to represent people, while IAM roles are used for workloads and AWS services. This separation keeps access models clear and reduces security risk.

Security Considerations:
  * MFA enabled for all privileged users
  * No access keys committed or stored
  * Explicit denial over broad allow policies
  * Continuous review using IAM Access Analyzer

Lessons Learned:
  * Most IAM security issues are design problems, not configuration mistakes, think before create!
  * IAM roles fundamentally change how cloud security should be approached
  * Simpler/clear policies are safer than overly flexible ones

Next Improvements:
  * Permission boundaries for delegated administration
  * SCPs using AWS Organizations
  * Temporary credentials via STS federation

References:
  * AWS IAM Documentation (https://docs.aws.amazon.com/iam/)
  * AWS Well-Architected Framework – Security Pillar
  * AWS Solutions Architect – Associate (SAA-C03)

Status
* Phase 1 – Foundations (In Progress)
