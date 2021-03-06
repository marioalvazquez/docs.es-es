---
title: '&lt;lista&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34347df88f1bc3097db0020526ec99943c8f7bd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="ltlistgt-visual-basic"></a>&lt;lista&gt; (Visual Basic)
Define una lista o tabla.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 El tipo de la lista. Debe ser "bullet" para una lista con viñetas, "number" para una lista numerada o "table" para una tabla de dos columnas.  
  
 `term`  
 Sólo se utiliza cuando `type` es "table". Término que se define en la etiqueta de descripción.  
  
 `description`  
 Cuando `type` es "bullet" o "número", `description` es un elemento de la lista cuando `type` es "table", `description` es la definición de `term`.  
  
## <a name="remarks"></a>Comentarios  
 El `<listheader>` bloque define el encabezado de una tabla o una definición de lista. Cuando se define una tabla, solo tiene que suministrar una entrada para `term` en el encabezado.  
  
 Cada elemento de la lista se especifica con un `<item>` bloque. Al crear una lista de definiciones, debe especificar tanto `term` y `description`. Sin embargo, para una tabla, una lista con viñetas o una lista numerada, solo tienes que proporcionar una entrada para `description`.  
  
 Una lista o una tabla puede tener tantos `<item>` bloquea según sea necesario.  
  
 Compile con el parámetro [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza la `<list>` etiqueta para definir una lista con viñetas en la sección Comentarios.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Etiquetas XML para comentarios](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
