---
title: Elegir entre DateTime, DateTimeOffset, TimeSpan y TimeZoneInfo
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d2ed7d037faa0bab649600128dc97580c7b972f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Elegir entre DateTime, DateTimeOffset, TimeSpan y TimeZoneInfo

Las aplicaciones de .NET que usan la información de fecha y hora son muy diversas y pueden usar esa información de varias maneras. Estos son algunos de los usos más comunes de la información de fecha y hora:

* Reflejar solo la fecha (la información de hora no es importante).

* Reflejar solo la hora (la información de fecha no es importante).

* Reflejar una fecha y una hora abstractas que no estén asociadas a una hora ni a un lugar concretos (por ejemplo, la mayoría de tiendas de una cadena internacional abren los días laborables a las 09:00).

* Para recuperar información de fecha y hora de orígenes de fuera de. NET, por lo general donde se almacena información de fecha y hora en un sencillo de tipo de datos.

* Identificar de forma exclusiva e inequívoca un solo punto en el tiempo. Algunas aplicaciones requieren que la fecha y la hora tan solo sean inequívocas en el sistema host; otras requieren que sean inequívocas en todos los sistemas (es decir, que una fecha serializada en un sistema se pueda deserializar y usar con sentido en otro sistema en cualquier lugar en el mundo).

* Conservar varias horas relacionadas (como la hora local del solicitante y la hora de recepción del servidor con respecto a una solicitud web).

* Realizar operaciones aritméticas de fecha y hora, posiblemente con un resultado que identifica de forma exclusiva e inequívoca un único punto en el tiempo.

.NET incluye la <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, y <xref:System.TimeZoneInfo> tipos, que puede usarse para compilar aplicaciones que funcionan con fechas y horas.

> [!NOTE]
> En este tema no se describe un cuarto tipo, <xref:System.TimeZone>, porque su funcionalidad está incorporada casi por completo en la clase <xref:System.TimeZoneInfo> . Siempre que sea posible, los desarrolladores deben usar la clase <xref:System.TimeZoneInfo> en lugar de la clase <xref:System.TimeZone> .

## <a name="the-datetime-structure"></a>DateTime (estructura)

