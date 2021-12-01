---
title: Working with a Conceptual Model (WCF Data Services)
description: Work with a conceptual model in WCF Data Services. Query data through objects instead of translating back and forth between database schemas and object models.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
---
# Work with a Conceptual Model (WCF Data Services)

When you use a conceptual model to describe the data in a database, you can query data through your objects instead of having to translate back and forth between a database schema and an object model.

You can use conceptual models with WCF Data Services applications. The following topics show how to query data through a conceptual model.

| Topic | Description |
| - | - |
| [How to: Execute Data Service queries](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Shows how to query a data service from a .NET application. |
| [How to: Project query results](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Shows how to reduce the amount of data returned through a data service query. |

When you use a conceptual model, you can define what kind of data is valid in the language that matches your domain. You can define valid data in the model, or you can add validation to operations that you perform on an entity or data service.

The following topics show how to add validation to WCF Data Services applications.

|Topic|Description|
|-----------|-----------------|
|[How to: Intercept Data Service messages](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Shows how to add validation to a data service operation.|

 The following topics show how to create, update, and delete data by performing operations on entities.

|Topic|Description|
|-----------|-----------------|
|[How to: Add, modify, and delete entities](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Shows how to create, update, and delete entity data in a data service.|
|[How to: Define entity relationships](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Shows how to create or change relationships in a data service.|

## See also

- [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Querying the Data Service](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)
