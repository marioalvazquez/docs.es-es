---
title: Byte (Tipo de datos, Visual Basic)
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6475ff3ed905abb022a9ef60204c04b45130ae22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="byte-data-type-visual-basic"></a>Tipo de datos de byte (Visual Basic)
Contiene enteros de (1-bytes) de 8 bits sin signo que van de un valor comprendido entre 0 y 255.

## <a name="remarks"></a>Comentarios

Use la `Byte` tipo de datos para contener datos binarios.  
  
El valor predeterminado de `Byte` es 0.

## <a name="literal-assignments"></a>Asignaciones de literales

Puede declarar e inicializar un `Byte` variable asignarle un decimal literal, un literal hexadecimal, un literal octal, o (a partir de Visual Basic de 2017) un literal binario. Si el literal entero está fuera del intervalo de un `Byte` (es decir, si es inferior a <xref:System.Byte.MinValue?displayProperty=nameWithType> o mayor que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), se produce un error de compilación.

En el siguiente ejemplo, enteros es igual a 201 que se representan como decimal, hexadecimal, y literales binarios se convierten implícitamente desde [entero](integer-data-type.md) a `byte` valores.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Use el prefijo `&h` o `&H` para denotar un literal hexadecimal, el prefijo `&b` o `&B` para denotar un literal binario y el prefijo `&o` o `&O` para denotar un literal octal. Los literales decimales no tienen prefijo.

A partir de Visual Basic de 2017, también puede utilizar el carácter de subrayado, `_`, como un separador de dígitos para mejorar la legibilidad, como en el ejemplo siguiente se muestra.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

## <a name="programming-tips"></a>Sugerencias de programación

-   **Números negativos.** Dado que `Byte` es un tipo sin signo, no puede representar un número negativo. Si se utiliza el operador unario menos (`-`) operador en una expresión que se evalúa como tipo `Byte`, Visual Basic convierte la expresión `Short` primero.
  
-   **Conversiones de formato.** Cuando Visual Basic lee o escribe archivos o cuando llama a archivos DLL, métodos y propiedades, puede convertir automáticamente entre los formatos de datos. Datos binarios almacenados en `Byte` matrices y variables se conservan durante estas conversiones de formato. No se debe usar un `String` variable para los datos binarios, ya que su contenido puede dañarse durante la conversión entre los formatos ANSI y Unicode.

-   **De ampliación.** El `Byte` tipo de datos se amplía a `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, o `Double`. Esto significa que se puede convertir `Byte` a cualquiera de estos tipos sin que se produzca una <xref:System.OverflowException?displayProperty=nameWithType> error.
  
-   **Caracteres de tipo.** `Byte`no tiene ningún carácter de tipo literal ni caracteres de tipo identificador.

-   **Tipo de Framework.** El tipo correspondiente en .NET Framework es la estructura <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente, `b` es un `Byte` variable. Las instrucciones muestran el intervalo de la variable y la aplicación de operadores de desplazamiento de bits a ella.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Vea también

 <xref:System.Byte?displayProperty=nameWithType>  
 [Tipos de datos](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funciones de conversión de tipos](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumen de conversión](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso eficiente de tipos de datos](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
