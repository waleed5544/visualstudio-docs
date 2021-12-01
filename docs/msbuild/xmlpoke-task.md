---
title: XmlPoke Task | Microsoft Docs
description: Learn how MSBuild uses the XmlPoke task to set values as specified by an XPath query into an XML file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
---
# XmlPoke task

Sets values as specified by an XPath query into an XML file.

## Parameters

 The following table describes the parameters of the `XmlPoke` task.

|Parameter|Description|
|---------------|-----------------|
|`Namespaces`|Optional `String` parameter.<br /><br /> Specifies the namespaces for XPath query prefixes. `Namespaces` is an XML snippet consisting of `Namespace` elements with attributes `Prefix` and `Uri`. The attribute `Prefix` specifies the prefix to associate with the namespace specified in `Uri` attribute. Do not use an empty `Prefix`.|
|`Query`|Optional `String` parameter.<br /><br /> Specifies the XPath query.|
|`Value`|Required <xref:Microsoft.Build.Framework.ITaskItem> parameter.<br /><br /> Specifies the value to be inserted into the specified path.|
|`XmlInputPath`|Optional <xref:Microsoft.Build.Framework.ITaskItem> parameter.<br /><br /> Specifies the XML input as a file path.|

## Remarks

 In addition to having the parameters that are listed in the table, this task inherits parameters from the <xref:Microsoft.Build.Tasks.TaskExtension> class, which itself inherits from the <xref:Microsoft.Build.Utilities.Task> class. For a list of these additional parameters and their descriptions, see [TaskExtension base class](../msbuild/taskextension-base-class.md).

## Example

Here is a sample.xml to modify:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

In this example, if you want to modify `/Package/mp:PhoneIdentity/PhoneProductId`, then use

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` is here used as an artificial namespace prefix for default namespace.

## See also

- [Tasks](../msbuild/msbuild-tasks.md)
- [Task reference](../msbuild/msbuild-task-reference.md)
