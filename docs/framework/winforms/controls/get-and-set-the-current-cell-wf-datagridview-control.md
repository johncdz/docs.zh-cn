---
title: "如何：获取和设置 Windows 窗体 DataGridView 控件中的当前单元格"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb63c48831e19ce3cbb166e899aeee8b6a331839
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>如何：获取和设置 Windows 窗体 DataGridView 控件中的当前单元格
与交互<xref:System.Windows.Forms.DataGridView>通常需要你以编程方式发现哪个单元格当前处于活动状态。 你可能还需要更改当前单元格。 你可以执行这些任务与<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>属性。  
  
> [!NOTE]
>  不能设置当前单元格的行或列具有其<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>属性设置为`false`。  
  
 具体取决于<xref:System.Windows.Forms.DataGridView>控件的选择模式，更改当前单元格可以更改选择。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的选择模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-get-the-current-cell-programmatically"></a>若要以编程方式获取当前单元格  
  
-   使用<xref:System.Windows.Forms.DataGridView>控件的<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>属性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>以编程方式设置当前单元格  
  
-   设置<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>属性<xref:System.Windows.Forms.DataGridView>控件。 在下面的代码示例中，当前单元格设置为 0，列 1 行。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   <xref:System.Windows.Forms.Button>控件名为`getCurrentCellButton`和`setCurrentCellButton`。 在[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]，必须将附加<xref:System.Windows.Forms.Control.Click>到关联的事件处理程序的代码示例中的每个按钮的事件。  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
-   对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [Windows 窗体 DataGridView 控件中的列、行和单元格基本功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Windows 窗体 DataGridView 控件中的选择模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
