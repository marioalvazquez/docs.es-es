---
title: "Cómo: Establecer la alineación horizontal y vertical de TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c581bb167c020e9e4f0de26b0e17e7a1d70704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a>Cómo: Establecer la alineación horizontal y vertical de TileBrush
En este ejemplo se muestra cómo controlar la alineación horizontal y vertical del contenido en un mosaico. Para controlar la alineación horizontal y vertical de un <xref:System.Windows.Media.TileBrush>, usar su <xref:System.Windows.Media.TileBrush.AlignmentX%2A> y <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propiedades.  
  
 El <xref:System.Windows.Media.TileBrush.AlignmentX%2A> y <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propiedades de un <xref:System.Windows.Media.TileBrush> se utilizan cuando alguna de las condiciones siguientes sea verdadera:  
  
-   El <xref:System.Windows.Media.TileBrush.Stretch%2A> propiedad es <xref:System.Windows.Media.Stretch.Uniform> o <xref:System.Windows.Media.Stretch.UniformToFill> y <xref:System.Windows.Media.TileBrush.Viewbox%2A> y <xref:System.Windows.Media.TileBrush.Viewport%2A> tienen relaciones de aspecto diferentes.  
  
-   El <xref:System.Windows.Media.TileBrush.Stretch%2A> propiedad es <xref:System.Windows.Media.Stretch.None> y <xref:System.Windows.Media.TileBrush.Viewbox%2A> y <xref:System.Windows.Media.TileBrush.Viewport%2A> tienen tamaños diferentes.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se alinea el contenido de un <xref:System.Windows.Media.DrawingBrush>, que es un tipo de <xref:System.Windows.Media.TileBrush>, a la esquina superior izquierda de su icono. Para alinear el contenido, el ejemplo se establece el <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propiedad de la <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.AlignmentX.Left> y <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propiedad <xref:System.Windows.Media.AlignmentY.Top>. Este ejemplo produce el siguiente resultado:  
  
 ![TileBrush con top &#45; alineación a la izquierda](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")  
TileBrush con alineación de contenido en la esquina superior izquierda  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se alinea el contenido de un <xref:System.Windows.Media.DrawingBrush> a la esquina inferior derecha de su icono estableciendo la <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propiedad <xref:System.Windows.Media.AlignmentX.Right> y la <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propiedad <xref:System.Windows.Media.AlignmentY.Bottom>. El ejemplo genera el siguiente resultado.  
  
 ![TileBrush con inferior &#45; alineación a la derecha](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")  
TileBrush con alineación de contenido en la esquina inferior derecha  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se alinea el contenido de un <xref:System.Windows.Media.DrawingBrush> a la esquina superior izquierda de su mosaico estableciendo el <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propiedad <xref:System.Windows.Media.AlignmentX.Left> y el <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propiedad <xref:System.Windows.Media.AlignmentY.Top>. También establece la <xref:System.Windows.Media.TileBrush.Viewport%2A> y <xref:System.Windows.Media.TileBrush.TileMode%2A> de la <xref:System.Windows.Media.DrawingBrush> para generar un modelo de mosaico. El ejemplo genera el siguiente resultado.  
  
 ![TileBrush en mosaico con top &#45; alineación a la izquierda](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")  
Patrón de mosaico con el contenido alineado en la parte superior izquierda en el mosaico base  
  
 La ilustración destaca el mosaico base, por lo que puede ver cómo se alinea el contenido. Tenga en cuenta que la <xref:System.Windows.Media.TileBrush.AlignmentX%2A> configuración no tiene ningún efecto porque el contenido de la <xref:System.Windows.Media.DrawingBrush> rellena horizontalmente todo el mosaico base.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo final se alinea el contenido de un mosaico <xref:System.Windows.Media.DrawingBrush> a la inferior derecha de su mosaico base estableciendo la <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propiedad <xref:System.Windows.Media.AlignmentX.Right> y <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propiedad a <xref:System.Windows.Media.AlignmentY.Bottom>. El ejemplo genera el siguiente resultado.  
  
 ![Un TileBrush en mosaico con la parte inferior &#45; directamente alineación](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")  
Patrón de mosaico con el contenido alineado en la parte inferior derecha en el mosaico base  
  
 Una vez más, la <xref:System.Windows.Media.TileBrush.AlignmentX%2A> configuración no tiene ningún efecto porque el contenido de la <xref:System.Windows.Media.DrawingBrush> rellena horizontalmente todo el mosaico base.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 Los ejemplos utilizan <xref:System.Windows.Media.DrawingBrush> objetos para mostrar cómo la <xref:System.Windows.Media.TileBrush.AlignmentX%2A> y <xref:System.Windows.Media.TileBrush.AlignmentY%2A> se usan propiedades. Estas propiedades se comportan exactamente igual para todos los pinceles de mosaico: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, y <xref:System.Windows.Media.VisualBrush>. Para más información sobre los pinceles en mosaicos, vea [Pintar con imágenes, dibujos y elementos visuales](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 [Pintar con imágenes, dibujos y elementos visuales](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
