---
title: Distribuidor de canal personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81512576e1d26b63cf65b3a0c9992c2d273d2779
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado
Este ejemplo muestra cómo crear la pila del canal de manera personalizada implementando <xref:System.ServiceModel.ServiceHostBase> directamente y cómo crear un distribuidor de canal personalizado en un entorno de host web. El distribuidor del canal interactúa con <xref:System.ServiceModel.Channels.IChannelListener> para aceptar los canales y recupera los mensajes de la pila del canal. Este ejemplo también proporciona un ejemplo básico para mostrar cómo integrar una pila del canal en un entorno de host web con <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>ServiceHostBase personalizado  
 En este ejemplo se implementa el tipo base <xref:System.ServiceModel.ServiceHostBase> en lugar de <xref:System.ServiceModel.ServiceHost> para mostrar cómo reemplazar la implementación de la pila de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] con un nivel de control de mensajes personalizado encima de la pila del canal. Se invalida el método virtual <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> para compilar los agentes de escucha del canal y el distribuidor de canal.  
  
 Para implementar un servicio hospedado en web, obtenga la extensión de servicio <xref:System.ServiceModel.Activation.VirtualPathExtension> de la colección de la propiedad <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> y agréguela al objeto <xref:System.ServiceModel.Channels.BindingParameterCollection> para que el nivel de transporte sepa cómo configurar el agente de escucha del canal según los valores de entorno de hospedaje, es decir, la configuración de Internet Information Services (IIS)/Servicio de activación de procesos de Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado  
 El distribuidor de canal personalizado extiende el tipo <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Este tipo implementa la lógica de programación del nivel del canal. En este ejemplo, solo se admite <xref:System.ServiceModel.Channels.IReplyChannel> para el patrón de intercambio de mensajes de solicitud-respuesta, pero el distribuidor del canal personalizado se puede extender con facilidad a otros tipos de canal.  
  
 El distribuidor abre el agente de escucha del canal primero y, a continuación, acepta el canal de respuesta singleton. Con el canal, empieza a enviar los mensajes (solicitudes) en un bucle infinito. Para cada solicitud, crea un mensaje de respuesta y lo envía de nuevo al cliente.  
  
## <a name="creating-a-response-message"></a>Crear un mensaje de respuesta  
 El procesamiento de mensajes se implementa en el tipo `MyServiceManager`. En el método `HandleRequest`, el encabezado de mensaje `Action` se comprueba primero para ver si se admite la solicitud. Se define una acción "http://tempuri.org/HelloWorld/Hello" de SOAP predefinida para permitir el filtrado de mensajes. Esto es similar al concepto de contrato de servicios en la implementación de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de <xref:System.ServiceModel.ServiceHost>.  
  
 En el caso de la acción SOAP correcta, el ejemplo recupera los datos de mensaje solicitados y genera una respuesta correspondiente a la solicitud similar a lo que se ve en el caso de <xref:System.ServiceModel.ServiceHost>.  
  
 Para administrar el verbo HTTP-GET en especial, devuelve un mensaje HTML personalizado, en este caso, para que pueda examinar el servicio desde un explorador para ver que está compilado correctamente. Si la acción SOAP no coincide, envíe a un mensaje de error para indicar que no se admite la solicitud.  
  
 El cliente de este ejemplo es un cliente de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] normal que no supone nada del servicio. De este modo, el servicio está diseñado especialmente para coincidir con lo que se obtiene de una implementación de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.ServiceHost> normal. Como resultado, solo se requiere un contrato de servicio en el cliente.  
  
## <a name="using-the-sample"></a>Utilizar el ejemplo  
 Al ejecutar la aplicación cliente directamente, se genera el siguiente resultado.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 También puede examinar el servicio desde un explorador para que se procese un mensaje HTTP-GET en el servidor. De esta forma obtiene de vuelta texto HTLM con formato correcto.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) [Ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4] para descargar todos los ejemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
