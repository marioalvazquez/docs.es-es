---
title: Consultas compiladas (LINQ to Entities)
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
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de490bac737520ffef5899c8515322c72b2a1144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="compiled-queries--linq-to-entities"></a>Consultas compiladas (LINQ to Entities)
Cuando una aplicación ejecuta muchas veces consultas que tienen una estructura similar en Entity Framework, se suele mejorar el rendimiento si se compila la consulta una vez y se ejecuta varias veces con parámetros diferentes. Por ejemplo, una aplicación puede tener que recuperar todos los clientes de una ciudad determinada; el usuario especifica en un formulario la ciudad en tiempo de ejecución. LINQ to Entities admite el uso de consultas compiladas para este fin.  
  
 A partir de .NET Framework 4.0.5, las consultas LINQ se almacenan en memoria caché automáticamente. Sin embargo, todavía puede usar consultas LINQ compiladas para reducir este costo en ejecuciones posteriores y las consultas compiladas pueden ser más eficaces que las consultas LINQ que se almacenan en memoria caché automáticamente. Tenga en cuenta que las consultas LINQ to Entities que aplican el operador `Enumerable.Contains` a colecciones en memoria no se almacenan en memoria caché automáticamente. Tampoco se permite parametrizar colecciones en memoria en consultas LINQ compiladas.  
  
 La clase <xref:System.Data.Objects.CompiledQuery> permite la compilación y el almacenamiento en memoria caché de las consultas para volverlas a utilizar. Desde un punto de vista conceptual, esta clase contiene un método <xref:System.Data.Objects.CompiledQuery> de `Compile` con varias sobrecargas. Llame al método `Compile` para crear un delegado nuevo que represente la consulta compilada. Los métodos `Compile`, con <xref:System.Data.Objects.ObjectContext> y valores de parámetros, devuelven un delegado que produce algún resultado (por ejemplo, una instancia de <xref:System.Linq.IQueryable%601>). La consulta compila una vez solo durante la primera ejecución. El conjunto de opciones de combinación de la consulta en el momento de la compilación no se puede cambiar posteriormente. Una vez compilada la consulta, solo se pueden proporcionar parámetros de tipo primitivo, pero no reemplazar las partes de la consulta que cambiarían el SQL generado. Para obtener más información, vea [opciones de combinación de Entity Framework y consultas compiladas](http://go.microsoft.com/fwlink/?LinkId=199591)  
  
 El [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] expresión de consulta que la <xref:System.Data.Objects.CompiledQuery>del `Compile` método compila se representa mediante una de la clase genérica `Func` delega, como <xref:System.Func%605>. A lo sumo, la expresión de consulta puede encapsular un parámetro `ObjectContext`, un parámetro de retorno y 16 parámetros de consulta. Si se requieren más de 16 parámetros de consulta, puede crear una estructura cuyas propiedades representan los parámetros de consulta. A continuación, puede utilizar las propiedades de la estructura de la expresión de consulta después de establecerlas.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila y, a continuación, se llama a una consulta que acepta un parámetro de entrada <xref:System.Decimal> y devuelve una secuencia de pedidos cuyo importe total a pagar es mayor o igual que 200 $:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila y, a continuación, se llama a una consulta que devuelve una instancia de <xref:System.Data.Objects.ObjectQuery%601>:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila y, a continuación, se llama a una consulta que devuelve el promedio de los precios de venta de productos en forma de valor <xref:System.Decimal>:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila y luego se llama a una consulta que acepta un parámetro de entrada <xref:System.String> y, a continuación, devuelve un elemento `Contact` cuya dirección de correo electrónico comienza con la cadena especificada:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila y luego se llama a una consulta que acepta los parámetros de entrada <xref:System.DateTime> y <xref:System.Decimal> y, a continuación, devuelve una secuencia de pedidos cuya fecha es posterior al 8 de marzo de 2003 y cuyo importe total que pagar es inferior a 300 $:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila y luego se llama a una consulta que acepta un parámetro de entrada <xref:System.DateTime> y, a continuación, devuelve una secuencia de pedidos cuya fecha es posterior al 8 de marzo de 2004. Esta consulta devuelve la información del pedido como una secuencia de tipos anónimos. El compilador deduce los tipos anónimos, de modo que no se pueden especificar parámetros de tipo en el método <xref:System.Data.Objects.CompiledQuery> de `Compile` y el tipo se define en la propia consulta.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila y luego se llama a una consulta que acepta un parámetro de entrada con una estructura definida por el usuario y, a continuación, devuelve una secuencia de pedidos. La estructura define los parámetros de la consulta correspondientes a la fecha de inicio, la fecha de fin y la deuda total, y la consulta devuelve los pedidos distribuidos entre el 3 de marzo y el 8 de marzo de 2003 con un importe total mayor que 700,00$.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 La estructura que define los parámetros de la consulta:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Vea también  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [Opciones de combinación de Entity Framework y consultas compiladas](http://go.microsoft.com/fwlink/?LinkId=199591)
