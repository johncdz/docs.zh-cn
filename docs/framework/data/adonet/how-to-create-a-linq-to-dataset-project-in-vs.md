---
title: "如何：在 Visual Studio 中创建 LINQ to DataSet 项目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 192273c6d364cebe828965ed016eea81135602f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>如何：在 Visual Studio 中创建 LINQ to DataSet 项目
不同类型的 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 项目需要某些导入的命名空间 (Visual Basic) 或 `using` 指令 (C#) 和引用。 最低要求是对 System.Core.dll 的引用和针对 `using` 的 <xref:System.Linq> 指令。 默认情况下，如果创建一个新的 [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] 项目，这些都可以自动提供。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 还需要对 System.Data.dll 和 System.Data.DataSetExtensions.dll 的引用以及 `Imports` (Visual Basic) 或 `using` (C#) 指令。  
  
 如果您要从早期版本的 Visual Studio 升级某个项目，则可能必须手动提供这些与 LINQ 相关的引用。 您可能还必须将项目手动设置为面向 .NET Framework 3.5 版。  
  
> [!NOTE]
>  如果你要在命令提示符下生成的则必须手动引用中与 LINQ 相关的 Dll `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5。  
  
### <a name="to-target-the-net-framework-35"></a>面向 .NET Framework 3.5  
  
1.  在 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] 中，创建一个新的 Visual Basic 或 C# 项目。 或者，您可以打开一个在 Visual Studio 2005 中创建的 Visual Basic 或 C# 项目，并按照提示将其转换为 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 项目。  
  
2.  对于 C# 项目，单击**项目**菜单，，然后单击**属性**。  
  
    1.  在**应用程序**属性页中，选择中的.NET Framework 3.5**目标框架**下拉列表。  
  
3.  对于 Visual Basic 项目中，单击**项目**菜单，，然后单击**属性**。  
  
    1.  在**编译**属性页中，单击**高级编译选项**，然后选择中的.NET Framework 3.5**目标 Framework （所有配置）**下拉列表。  
  
4.  上**项目**菜单上，单击**添加引用**，单击**.NET**选项卡上，向下滚动到**System.Core**，请单击它，，然后单击**确定**。  
  
5.  向源代码文件或项目中添加用于 `using` 的 <xref:System.Linq> 指令或导入的命名空间。  
  
     有关详细信息，请参阅[using 指令](~/docs/csharp/language-reference/keywords/using-directive.md)或[如何： 添加或删除已导入命名空间 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>启用 LINQ to DataSet 功能  
  
1.  必要时，按照本主题前面的步骤添加对 System.Core.dll 的引用和用于 System.Linq 的 `using` 指令或导入的命名空间。  
  
2.  在 C# 或 Visual Basic 中，单击**项目**菜单，，然后单击**添加引用**。  
  
3.  在**添加引用**对话框中，单击**.NET**选项卡上，如果不在最前面。 向下滚动到**System.Data**和**System.Data.DataSetExtensions**并单击它们。 单击**确定**按钮。  
  
4.  向源代码文件或项目中添加用于 `using` 的 <xref:System.Data> 指令或导入的命名空间。 有关详细信息，请参阅[using 指令](~/docs/csharp/language-reference/keywords/using-directive.md)或[如何： 添加或删除已导入命名空间 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。  
  
5.  添加对 System.Data.DataSetExtensions.dll 的引用以便可以使用 LINQ to Dataset 的功能。 添加对 System.Data.dll 的引用（如果尚不存在）。  
  
6.  或者，添加用于 `using` 或 `System.Data.Common` 的 `System.Data.SqlClient` 指令或导入的命名空间，具体取决于如何连接到数据库。  
  
## <a name="see-also"></a>另请参阅  
 [入门](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [LINQ 入门](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
