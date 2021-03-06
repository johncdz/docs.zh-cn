---
title: "查询表达式语法示例：导航关系"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d86fa3aab55daff9c7a3724c93ad68be27a6908b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>查询表达式语法示例：导航关系
[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]中的导航属性是快捷方式属性，用于定位位于关联各端的实体。 导航属性允许用户通过关联集从一个实体导航到另一个实体或从一个实体导航到多个相关的实体。 本主题以查询表达式语法提供相关的示例，以介绍如何通过 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查询中的导航属性来导航关系。  
  
 这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。  
  
 本主题中的示例使用以下`using` / `Imports`语句：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>示例  
 以下示例使用 <xref:System.Linq.Queryable.Select%2A> 方法以获取所有联系人 ID 和姓氏为“Zhou”的每个联系人的应付款总计。 `Contact.SalesOrderHeader` 导航属性用于获取每个联系人的 `SalesOrderHeader` 对象的集合。 `Sum` 方法使用 `Contact.SalesOrderHeader` 导航属性以汇总每个联系人的所有订单的应付款总计。  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>示例  
 以下示例获取其姓氏为“Zhou”的联系人的所有订单。 `Contact.SalesOrderHeader` 导航属性用于获取每个联系人的 `SalesOrderHeader` 对象的集合。 联系人的姓名和订单以匿名类型返回。  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>示例  
 以下示例使用 `SalesOrderHeader.Address` 和 `SalesOrderHeader.Contact` 导航属性以获取与每个订单关联的 `Address` 对象和 `Contact` 对象的集合。 Seattle 城市发生的每个订单的联系人姓氏、街道地址、销售订单号和应付款总计将以匿名类型返回。  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>示例  
 以下示例使用 `Where` 方法以查找在 2003 年 12 月 1 日之后生成的订单，然后使用 `order.SalesOrderDetail` 导航属性以获取每个订单的详细信息。  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>另请参阅  
 [在 LINQ to Entities 查询](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
