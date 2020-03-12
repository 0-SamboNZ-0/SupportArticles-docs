---
title: V4 print drivers produce 0-byte spool file
description: Workaround V4 print drivers attempting to send PCL/Postscript data in RAW mode to a printer and producing a 0-byte spool file
ms.date: 03/09/2020
ms.prod-support-area-path:
ms.reviewer: v-mafect
---
# V4 Print Drivers using RAW mode to send PCL/Postscript have 0 byte spool file

This article explains how to workaround V4 print drivers attempting to send PCL/Postscript data in RAW mode to a printer and producing a 0-byte spool file.

_Original version:_ &nbsp; Windows 8  
_Original KB number:_ &nbsp; 2779300

## Symptoms

V4 print drivers attempting to send PCL/Postscript data in RAW mode to a printer produces a 0-byte spool file.

## Cause

V4 drivers are XPS-based drivers. RAW databases aren't compatible. Similar issues occur when using a v3 XPS printer driver (XPSDrv) with Vista or Windows 7.

## Resolution

Use XPS_PASS instead of RAW to pass information directly to the print filter pipeline in v4 and v3 XPSDrv drivers. Here's how to proceed with Windows 8:

1. Call GetPrinterDriver to retrieve the DRIVER_INFO_8 structure.
2. Check DRIVER_INFO_8::dwPrinterDriverAttributes for the PRINTER_DRIVER_XPS flag.
3. Choose your datatype based on the presence or absence of the flag:
    1. If the flag is set, use **XPS_PASS**.
    2. If the flag isn't set, use **RAW**.

## More Information

The XPS_PASS datatype was introduced in Windows Vista to pass XPS directly to the print filter pipeline for a v3 XPSDrv driver. That prevents overloading the RAW datatype for v3 drivers. XPS_PASS has replaced RAW for v4 drivers.

- [How To: Send Data Directly to an XPS Printer](https://msdn.microsoft.com/library/windows/desktop/ff686812%28v=vs.85%29.aspx)

- [GetPrinterDriver Function](https://msdn.microsoft.com/library/windows/desktop/dd144914%28v=vs.85%29.aspx)

- [DRIVER_INFO_8 Structure](https://msdn.microsoft.com/library/windows/hardware/ff548512%28v=vs.85%29.aspx)
