---
title: "&lt;消息&gt;此错误也可能是由于文件引用与程序集 &#39; 的项目引用混合使用&lt;assemblyname&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30e5d5aca09e7b74e16dd05cdc0c5c361c1657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;消息&gt;此错误也可能是由于文件引用与程序集 &#39; 的项目引用混合使用&lt;assemblyname&gt;&#39;
\<消息 > 此错误也可能是由于混合文件引用与程序集的项目引用\<程序集名称 >。 在这种情况下，请尝试替换为对的文件引用\<assemblyfilename > 项目中\<projectname1 > 的项目引用与\<项目名称 2> >。  
  
 你项目中的代码访问了另一个项目的成员，但你的解决方案配置不允许使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 编译器来解析引用。  
  
 若要访问另一个程序集中定义的类型， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 编译器必须具有对该程序集的引用。 此引用必须单一、明确，不会导致项目之间循环引用。  
  
 **错误 ID：** BC30971  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  确定产生最佳程序集引用的项目。 为便于确定，你可以使用文件访问轻松程度和更新频率等条件。  
  
2.  在项目属性中，添加对包含某程序集的项目的引用，该程序集定义正在使用的类型。  
  
## <a name="see-also"></a>另请参阅  
 [管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)  
 [对已声明元素的引用](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB 如何：使用“添加引用”对话框添加或删除引用](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)  
 [有关无效的引用的疑难解答](/visualstudio/ide/troubleshooting-broken-references)
