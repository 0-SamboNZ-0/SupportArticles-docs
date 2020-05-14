---
title: HTTP Error 404.13 when you visit website
description: Describes a problem that occurs because a client request contains a Content-Length header that is larger than the value that is specified for this header in the ApplicationHost.config file.
ms.date: 04/17/2020
ms.prod-support-area-path:
ms.reviewer: mlaing
---
# HTTP Error 404.13 - CONTENT_LENGTH_TOO_LARGE when you visit a web site that is hosted on a server that is running IIS 7.0

This article provides information about resolving the **HTTP Error 404.13 - CONTENT_LENGTH_TOO_LARGE** error when visiting a website in Internet Information Services (IIS).

_Original product version:_ &nbsp; Internet Information Services 7.0  
_Original KB number:_ &nbsp; 942074

## Symptoms

Consider the following scenario. You have a web site that is hosted on a server that is running IIS 7.0. When a user visits this web site, the user receives an error message that resembles the following error message:

> Server Error in Application "**application name**"  
> HTTP Error 404.13 - CONTENT_LENGTH_TOO_LARGE  
> HRESULT: 0  
> Description of HRESULT # The operation completed successfully.

## Cause

This problem occurs because the client request contains a `Content-Length` header that is larger than the value that is specified for this header in the `maxAllowedContentLength` property in the *ApplicationHost.config* file.

## Resolution

To resolve this problem, follow these steps:

1. Click **Start**. In the **Start Search** box, type *Notepad*. Right-click **Notepad**, and then click **Run as administrator**.

    > [!NOTE]
    > If you are prompted for an administrator password or for a confirmation, type the password, or click **Continue**.

2. On the **File** menu, click **Open**. In the **File name** box, type `%windir%\system32\inetsrv\config\applicationhost.config`, and then click **Open**.

3. In the *ApplicationHost.config* file, locate the `<requestLimits>` node.
4. Remove the `maxAllowedContentLength` property. Or, add a value that matches the size of the `Content-Length` header that the client sends as part of the request. By default, the value of the `maxAllowedContentLength` property is 30000000.

    For example, modify the following configuration data inside the `<requestFiltering>`section.

    ```xml
    <requestLimits maxAllowedContentLength ="<length>" />
    ```

5. Save the *ApplicationHost.config* file.
