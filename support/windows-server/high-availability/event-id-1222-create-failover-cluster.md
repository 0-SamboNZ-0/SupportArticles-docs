---
title: Event ID 1222 when you create failover cluster
description: Resolves an issue in which event ID 1222 is generated in the System log when you create a Windows Server 2012 failover cluster.
ms.date: 09/11/2020
author: Deland-Han
ms.author: delhan
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: robsmi, kaushika
ms.prod-support-area-path: Setup and configuration of clustered services and applications
ms.technology: HighAvailability
---
# Event ID 1222 when you create a Windows Server 2012 failover cluster

This article provides a solution to solve an issue where the event ID 1222 is logged when you create a Windows Server 2012 failover cluster.

_Original product version:_ &nbsp; Windows Server 2012 R2  
_Original KB number:_ &nbsp; 2770582

## Symptoms

When you create a Windows Server 2012 failover cluster, the event ID 1222 is logged in the System log.

## Cause

When you create a Windows Server failover cluster, a Cluster Computer object for the cluster name is created in Active Directory Domain Services (AD DS). The object is called a Cluster Name Object (CNO).

A new feature in Windows Server 2012 flags Cluster Computer objects to prevent them being deleted accidentally. If you do not have sufficient rights to the organizational unit (OU) in AD DS where the Computer objects are being created, an event is logged that notifies you that the cluster objects are not protected from accidental deletion.

## Resolution

To resolve this issue, follow these steps:

1. Start Active Directory Administrative Center, and then select the tree view.
2. Select the CNO's organizational unit (OU).
3. Locate and right-click the CNO, and then click **Properties**.
4. Click to select the **Protect from accidental deletion**  check box, and then click **OK**.

> [!NOTE]
> Cluster Computer objects that are not protected from accidental deletion have no adverse effect on the functionality of the cluster. If you are not concerned about the unintentional deletion of Cluster Computer objects, you can safely ignore this warning.

## More information

To improve the level of protection and ability to recover from the accidental deletion of Custer Computer objects, we recommend that you enable the Active Directory Recycle Bin feature. For more information about how to do this, go to the following TechNet websites: [Step-by-step guide to the Active Directory Recycle Bin feature](https://technet.microsoft.com/library/dd392261%28v=ws.10%29.aspx) 

[How to configure accounts in Active Directory](https://technet.microsoft.com/library/cc731002%28v=ws.10%29.aspx) 
For more information about the failover cluster security model, click the following article number to view the article in Microsoft Knowledge Base: [947049](https://support.microsoft.com/help/947049) Description of the failover cluster security model in Windows Server 2008
For more information about Cluster Computer Objects, go to the following MSDN website: [How to identify stale Cluster Computer objects](https://blogs.msdn.com/b/clustering/archive/2011/08/17/10197069.aspx) 
For more information about the Protect object from accidental deletion option, go to the following TechNet website: [How to preventing unwanted or accidental deletions and how to restore deleted objects in Active Directory](https://blogs.technet.com/b/abizerh/archive/2009/06/09/preventing-unwanted-accidental-deletions-and-restore-deleted-objects-in-active-directory.aspx)
