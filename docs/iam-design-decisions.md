## TASK 1 — Identity model choices

Why permissions are attached to groups, not users
Groups scale better than user-by-user permissions and reduce permission drift over time.

Why no access keys for human users
Long-lived access keys increase risk. For AWS services, roles should be used; for humans, prefer console access with MFA (and later, SSO).

