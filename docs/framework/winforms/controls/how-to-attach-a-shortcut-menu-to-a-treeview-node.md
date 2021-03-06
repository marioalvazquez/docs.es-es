---
title: "Cómo: Asociar un menú contextual a un nodo TreeView"
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
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d3814e95ad2d91157181682984fc9b53254ba813
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Cómo: Asociar un menú contextual a un nodo TreeView
Los formularios Windows Forms <xref:System.Windows.Forms.TreeView> control muestra una jerarquía de nodos, similares a los archivos y las carpetas que aparecen en el panel izquierdo del explorador de Windows. Estableciendo la <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propiedad, puede proporcionar operaciones contextuales al usuario cuando haga clic en el <xref:System.Windows.Forms.TreeView> control. Asociando un <xref:System.Windows.Forms.ContextMenuStrip> componente de individual <xref:System.Windows.Forms.TreeNode> elementos, puede agregar un nivel personalizado de funcionalidad del menú contextual para su <xref:System.Windows.Forms.TreeView> controles.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Para asociar un menú contextual a un objeto TreeNode mediante programación  
  
1.  Crear una instancia de un <xref:System.Windows.Forms.TreeView> controlar con la configuración de la propiedad adecuada, cree una raíz <xref:System.Windows.Forms.TreeNode>y, a continuación, agregue los subnodos.  
  
2.  Crear una instancia de un <xref:System.Windows.Forms.ContextMenuStrip> componente y, a continuación, agregue un <xref:System.Windows.Forms.ToolStripMenuItem> para cada operación que desee que estén disponibles en tiempo de ejecución.  
  
3.  Establecer el <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> propiedad de los <xref:System.Windows.Forms.TreeNode> en el menú contextual que cree.  
  
4.  Cuando se establece esta propiedad, se mostrará el menú contextual cuando haga clic en el nodo.  
  
 En el ejemplo de código siguiente se crea un basic <xref:System.Windows.Forms.TreeView> y <xref:System.Windows.Forms.ContextMenuStrip> asociado a la raíz <xref:System.Windows.Forms.TreeNode> de la <xref:System.Windows.Forms.TreeView>. Debe personalizar las opciones de menú a los que se ajusten a los <xref:System.Windows.Forms.TreeView> que está desarrollando. Además, desea escribir código para controlar la <xref:System.Windows.Forms.ToolStripItem.Click> eventos para estos elementos de menú.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [TreeView (control)](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
