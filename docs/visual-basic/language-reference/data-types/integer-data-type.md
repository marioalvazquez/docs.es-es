---
title: Integer (Tipo de datos, Visual Basic)
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69c7fb6caf5d9a10c7d033d1ba0a05c9230d472c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="integer-data-type-visual-basic"></a>Tipo de datos entero (Visual Basic)
Contiene enteros de 32 bits con signo (4 bytes) comprendidos en el intervalo entre -2.147.483.648 y 2.147.483.647.  
  
## <a name="remarks"></a>Comentarios
 El tipo de datos `Integer` proporciona un rendimiento óptimo en un procesador de 32 bits. Los demás tipos enteros son más lentos a la hora de cargarse y almacenarse en la memoria.  
  
 El valor predeterminado de `Integer` es 0.  

## <a name="literal-assignments"></a>Asignaciones de literales

Puede declarar e inicializar un `Integer` variable asignarle un decimal literal, un literal hexadecimal, un literal octal, o (a partir de Visual Basic de 2017) un literal binario. Si el literal entero está fuera del intervalo de `Integer` (es decir, si es inferior a <xref:System.Int32.MinValue?displayProperty=nameWithType> o mayor que <xref:System.Int32.MaxValue?displayProperty=nameWithType>, se produce un error de compilación.

En el ejemplo siguiente, los enteros que equivalen a 16 342 que se representan como literales binarios, hexadecimales y decimales se asignan a valores `Integer`.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Use el prefijo `&h` o `&H` para denotar un literal hexadecimal, el prefijo `&b` o `&B` para denotar un literal binario y el prefijo `&o` o `&O` para denotar un literal octal. Los literales decimales no tienen prefijo.

A partir de Visual Basic de 2017, también puede utilizar el carácter de subrayado, `_`, como un separador de dígitos para mejorar la legibilidad, como en el ejemplo siguiente se muestra.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

También pueden incluir literales numéricos el `I` [escriba carácter](../../programming-guide\language-features\data-types/type-characters.md) para denotar el `Integer` tipo de datos, como se muestra en el ejemplo siguiente.

```vb
Dim number = &H035826I
```

## <a name="programming-tips"></a>Sugerencias de programación

-   **Consideraciones de interoperabilidad.** Si interactúa con componentes no se han escrito para .NET Framework, como los objetos de automatización o COM, recuerde que `Integer` tiene un ancho de datos diferente (16 bits) en otros entornos. Al pasar un argumento de 16 bits a esos componentes, declárelo en el código de Visual Basic como `Short` en lugar de como `Integer`.  
  
-   **De ampliación.** El tipo de datos `Integer` se amplía a `Long`, `Decimal`, `Single` o `Double`. Esto significa que puede convertir un tipo de datos `Integer` en cualquiera de estos tipos sin que se produzca un error <xref:System.OverflowException?displayProperty=nameWithType>.  
  
-   **Caracteres de tipo.** Al agregar el carácter de tipo literal `I` a un literal, el tipo de datos se convierte forzosamente en el tipo de datos `Integer`. Si se agrega el carácter de tipo identificador `%` a cualquier identificador, se convierte forzosamente al tipo `Integer`.  
  
-   **Tipo de Framework.** El tipo correspondiente en .NET Framework es la estructura <xref:System.Int32?displayProperty=nameWithType>.  
  
## <a name="range"></a>Intervalo

Si intenta establecer una variable de un tipo entero en un número que está fuera del intervalo correspondiente a ese tipo, se produce un error. Si intenta establecerlo en una fracción, el número se redondea hacia arriba o hacia abajo al valor entero más cercano. Si el número está equidistante a dos valores enteros, el valor se redondea al entero par más próximo. Este comportamiento minimiza los errores de redondeo que se derivan de redondear de forma consistente un valor de punto medio en una dirección única. En el código siguiente se muestran ejemplos de redondeo.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Vea también

<xref:System.Int32?displayProperty=nameWithType>   
 [Tipos de datos](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Long (tipo de datos)](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Short (tipo de datos)](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Funciones de conversión de tipos](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumen de conversión](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso eficiente de tipos de datos](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
