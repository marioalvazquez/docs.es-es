---
title: DataGrid
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63eb1b7aec0c65192f67035fc7bc624fa1d2ae81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="datagrid"></a>DataGrid
El <xref:System.Windows.Controls.DataGrid> control le permite mostrar y editar datos de muchos orígenes diferentes, como en una base de datos SQL, consulta LINQ o cualquier otro origen de datos se puede enlazar. Para más información, consulte [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md) (Introducción a los orígenes de enlace).  
  
 Las columnas pueden mostrar texto, controles, como un <xref:System.Windows.Controls.ComboBox>, o cualquier otro contenido WPF, como imágenes, botones o cualquier contenido incluido en una plantilla. Puede usar un <xref:System.Windows.Controls.DataGridTemplateColumn> para mostrar los datos definidos en una plantilla. En la tabla siguiente se enumera los tipos de columna que se proporcionan de forma predeterminada.  
  
|Tipo de columna generada|Tipo de datos|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>se pueden personalizar de apariencia, como el tamaño, color y fuente de la celda. <xref:System.Windows.Controls.DataGrid>admite toda la funcionalidad de estilos y plantillas de otros controles WPF. <xref:System.Windows.Controls.DataGrid>También incluye comportamientos predeterminados y personalizables para la edición, ordenación y validación.  
  
 En la tabla siguiente se enumera algunas de las tareas comunes para <xref:System.Windows.Controls.DataGrid> y cómo realizarlas. Al ver la API relacionada, puede encontrar más información y código de ejemplo.  
  
|Escenario|Enfoque|  
|--------------|--------------|  
|Colores de fondo alternos|Establecer el <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> propiedad a 2 o más y, a continuación, asignar un <xref:System.Windows.Media.Brush> a la <xref:System.Windows.Controls.DataGrid.RowBackground%2A> y <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> propiedades.|  
|Definir el comportamiento de la selección de celdas y filas|Establezca las propiedades <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> y <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Personalizar la apariencia visual de encabezados, celdas y filas|Aplicar un nuevo <xref:System.Windows.Style> a la <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, o <xref:System.Windows.Controls.DataGrid.RowStyle%2A> propiedades.|  
|Establecer opciones de tamaño|Establecer el <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, o <xref:System.Windows.FrameworkElement.MinWidth%2A> propiedades. Para obtener más información, consulte [opciones de ajuste de tamaño en el DataGrid Control](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md).|  
|Elementos de acceso seleccionada|Compruebe el <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> propiedad para obtener las celdas seleccionadas y <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> propiedad para obtener las filas seleccionadas. Para obtener más información, consulta <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Personalizar las interacciones del usuario final|Establecer el <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, y <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> propiedades.|  
|Cancelar o cambiar las columnas generadas automáticamente|Controlar la <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> eventos.|  
|Inmovilizar una columna|Establecer el <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> propiedad en 1 y mueva la columna a la posición más a la izquierda estableciendo la <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> propiedad en 0.|  
|Usar datos XML como origen de datos|Enlazar el <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> en la <xref:System.Windows.Controls.DataGrid> a la consulta de XPath que representa la colección de elementos. Cree cada columna en el <xref:System.Windows.Controls.DataGrid>. Enlazar cada columna estableciendo el XPath en el enlace a la consulta que obtiene la propiedad en el origen del elemento. Para obtener un ejemplo, consulta <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Mostrar los datos de una base de datos de SQL Server en un control DataGrid](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Describe cómo configurar un nuevo proyecto WPF, agregue un elemento de Entity Framework, establezca el origen y mostrar los datos en un <xref:System.Windows.Controls.DataGrid>.|  
|[Agregar detalles de fila a un control DataGrid](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|Describe cómo crear los detalles de las filas para un <xref:System.Windows.Controls.DataGrid>.|  
|[Implementar la validación con el control DataGrid](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|Describe cómo validar los valores de <xref:System.Windows.Controls.DataGrid> celdas y filas y mostrar comentarios de validación.|  
|[Comportamiento predeterminado de teclado y mouse en el control DataGridView](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Describe cómo interactuar con el <xref:System.Windows.Controls.DataGrid> control mediante el teclado y mouse (ratón).|  
|[Agrupar, ordenar y filtrar datos en el control DataGrid](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Describe cómo ver los datos en un <xref:System.Windows.Controls.DataGrid> de maneras diferentes, agrupar, ordenar y filtrar los datos.|  
|[Opciones de ajuste de tamaño en el control DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|Describe cómo controlar el ajuste de tamaño absoluto y automático en el <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Controls.DataGrid>  
 [Aplicar estilos y plantillas](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Información general sobre el enlace de datos](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Información general sobre plantillas de datos](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Controles](../../../../docs/framework/wpf/controls/index.md)  
 [WPF Content Model](../../../../docs/framework/wpf/controls/wpf-content-model.md) (Modelo de contenido de WPF)
