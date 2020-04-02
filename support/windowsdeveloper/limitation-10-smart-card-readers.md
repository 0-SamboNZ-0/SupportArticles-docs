---
title: Limitation of 10 smart card readers
description: Explains that Windows Server 2012, Windows 8, and later versions of Windows Server and Windows are limited to using 10 smartcard readers.
ms.date: 03/16/2020
ms.prod-support-area-path: 
---
# Limitation of 10 smartcard readers in Windows Server 2012 R2, Windows 8, and later

_Original product version:_ &nbsp; Windows Server 2012 and later versions, Windows 8 and later versions  
_Original KB number:_ &nbsp; 3144446

Starting in Windows 8, the Windows platform supports a maximum of 10 smartcard readers. If more than 10 smartcard readers are available, APIs such as `SCardListReaders` return a maximum of 10. All other readers are ignored.

Although the Smart Card APIs never enforced a reader limit, some parts of the system were limited to 10 smartcard readers. This sometimes caused sporadic errors when `SCard` APIs were used over terminal server redirection. There were also some performance issues that occurred in this situation. To resolve these issues, a limit of 10 smartcard was built into the APIs and other parts of the code. This made it consistent with the whole smartcard stack.
