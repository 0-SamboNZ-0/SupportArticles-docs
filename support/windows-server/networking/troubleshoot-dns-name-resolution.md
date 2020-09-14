---
title: Troubleshoot DNS name resolution on the Internet
description: Describes how to troubleshoot DNS name resolution on the Internet in Microsoft Windows Server.
ms.date: 09/08/2020
author: Deland-Han
ms.author: delhan
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: kaushika
ms.prod-support-area-path: DNS
ms.technology: Networking
---
# Troubleshoot DNS name resolution on the Internet in Windows Server

This article provides methods to troubleshoot Domain Name System (DNS) name resolution on the Internet in Microsoft Windows Server.

_Original product version:_ &nbsp; Windows Server 2012 R2  
_Original KB number:_ &nbsp; 816567

## Summary

This article describes methods that you can use to configure DNS if queries that are directed to the Internet are not resolved correctly, but local intranet name resolution functions correctly.

The Cache.dns file that stores root hints on your Windows Server 2003-based computer may be missing or damaged. You can manually add root hints by using the DNS snap-in, replace the Cache.dns file on your hard disk with the backup Cache.dns file or replace it with the original version of the Cache.dns file from the Windows Server 2003 CD.


### To update root hints by using the DNS snap-in

To update root hints:


#### On a non-domain controller

To manually add root hints on a Windows Server 2003-based DNS server that is not configured as a domain controller:

1. Click **Start**, point to
 **Administrative Tools**, and then click **DNS**.

2. In the right pane, right-click
 ****ServerName****, where
 **ServerName** is the name of the server, and then click
 **Properties**  
3. Click the **Root Hints** tab, and then click
 **Add**.
4. Specify the fully qualified domain name (FQDN) and the IP address of the root server that you want to add, and then click
 **OK**. 

#### On a domain controller

To update root hints on a Windows Server 2003-based DNS server that is configured as a domain controller:

1. Click **Start**, point to **Administrative Tools**, and then click **DNS**.
2. In the right pane, right-click
 ****ServerName****, where
 **ServerName** is the name of the server, and then click
 **Properties**  
3. Click the **Root Hints** tab.
4. Do one of the following:
   - Add a root server to the list. To do so, click **Add**, specify the FQDN and the IP address of the root server that you want to add, and then click **OK**.
   - Copy the root hints from another DNS server. To do so, click **Copy from Server**, specify the IP address of the DNS server where you want to copy the root hints from, and then click **OK**.
5. Click **OK**.

> [!NOTE]
> The following is a list root servers as specified by Network Solutions:a.root-servers.net. 198.41.0.4

b.root-servers.net. 128.9.0.107

c.root-servers.net. 192.33.4.12

d.root-servers.net. 128.8.10.90

e.root-servers.net. 192.203.230.10

f.root-servers.net. 192.5.5.241

g.root-servers.net. 192.112.36.41

h.root-servers.net. 128.63.2.53

i.root-servers.net. 192.36.148.17

j.root-servers.net. 192.58.128.30

k.root-servers.net. 193.0.14.129

l.root-servers.net. 198.32.64.12

m.root-servers.net. 202.12.27.33

### To copy and use the backup Cache.dns file

To rename and replace the Cache.dns file in the %SystemRoot%\System32\Dns folder with the backup Cache.dns file:

1. Click **Start**, and then click
 **Run**.
2. In the **Open** box, type
 cmd, and then click **OK**.
3. Stop the DNS service. To do so, at the command prompt, type
 net stop dns , and then press ENTER.
4. Rename the Cache.dns file in the %SystemRoot%\System32\Dns folder to Cache.old. To do so, at the command prompt, type the following lines. Press ENTER after each line: cd %systemroot%\Sytem32\Dns
ren cache.dns cache.old
copy backup\cache.dns 

5. Start the DNS service. To do so, at the command prompt, type net start dns, and then press ENTER.

### To copy and use the Cache.dns file from the Windows Server 2003 CD

To extract the Cache.dns file from the Windows Server 2003 CD to the %SystemRoot%\System32\Dns folder on the hard disk.

1. Click **Start**, and then click
 **Run**.
2. In the **Open** box, type
 cmd, and then click **OK**.
3. At the command prompt, type the following lines, where
 **Drive** is the drive letter of the computer's CD-ROM or DVD-ROM drive that contains the Windows Server 2003 CD. Press ENTER after each line: **Drive:
cd i386
expand cache.dn_ %systemroot%\System32\Dns\Cache.dns 

4. Type exit to quit Command Prompt.

## References

For additional information about how to configure DNS for Internet access in Windows Server 2003, click the following article number to view the article in the Microsoft Knowledge Base: [323380](/EN-US/help/323380) How To Configure DNS for Internet Access in Windows Server 2003  
 For additional information about how to install and configure DNS in Windows Server 2003, click the following article number to view the article in the Microsoft Knowledge Base: [814591](/EN-US/help/814591) How To Install and Configure DNS Server in Windows Server 2003  
