### Least Privilege - Practical Notes

This document captures how the principle of least privilege is applied throughout this repository, along with areas intentionally left broader during early learning stages.

The goal is not perfection from day one, but progressive tightening of access as understanding improves.

#### TASK 1 - Baseline Access Model
For the initial IAM foundations, AWS-managed policies were used to establish clear access boundaries:

- Admins → `AdministratorAccess`  
- Developers → `PowerUserAccess`  
- ReadOnly → `ReadOnlyAccess`  

These policies provide a reliable baseline while learning core IAM concepts such as users, groups, and role separation.

Why AWS-managed policies were used initially?
  * During early learning, AWS-managed policies reduce the risk of misconfiguration and allow focus on understanding how access is evaluated rather than debugging policy syntax.

Using managed policies at this stage also makes it easier to reason about:
  - What actions are implicitly allowed
  - Which services are accessible by each role
  - How permission boundaries affect real usage

Known Limitations:

Some of the permissions granted at this stage are intentionally broader than what would be acceptable in production:
  - `PowerUserAccess` allows access to many services beyond what is strictly required
  - `AdministratorAccess` bypasses most guardrails

Planned Improvements:

As this repository evolves, the following improvements are planned:
  - Replace `PowerUserAccess` with custom, service-specific policies
  - Scope permissions to specific resources where possible
  - Introduce permission boundaries for delegated access
  - Validate permissions using IAM Access Analyzer

Key Takeaway:
  * Least privilege is not a one-time configuration.  
  * It is an iterative process that improves as systems, requirements, and understanding evolve.





