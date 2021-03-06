---
title: "Cómo: Cambiar la propiedad FlowDirection de contenido mediante programación"
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
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca4c94fe073fd618ca79d08812c42550594f445d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Cómo: Cambiar la propiedad FlowDirection de contenido mediante programación
Este ejemplo muestra cómo cambiar mediante programación el <xref:System.Windows.FrameworkElement.FlowDirection%2A> propiedad de un <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Ejemplo  
 Dos <xref:System.Windows.Controls.Button> se crea ningún elemento, cada uno representa uno de los valores posibles de <xref:System.Windows.FlowDirection>. Cuando se hace clic en un botón, el valor de la propiedad asociada se aplica al contenido de un <xref:System.Windows.Controls.FlowDocumentReader> denominado `tf1`.  El valor de propiedad también se escribe en un <xref:System.Windows.Controls.TextBlock> denominado `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Ejemplo  
 Los eventos asociados a los clics de botón definidos anteriormente se administran en un [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] archivo de código subyacente.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
