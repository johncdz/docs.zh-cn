---
title: "如何：引发和使用事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d052c865a554977ce5c8b0a347337d9d9b92fc57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-raise-and-consume-events"></a>如何：引发和使用事件
本主题中的示例演示如何处理事件。 它们包含 <xref:System.EventHandler>、<xref:System.EventHandler%601> 委托和自定义委托的示例，用于说明包含数据和不包含数据的事件。  
  
 示例使用中所述的概念[事件](../../../docs/standard/events/index.md)文章。  
  
## <a name="example"></a>示例  
 第一个示例演示如何引发和使用一个没有数据的事件。 它包含一个名为 `Counter` 类，该类具有一个名为 `ThresholdReached` 的事件。 当计数器值等于或者超过阈值时，将引发此事件。 <xref:System.EventHandler> 委托与此事件关联，因为没有提供任何事件数据。  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>示例  
 下一个示例演示如何引发和使用提供数据的事件。 <xref:System.EventHandler%601> 委托与此事件关联，示例还提供了一个自定义事件数据对象的实例。  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>示例  
 下一个示例演示如何声明事件的委托。 该委托名为 `ThresholdReachedEventHandler`。 这只是一个示例。 通常不需要为事件声名委托，因为可以使用 <xref:System.EventHandler> 或者 <xref:System.EventHandler%601> 委托。 只有在极少数情况下才应声明委托，例如，在向无法使用泛型的旧代码提供类时，就需要如此。  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>另请参阅  
 [事件](../../../docs/standard/events/index.md)
