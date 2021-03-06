---
title: "Cómo: Dibujar texto con GDI"
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
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48644ce8449c8d8eea7306eff1e43539659370c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-with-gdi"></a>Cómo: Dibujar texto con GDI
Con el <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método en el <xref:System.Windows.Forms.TextRenderer> (clase), puede tener acceso a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funcionalidad para dibujar texto en un formulario o control. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]representación de texto normalmente ofrece un mejor rendimiento y una medida de texto más preciso [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  El <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos de la <xref:System.Windows.Forms.TextRenderer> clase no se admiten para la impresión. Al imprimir, utilice siempre la <xref:System.Drawing.Graphics.DrawString%2A> métodos de la <xref:System.Drawing.Graphics> clase.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo dibujar texto en varias líneas dentro de un rectángulo utilizando el <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Para representar texto con la <xref:System.Windows.Forms.TextRenderer> (clase), necesita un <xref:System.Drawing.IDeviceContext>, como un <xref:System.Drawing.Graphics> y un <xref:System.Drawing.Font>, una ubicación para dibujar el texto y el color en el que se debe dibujar. Si lo desea, puede especificar el texto con formato mediante el uso de la <xref:System.Windows.Forms.TextFormatFlags> enumeración.  
  
 Para obtener más información acerca de cómo obtener un <xref:System.Drawing.Graphics>, consulte [Cómo: crear objetos Graphics para dibujar](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Para obtener más información sobre cómo generar un <xref:System.Drawing.Font>, consulte [Cómo: construir fuentes y familias de fuentes](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Compilar el código  
 El ejemplo de código anterior está diseñado para su uso con Windows Forms y requiere el <xref:System.Windows.Forms.PaintEventArgs> `e`, que es un parámetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [Utilizar fuentes y texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
