---
title: Eventos de Connection
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
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e551a09ef6dc778f5dfab9ba8cf263f803556f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="connection-events"></a>Eventos de Connection
Todos los proveedores de datos de .NET Framework tienen **conexión** objetos con dos eventos que puede usar para recuperar mensajes informativos de un origen de datos o para determinar si el estado de un **conexión** tiene cambiar. La tabla siguiente describen los eventos de la **conexión** objeto.  
  
|Evento|Descripción|  
|-----------|-----------------|  
|**InfoMessage**|Se produce cuando se devuelve un mensaje informativo desde un origen de datos. Los mensajes informativos son aquellos procedentes de orígenes de datos que no inician una excepción.|  
|**StateChange**|Se produce cuando el estado de la **conexión** cambios.|  
  
## <a name="working-with-the-infomessage-event"></a>Trabajar con el evento InfoMessage  
 Con el evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> del objeto <xref:System.Data.SqlClient.SqlConnection> puede recuperar advertencias o mensajes informativos de un origen de datos de SQL Server. Si se devuelven errores desde el origen de datos con un nivel de seguridad entre 11 y 16, se inicia una excepción. Sin embargo, el evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> se puede utilizar para obtener mensajes del origen de datos que no estén asociados a un error. En el caso de Microsoft SQL Server, cualquier error que tenga la gravedad 10, como máximo, se considera de tipo informativo y se captura mediante el evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>. Para obtener más información, vea el tema "Niveles de gravedad de mensajes de error" en los Libros en pantalla de SQL Server.  
  
 El <xref:System.Data.SqlClient.SqlConnection.InfoMessage> evento recibe un <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objeto que contiene en su **errores** propiedad, una colección de los mensajes del origen de datos. Puede consultar la **Error** objetos de esta colección para el texto de número y el mensaje de error, así como el origen del error. El proveedor de datos .NET Framework para SQL Server incluye asimismo datos acerca de la base de datos, el procedimiento almacenado y el número de línea donde se originó el mensaje.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo se puede agregar un controlador de eventos para el evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>Controlar errores como InfoMessages  
 Normalmente, el evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> solo se activa para mensajes informativos y de advertencia enviados desde el servidor. Sin embargo, cuando real se produce un error, la ejecución de la **ExecuteNonQuery** o **ExecuteReader** método que inició la operación de servidor se detiene y se produce una excepción.  
  
 Si desea seguir procesando el resto de las instrucciones de un comando, independientemente de los errores producidos en el servidor, establezca la propiedad <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> de <xref:System.Data.SqlClient.SqlConnection> como `true`. De esta forma, la conexión activa el evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> para errores, en lugar de iniciar una excepción e interrumpir el procesamiento. La aplicación cliente puede controlar el evento y reaccionar ante las situaciones de error.  
  
> [!NOTE]
>  Los errores con un nivel de gravedad de 17, como mínimo, que hacen que el servidor interrumpa el procesamiento de comandos, deben controlarse como excepciones. En este caso, se inicia una excepción, independientemente del modo en que se controle el error en el evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.  
  
## <a name="working-with-the-statechange-event"></a>Trabajar con el evento StateChange  
 El **StateChange** evento tiene lugar cuando el estado de un **conexión** cambios. El **StateChange** recibe el evento <xref:System.Data.StateChangeEventArgs> que le permiten determinar el cambio de estado de la **conexión** mediante el uso de la **OriginalState** y **CurrentState** propiedades. El **OriginalState** propiedad es una <xref:System.Data.ConnectionState> enumeración que indica el estado de la **conexión** antes del cambio. **CurrentState** es un <xref:System.Data.ConnectionState> enumeración que indica el estado de la **conexión** después del cambio.  
  
 El siguiente ejemplo de código utiliza el **StateChange** eventos para escribir un mensaje en la consola cuando el estado de la **conexión** cambios.  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Conexión a un origen de datos](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Proveedores administrados de ADO.NET y Centro para desarrolladores de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
