---
title: "Cómo: establecer el título de una ventana de una página"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 412771e3f43bc3755bdf9236743310ac8060165c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Cómo: establecer el título de una ventana de una página
Este ejemplo muestra cómo establecer el título de la ventana en la que un <xref:System.Windows.Controls.Page> se hospeda.  
  
## <a name="example"></a>Ejemplo  
 Una página puede cambiar el título de la ventana que se hospeda estableciendo la <xref:System.Windows.Controls.Page.WindowTitle%2A> propiedad, así:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Establecer el <xref:System.Windows.Controls.Page.Title%2A> propiedad de una página no cambia el valor de título de la ventana. En su lugar, <xref:System.Windows.Controls.Page.Title%2A> especifica el nombre de una entrada de página en el historial de navegación.
