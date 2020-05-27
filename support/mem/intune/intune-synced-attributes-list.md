---
title: Attributes list synced by Intune
description: Describes a table that lists the attributes that are synced from the on-premises Active Directory Domain Services to Intune.
ms.date: 05/11/2020
ms.prod-support-area-path:
ms.reviewer: colinfr
---
# List of attributes that are synced by Microsoft Intune

This article documents the attributes that are synced from the on-premises Active Directory Domain Services (AD DS) to Microsoft Intune.

_Original product version:_ &nbsp; Microsoft Intune  
_Original KB number:_ &nbsp; 3033218

## Attributes synced by Microsoft Intune

The following table lists the attributes that are synced from the on-premises AD DS to Microsoft Intune.

> [!NOTE]
> Be aware that objects must contain values in the following attributes to be considered for sync:

|Attribute name|User|Contact|Group|Intune required|Description of attribute|
|---|---|---|---|---|---|
| AccountEnabled|X|||X|States whether the account is active|
| c|X|X||X|Country code|
| cn|X||X||Common name of the object|
| description|X|X|X|X|Human-readable descriptive phrases about the object|
| displayName|X|X|X|X|Display name for the object, usually the combination of the user's first name, middle initial, and last name|
| mail|X|X|X|X|Lists the email addresses for a user or contact|
| mailnickname|X|X|X|X|Friendly name for mail|
| member|||X|X|Object, not attribute|
| objectSID|X||||Unique object ID|
| proxyAddresses|X|X|X|X|The address by which a Microsoft Exchange Server recipient object is recognized in a foreign mail system|
| pwdLastSet|X||||Stores the time of last password change|
| securityEnabled|||X|X|Specifies whether the group is a security group|
| sourceAnchor|X|X|||Each account in your local on-premises environment will be linked to the corresponding Azure AD account through the `sourceAnchor` value|
| usageLocation|X||||Usage location|
| userPrincipalName|X||X|X|UPN|
|||||||
