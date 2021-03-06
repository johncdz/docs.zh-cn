---
title: "&lt;绑定&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b729141055f67f1d37cadfa4422417fe2d73139e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2017
---
# <a name="ltbindingsgt"></a>&lt;绑定&gt;
此节包含标准绑定和自定义绑定的集合。 每一项都是一个可由其唯一 `binding` 进行标识的 `name` 元素。 服务通过用 `name` 与绑定进行链接来使用绑定。 从 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 开始，不要求绑定和行为具有名称。 有关默认配置和无名称的绑定和行为的详细信息，请参阅[简化配置](../../../../../docs/framework/wcf/simplified-configuration.md)和[简化配置 WCF 服务](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
## <a name="system-provided-binding"></a>系统提供的绑定  
 系统提供的绑定可以消除 WCF 消息堆栈的复杂性。 使用系统提供的绑定的应用程序不需要对堆栈的完全控制权限。 在每个系统提供的绑定上公开的属性最适合绑定所针对的使用方案。  
  
 每个系统提供的绑定的配置节可以定义用于配置此绑定的一些配置。 每个配置均由唯一的名称进行标识。  
  
 无法向系统提供的绑定添加元素或属性。 为此，应该按照本主题的“自定义绑定”节中的描述来实现自定义绑定。 可以定义一个自定义绑定，该自定义绑定将完全模仿系统提供的绑定，并添加用户应用程序希望获得其控制权限的一些设置。  
  
 系统提供的绑定的列表，请参阅[系统提供的绑定](../../../../../docs/framework/wcf/system-provided-bindings.md)。  
  
## <a name="custom-binding"></a>自定义绑定  
 自定义绑定提供了对 WCF 消息堆栈的完全控制。 单个绑定按照堆栈元素在堆栈上出现的顺序来指定它们的配置元素，从而定义消息堆栈。 每个元素都定义和配置了该堆栈的一个元素。 在每个自定义绑定中，必须有且只能有一个 `transport` 元素。 如果没有该元素，消息堆栈将是不完整的。  
  
 元素在堆栈中出现的顺序非常重要，因为在将操作应用于消息时会采用该顺序。 所需的堆栈元素顺序如下：  
  
1.  事务（可选）  
  
2.  可靠消息（可选）  
  
3.  安全（可选）  
  
4.  编码器  
  
5.  传输  
  
 自定义绑定由其 `name` 特性来标识。 有关自定义绑定的详细信息，请参阅[自定义绑定](../../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [绑定](../../../../../docs/framework/wcf/bindings.md)  
 [自定义绑定](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [\<绑定 >](../../../../../docs/framework/misc/binding.md)
