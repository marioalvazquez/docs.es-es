---
title: "Cómo: Definir el comportamiento de cambio de tamaño y colocación de una ventana dividida"
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
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db4a99c7dae7783e8ea51f43ad51fcd2214997e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Cómo: Definir el comportamiento de cambio de tamaño y colocación de una ventana dividida
Los paneles de la <xref:System.Windows.Forms.SplitContainer> control prestan apropiado para la que se va a cambiar de tamaño y manipulados por los usuarios. Sin embargo, habrá veces cuando desea controlar mediante programación el divisor, donde se coloca y hasta qué punto se puede mover.  
  
 El <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propiedad y las demás propiedades en el <xref:System.Windows.Forms.SplitContainer> control ofrecen un control preciso sobre el comportamiento de la interfaz de usuario para satisfacer sus necesidades. Estas propiedades se muestran en la tabla siguiente.  
  
|Nombre|Descripción|  
|----------|-----------------|  
|Propiedad <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Determina si el divisor se puede mover mediante el teclado o mouse (ratón).|  
|Propiedad <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Determina la distancia en píxeles desde el borde izquierdo o superior de la barra de división puede mover.|  
|Propiedad <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Determina la distancia mínima, en píxeles, que se puede mover el divisor por el usuario.|  
  
 El ejemplo siguiente se modifica el <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propiedad que se va a crear un efecto de "divisor con ajuste"; cuando el usuario arrastra el divisor, avanza en bloques de 10 píxeles en lugar de con el valor predeterminado 1.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>Para definir el comportamiento de cambio de tamaño de SplitContainer  
  
1.  En un procedimiento, establezca la <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propiedad tenga el tamaño deseado, por lo que se consigue el comportamiento de 'ajuste' del divisor.  
  
     En el ejemplo de código siguiente dentro del formulario <xref:System.Windows.Forms.Form.Load> evento, el divisor dentro del <xref:System.Windows.Forms.SplitContainer> control se establece en 10 píxeles cuando arrastra de salto.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Coloque el código siguiente en el constructor del formulario para registrar el controlador de eventos.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Mover el divisor ligeramente hacia la izquierda o derecha no tendrá ningún efecto visible; Sin embargo, cuando el puntero del mouse desplace 10 píxeles en cualquier dirección, el divisor se ajustará a la nueva posición.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
