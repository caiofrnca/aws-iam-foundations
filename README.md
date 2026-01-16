# aws-iam-foundations

Overview

This project demonstrates practical and architectural understanding of AWS Identity and Access Management (IAM).
The goal is to design and implement secure, least-privilege access patterns using users, groups, roles, and policies, aligned with AWS best practices.

This repository is part of my AWS Solutions Architect – Associate (SAA-C03) learning path and focuses on how AWS expects identity to be designed, not just configured.

Objectives

Understand the difference between authentication and authorization

Implement least-privilege access using custom IAM policies

Use IAM roles instead of long-lived credentials

Apply security best practices such as MFA and access analysis

What Was Built
1. IAM Users and Groups

Separate users for administrative, developer, and read-only access

Group-based permission management

Explicit avoidance of user-attached permissions where possible

2. IAM Policies

Custom JSON policy granting read-only access to S3

Comparison between AWS-managed and customer-managed policies

Policy evaluation logic (Allow, Deny, implicit deny)

3. IAM Roles

IAM role assumed by an EC2 instance to access AWS services

Trust policy configuration

No use of access keys for AWS services

4. Multi-Factor Authentication (MFA)

MFA enforced for privileged users

Explanation of risk reduction for compromised credentials

5. IAM Security Tools

IAM Access Analyzer

Credential reports

Identification of overly permissive access

Repository Structure
aws-iam-foundations/
├── README.md
├── docs/
│   ├── iam-design-decisions.md
│   └── least-privilege-examples.md
├── policy-examples/
│   ├── s3-readonly-custom-policy.json
│   └── ec2-assume-role-trust-policy.json
├── cli-commands/
│   └── commands.md
└── evidence/
    └── screenshots/

Key Design Decisions

Roles over access keys
IAM roles eliminate long-lived credentials and reduce blast radius.

Group-based access control
Permissions are assigned to groups, not individual users, for scalability.

Least privilege by default
Policies are scoped to specific actions and resources.

Separation of human and machine identities
Users represent people; roles represent workloads.

Security Considerations

MFA enabled for all privileged users

No access keys committed or stored

Explicit denial preferred over broad allow policies

Continuous review using IAM Access Analyzer

Lessons Learned

Most IAM security issues are design problems, not configuration mistakes

IAM roles fundamentally change how cloud security should be approached

Simpler policies are safer than overly flexible ones

Next Improvements

Permission boundaries for delegated administration

SCPs using AWS Organizations

Temporary credentials via STS federation

References

AWS IAM Documentation

AWS Well-Architected Framework – Security Pillar

AWS Solutions Architect – Associate (SAA-C03)

Status: Phase 1 – Foundations (In Progress)
