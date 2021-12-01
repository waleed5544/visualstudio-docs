---
title: "&lt;customErrorReporting&gt; Element (ClickOnce Deployment) | Microsoft Docs"
description: The customErrorReporting element specifies a URI to show when an error occurs instead of an error dialog box showing the exception stack.
ms.custom: SEO-VS-2020
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords:
  - "<customErrorReporting> element [ClickOnce deployment manifest]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
  - "multiple"
---
# &lt;customErrorReporting&gt; element (ClickOnce deployment)
Specifies a URI to show when an error occurs.

## Syntax

```xml
<customErrorReporting
   uri
/>
```

## Remarks
 This element is optional. Without it, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] displays an error dialog box showing the exception stack. If the `customErrorReporting` element is present, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] will instead display the URI indicated by the `uri` parameter. The target URI will include the outer exception class, the inner exception class, and the inner exception message as parameters.

 Use this element to add error reporting functionality to your application. Since the generated URI includes information about the type of error, your Web site can parse that information and display, for example, an appropriate troubleshooting screen.

## Example
 The following snippet shows the `customErrorReporting` element, together with the generated URI it might produce.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## See also
- [ClickOnce deployment manifest](../deployment/clickonce-deployment-manifest.md)