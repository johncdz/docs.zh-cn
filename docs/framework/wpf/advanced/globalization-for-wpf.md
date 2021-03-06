---
title: "WPF 的全球化"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 418a1b6d2033b8bc84a18578cfc227c5f227ad91
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2017
---
# <a name="globalization-for-wpf"></a>WPF 的全球化
本主题介绍你应注意的编写时的问题[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]面向全球市场的应用程序。 全球化编程元素中定义[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]中`System.Globalization`。  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a>XAML 全球化  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]基于[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]利用中定义的全球化支持[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]规范。 以下部分介绍一些[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]你应注意的功能。  
  
<a name="char_reference"></a>   
### <a name="character-references"></a>字符引用  
字符引用提供了特定的 UTF16 代码单位[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]字符它表示，以十进制或十六进制。 下面的示例演示科普特语 CAPITAL LETTER HORI 或 Ϩ 十进制字符引用：

```
&#1000;
```

下面的示例演示的十六进制字符引用。 请注意，它具有**x**十六进制数的前面。

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a>编码  
 支持的编码[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是[!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]， [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF 16 和 utf-8。 编码的语句; 在开始处[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文档。 如果不存在编码特性，并且没有任何字节顺序，则分析器默认为 UTF-8。 UTF-8 和 UTF-16 都是首选编码。 不支持 UTF-7。 下面的示例演示如何指定中的 utf-8 编码[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件。  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a>语言特性  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用[xml: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)来表示一个元素的 language 特性。  若要利用<xref:System.Globalization.CultureInfo>类，语言特性值需要是由预定义的区域性名称之一<xref:System.Globalization.CultureInfo>。 [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) 在元素树中可继承（可按 XML 规则继承，但并不一定这样继承，因为存在依赖属性继承）；在未明确赋值的情况下，其默认值为空字符串。  
  
 语言特性对指定方言非常有用。 例如，法语在法国、魁北克、比利时和瑞士的拼写、词汇和发音各不相同。 此外中文、 日语和朝鲜语共享中的代码点[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，但象形形状不同，它们使用完全不同的字体。  
  
 以下[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]示例使用`fr-CA`language 特性指定加拿大法语。  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a>Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]支持所有[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]功能包括代理项。 只要的字符集可以映射到[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，支持它。 例如，GB18030 中引入了某些可映射到中文、日语和朝鲜语 (CFK) 扩展 A 和 B 以及代理项对的字符，因此完全受支持。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序可以使用<xref:System.Globalization.StringInfo>操作而无需知道它们是否具有代理项对或组合字符的字符串。  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a>使用 XAML 设计国际用户界面  
 本部分介绍[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]时编写的应用程序应考虑的功能。  
  
<a name="intl_text"></a>   
### <a name="international-text"></a>国际化文本  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]包括所有的内置处理[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]支持书写系统。  
  
 目前支持以下脚本：  
  
-   阿拉伯语  
  
-   孟加拉语  
  
-   梵文  
  
-   西里尔文  
  
-   希腊语  
  
-   古吉拉特语  
  
-   果鲁穆奇语  
  
-   希伯来语  
  
-   表意文字脚本  
  
-   卡纳达语  
  
-   老挝语  
  
-   拉丁语  
  
-   马拉雅拉姆语  
  
-   蒙古语  
  
-   奥里亚语  
  
-   叙利亚语  
  
-   泰米尔语  
  
-   泰卢固语  
  
-   塔安那文  
  
-   泰语*  
  
-   藏语  
  
 *此版本支持显示和编辑泰语文本，但不支持断词。  
  
 目前不支持以下脚本：  
  
-   高棉语  
  
-   古朝鲜语  
  
-   缅甸语  
  
-   僧伽罗语  
  
 所有的书写体系引擎都支持[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字体。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]可以包括字体[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]使设计更好地国际和高端的排字字体的字体创建者的布局表。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]字体布局表包含有关标志符号替换项、 标志符号定位、 理由，和基线定位，信息使文本处理应用程序，以改进文本布局。  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]字体允许处理大型标志符号设置使用[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]编码。 这种编码享有广泛的国际支持，并支持版式字形变体。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]文本呈现并且采用[!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]子像素技术支持解析独立性。 这极大地提高了可读性，并为所有脚本提供了支持高质量杂志样式文档的功能。  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a>国际化布局  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一种支持水平、双向和垂直布局的简便方式。 在演示框架<xref:System.Windows.FrameworkElement.FlowDirection%2A>属性可以用于定义布局。 流方向模式包括：  
  
-   *LeftToRight* - 适用于拉丁语和东亚语等语言的水平布局。  
  
-   *RightToLeft* - 适用于阿拉伯语和希伯来语等语言的双向布局。  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a>开发可本地化的应用程序  
 编写供全球使用的应用程序时，应牢记应用程序必须可本地化。 以下主题指出了若干注意事项。  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a>多语言用户界面  
 多语言用户界面 (MUI) 是[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]支持用于切换[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]从一种语言到另一个。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序使用的程序集模型以支持 MUI。 一个应用程序包含非特定语言程序集和与语言相关的附属资源程序集。 入口点是主程序集中的托管 .EXE。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]资源加载程序利用[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]的资源管理器以支持资源查找和回退。 多个语言附属程序集使用同一个主程序集。 加载的资源程序集依赖于<xref:System.Globalization.CultureInfo.CurrentUICulture%2A>当前线程。  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a>可本地化的用户界面  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]来定义其[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 通过 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，开发人员可使用一组属性和逻辑指定对象的层次结构。 主要用途[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是开发[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序，但它可以用于指定层次结构的任何[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]对象。 大多数开发人员使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]以指定其应用程序的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]并且使用一种编程语言，如[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]以响应用户交互。  
  
 从资源的角度来看，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件旨在描述依赖于语言的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]是一个资源元素，因此其最终分发格式必须是可本地化以支持国际语言。 因为[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]无法处理事件许多[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]应用程序包含要执行此操作的代码块。 有关详细信息，请参阅[XAML 概述 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。 去掉代码并将其编译到不同的二进制文件时[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件会词汇切分为 XAML 的 BAML 形式。 BAML 形式的 XAML 文件、图像以及其他类型的托管资源对象将嵌入附属资源程序集中，该程序集可本地化为其他语言，如果不需要进行本地化，以上各项就会嵌入主程序集中。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序都支持所有[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)][!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]资源包括字符串表、 图像和等。  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a>生成可本地化的应用程序  
 本地化即以适应[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]到不同的区域性。 若要使[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序可本地化，开发人员需要将内置资源程序集的所有可本地化的资源。 资源程序集已本地化为不同的语言，并隐藏代码使用资源管理[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]加载。 所需的文件之一[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序是项目文件 (.proj)。 应用程序中使用的所有资源都应包括在项目文件中。 以下 .csproj 文件示例演示如何执行此操作。  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 若要使用你的应用程序中的资源实例化<xref:System.Resources.ResourceManager>并加载你想要使用的资源。 下面的示例演示如何执行此操作。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a>在本地化的应用程序中使用 ClickOnce  
 ClickOnce 是将随附的新 Windows 窗体部署技术[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]。 通过该技术可安装应用程序和升级 Web 应用程序。 对使用 ClickOnce 部署的应用程序进行本地化后，只能在本地化的区域性中查看该应用程序。 例如，如果部署的应用程序本地化为日语它可以仅在查看日语[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]不能在英语版[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]。 这会带来问题，因为它是一个常见方案用于日语用户运行英语版本的[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]。  
  
 此问题的解决方案是设置非特定语言回退特性。 应用程序开发人员可选择从主程序集中删除资源，并指定可在特定区域性对应的附属程序集中找到该资源。 若要控制此过程，请使用<xref:System.Resources.NeutralResourcesLanguageAttribute>。 构造函数<xref:System.Resources.NeutralResourcesLanguageAttribute>类具有两个签名，另一个采用<xref:System.Resources.UltimateResourceFallbackLocation>参数指定的位置其中<xref:System.Resources.ResourceManager>应提取回退资源： 主程序集或附属程序集。 下面的示例演示如何使用此特性。 对于最终的回退位置，代码会导致<xref:System.Resources.ResourceManager>查找当前正在执行的程序集的目录的"de"子目录中的资源。  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a>另请参阅  
 [WPF 全球化和本地化概述](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