Un valor <xref:System.DateTime> define una fecha y hora concretas. Incluye un <xref:System.DateTime.Kind%2A> propiedad que proporciona información limitada sobre la zona horaria a la que esa fecha y hora pertenece. El <xref:System.DateTimeKind> valor devuelto por la <xref:System.DateTime.Kind%2A> propiedad indica si la <xref:System.DateTime> valor representa la hora local (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), hora Universal coordinada (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), o una hora no especificada (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

La estructura <xref:System.DateTime> es adecuada para aplicaciones que hacen lo siguiente:

* Trabajar solo con fechas.

* Trabajar solo con horas.

* Trabajar con fechas y horas abstractas.

* Trabajar con fechas y horas cuya información de zona horaria no esté disponible.

* Trabajar solo con fechas y horas UTC.

* Recuperar información de fecha y hora de orígenes fuera de. NET, como bases de datos SQL. Normalmente, estos orígenes almacenan la información de fecha y hora en un formato sencillo que es compatible con la estructura <xref:System.DateTime> .

* Realizar operaciones aritméticas de fecha y hora, pero con interés por los resultados generales. Por ejemplo, en una operación que suma seis meses a una determinada fecha y hora, a menudo no resulta importante si el resultado se ajusta al horario de verano.

A menos que un determinado valor <xref:System.DateTime> represente la hora UTC, ese valor de fecha y hora suele ser ambiguo o limitado en su movilidad. Por ejemplo, si un valor <xref:System.DateTime> representa la hora local, entonces se puede mover en la zona horaria local (es decir, si el valor se deserializa en otro sistema de la misma zona horaria, dicho valor sigue identificando inequívocamente un único punto en el tiempo). Fuera de la zona horaria local, ese valor <xref:System.DateTime> puede tener varias interpretaciones. Si la propiedad <xref:System.DateTime.Kind%2A> del valor es <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, es aún menos móvil: ahora es ambiguo dentro de la misma zona horaria y posiblemente incluso en el mismo sistema en el que se serializó por primera vez. Solo si un valor <xref:System.DateTime> representa la hora UTC, ese valor identificará inequívocamente un único punto con independencia del sistema o la zona horaria en los que se usa el valor.

> [!IMPORTANT]
> Al guardar o compartir datos de <xref:System.DateTime>, debe usarse la hora UTC, y la propiedad <xref:System.DateTime.Kind%2A> del valor <xref:System.DateTime> debe establecerse en <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset (estructura)

La estructura <xref:System.DateTimeOffset> representa un valor de fecha y hora, junto con un desplazamiento que indica la diferencia de ese valor con respecto a la hora UTC. Por lo tanto, el valor identifica siempre de forma inequívoca un único punto en el tiempo.

El tipo <xref:System.DateTimeOffset> incluye toda la funcionalidad del tipo <xref:System.DateTime> junto con la zona horaria. Esto resulta adecuado para aplicaciones que haga lo siguiente:

* Identificar de forma exclusiva e inequívoca un solo punto en el tiempo. El tipo <xref:System.DateTimeOffset> puede usarse para definir inequívocamente el significado de “ahora”, para registrar los tiempos de transacción, para registrar la hora de eventos del sistema o de aplicaciones, y para registrar los tiempos de creación y modificación de archivos.

* Realizar operaciones aritméticas generales de fecha y hora.

* Conservar varias horas relacionadas, siempre que esas horas se almacenen como dos valores independientes o como dos miembros de una estructura.

> [!NOTE]
> Estos usos de valores <xref:System.DateTimeOffset> son mucho más comunes que los de valores <xref:System.DateTime> . Como resultado, <xref:System.DateTimeOffset> debe considerarse como el tipo de fecha y hora predeterminado para el desarrollo de aplicaciones.

Un valor <xref:System.DateTimeOffset> no está asociado a una zona horaria determinada, pero puede originarse en distintas zonas horarias. Para ilustrar esto, en el ejemplo siguiente se enumeran las zonas horarias a las que pueden pertenecer varios valores <xref:System.DateTimeOffset> (incluida una hora estándar local del Pacífico).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

La salida muestra que cada valor de fecha y hora de este ejemplo puede pertenecer al menos a tres zonas horarias diferentes. El valor <xref:System.DateTimeOffset> de 6/10/2007 muestra que si un valor de fecha y hora representa un horario de verano, su desplazamiento de la hora UTC no tiene que corresponderse necesariamente con el desplazamiento de UTC base de la zona horaria de origen o con el desplazamiento de UTC de su nombre para mostrar. Esto significa que, dado que un solo valor <xref:System.DateTimeOffset> no está asociado estrechamente con su zona horaria, no puede reflejar un cambio de zona horaria con respecto al horario de verano. Esto puede ser particularmente problemático cuando se usan operaciones aritméticas de fecha y hora para manipular un valor <xref:System.DateTimeOffset> . (Para obtener información sobre cómo realizar operaciones aritméticas de fecha y hora teniendo en cuenta las reglas de ajuste de una zona horaria, vea el artículo [Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)).

## <a name="the-timespan-structure"></a>TimeSpan (estructura)

La estructura <xref:System.TimeSpan> representa un intervalo de tiempo. Sus dos usos típicos son:

* Reflejar el intervalo de tiempo entre dos valores de fecha y hora. Por ejemplo, restar un valor <xref:System.DateTime> de otro devuelve un valor <xref:System.TimeSpan> .

* Medir el tiempo transcurrido. Por ejemplo, el <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> propiedad devuelve un <xref:System.TimeSpan> valor que refleja el intervalo de tiempo que ha transcurrido desde la llamada a uno de los <xref:System.Diagnostics.Stopwatch> métodos que empieza a medir el tiempo transcurrido.

Un valor <xref:System.TimeSpan> también puede usarse como sustituto de un valor <xref:System.DateTime> cuando ese valor refleja una hora sin referencia a una hora determinada del día. Este uso es similar a la <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> y <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> propiedades, que devuelven un <xref:System.TimeSpan> valor que representa el tiempo sin referencia a una fecha. Por ejemplo, la estructura <xref:System.TimeSpan> puede usarse para reflejar la hora diaria de apertura o cierre de una tienda, o puede usarse para representar la hora en que se produce cualquier evento habitual.

En el ejemplo siguiente se define una estructura `StoreInfo` que incluye objetos <xref:System.TimeSpan> para las horas de apertura y cierre de la tienda, así como un objeto <xref:System.TimeZoneInfo> que representa la zona horaria de la tienda. La estructura también incluye dos métodos, `IsOpenNow` e `IsOpenAt`, que indican si la tienda está abierta en el momento especificado por el usuario, quien se supone que está en la zona horaria local.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

La estructura `StoreInfo` puede usarla un código de cliente como este.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo (clase)

La clase <xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone. La clase <xref:System.TimeZoneInfo> permite trabajar con valores de fecha y hora de forma que cada uno de esos valores identifique de forma inequívoca un único punto en el tiempo. La clase <xref:System.TimeZoneInfo> también es extensible. Aunque depende de la información de zona horaria proporcionada para los sistemas Windows y definida en el Registro, admite la creación de zonas horarias personalizadas. También admite la serialización y deserialización de la información de zona horaria.

En algunos casos, si desea aprovechar al máximo la clase <xref:System.TimeZoneInfo> puede que tenga que desarrollar aún más. Si los valores de fecha y hora no están estrechamente con las zonas horarias en la que pertenecen, continuar trabajando es necesario. A menos que la aplicación proporcione algún mecanismo para vincular una fecha y hora con su zona horaria asociada, es fácil para un determinado valor de fecha y hora se desasocie de su zona horaria. Un método para vincular esta información es definir una clase o estructura que contenga el valor de fecha y hora, y su objeto de zona horaria asociada.

Aprovechar la compatibilidad de zona horaria en .NET solo es posible si se conoce la zona horaria a la que pertenece un valor de fecha y hora cuando se crea una instancia de ese objeto de fecha y hora. A menudo este no es el caso, especialmente en aplicaciones web o de red.

## <a name="see-also"></a>Vea también

[Fechas, horas y zonas horarias](../../../docs/standard/datetime/index.md)
