---
title: "Diseño de propiedades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 477b3b69ce1b8a3bb160e8e120885239e3d99e56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="property-design"></a>Diseño de propiedades
Aunque las propiedades son técnicamente muy similares a los métodos, son bastante diferentes en cuanto a sus escenarios de uso. Deben considerarse como campos inteligentes. Y tienen la sintaxis de llamada de campos y la flexibilidad de los métodos.  
  
 **✓ HACER** crear propiedades get-only si el llamador no debe estar autorizado cambiar el valor de la propiedad.  
  
 Tenga en cuenta que, si el tipo de la propiedad es un tipo de referencia mutable, el valor de propiedad puede cambiarse incluso si la propiedad es de solo get.  
  
 **X DO NOT** proporcionan solo para establecer propiedades o propiedades con el establecedor tener accesibilidad más amplio que el captador.  
  
 Por ejemplo, no utilice las propiedades con un establecedor público y un captador protegido.  
  
 Si no se puede proporcionar el captador de propiedad, implementar la funcionalidad que un método en su lugar. Considere la posibilidad de iniciar el nombre del método con `Set` y siga con lo que habría denominado la propiedad. Por ejemplo, <xref:System.AppDomain> tiene un método denominado `SetCachePath` en lugar de tener una propiedad de sólo establecimiento denominada `CachePath`.  
  
 **✓ HACER** proporcionan valores predeterminados razonables para todas las propiedades, garantizando que los valores predeterminados no producen una vulnerabilidad de seguridad o un código muy ineficaz.  
  
 **✓ HACER** permite que las propiedades que se establecerán en cualquier orden, incluso si esto da como resultado un estado temporal no válido del objeto.  
  
 Es habitual que dos o más propiedades para estar interrelacionados a un punto donde algunos valores de una propiedad pueden no ser válidos, dados los valores de otras propiedades en el mismo objeto. En tales casos, se deben posponer las excepciones resultantes de dicho estado no válido hasta que las propiedades interrelacionadas realmente se utilizan conjuntamente por el objeto.  
  
 **✓ HACER** conservar el valor anterior si un establecedor de propiedad inicia una excepción.  
  
 **X evitar** iniciar excepciones desde los captadores de propiedades.  
  
 Captadores de propiedades deberían ser operaciones simples y no deben tener las condiciones previas. Si un captador puede producir una excepción, se debe probablemente volver a diseñar para que sea un método. Tenga en cuenta que esta regla no se aplica a los indizadores, donde se espera excepciones como resultado de la validación de los argumentos.  
  
### <a name="indexed-property-design"></a>Diseño de propiedades indizadas  
 Una propiedad indizada es una propiedad especial que puede tener parámetros y se puede llamar con una sintaxis especial similar a la indización de matriz.  
  
 Propiedades indizadas se conocen normalmente como indizadores. Los indizadores deben usarse solo en las API que proporcionan acceso a los elementos de una colección lógica. Por ejemplo, una cadena es una colección de caracteres y el indizador en <xref:System.String?displayProperty=nameWithType> se agregó para tener acceso a los caracteres.  
  
 **✓ Considere la posibilidad de** utilizar indizadores para proporcionar acceso a los datos almacenados en una matriz interna.  
  
 **✓ Considere la posibilidad de** proporcionar indizadores en los tipos que representan colecciones de elementos.  
  
 **X evitar** utilizando las propiedades con más de un parámetro indizadas.  
  
 Si el diseño requiere varios parámetros, reconsidere si la propiedad representa realmente un descriptor de acceso a una colección lógica. Si no es así, utilice métodos en su lugar. Considere la posibilidad de iniciar el nombre del método con `Get` o `Set`.  
  
 **X evitar** indizadores con tipos de parámetro distinto de <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, o una enumeración.  
  
 Si el diseño requiere otros tipos de parámetros, fuertemente vuelva a evaluar si la API realmente representa un descriptor de acceso a una colección lógica. Si no es así, utilice un método. Considere la posibilidad de iniciar el nombre del método con `Get` o `Set`.  
  
 **✓ HACER** utilizar el nombre `Item` para propiedades indizadas a menos que haya nombre obviamente mejor (p. ej., vea el <xref:System.String.Chars%2A> propiedad `System.String`).  
  
 En C#, los indizadores son de forma predeterminada con el nombre de elemento. La <xref:System.Runtime.CompilerServices.IndexerNameAttribute> puede usarse para personalizar este nombre.  
  
 **X DO NOT** proporciona un indizador y métodos que son semánticamente equivalentes.  
  
 **X DO NOT** proporcionar más de una familia de indizadores sobrecargados en un tipo.  
  
 Esto se aplica por el compilador de C#.  
  
 **X DO NOT** no predeterminado de usar las propiedades indizadas.  
  
 Esto se aplica por el compilador de C#.  
  
### <a name="property-change-notification-events"></a>Eventos de notificación de cambio de propiedad  
 A veces resulta útil proporcionar un evento notificar al usuario de los cambios en un valor de propiedad. Por ejemplo, `System.Windows.Forms.Control` genera un `TextChanged` eventos después del valor de su `Text` propiedad ha cambiado.  
  
 **✓ Considere la posibilidad de** cuando se genera cambiar eventos de notificación cuando se modifican los valores de propiedad en las API de alto nivel (normalmente componentes de diseñador).  
  
 Si hay un caso apropiado para un usuario saber cuando cambia una propiedad de un objeto, el objeto debería generar un evento de notificación de cambio para la propiedad.  
  
 Sin embargo, es probable que tenga que vale la pena la sobrecarga para provocar estos eventos para las API de bajo nivel, como tipos base o colecciones. Por ejemplo, <xref:System.Collections.Generic.List%601> no generaría dichos eventos cuando se agrega un nuevo elemento a la lista y `Count` cambios de propiedad.  
  
 **✓ Considere la posibilidad de** cuando se genera los eventos de notificación cuando cambia el valor de una propiedad a través de fuerzas externas cambio.  
  
 Si cambia un valor de propiedad a través de alguna causa externa (de forma distinto mediante una llamada a métodos en el objeto), se producirá eventos indican al programador que el valor cambia y se ha cambiado. Un buen ejemplo es la `Text` propiedad de un control de cuadro de texto. Cuando el usuario escribe texto en un `TextBox`, cambia automáticamente el valor de propiedad.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Reservados todos los derechos.*  
  
 *Volver a imprimir en el permiso de educación de Pearson, Inc. de [directrices de diseño de marco de trabajo: convenciones, expresiones y patrones para las bibliotecas .NET de reutilizable, 2ª edición](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina y Brad Abrams, publicado el 22 de octubre de 2008 por Addison-Wesley Professional como parte de la serie de desarrollo de Microsoft Windows.*  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de diseño de miembros](../../../docs/standard/design-guidelines/member.md)  
 [Instrucciones de diseño de .NET Framework](../../../docs/standard/design-guidelines/index.md)
