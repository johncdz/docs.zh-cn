---
title: "&lt;system.diagnostics&gt;元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d336a0f733451cb28d8fe57af20585515b71ca4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemdiagnosticsgt-element"></a>&lt;system.diagnostics&gt;元素
指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。  
  
 \<configuration>  
\<system.diagnostics >  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<assert>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|指定调用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法时是否显示消息框；另外指定要写入消息的文件的名称。|  
|[\<performanceCounters>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|指定由性能计数器共享的全局内存的大小。|  
|[\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|包含任何源或跟踪元素可以引用的侦听器。 标识为共享的侦听器可以按名称添加到源或跟踪侦听器。|  
|[\<sources>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|指定启动跟踪消息的跟踪源。|  
|[\<switches>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|包含跟踪开关和在其中设置跟踪开关的级别。|  
|[\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|包含用于收集、存储和路由跟踪消息的侦听器。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何将跟踪开关和跟踪侦听器嵌入 **\<system.diagnostics >**元素。 `General`跟踪开关设置为<xref:System.Diagnostics.TraceLevel>级别。 跟踪侦听器`myListener`创建名为的文件`MyListener.log`并将输出写入文件。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，你可以使用文本指定开关值。 例如，可以指定`true`为<xref:System.Diagnostics.BooleanSwitch>或使用如表示一个枚举值的文本`Error`为<xref:System.Diagnostics.TraceSwitch>。 行 `<add name="myTraceSwitch" value="Error" />` 等于 `<add name="myTraceSwitch" value="1" />`。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
