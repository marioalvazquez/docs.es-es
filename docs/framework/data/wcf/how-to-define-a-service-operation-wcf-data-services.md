---
title: "Cómo: Definir una operación de servicio (Data Services de WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dcf4ffd46bbbca0e7e00cad7ae0b2a88f7bd986b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Cómo: Definir una operación de servicio (Data Services de WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expone métodos que se definen en el servidor como operaciones de servicio. Las operaciones de servicio permite que un servicio de datos proporcionar acceso a través de un URI a un método que se define en el servidor. Para definir una operación de servicio, se aplican los [`WebGet]` o `[WebInvoke]` atributo al método. Para admitir operadores de consulta, la operación de servicio debe devolver un <xref:System.Linq.IQueryable%601> instancia. Las operaciones del servicio pueden tener acceso al origen de datos subyacente por medio de la propiedad <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> en <xref:System.Data.Services.DataService%601>. Para obtener más información, consulte [las operaciones del servicio](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 En el ejemplo de este tema se define una operación del servicio denominada `GetOrdersByCity` que devuelve una instancia de <xref:System.Linq.IQueryable%601> filtrada de los objetos `Orders` y `Order_Details` relacionados. En el ejemplo se obtiene acceso a la instancia de <xref:System.Data.Objects.ObjectContext> que es el origen de datos del servicio de datos de ejemplo Northwind. Este servicio se crea al completar la [inicio rápido de WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Para definir una operación del servicio en el servicio de datos Northwind  
  
1.  En el proyecto del servicio de datos Northwind, abra el archivo Northwind.svc.  
  
2.  En la clase `Northwind`, defina un método de operación de servicio denominado `GetOrdersByCity` como sigue:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  En el método `InitializeService` de la clase `Northwind`, agregue el siguiente código para permitir el acceso a la operación del servicio:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>Para consultar la operación del servicio GetOrdersByCity  
  
-   En un explorador web, escriba uno de los siguientes URI para invocar la operación del servicio que se define en el siguiente ejemplo:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se implementa una operación del servicio denominada `GetOrderByCity` en el servicio de datos Northwind. Esta operación utiliza ADO.NET Entity Framework para devolver un conjunto de objetos `Orders` y `Order_Details` relacionados como una instancia de <xref:System.Linq.IQueryable%601> basada en el nombre de ciudad suministrado.  
  
> [!NOTE]
>  Los operadores de consulta se admiten en este extremo de la operación del servicio porque el método devuelve una instancia de <xref:System.Linq.IQueryable%601>.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Vea también  
 [Definir Servicios de datos de WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
