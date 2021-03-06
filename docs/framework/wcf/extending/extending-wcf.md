---
title: "Extensión de WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3d436690108158cfd7675cf00788a564b8a1dc6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="extending-wcf"></a>Extensión de WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] le permite modificar y extender los componentes en tiempo de ejecución para controlar y extender precisamente las aplicaciones basadas en servicio. Los temas de esta sección hacen profundizan en la arquitectura de la extensibilidad. Para obtener más información acerca de la programación básica, consulte [programación básica de WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Extensión de ServiceHost y la capa del modelo de servicio](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 El nivel de modelo de servicio es responsable de extraer los mensajes entrantes de los canales subyacentes, de modo que los traduce en código de aplicación en las invocaciones de método y devuelve los resultados al agente de llamada.  Las extensiones de modelo de servicio modifican o implementan la ejecución o comportamiento de la comunicación y características implicadas en la funcionalidad del distribuidor, comportamientos personalizados, interceptación de mensaje y parámetro, y otra funcionalidad de extensibilidad.  
  
 [Extensión de enlaces](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 Los enlaces son los objetos que describen los datos de comunicación exigidos para conectar a un punto de conexión. Las extensiones de enlace o enlaces personalizados implementan la funcionalidad de la comunicación personalizada exigida para admitir las características de la aplicación.  
  
 [Extender la capa del canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 El nivel del canal se encuentra bajo el nivel de modelo de servicio y es responsable para el intercambio de mensajes entre los clientes y servicios. Las extensiones de canal pueden implementar la nueva funcionalidad de protocolo, como la seguridad. Las extensiones del canal también transportan la funcionalidad, como implementar un nuevo transporte de red para llevar los mensajes SOAP.  
  
 [Extensión de la seguridad](../../../../docs/framework/wcf/extending/extending-security.md)  
 La seguridad en [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consiste en transferir seguridad (integridad, confidencialidad y autenticación), control de acceso (autorización) y auditoría. `IdentityModel` utiliza las clases situadas en el espacio de nombres [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para el control de acceso. Entender la arquitectura de seguridad le permite crear tipos de notificación personalizados para alojar los sistemas de control de acceso personalizados.  
  
 [Extender el sistema de metadatos](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 El sistema de metadatos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] es un grupo de clases e interfaces que representan los metadatos requeridos para implementar las aplicaciones basadas en el servicio. Modifique o extienda las clases o implemente y configure las interfaces para exportar e importar metadatos personalizados, como las extensiones de Lenguaje de descripción de servicios Web (WSDL) o las aserciones personalizadas de WS-PolicyAttachments.  
  
 [Extensión de codificadores y serializadores](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 Los codificadores y serializadores traducen los datos de un formulario a otro. Los temas de esta sección exponen cómo extender las clases proporcionadas para cumplir los requisitos especiales.  
  
## <a name="reference"></a>Referencia  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Programación básica de WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [Detalles de las características de WCF](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [Instrucciones y procedimientos recomendados](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
