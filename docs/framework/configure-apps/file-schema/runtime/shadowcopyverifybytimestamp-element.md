---
title: "&lt;shadowCopyVerifyByTimestamp&gt;元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 261962819e9b2b37682a13bffb53d2912a660566
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a>&lt;shadowCopyVerifyByTimestamp&gt;元素
指定卷影复制是否使用 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 中引入的默认启动行为，或恢复到 .NET Framework 的早期版本的启动行为。  
  
 \<配置 > 元素  
\<运行时 > 元素  
\<shadowCopyVerifyByTimestamp > 元素  
  
## <a name="syntax"></a>语法  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|enabled|必需的特性。<br /><br /> 指定启动，以确定是否在卷影复制程序集之前更新此程序集时，使用卷影复制的应用程序域是否比较程序集的时间戳。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|值|描述|  
|-----------|-----------------|  
|true|在启动时，将复制仅以来它们上次复制到卷影复制目录，已更新的程序集。 这是默认值[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。|  
|false|恢复到的启动行为的以前版本的.NET Framework 中，这是将在启动的所有文件复制。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 从开始[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，程序集进行影像复制仅当其时间戳指示上次它们已将其复制到卷影复制目录以来已更改。 这将提高使用卷影复制的许多应用程序的启动时间中所述[影像复制程序集](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)。 对于程序集更新百分比和频率都很高的应用程序，可能不会从此行为改变中获益。 在此情况下，可以使用此元素存储 .NET Framework 早先版本的行为。  
  
## <a name="example"></a>示例  
 下面的示例演示如何禁用中卷影复制的默认启动行为[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，并恢复为以前版本的.NET Framework 的启动行为。  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅  
 [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [卷影复制程序集](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
