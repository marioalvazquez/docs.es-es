---
title: "Referencias y la instrucción Imports (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 739934b65241a7846b5323d5e75446832d83e5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Referencias y la instrucción Imports (Visual Basic)
Se pueden disponer de objetos externos a su proyecto eligiendo la **Agregar referencia** comando el **proyecto** menú. Hace referencia en [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pueden apuntar a ensamblados, que son similares a las bibliotecas de tipos, pero contienen más información.  
  
## <a name="the-imports-statement"></a>La instrucción Imports  
 Los ensamblados incluyen uno o varios espacios de nombres. Cuando se agrega una referencia a un ensamblado, también puede agregar un `Imports` instrucción a un módulo que controla la visibilidad de los espacios de nombres del ensamblado dentro del módulo. El `Imports` instrucción proporciona un contexto de ámbito que permite utilizar solamente la parte del espacio de nombres necesaria para suministrar una referencia única.  
  
 El `Imports` instrucción tiene la siguiente sintaxis:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`hace referencia a un nombre corto que se puede utilizar dentro de código para hacer referencia a un espacio de nombres importado. `Namespace`es un espacio de nombres disponible a través de una referencia de proyecto, una definición dentro del proyecto, o a través de un anterior `Imports` instrucción.  
  
 Un módulo puede contener cualquier número de `Imports` instrucciones. Deben aparecer después de cualquier `Option` instrucciones, si está presente, pero antes que cualquier otro código.  
  
> [!NOTE]
>  No confunda las referencias de proyecto con el `Imports` instrucción o `Declare` instrucción. Referencias del proyecto que pueda objetos externos, como los objetos de ensamblados, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] proyectos. El `Imports` instrucción se utiliza para simplificar el acceso a las referencias del proyecto, pero no proporciona acceso a estos objetos. El `Declare` instrucción se utiliza para declarar una referencia a un procedimiento externo en una biblioteca de vínculos dinámicos (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Uso de alias con la instrucción Imports  
 El `Imports` instrucción resulta más fácil acceso a los métodos de clases por lo que elimina la necesidad de escribir explícitamente los nombres completos de referencias. Los alias permiten asignar un nombre más descriptivo para solamente una parte de un espacio de nombres. Por ejemplo, el retorno de carro/avance secuencia que produce un único fragmento de texto para mostrarse en varias líneas de línea es parte de la <xref:Microsoft.VisualBasic.ControlChars> módulo en el <xref:Microsoft.VisualBasic?displayProperty=nameWithType> espacio de nombres. Para utilizar esta constante en un programa sin alias, se tendría que escribir el código siguiente:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`instrucciones siempre deben ser las primeras líneas inmediatamente después de cualquier `Option` instrucciones de un módulo. El siguiente fragmento de código muestra cómo importar y asignar un alias a la <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> módulo:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Las futuras referencias a este espacio de nombres pueden ser mucho más breves:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Si un `Imports` instrucción no incluye un nombre de alias, los elementos definidos en el espacio de nombres importado pueden utilizarse en el módulo sin calificación. Si se especifica el nombre de alias, debe usarse como un calificador de nombres dentro de ese espacio de nombres.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [Espacios de nombres en Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Ensamblados y Caché global de ensamblados](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Crear y utilizar ensamblados mediante la línea de comandos](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Imports (instrucción), espacio de nombres y tipo .NET](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
