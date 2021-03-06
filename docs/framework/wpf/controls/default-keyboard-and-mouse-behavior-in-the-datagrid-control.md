---
title: Comportamiento predeterminado de teclado y mouse en el control DataGridView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddbbab88a22a4350626a36f79236aab67da24a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>Comportamiento predeterminado de teclado y mouse en el control DataGridView
Este tema describe cómo los usuarios pueden interactuar con el <xref:System.Windows.Controls.DataGrid> control mediante el teclado y mouse (ratón).  
  
 Interacciones típicas con el <xref:System.Windows.Controls.DataGrid> incluyen la navegación, la selección y la edición. Comportamiento de la selección se ve afectado por la <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> y <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> propiedades. Los valores predeterminados que provocan el comportamiento descrito en este tema son <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> y <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Si cambia estos valores podría producir un comportamiento que es diferente del que se describe. Cuando una celda está en modo de edición, el control de edición puede invalidar el comportamiento de teclado estándar de la <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Comportamiento predeterminado del teclado  
 En la tabla siguiente enumera el comportamiento predeterminado del teclado para el <xref:System.Windows.Controls.DataGrid>.  
  
|Tecla o combinación de teclas|Descripción|  
|----------------------------|-----------------|  
|FLECHA ABAJO|Mueve el foco a la celda situada directamente debajo de la celda actual. Si el foco está en la última fila, al presionar la flecha hacia abajo, no hace nada.|  
|FLECHA ARRIBA|Mueve el foco a la celda directamente encima de la celda actual. Si el foco está en la primera fila, al presionar la flecha arriba, no hace nada.|  
|FLECHA IZQUIERDA|Mueve el foco a la celda anterior de la fila. Si el foco está en la primera celda de la fila, al presionar la flecha izquierda no hace nada.|  
|FLECHA DERECHA|Mueve el foco a la siguiente celda en la fila. Si el foco está en la última celda de la fila, al presionar la flecha derecha, no hace nada.|  
|INICIO|Mueve el foco a la primera celda de la fila actual.|  
|FIN|Mueve el foco a la última celda de la fila actual.|  
|AV PÁG|Si no se agrupan las filas, desplaza hacia abajo el control por el número de filas que se muestran completamente. Mueve el foco a la última fila muestra totalmente sin cambiar las columnas.<br /><br /> Si se agrupan las filas, mueve el foco a la última fila en la <xref:System.Windows.Controls.DataGrid> sin cambiar las columnas.|  
|RE PÁG|Si no se agrupan las filas, desplaza el control hacia arriba por el número de filas que se muestran completamente. Mover el foco a la primera fila mostrada sin cambiar las columnas.<br /><br /> Si se agrupan las filas, mueve el foco a la primera fila de la <xref:System.Windows.Controls.DataGrid> sin cambiar las columnas.|  
|TAB|Mueve el foco a la siguiente celda en la fila actual. Si el foco está en la última celda de la fila, mueve el foco a la primera celda de la fila siguiente. Si el foco está en la última celda en el control, mueve el foco al siguiente control en el orden de tabulación del contenedor primario.<br /><br /> Si la celda actual está en modo de edición y presiona enfoque de causas de PESTAÑA se mueva fuera de la fila actual, los cambios realizados en la fila se confirman antes de que se cambie el foco.|  
|MAYÚS+TAB|Mueve el foco a la celda anterior de la fila actual. Si el foco está en la primera celda de la fila, mueve el foco a la última celda de la fila anterior. Si el foco está en la primera celda del control, desplaza el foco al control anterior en el orden de tabulación del contenedor primario.<br /><br /> Si la celda actual está en modo de edición y presiona enfoque de causas de PESTAÑA se mueva fuera de la fila actual, los cambios realizados en la fila se confirman antes de que se cambie el foco.|  
|CTRL+FLECHA ABAJO|Mueve el foco a la última celda de la columna actual.|  
|CTRL+FLECHA ARRIBA|Mueve el foco a la primera celda de la columna actual.|  
|CTRL+FLECHA DERECHA|Mueve el foco a la última celda de la fila actual.|  
|CTRL+FLECHA IZQUIERDA|Mueve el foco a la primera celda de la fila actual.|  
|CTRL + INICIO|Mueve el foco a la primera celda del control.|  
|CTRL + FIN|Mueve el foco a la última celda en el control.|  
|CTRL+AV PÁG|Igual que AV PÁG.|  
|CTRL+RE PÁG|Igual que retroceder.|  
|F2|Si el <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> propiedad es `false` y <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> propiedad es `false` para la columna actual, coloca la celda actual en modo de edición de la celda.|  
|ENTRAR|Confirma los cambios a la celda actual y la fila y mueve el foco a la celda situada directamente debajo de la celda actual. Si el foco está en la última fila, confirma los cambios sin mover el foco.|  
|ESC|Si el control está en modo de edición, se cancela la edición y revierte todos los cambios realizados en el control. Si el origen de datos subyacente implementa <xref:System.ComponentModel.IEditableObject>, al presionar ESC una segunda vez cancela el modo de edición para toda la fila.|  
|RETROCESO|Elimina el carácter situado delante del cursor al editar una celda.|  
|SUPRIMIR|Elimina el carácter después del cursor al editar una celda.|  
|CTRL+ENTRAR|Confirma los cambios en la celda actual sin mover el foco.|  
|CTRL+A|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> está establecido en <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, selecciona todas las filas en el <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Teclas de selección  
 Si el <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> propiedad está establecida en <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, el comportamiento de navegación no cambia, pero navega con el teclado mientras se presiona MAYÚS (incluyendo CTRL+MAYÚS) modificará una selección de varias filas. Antes de comenzar la navegación, el control marca la fila actual como una fila de anclaje. Si mientras navega mientras presiona la tecla MAYÚS, la selección incluye todas las filas entre la fila delimitadora y la fila actual.  
  
 Las siguientes claves de selección modifican la selección de varias filas.  
  
