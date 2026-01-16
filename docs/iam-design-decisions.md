### TASK 1 — User Authentication & Identity

First question: Who is the user, and how they authenticate?

Why permissions are attached to groups, not users
Groups scale better than user-by-user permissions and reduce permission drift over time.

Why no access keys for human users
Long-lived access keys increase risk. For AWS services, roles should be used; for humans, prefer console access with MFA (and later, SSO).



