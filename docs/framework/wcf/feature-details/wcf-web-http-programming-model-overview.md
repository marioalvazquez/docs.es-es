---
title: "Información general del modelo de programación web HTTP de WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb32d1c9c0c0922dae27b2933259df9470cceeba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-programming-model-overview"></a>Información general del modelo de programación web HTTP de WCF
El modelo de programación WEB HTTP de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] proporciona los elementos de marco de trabajo básicos que son necesarios para compilar servicios WEB HTTP con [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Los servicios WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] están diseñados para que la gama más amplia de clientes posible tenga acceso a ellos, incluidos los exploradores web, y tienen los requisitos únicos siguientes:  
  
-   **URI y procesamiento de URI** URI juegan un papel fundamental en el diseño de servicios WEB HTTP. El modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa las clases <xref:System.UriTemplate> y <xref:System.UriTemplateTable> para proporcionar las funciones de procesamiento de URI.  
  
-   **Compatibilidad con las operaciones GET y POST** servicios WEB HTTP usan el verbo GET para la recuperación de datos, además de varios verbos de modificación de datos y la invocación remota de invocación. El modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa los atributos <xref:System.ServiceModel.Web.WebGetAttribute> y <xref:System.ServiceModel.Web.WebInvokeAttribute> para asociar las operaciones de servicio con el verbo GET y otros verbos HTTP, como PUT, POST y DELETE.  
  