-   MAYÚS+FLECHA ABAJO  
  
-   MAYÚS+FLECHA ARRIBA  
  
-   MAYÚS+AV PÁG  
  
-   MAYÚS+RE PÁG  
  
-   CTRL+MAYÚS+FLECHA ABAJO  
  
-   CTRL+MAYÚS+FLECHA ARRIBA  
  
-   CTRL + MAYÚS + INICIO  
  
-   CTRL + MAYÚS + FIN  
  
## <a name="default-mouse-behavior"></a>Comportamiento predeterminado del Mouse  
 En la tabla siguiente enumera el comportamiento predeterminado del mouse para el <xref:System.Windows.Controls.DataGrid>.  
  
|Acción del mouse|Descripción|  
|------------------|-----------------|  
|Haga clic en una fila no seleccionada|Hace que la fila hace clic en la fila actual y la celda hace clic en la celda actual.|  
|Haga clic en la celda actual|Pone la celda actual en modo de edición.|  
|Arrastre una celda de encabezado de columna|Si el <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> propiedad es `true` y <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> propiedad es `true` para la columna actual, mueve la columna para que se pueda colocar en una nueva posición.|  
|Arrastre un separador de encabezado de columna|Si el <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> propiedad es `true` y <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> propiedad es `true` para la columna actual, cambia el tamaño de la columna.|  
|Haga doble clic en un separador de encabezado de columna|Si el <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> propiedad es `true` y <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> propiedad es `true` para la columna actual, tamaños de automáticamente la columna mediante el <xref:System.Windows.Controls.DataGridLength.Auto%2A> modo de ajuste.|  
|Haga clic en una celda de encabezado de columna|Si el <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> propiedad es `true` y <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> propiedad es `true` para la columna actual, ordena la columna.<br /><br /> Haga clic en el encabezado de una columna que ya se han ordenado, se invertirá la dirección de ordenación de esa columna.<br /><br /> Si presiona la tecla MAYÚS mientras hace clic en varios encabezados de columna se ordenará por varias columnas en el orden que se hace clic en.|  
|CTRL + clic en una fila|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> se establece en <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, modifica una selección de varias filas no contiguas.<br /><br /> Si la fila ya está seleccionada, anula la selección de la fila.|  
|Mayús + clic en una fila|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> se establece en <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, modifica una selección de varias filas contiguas.|  
|Haga clic en un encabezado de grupo de filas|Se expande o contrae el grupo.|  
|Haga clic en el botón Seleccionar todo en la esquina superior izquierda de la<xref:System.Windows.Controls.DataGrid>|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> está establecido en <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, selecciona todas las filas en el <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Selección del mouse  
 Si el <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> propiedad está establecida en <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, haga clic en una fila mientras se presiona la tecla CTRL o MAYÚS modificará una selección de varias filas.  
  
 Al hacer clic en una fila mientras presiona la tecla CTRL, la fila cambiará su estado de selección mientras todas las demás filas conservan su estado de selección actual. Hacer esto para seleccionar filas no adyacentes.  
  
 Al hacer clic en una fila mientras presiona la tecla MAYÚS, la selección incluye todas las filas comprendidas entre la fila actual y la fila delimitadora ubicado en la posición de la fila actual antes de la haga clic en. Los clics sucesivos mientras presiona la tecla MAYÚS cambian la fila actual, pero no la fila delimitadora. Hacer esto para seleccionar un intervalo de filas adyacentes.  
  
 CTRL + MAYÚS se pueden combinar para seleccionar rangos no adyacentes de filas adyacentes. Para ello, seleccione el primer intervalo mediante MAYÚS + clic como se describió anteriormente. Después de selecciona el primer intervalo de filas, utilice CTRL + haga clic para seleccionar la primera fila en el intervalo siguiente y, a continuación, haga clic en la última fila en el siguiente intervalo mientras presiona la tecla CTRL + MAYÚS.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
