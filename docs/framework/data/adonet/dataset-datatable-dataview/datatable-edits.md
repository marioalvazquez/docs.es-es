---
title: Ediciones de DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d33bd8900c48222142a46ed2c5bd64412d2eaab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-edits"></a>Ediciones de DataTable
Cuando se cambian los valores de las columnas en una <xref:System.Data.DataRow>, los cambios se sitúan inmediatamente en el estado actual de la fila. El <xref:System.Data.DataRowState> , a continuación, se establece en **Modified**, y los cambios se aceptan o rechazan mediante el <xref:System.Data.DataRow.AcceptChanges%2A> o <xref:System.Data.DataRow.RejectChanges%2A> métodos de la **DataRow**. El **DataRow** proporciona también tres métodos que puede usar para suspender el estado de la fila mientras se está editando. Estos métodos son <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> y <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Al modificar los valores de columna en una **DataRow** directamente, la **DataRow** administra los valores de columna mediante el **actual**, **predeterminado**, y **Original** versiones de fila. Además de estas versiones de fila, el **BeginEdit**, **EndEdit**, y **CancelEdit** métodos utilizan una cuarta versión de fila: **propuesto**. Para obtener más información acerca de las versiones de fila, vea [Estados de fila y versiones de fila](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 El **propuesto** versión de fila existe mientras dura una operación de edición que se inicia mediante una llamada a **BeginEdit** y finaliza mediante el uso de **EndEdit** o **CancelEdit,**  o mediante una llamada a **AcceptChanges** o **RejectChanges**.  
  
 Durante la operación de edición, puede aplicar lógica de validación a las columnas individualmente evaluando el **ProposedValue** en el **ColumnChanged** eventos de la **DataTable**. El **ColumnChanged** contiene eventos **DataColumnChangeEventArgs** que guardan una referencia a la columna que está cambiando a la **ProposedValue**. Después de evaluar el valor propuesto, se puede modificar o cancelar la edición. Cuando finaliza la edición, la fila se mueve fuera de la **propuesto** estado.  
  
 Modificaciones se pueden confirmar llamando a **EndEdit**, o se puede cancelar mediante una llamada a **CancelEdit**. Tenga en cuenta que mientras **EndEdit** confirma las modificaciones, el **conjunto de datos** no las acepta realmente hasta que **AcceptChanges** se llama. Tenga en cuenta también que si se llama a **AcceptChanges** antes de que haya finalizado la edición con **EndEdit** o **CancelEdit**, dicha edición finaliza y la **propuesto** se aceptan valores de fila tanto para el **actual** y **Original** versiones de fila. De la misma manera, una llamada a **RejectChanges** finaliza la edición y descarta el **actual** y **propuesto** versiones de fila. Al llamar a **EndEdit** o **CancelEdit** después de llamar a **AcceptChanges** o **RejectChanges** no tiene ningún efecto porque la edición ya ha ha finalizado.  
  
 En el ejemplo siguiente se muestra cómo usar **BeginEdit** con **EndEdit** y **CancelEdit**. El ejemplo también se comprueba la **ProposedValue** en el **ColumnChanged** eventos y se decide si cancelar la edición.  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [Manipular datos en un objeto DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Control de eventos de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [Proveedores administrados de ADO.NET y Centro para desarrolladores de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
