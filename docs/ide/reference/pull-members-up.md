---
title: Pull Members Up
description: Learn how to use the Quick Actions and Refactorings menu to pull members up to the base type.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
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
# Pull members up

This refactoring applies to:

- C#

- Visual Basic

**What:** Lets you pull members up to the base type.

**When:** You have implemented an interface and you want to move a member to the base type.

**Why:** Pulling members up enables other implementations of your interface to inherit those members as well.

## How-to

1. Place your cursor in any member of an implemented interface.
2. Press **Ctrl**+**.** to trigger the **Quick Actions and Refactorings** menu.

   ![Pull Members up](media/pull-members-up.png)

2. Select **Pull Members up to base type**.

3. In the dialog, select what members you would like to add to the selected interface.

   ![Pull Member up](media/pull-members-up-dialog.png)

4. Choose **OK**. The selected members are pulled up to the interface.

   ![Pull Member up completed](media/pull-members-up-completed.png)

## See also

- [Refactoring](../refactoring-in-visual-studio.md)
