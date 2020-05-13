---
title: HTTP Error 403.14 with IIS webpages
description: Describes the problem in which you may receive an HTTP Error 403.14 error message when you visit a Web site that is hosted on IIS 7.0.
ms.date: 04/16/2020
ms.prod-support-area-path:
---
# HTTP Error 403.14 - Forbidden when you open an IIS Webpage

This article provides information about resolving the **HTTP Error 403.14 - Forbidden** error when you open an Internet Information Services (IIS) Webpage.

_Original product version:_ &nbsp; Internet Information Services 7.0 and later versions  
_Original KB number:_ &nbsp; 942062

> [!NOTE]
> The target audience for this article is website administrators or web developers.

## Symptoms

You have a Web site that is hosted on IIS 7.0 or a later version. When you visit the Web site in a Web browser, you may receive an error message that resembles the following:

> Server Error in Application "**application name**"  
> HTTP Error 403.14 - Forbidden  
> HRESULT: 0x00000000  
> Description of HRESULT : The Web server is configured to not list the contents of this directory.

## Resolution for end users

If you are an end user, you should contact the website administrators in order to let them know that this error has occurred for this URL address. Then, the website administrators will fix this issue later.

## Resolution for site administrators

This problem occurs because the Web site does not have the Directory Browsing feature enabled, and the default document is not configured. To resolve this problem, use one of the following methods:

### Method 1: Enable the Directory Browsing feature in IIS (Recommended)

To resolve this problem, follow these steps:

1. Start IIS Manager. To do this, click **Start**, click **Run**, type *inetmgr.exe*, and then click **OK**.
2. In IIS Manager, expand **server name**, expand **Web sites**, and then click the website that you want to modify.
3. In the **Features** view, double-click **Directory Browsing**.
4. In the **Actions** pane, click **Enable**.

### Method 2: Add a default document

To resolve this problem, follow these steps:

1. Start IIS Manager. To do this, click **Start**, click **Run**, type *inetmgr.exe*, and then click **OK**.
2. In IIS Manager, expand **server name**, expand **Web sites**, and then click the website that you want to modify.
3. In the **Features** view, double-click **Default Document**.
4. In the **Actions** pane, click **Enable**.
5. In the **File Name** box, type the name of the default document, and then click **OK**.

### Method 3: Enable the Directory Browsing feature in IIS Express

> [!NOTE]
> This method is for the web developers who experience the issue when they use IIS Express.

To do this, follow these steps:

1. Open a command prompt, and then go to the IIS Express folder on your computer. For example, go to the following folder in a command prompt:

    ```console
    C:\Program Files\IIS Express
    ```

2. Type the following command, and then press Enter:

    ```console
    appcmd set config /section:directoryBrowse /enabled:true
    ```

For more information about the appcmd.exe command lines, view [Getting Started with AppCmd.exe](http://www.iis.net/learn/get-started/getting-started-with-iis/getting-started-with-appcmdexe).
