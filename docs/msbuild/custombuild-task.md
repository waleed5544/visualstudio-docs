---
title: CustomBuild Task | Microsoft Docs
description: This article describes the MSBuild CustomBuild task, which is used by MSBuild to support customizing the C++ build process.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
---
# CustomBuild task

Wraps the Microsoft C++ compiler tool, cmd.exe. This class derives from [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), but does not use file tracking to discover file dependencies. All dependencies should be explicitly specified as AdditionalDependencies for incremental build working properly.

## Parameters

The following table describes the parameters of the **CustomBuild** task.

|Parameter|Description|
|---------------|-----------------|
|**BuildSuffix**|Optional **string** parameter.|
|**Sources**|Required **ITaskItem[]** parameter.|
|**TrackerLogDirectory**|Optional **string** parameter.|

## See also

[Task reference](../msbuild/msbuild-task-reference.md)
