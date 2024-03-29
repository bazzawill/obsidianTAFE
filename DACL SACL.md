## Discretionary Access Control List (DACL) and a System Access Control List (SACL).
Generally, a DACL is used for controlling access to an object, and a SACL is used to account for and log access attempts. This section will examine the DACL, but the same concepts would apply to a SACL.

D:(A;;CCLCSWRPLORC;;;AU)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;SY)
This amalgamation of characters crunched together and delimited by opened and closed parentheses is in a format known as the Security Descriptor Definition Language (SDDL).

We may be tempted to read from left to right because that is how the English language is typically written, but it can be much different when interacting with computers. Read the entire security descriptor for the Windows Update (wuauserv) service in this order starting with the first letter and set of parentheses:

D: (A;;CCLCSWRPLORC;;;AU)
Using the Get-Acl PowerShell cmdlet, we can examine service permissions by targeting the path of a specific service in the registry.ters are DACL permissions

D: - the proceeding characGenerally, a DACL is used for controlling access to an object, and a SACL is used to account for and log access attempts. This section will examine the DACL, but the same concepts would apply to a SACL.

D:(A;;CCLCSWRPLORC;;;AU)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;SY)
This amalgamation of characters crunched together and delimited by opened and closed parentheses is in a format known as the Security Descriptor Definition Language (SDDL).

We may be tempted to read from left to right because that is how the English language is typically written, but it can be much different when interacting with computers. Read the entire security descriptor for the Windows Update (wuauserv) service in this order starting with the first letter and set of parentheses:

D: (A;;CCLCSWRPLORC;;;AU)

D: - the proceeding characters are DACL permissions
AU: - defines the security principal Authenticated Users
A;; - access is allowed
CC - SERVICE_QUERY_CONFIG is the full name, and it is a query to the service control manager (SCM) for the service configuration
LC - SERVICE_QUERY_STATUS is the full name, and it is a query to the service control manager (SCM) for the current status of the service
SW - SERVICE_ENUMERATE_DEPENDENTS is the full name, and it will enumerate a list of dependent services
RP - SERVICE_START is the full name, and it will start the service
LO - SERVICE_INTERROGATE is the full name, and it will query the service for its current status
RC - READ_CONTROL is the full name, and it will query the security descriptor of the service
As we read the security descriptor, it can be easy to get lost in the seemingly random order of characters, but recall that we are essentially viewing access control entries in an access control list. Each set of 2 characters in between the semi-colons represents actions allowed to be performed by a specific user or group.

;;CCLCSWRPLORC;;;

After the last set of semi-colons, the characters specify the security principal (User and/or Group) that is permitted to perform those actions.

;;;AU

The character immediately after the opening parentheses and before the first set of semi-colons defines whether the actions are Allowed or Denied.

A;;

This entire security descriptor associated with the Windows Update (wuauserv) service has three sets of access control entries because there are three different security principals. Each security principal has specific permissions applied.

Examine service permissions using PowerShell
Using the Get-Acl PowerShell cmdlet, we can examine service permissions by targeting the path of a specific service in the registry.
ters are DACL permissions
AU: - defines the security principal Authenticated Users
A;; - access is allowed
CC - SERVICE_QUERY_CONFIG is the full name, and it is a query to the service control manager (SCM) for the service configuration
LC - SERVICE_QUERY_STATUS is the full name, and it is a query to the service control manager (SCM) for the current status of the service
SW - SERVICE_ENUMERATE_DEPENDENTS is the full name, and it will enumerate a list of dependent services
RP - SERVICE_START is the full name, and it will start the service
LO - SERVICE_INTERROGATE is the full name, and it will query the service for its current status
RC - READ_CONTROL is the full name, and it will query the security descriptor of the service
As we read the security descriptor, it can be easy to get lost in the seemingly random order of characters, but recall that we are essentially viewing access control entries in an access control list. Each set of 2 characters in between the semi-colons represents actions allowed to be performed by a specific user or group.

;;CCLCSWRPLORC;;;

After the last set of semi-colons, the characters specify the security principal (User and/or Group) that is permitted to perform those actions.

;;;AU

The character immediately after the opening parentheses and before the first set of semi-colons defines whether the actions are Allowed or Denied.

A;;

This entire security descriptor associated with the Windows Update (wuauserv) service has three sets of access control entries because there are three different security principals. Each security principal has specific permissions applied.

Examine service permissions using PowerShell
Using the Get-Acl PowerShell cmdlet, we can examine service permissions by targeting the path of a specific service in the registry.