-   **Varios formatos de datos** servicios de estilo Web procesan muchos tipos de datos además de los mensajes SOAP. El modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa <xref:System.ServiceModel.WebHttpBinding> y <xref:System.ServiceModel.Description.WebHttpBehavior> para admitir muchos formatos de datos diferentes incluyendo documentos XML, objeto de datos de JSON y secuencias de contenido binario como imágenes, archivos de vídeo o texto sin formato.  
  
 El modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] extiende el alcance de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para abarcar escenarios de tipo web que incluyen los servicios WEB HTTP, AJAX y JSON, así como las fuentes de distribución (ATOM/RSS). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Servicios de AJAX y JSON, consulte [integración de AJAX y compatibilidad de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Distribución, consulte [información general de la distribución de WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 No existen restricciones adicionales en los tipos de datos que puedan devolverse desde un servicio WEB HTTP. Cualquier tipo serializable se puede devolver a partir de una operación de servicio WEB HTTP de WCF. Puesto que estas operaciones de servicio WEB HTTP las puede invocar un explorador web existe un límite en los tipos de datos que se pueden especificar en una dirección URL. Para obtener más información sobre los tipos admitidos de forma predeterminada, consulte el **parámetros de cadena de consulta de UriTemplate y las direcciones URL** sección más adelante. El comportamiento predeterminado se puede cambiar proporcionando su propia implementación de la clase T:System.ServiceModel.Dispatcher.QueryStringConverter que especifica cómo convertir los parámetros especificados de una dirección URL en el tipo de parámetro real. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Los servicios escritos mediante el modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no usan mensajes SOAP. Por este motivo, no se podrán usar las características de seguridad proporcionadas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Sin embargo, puede usar la seguridad basada en el transporte hospedando el servicio con HTTPS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seguridad, consulte [información general sobre seguridad](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Si se instala la extensión WebDAV para IIS, se puede provocar que los servicios web HTTP devuelvan un error 405 HTTP cuando la extensión WebDAV intente administrar todas las solicitudes PUT. Para evitar este problema puede desinstalar la extensión WebDAV o deshabilitarla para su sitio web. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][IIS y WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Procesamiento de URI con UriTemplate y UriTemplateTable  
 Las plantillas URI proporcionan una sintaxis eficaz para expresar grandes conjuntos de URI similares estructuralmente. Por ejemplo, la siguiente plantilla expresa el conjunto de todos los URI de tres segmentos que comienzan en "a" y acaban en "c" sin tener en cuenta el valor del segmento intermedio: a/{segmento}/c  
  
 Esta plantilla describe los URI de la siguiente manera:  
  
-   a/x/c  
  
-   a/y/c  
  
-   a/z/c  
  
-   etc.  
  
 En esta plantilla, la notación de la llave (" {segmento}") indica un segmento variable en lugar de un valor literal.  
  
 .NET Framework proporciona una API para trabajar con plantillas de URI denominadas <xref:System.UriTemplate>. `UriTemplates` permite hacer lo siguiente:  
  
-   Puede llamar a uno de los `Bind` métodos con un conjunto de parámetros para generar un *URI totalmente cerrado* que coincide con la plantilla. Esto significa que todas las variables dentro de la plantilla URI se reemplaza con valores reales.  
  
-   Puede llamar `Match`() con un URI candidato, que utiliza una plantilla para dividir un URI candidato en sus partes constituyentes y devuelve un diccionario que contiene las partes diferentes del URI etiquetadas según las variables de la plantilla.  
  
-   `Bind`() y `Match`() son inversos para que pueda llamar `Match`( `Bind`(x)) y vuelven con el mismo entorno con el que comenzó.  
  
 Hay muchas veces (sobre todo en el servidor, donde es necesario enviar una solicitud a una operación de servicio basada en el URI) que desea realizar el seguimiento de un conjunto de objetos <xref:System.UriTemplate> en una estructura de datos que se puede direccionar independientemente de cada una de las plantillas contenidas. <xref:System.UriTemplateTable> representa un conjunto de plantillas de URI y selecciona la mejor coincidencia dado un conjunto de plantillas y un URI candidato. Esto no está asociado a ninguna pila de conexión de red determinada (incluido [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]) por lo que puede utilizarlo dondequiera que necesario.  
  
 El modelo de servicio de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hace uso de <xref:System.UriTemplate> y <xref:System.UriTemplateTable> para asociar las operaciones del servicio a un conjunto de URI descrito mediante una <xref:System.UriTemplate>. Una operación de servicio está asociada a una <xref:System.UriTemplate>, utilizando <xref:System.ServiceModel.Web.WebGetAttribute> o <xref:System.ServiceModel.Web.WebInvokeAttribute>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.UriTemplate> y <xref:System.UriTemplateTable>, consulte [UriTemplate y UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Atributos WebGet y WebInvoke  
 Los servicios WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hacen uso de verbos de recuperación (por ejemplo, HTTP GET), además de varios verbos de invocación (por ejemplo, HTTP POST, PUT y DELETE). El modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permite a los desarrolladores de servicios controlar la plantilla URI y el verbo asociado con sus operaciones de servicio con <xref:System.ServiceModel.Web.WebGetAttribute> y <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> y <xref:System.ServiceModel.Web.WebInvokeAttribute> le permiten controlar cómo las operaciones individuales se enlazan a los URI y los métodos HTTP asociados a esos URI. Por ejemplo, agregando en el siguiente código, <xref:System.ServiceModel.Web.WebGetAttribute> y <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,   
                               string newName );  
}  
```  
  
 El código anterior le permite realizar las solicitudes HTTP siguientes.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> establece como valor predeterminado POST pero también puede utilizarlo para otros verbos.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Para ver un ejemplo completo de un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] servicio que utiliza el [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP de modelo de programación, vea [Cómo: crear un servicio básico de HTTP de Web de WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Parámetros de cadena de consulta y direcciones URL de UriTemplate  
 Se puede llamar a los servicios de tipo web desde un explorador web escribiendo una URL que está asociada a una operación del servicio. Estas operaciones del servicio pueden tomar parámetros de cadena de consulta que se deben especificar en forma de cadena dentro de la dirección URL. La siguiente tabla muestra los tipos que se pueden pasar dentro de una dirección URL y el formato utilizado.  
  
|Tipo|Formato|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (no se requiere la notación exponencial)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (no se requiere la notación exponencial)|  
|<xref:System.Char>|Cualquier carácter individual|  
|<xref:System.Decimal>|Cualquier decimal en notación estándar (sin exponente)|  
|<xref:System.Boolean>|True o False (sin distinción entre mayúsculas y minúsculas)|  
|<xref:System.String>|Cualquier cadena (no se admite la cadena nula y no se utilizan caracteres de escape)|  
|<xref:System.DateTime>|MM/DD/YYYY<br /><br /> MM/DD/AAAA HH [AM &#124; PM]<br /><br /> Mes día año<br /><br /> Mes día año hh [AM &#124; PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Donde DD = Días, HH = Horas, MM = minutos, SS = Segundos|  
|<xref:System.Guid>|Un GUID, por ejemplo:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> Donde DD = Días, HH = Horas, MM = minutos, SS = Segundos|  
|Enumeraciones|El valor de enumeración, por ejemplo, que define la enumeración como se muestra en el código siguiente.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Cualquiera de los valores de enumeración individuales (o sus valores enteros correspondientes) se puede especificar en la cadena de consulta.|  
|Tipos que tienen `TypeConverterAttribute` que puede convertir el tipo en una representación de cadena y viceversa.|Según el convertidor de tipos.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Los formatos y el modelo de programación WEB HTTP de WCF  
 El modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tiene nuevas características que funcionan con muchos formatos de datos diferentes. En la capa de enlace, <xref:System.ServiceModel.WebHttpBinding> puede leer y escribir los siguientes tipos diferentes de datos:  
  
-   XML  
  
-   JSON  
  
-   Secuencias binarias opacas  
  
 Esto significa que el modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puede administrar cualquier tipo de datos, pero puede estar programando con <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] proporciona compatibilidad con datos JSON (AJAX) y las fuentes de distribución (incluidas ATOM y RSS). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Estas características, consulte [Web HTTP de WCF formato](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[información general de la distribución de WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) y [integración de AJAX y compatibilidad de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>El modelo de programación WEB HTTP de WCF y la seguridad  
 Dado que el modelo de programación WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no admite los protocolos WS-*, la única manera de proteger un servicio WEB HTTP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consiste en exponer el servicio a través de HTTPS mediante SSL. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Cómo configurar SSL con [!INCLUDE[iisver](../../../../includes/iisver-md.md)], vea [cómo implementar SSL en IIS](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Solución de problemas relacionados con el modelo de programación WEB HTTP de WCF  
 Al llamar a los servicios WEB HTTP de WCF mediante un objeto <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> para crear un canal, <xref:System.ServiceModel.Description.WebHttpBehavior> usa la clase <xref:System.ServiceModel.EndpointAddress> establecida en el archivo de configuración, aunque se pase una <xref:System.ServiceModel.EndpointAddress> diferente al <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Vea también  
 [Distribución de WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 [Modelo de objetos de programación Web HTTP de WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [Modelo de programación Web HTTP de WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
