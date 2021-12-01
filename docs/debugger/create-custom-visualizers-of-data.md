---
title: "Create custom data visualizers | Microsoft Docs"
description: Visual Studio debugger visualizers are components that display data. Learn about the six standard visualizers, and about how you can write or download others. 
ms.custom: SEO-VS-2020
ms.date: "07/29/2021"
ms.topic: "conceptual"
f1_keywords:
  - "vs.debug.visualizer.troubleshoot"
dev_langs:
  - "CSharp"
  - "VB"
  - "FSharp"
  - "C++"
  - "JScript"
helpviewer_keywords:
  - "debugger, visualizers"
  - "visualizers"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
  - "multiple"
---
# Create custom data visualizers

 A *visualizer* is part of the [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugger user interface that displays a variable or object in a manner appropriate to its data type. For example, an HTML visualizer interprets an HTML string and displays the result as it would appear in a browser window. A bitmap visualizer interprets a bitmap structure and displays the graphic it represents. Some visualizers let you modify as well as view the data.

 The [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugger includes six standard visualizers. The text, HTML, XML, and JSON visualizers work on string objects. The WPF Tree visualizer displays the properties of a WPF object visual tree. The dataset visualizer works for DataSet, DataView, and DataTable objects.

More visualizers may be available for download from Microsoft, third parties, and the community. You can also write your own visualizers and install them in the [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugger.

In the debugger, a visualizer is represented by a magnifying glass icon ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Visualizer icon"). You can select the icon in a **DataTip**, debugger **Watch** window, or **QuickWatch** dialog box, and then select the appropriate visualizer for the corresponding object.

## Write custom visualizers

 > [!NOTE]
 > To create a custom visualizer for native code, see the [SQLite native Debugger Visualizer](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) sample. Custom visualizers are not supported for UWP and Windows 8.x apps.

You can write a custom visualizer for an object of any managed class except for <xref:System.Object> and <xref:System.Array>.

The architecture of a debugger visualizer has two parts:

- The *debugger side* runs within the Visual Studio debugger, and creates and displays the visualizer user interface. 

  Because Visual Studio executes on the .NET Framework Runtime, this component has to be written for .NET Framework. For this reason, it is not possible to write it for .NET Core.

- The *debuggee side* runs within the process Visual Studio is debugging (the *debuggee*). The data object to visualize (for example, a String object) exists in the debuggee process. The debuggee side sends the object to the debugger side, which displays it in the user interface you create.

  The runtime for which you build this component should match the one in which the debuggee process will run, that is, either .NET Framework or .NET Core.

The debugger side receives the data object from an *object provider* that implements the <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interface. The debuggee side sends the object through the *object source*, which is derived from <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

The object provider can also send data back to the object source, which lets you write a visualizer that can edit data. You override the object provider to talk to the expression evaluator and the object source.

The debuggee side and debugger side communicate with each other through <xref:System.IO.Stream> methods that serialize a data object into a <xref:System.IO.Stream> and deserialize the <xref:System.IO.Stream> back into a data object.

You can write a visualizer for a generic type only if the type is an open type. This restriction is the same as the restriction when using the `DebuggerTypeProxy` attribute. For details, see [Use the DebuggerTypeProxy attribute](../debugger/using-debuggertypeproxy-attribute.md).

Custom visualizers may have security considerations. See [Visualizer security considerations](../debugger/visualizer-security-considerations.md).

The following steps give a high-level overview of visualizer creation. For detailed instructions, see [Walkthrough: Write a visualizer in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) or [Walkthrough: Write a visualizer in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### To create the debugger side

To create the visualizer user interface on the debugger side, you create a class that inherits from <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>, and override the <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> method to display the interface. You can use <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> to display Windows forms, dialogs, and controls in your visualizer.

1. Use <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> methods to get the visualized object on the debugger side.

1. Create a class that inherits from <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Override the <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> method to display your interface. Use <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> methods to display Windows forms, dialogs, and controls in your interface.

1. Apply <xref:System.Diagnostics.DebuggerVisualizerAttribute>, giving it the visualizer to display (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

#### Special debugger side considerations for .NET 5.0+

Custom Visualizers transfer data between the *debuggee* and *debugger* sides through binary serialization using
the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class by default. However, that kind of
serialization is being curtailed in .NET 5 and above due to security concerns regarding its *unfixible* vulnerabilities.
Moreover, it has been marked completely obsolete in ASP.NET Core 5 and its usage will throw as described in the
[ASP.NET Core Documentation](/dotnet/core/compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete).
This section describes the steps you should take to make sure your visualizer is still supported in
this scenario.

- For compatibility reasons, the <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A> method
that was overridden in the preceding section still takes in an <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>. However, starting in Visual Studio 2019 version 16.10, it is actually of type <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider2>.
For this reason, cast the `objectProvider` object to the updated interface.

- When sending objects, like commands or data, to the *debuggee-side* use the `IVisualizerObjectProvider2.Serialize` method
to pass it to a stream, it will determine the best serialization format to use based on the runtime of the *debuggee* process.
Then, pass the stream to the `IVisualizerObjectProvider2.TransferData` method.

- If the *debuggee-side* visualizer component needs to return anything to the *debugger-side*, it will be located in the
<xref:System.IO.Stream> object returned by the <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A>
method. Use the `IVisualizerObjectProvider2.GetDeserializableObjectFrom` method to get an
<xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> instance from it and process it as required.

Please refer to the [Special debuggee side considerations for .NET 5.0+](#special-debuggee-side-considerations-for-net-50)
section to learn what other changes are required on the *debuggee-side* when using Binary Serialization is not supported.

> [!NOTE]
> If you would like more information on the issue, see the [BinaryFormatter security guide](/dotnet/standard/serialization/binaryformatter-security-guide).

### To create the visualizer object source for the debuggee side

In the debugger side code, edit the <xref:System.Diagnostics.DebuggerVisualizerAttribute>, giving it the type to visualize (the debuggee-side object source) (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). The `Target` property sets the object source. If you omit the object source, the visualizer will use a default object source.

::: moniker range=">=vs-2019"
The debuggee side code contains the object source that gets visualized. The data object can override methods of <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. A debuggee side DLL is necessary if you want to create a standalone visualizer.
::: moniker-end

In the debuggee-side code:

- To let the visualizer edit data objects, the object source must inherit from from <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> and override the `TransferData` or `CreateReplacementObject` methods.

- If you need to support multi-targeting in your visualizer, you can use the following Target Framework Monikers (TFMs) in the debuggee-side project file.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   These are the only supported TFMs.

#### Special debuggee side considerations for .NET 5.0+

> [!IMPORTANT]
> Additional steps might be needed for a visualizer to work starting in .NET 5.0 due to security concerns regarding the underlying binary
serialization method used by default. Please read this [section](#special-debugger-side-considerations-for-net-50) before continuing.

- If the visualizer implements the <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A> method, 
use the newly added <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetDeserializableObject%2A> method that
is available in the latest version of `VisualizerObjectSource`. The <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject>
it returns helps to determine the object's serialization format (binary or JSON) and to deserialize the underlying object so that it may be used.

- If the *debuggee-side* returns data to the *debugger-side* as part of the `TransferData` call, serialize the response to the
*debugger-side's* stream via the <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A> method.

## See also

- [Walkthrough: Write a visualizer in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Walkthrough: Write a visualizer in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [How to: Install a visualizer](../debugger/how-to-install-a-visualizer.md)
- [How to: Test and debug a visualizer](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Visualizer API reference](../debugger/visualizer-api-reference.md)
- [View data in the debugger](../debugger/viewing-data-in-the-debugger.md)
