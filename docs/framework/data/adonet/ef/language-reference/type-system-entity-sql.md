---
title: Sistema de tipos (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b951a51c4a9daee44ba55aa3589900ca4cad188a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="type-system-entity-sql"></a>Sistema de tipos (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]admite un número de tipos:  
  
-   Tipos primitivos (simples), como `Int32` y `String.`.  
  
-   Tipos nominales que se definen en el esquema, como <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> y <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
-   Tipos anónimos que no se definen explícitamente en el esquema: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> y <xref:System.Data.Metadata.Edm.RefType>.  
  
 En esta sección se explican los tipos anónimos que no se definen explícitamente en el esquema pero que se admiten a través de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Para obtener información sobre los tipos nominales y primitivos, vea [tipos de modelo Conceptual (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).  
  
## <a name="rows"></a>Filas  
 La estructura de una fila depende de la secuencia de miembros con nombre y con tipo de que consta la misma. Un tipo de fila no tiene ninguna identidad y no se puede heredar. Las instancias del mismo tipo de fila son equivalentes si los miembros son respectivamente equivalentes. Las filas no tienen ningún otro comportamiento más allá de su equivalencia estructural y no tienen ningún equivalente en Common Language Runtime. Las consultas pueden producir estructuras que contienen filas o colecciones de filas. El enlace de API entre las consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] y el lenguaje del host define el modo en que las filas se materializan en la consulta que generó el resultado. Para obtener información sobre cómo construir una instancia de fila, vea [construir tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Colecciones  
 Los tipos de colección representan cero o más instancias de otros objetos. Para obtener información sobre cómo construir la colección, consulte [construir tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="references"></a>Referencias  
 Una referencia es un puntero lógico a una entidad concreta en un conjunto de entidades específico.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] admite los operadores siguientes para construir, anular la construcción y navegar a través de referencias.  
  
-   [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [CLAVE](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 Puede navegar por una referencia utilizando el operador de acceso a miembros (`.`) (punto). El fragmento de código siguiente extrae la propiedad Id (de Order) navegando por la propiedad r (referencia).  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Si el valor de referencia es NULL o si el destino de la referencia no existe, el resultado es NULL.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Referencia de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CONVERSIÓN DE TIPOS](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)  
 [Especificaciones CSDL, SSDL MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
