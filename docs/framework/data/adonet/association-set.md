---
title: conjunto de asociaciones
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db293cbc636d0ae4e532f24b2852444395f603c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="association-set"></a>conjunto de asociaciones
Un *conjunto de asociaciones* es un contenedor lógico para [asociación](../../../../docs/framework/data/adonet/association-type.md) instancias del mismo tipo. Un conjunto de asociaciones no es una construcción del modelado de datos; es decir, no describe la estructura de datos o relaciones. En su lugar, un conjunto de asociaciones proporciona una construcción para que un entorno de hospedaje o de almacenamiento (como Common Language Runtime o una base de datos de SQL Server) agrupe las instancias de asociaciones a fin de que se puedan asignar a un almacén de datos.  
  
 Un conjunto de asociaciones se define dentro de un [contenedor de entidades](../../../../docs/framework/data/adonet/entity-container.md), que es una agrupación lógica de [conjuntos de entidades](../../../../docs/framework/data/adonet/entity-set.md) y conjuntos de asociaciones.  
  
 Una definición de un conjunto de asociaciones contiene la información siguiente:  
  
-   El nombre del conjunto de asociaciones. (Necesario)  
  
-   La asociación cuyas instancias contendrá. (Necesario)  
  
-   Dos [extremos del conjunto de asociaciones](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Ejemplo  
 El diagrama siguiente muestra un modelo conceptual con dos asociaciones: `PublishedBy` y `WrittenBy`. Aunque la información sobre los conjuntos de asociaciones no se muestra en el diagrama, el diagrama siguiente muestra un ejemplo de conjuntos de asociaciones y conjuntos de entidades basados en este modelo.  
  
 ![Ejemplo de modelo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 El siguiente ejemplo muestra un conjunto de asociaciones (`PublishedBy` y dos conjuntos de entidades (`Books` y `Publishers`) basados en el modelo conceptual mostrado anteriormente. BI en el `Books` conjunto de entidades representa una instancia de la `Book` tipo de entidad en tiempo de ejecución. De forma similar, Pj representa un `Publisher` de instancia de la `Publishers` conjunto de entidades. BiPj representa una instancia de la `PublishedBy` asociación en el `PublishedBy` conjunto de asociaciones.  
  
 ![Establece en el ejemplo se](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 El [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa un lenguaje específico de dominio (DSL) denominado lenguaje de definición de esquemas conceptuales ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir los modelos conceptuales. El siguiente CSDL define un contenedor de entidad con un conjunto de asociaciones para cada asociación en el diagrama anterior. Observe que el nombre y asociación para cada conjunto de asociaciones se definen utilizando los atributos XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Es posible definir varios conjuntos de asociaciones por asociación, siempre y cuando ningún recurso compartido de conjuntos de dos asociación un [final del conjunto de asociaciones](../../../../docs/framework/data/adonet/association-set-end.md). En el siguiente CSDL se define un contenedor de entidades con dos conjuntos de asociaciones para la asociación `WrittenBy`. Observe que se han definido varios conjuntos de entidades para los tipos de entidad `Book` y `Author` y que ningún conjunto de asociaciones comparte un extremo del conjunto de asociaciones.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de modelo de datos de entidad](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [propiedad de clave externa](../../../../docs/framework/data/adonet/foreign-key-property.md)
