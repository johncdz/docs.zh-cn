---
title: "如何：向 ContextMenuStrip 添加菜单项"
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
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad9aa3ced90793b8051b377f499c94466bc3751a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a>如何：向 ContextMenuStrip 添加菜单项
可以将一个菜单项或多个项添加到的一次<xref:System.Windows.Forms.ContextMenuStrip>。  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a>若要向 ContextMenuStrip 添加一个菜单项  
  
-   使用<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法将添加到的一个菜单项<xref:System.Windows.Forms.ContextMenuStrip>。  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a>若要向 ContextMenuStrip 添加多个菜单项  
  
-   使用<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>方法将添加到多个菜单项<xref:System.Windows.Forms.ContextMenuStrip>。  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [ContextMenuStrip 控件](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
