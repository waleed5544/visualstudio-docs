---
title: Parameter info, list members, and quick info
description: "Learn how to use these IntelliSense features:  List Members, Parameter Info, Quick Info, and Complete Word."
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
---
# IntelliSense in Visual Studio

IntelliSense is a code-completion aid that includes a number of features: List Members, Parameter Info, Quick Info, and Complete Word. These features help you to learn more about the code you're using, keep track of the parameters you're typing, and add calls to properties and methods with only a few keystrokes.

Many aspects of IntelliSense are language-specific. For more information about IntelliSense for different languages, see the topics listed in the [See also](#see-also) section.

## List Members

A list of valid members from a type (or namespace) appears after you type a trigger character (for example, a period (`.`) in managed code or `::` in C++). If you continue typing characters, the list is filtered to include only the members that begin with those characters or where the beginning of *any* word within the name starts with those characters. IntelliSense also performs "camel case" matching, so you can just type the first letter of each camel-cased word in the member name to see the matches.

After selecting an item, you can insert it into your code by pressing **Tab** or by typing a space. If you select an item and type a period, the item appears followed by the period, which brings up another member list. When you select an item but before you insert it, you get Quick Info for the item.

In the member list, the icon to the left represents the type of the member, such as namespace, class, function, or variable. For a list of icons, see [Class View and Object Browser icons](../ide/class-view-and-object-browser-icons.md). The list may be quite long, so you can press **PgUp** and **PgDn** to move up or down in the list.

![Visual Studio Member List](../ide/media/vs2015_intellisense.png)

You can invoke the **List Members** feature manually by typing **Ctrl**+**J**, choosing **Edit** > **IntelliSense** > **List Members**, or by choosing the **List Members** button on the editor toolbar. When it is invoked on a blank line or outside a recognizable scope, the list displays symbols in the global namespace.

To turn List Members off by default (so that it does not appear unless specifically invoked), go to **Tools** > **Options** > **All Languages** and deselect **Auto list members**. If you want to turn off List Members only for a specific language, go to the **General** settings for that language.

You can also change to suggestion mode, in which only the text you type is inserted into the code. For example, if you enter an identifier that is not in the list and press **Tab**, in completion mode the entry would replace the typed identifier. To toggle between completion mode and suggestion mode, press **Ctrl**+**Alt**+**Space**, or choose **Edit** > **IntelliSense** > **Toggle Completion Mode**.

## Parameter Info

Parameter Info gives you information about the number, names, and types of parameters required by a method, attribute generic type parameter (in C#), or template (in C++).

The parameter in bold indicates the next parameter that is required as you type the function. For overloaded functions, you can use the **Up** and **Down** arrow keys to view alternative parameter information for the function overloads.

![Parameter Info](../ide/media/vs2015_param_info.png)

When you annotate functions and parameters with XML Documentation comments, the comments will display as Parameter Info. For more information, see [Supply XML code comments](reference/generate-xml-documentation-comments.md).

You can manually invoke Parameter Info by choosing **Edit** > **IntelliSense** > **Parameter Info**, by pressing **Ctrl**+**Shift**+**Space**, or by choosing the **Parameter Info** button on the editor toolbar.

## Quick Info

Quick Info displays the complete declaration for any identifier in your code.

![Visual Studio Quick Info](../ide/media/vs2015_quick_info.png)

When you select a member from the **List Members** box, Quick Info also appears.

![Parameter Info in a C&#35; code file](../ide/media/vs2015_paraminfo.png)

You can manually invoke Quick Info by choosing **Edit** > **IntelliSense** > **Quick Info**, by pressing **Ctrl**+**K**, **Ctrl**+**I**, or by choosing the **Quick Info** button on the editor toolbar.

If a function is overloaded, IntelliSense may not display information for all forms of the overload.

You can turn Quick Info off for C++ code by navigating to **Tools** > **Options** > **Text Editor** > **C/C++** > **Advanced**, and setting **Auto Quick Info** to `false`.

## Complete Word

Complete Word completes the rest of a variable, command, or function name after you have entered enough characters to disambiguate the term. You can invoke Complete Word by choosing **Edit** > **IntelliSense** > **Complete Word**, by pressing **Ctrl**+**Space**, or by choosing the **Complete Word** button on the editor toolbar.

## IntelliSense options

IntelliSense options are on by default. To turn them off, choose **Tools** > **Options** > **Text Editor** and deselect **Parameter information** or **Auto list members** if you do not want the List Members feature.

## IntelliSense icons
The icons in IntelliSense can convey additional meaning with icon modifiers. These are stars, hearts, and locks layered on top of the object's icon that convey protected, internal, or private, respectively.

|    Icon    |    Accessibility    |    Description    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Public Icon Modifier](../ide/media/intellisensePublicNoModifier.png)       |    Public class    |    Access is not restricted.   |
| ![Protected Icon Modifier](../ide/media/intellisenseProtectedModifier.png)       |    Protected class    |    Access is limited to the containing class or types derived from the containing class.    |
| ![Protected Internal Icon Modifier](../ide/media/intellisenseProtectedInternalModifier.png)       |    Protected internal class    |    Access is limited to the current assembly or types derived from the containing class.    |
| ![Internal Icon Modifier](../ide/media/intellisenseInternalModifier.png)       |    Internal class    |    Access is limited to the current assembly.    |
|![Private Icon Modifier](../ide/media/intellisensePrivateModifier.png)        |    Private class    |    Access is limited to the containing class or types derived from the containing class within the current assembly. (Available since C# 7.2.)    |

## Troubleshoot IntelliSense

The IntelliSense options may not work as you expect in certain cases.

**The cursor is below a code error.** You might not be able to use IntelliSense if an incomplete function or other error exists in the code above the cursor because IntelliSense might not be able to parse the code elements. You can resolve this problem by commenting out the applicable code.

**The cursor is in a code comment.** You can't use IntelliSense if the cursor is in a comment in your source file.

**The cursor is in a string literal.** You can't use IntelliSense if the cursor is in the quotation marks around a string literal, as in the following example:

```cpp
MessageBox( hWnd, "String literal|")
```

**The automatic options are turned off.** By default, IntelliSense works automatically, but you can disable it. Even if automatic statement completion is disabled, you can invoke an IntelliSense feature.

## See also

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [Python IntelliSense](../python/editing-python-code-in-visual-studio.md#intellisense)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Write and refactor code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Supply XML code comments](reference/generate-xml-documentation-comments.md)
