---
title: "Integración de System.Web.Routing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73ec25ab5376841b2970fedf17ad1de176923f16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="systemwebrouting-integration"></a>Integración de System.Web.Routing
Al hospedar un servicio de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] en Internet Information Service (IIS), se coloca un archivo .svc en el directorio virtual. Este archivo .svc especifica el generador de host de servicio que se debe usar, así como la clase que implementa el servicio. Al realizar solicitudes al servicio, debe especificar el archivo .svc en el URI, por ejemplo: http://contoso.com/ServicioDeEmpleados.svc. Para programadores que escriben servicios de REST, este tipo de URI no es óptimo. Los URI para los servicios de REST especifican un recurso determinado y normalmente no tienen ninguna extensión. La característica de integración <xref:System.Web.Routing> le permite hospedar un servicio de REST de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que responde a URI sin extensión. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Vea enrutamiento [el enrutamiento de ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) y [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) ejemplo.  
  
## <a name="using-systemwebrouting-integration"></a>Usar la integración de System.Web.Routing  
 Para usar la característica de integración de <xref:System.Web.Routing>, utilice la clase <xref:System.ServiceModel.Activation.ServiceRoute> para crear una o más rutas y agregarlas a <xref:System.Web.Routing.RouteTable> en un archivo Global.asax. Estas rutas especifican los URI relativos a los que responde el servicio. En el ejemplo siguiente se muestra cómo hacerlo.  
  
```  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
```  
  
 Esto enruta todas las solicitudes con un URI relativo que empiece por Customers (Clientes) al servicio `Service`.  
  
 En el archivo Web.config, debe agregar el módulo `System.Web.Routing.UrlRoutingModule`, establecer el atributo `runAllManagedModulesForAllRequests` como `true` y agregar el controlador `UrlRoutingHandler` al elemento `<system.webServer>`, tal y como se muestra en el siguiente ejemplo.  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 Esto carga un módulo y el controlador requerido para el enrutamiento. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Enrutamiento](../../../../docs/framework/wcf/feature-details/routing.md). También debe establecer el atributo `aspNetCompatibilityEnabled` como `true` en el elemento `<serviceHostingEnvironment>`, tal y como se muestra en el siguiente ejemplo.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 La clase que implementa el servicio debe habilitar los requisitos de compatibilidad de ASP.NET, tal y como se muestra en el siguiente ejemplo.  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Vea también  
 [Modelo de programación Web HTTP de WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Enrutamiento de ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660)
