---
title: "Return (Instrucción, Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a>Return (Instrucción, Visual Basic)
Devuelve el control al código que llamó una `Function`, `Sub`, `Get`, `Set`, o `Operator` procedimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Parte  
 `expression`  
 Necesario en un `Function`, `Get`, o `Operator` procedimiento. Expresión que representa el valor que se devuelve al código de llamada.  
  
## <a name="remarks"></a>Comentarios  
 En un `Sub` o `Set` procedimiento, el `Return` instrucción es equivalente a un `Exit Sub` o `Exit Property` (instrucción), y `expression` no se debe proporcionar.  
  
 En un `Function`, `Get`, o `Operator` procedimiento, el `Return` debe incluir la instrucción `expression`, y `expression` se debe evaluar como un tipo de datos que se pueda convertir al tipo de valor devuelto del procedimiento. En un `Function` o `Get` procedimiento, también tiene la alternativa de asignación de una expresión para el nombre del procedimiento para que actúe como el valor devuelto y, a continuación, ejecutar una `Exit Function` o `Exit Property` instrucción. En un `Operator` procedimiento, debe usar `Return``expression`.  
  
 Puede incluir tantos `Return` instrucciones según corresponda en el mismo procedimiento.  
  
> [!NOTE]
>  El código en un `Finally` bloque se ejecuta después de un `Return` instrucción en un `Try` o `Catch` bloque es encontró, pero antes de que `Return` se ejecuta la instrucción. A `Return` instrucción no puede incluirse en un `Finally` bloque.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el `Return` instrucción varias veces para volver al código de llamada cuando el procedimiento no tiene que hacer nada más.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Function (instrucción)](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub (instrucción)](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get (instrucción)](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set (instrucción)](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator (instrucción)](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property (instrucción)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit (instrucción)](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try...Catch...Finally (instrucción)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
