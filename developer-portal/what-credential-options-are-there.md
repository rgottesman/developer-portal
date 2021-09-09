### What credential options are there?

Your authentication token gives you access to the API operations
according to your role and its credentials. The different credentials
are described in the following table::

| Role     | Credentials                                               |
|----------|-----------------------------------------------------------|
| Reseller partner | Reseller partners can create organizations, sub-partners, and reseller partner contacts. They can make any calls related to organizations and reseller partners. Additionally, they can make calls related to a specific organization, such as adding devices or modifying events.<br><br> Reseller partners can also create a token with admin credentials that is valid for twenty-four hours to authenticate any calls sent during that time for a specific organization. They can give this token to others to use, without having to create a permanent user with admin credentials. For more information about this token, see [Organization authentication](organization-authentication.md). |
| Sub-partners | Sub-partnerss can create organizations. They can make any calls related to organizations and reseller partners. Additionally, they can make calls related to a specific organization, such as adding devices or modifying events. |
| Admin    | Administrators can make calls related to a specific organization, such as adding devices or modifying events. |
| Supervisor | Supervisors have the same credentials as an administrator, but cannot add, modify or remove users. |
| User     | Users have the came credentials as a supervisor, but cannot add new devices or create new groups. |
| Restriced | Restricted users are defined in the system but cannotmake any calls. |
