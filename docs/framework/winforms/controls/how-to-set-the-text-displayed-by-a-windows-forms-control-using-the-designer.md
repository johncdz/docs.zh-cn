---
title: "如何：使用设计器设置 Windows 窗体控件显示的文本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59d66df2c6f18ad28ad4b912c00e35f786d773da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>如何：使用设计器设置 Windows 窗体控件显示的文本
Windows 窗体控件通常显示一些与控件的主要功能相关的文本。 例如，<xref:System.Windows.Forms.Button>控件通常显示的标题，该值指示当单击该按钮时，将执行什么操作。 对于所有控件而言，都可通过使用 <xref:System.Windows.Forms.Control.Text%2A> 属性来设置或返回文本。 可以使用 <xref:System.Windows.Forms.Control.Font%2A> 属性更改字体。  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>若要设置的文本和与设计器的字体  
  
1.  在属性窗口中，设置<xref:System.Windows.Forms.Control.Text%2A>为相应字符串控件属性。  
  
     若要创建带下划线的快捷键，包含一个 & 号 (&) 将的快捷键的字母前。  
  
2.  在属性窗口中，单击省略号按钮 (![VisualStudioEllipsesButton 屏幕快照](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁边<xref:System.Windows.Forms.Control.Font%2A>属性。  
  
     在标准字体对话框中，选择的字体、 字体样式、 大小、 效果 （如删除线或下划线） 和脚本所需。  
  
## <a name="see-also"></a>另请参阅  
 [如何：设置 Windows 窗体控件显示的文本](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [使用字体和文本](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [标记各个 Windows 窗体控件并创建它们的快捷键](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
