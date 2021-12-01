---
title: Unused values and parameters
description: Learn about unused value assignments, variables, and parameters and how they appear in the code editor in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
  - CSharp
  - VB
ms.workload:
  - "dotnet"
---
# Unused value assignments, variables, and parameters

This refactoring applies to:

- C#
- Visual Basic

**What:** Fades out unused parameters and generates a warning for unused expression values. The compiler also performs a flow analysis to find any unused value assignments. Unused value assignments fade out and a light bulb appears with a [Quick Action](../quick-actions.md) to remove the redundant assignment. Unused variables with unknown values show a [Quick Action](../quick-actions.md) suggestion to use [discards](/dotnet/csharp/discards) instead. (Discards are temporary, dummy variables that are intentionally unused in application code. They can reduce memory allocation and make your code easier to read.)

**When:** You have value assignments, parameters, or expression values that are never used.

**Why:** Sometimes it's difficult to tell if a value assignment, variable, or parameter is no longer being used. By fading out these values or generating a warning, you get a visual cue of what code you can delete.

## Unused expression values and parameters diagnostic

1. Have any value assignment, variable, or parameter that isn't used.
2. The unused value assignment or parameter appears faded out. The unused expression value generates a warning.

  ![Unused parameter](media/unused-parameter.png)
  ![Unused value](media/unused-value.png)
  ![Unused value assignment](media/unused-value-assignment.png)
  ![Unused value discard](media/unused-value-discard.png)

## See also

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tips for .NET Developers](../csharp-developer-productivity.md)
