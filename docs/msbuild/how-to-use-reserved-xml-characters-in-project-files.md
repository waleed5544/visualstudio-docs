---
title: 'How to: Use Reserved XML Characters in Project Files | Microsoft Docs'
description: Learn how to replace reserved XML characters with corresponding named entities in MSBuild project files.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
---
# How to: Use reserved XML characters in project files

When you author project files, you might need to use reserved XML characters, for example, in property values or in task parameter values. However, some reserved characters must be replaced by a named entity so that the project file can be parsed.

## Use reserved characters

 The following table describes the reserved XML characters that must be replaced by the corresponding named entity so that the project file can be parsed.

|Reserved character|Named entity|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### To use double quotes in a project file

- Replace the double quotes with the corresponding named entity, &amp;quot;. For example, to place double quotes around the `EXEFile` item list, type:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## Example

 In the following code example, double quotes are used to highlight the file name in the message that is output by the project file.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## See also

- [MSBuild reference](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
