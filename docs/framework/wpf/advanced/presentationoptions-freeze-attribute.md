---
title: PresentationOptions:Freeze (Atributo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8f1a876f65941afb159d4c3d8904ab4426d9177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze (Atributo)
Establece el <xref:System.Windows.Freezable.IsFrozen%2A> estado `true` en la que contiene <xref:System.Windows.Freezable> elemento. Comportamiento para predeterminado un <xref:System.Windows.Freezable> sin el `PresentationOptions:Freeze` el atributo especificado es que <xref:System.Windows.Freezable.IsFrozen%2A> es `false` en tiempo de carga y depende de general <xref:System.Windows.Freezable> comportamiento en tiempo de ejecución.  
  
## <a name="xaml-attribute-usage"></a>Uso de atributos XAML  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`PresentationOptions`|Un prefijo de espacio de nombres XML, que puede ser cualquier cadena de prefijo, según la especificación XML 1.0. El prefijo `PresentationOptions` se utiliza para propósitos de identificación en esta documentación.|  
|`freezableElement`|Un elemento que se crea una instancia de cualquier clase derivada de <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Comentarios  
 El `Freeze` es el único atributo u otro elemento de programación definido en el `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` espacio de nombres XML. El `Freeze` atributo existe en este espacio de nombres especial específicamente para que pueden designarse como puede pasar por alto, con [mc: Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) como parte de las declaraciones de elemento raíz. El motivo que `Freeze` debe ser capaz de ser puede pasar por alto es porque no todos los [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] las implementaciones de procesador pueden inmovilizar un <xref:System.Windows.Freezable> en tiempo de carga; esta funcionalidad no está forma parte de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] especificación.  
  
 La capacidad para procesar el `Freeze` atributo específicamente integrado en el [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesador que procesa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para aplicaciones compiladas. El atributo no es compatible con cualquier clase, y la sintaxis de atributo no es extensible ni modificable. Si está implementando su propio [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesador puede hacer que el comportamiento de inmovilización de en paralelo el [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesador al procesar la `Freeze` atributo <xref:System.Windows.Freezable> elementos en tiempo de carga.  
  
 Cualquier valor para el `Freeze` atributo distinto de `true` (no entre mayúsculas y minúsculas) genera un error en tiempo de carga. (Especificar el `Freeze` atributo como `false` no es un error, pero que ya es el valor predeterminado, por lo que si se establece en `false` no hace nada).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Freezable>  
 [Información general sobre objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [mc:Ignorable (atributo)](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
