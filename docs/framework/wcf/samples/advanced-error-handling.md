---
title: Control de errores avanzado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 046907af6a8f88760f2be12c3c5608b16a24b28a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-error-handling"></a>Control de errores avanzado
En este ejemplo se muestra el servicio de enrutamiento de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. El servicio de enrutamiento es un componente de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que permite incluir fácilmente un enrutador basado en contenido en una aplicación. Este ejemplo muestra el modo en que el servicio de enrutamiento se recupera de los errores de forma inteligente, utilizando transacciones y otros conceptos de mensajería más complejos, como la multidifusión.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) [Ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4] para descargar todos los ejemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Detalles del ejemplo  
 En este ejemplo, el servicio de enrutamiento se configura para leer un mensaje de una cola de MSMQ y multidifundirlo a dos listas de colas. Una lista se utiliza para las colas de servicios y la otra para las colas de registro.  
  
 Dado que, de forma predeterminada, el enlace MSMQ para el que el servicio de enrutamiento está configurado para usar admite el uso de transacciones, el servicio de enrutamiento se asegura de que el mensaje es transaccional y se recibe en al menos una cola de cada lista antes de informar a la cola entrante (`InQ`) de que el mensaje se enrutó correctamente. Así, en el caso en el que tanto las colas de servicios como las colas de registro no estén disponibles, los informes del servicio de enrutamiento en las que no se pudo enrutar el mensaje y la cola entrante deberían actuar. Esta actuación consiste en mover el mensaje a la cola de mensajes no enviados del sistema.  
  
#### <a name="to-use-this-sample"></a>Para utilizar este ejemplo  
  
1.  > [!IMPORTANT]
    >  Instale MSMQ antes de ejecutar este ejemplo. Si MSMQ no está instalado, se devuelve un mensaje de excepción al ejecutar el ejemplo. Encontrará instrucciones para instalar MSMQ en [instalar Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Con [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra AdvancedErrorHandling.sln.  
  
2.  Presione **F5** o **CTRL + MAYÚS + B** en [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Si compila la aplicación con CTRL+MAYÚS+B, debe iniciar la aplicación en ./RoutingService/bin/debug/RoutingService.exe.  
  
3.  En la ventana de la consola, presione ENTRAR para iniciar el cliente.  
  
4.  El cliente devuelve estadísticas diferentes acerca de las colas en cada caso.  
  
    1.  El siguiente es el resultado devuelto para el caso 1 (no hay errores).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  El siguiente es el resultado devuelto para el caso 3 (errores en las colas de servicio y registro principales).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  El siguiente es el resultado devuelto para el caso 4 (errores en las colas de registro principal y de reserva, y en la cola del servicio).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  El siguiente es el resultado devuelto para el caso 2 (error en la cola de servicio principal).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurable a través de código o App.onfig  
 El ejemplo viene configurado para utilizar un archivo App.config que define el comportamiento del enrutador. También puede cambiar el nombre del archivo RoutingService\App.config para que no se reconozca y cambiar el valor del campo `configDriven` en RoutingService\Program.cs a `false` para utilizar la configuración definida en el código. Cualquier método provoca el mismo comportamiento del enrutador.  
  
### <a name="scenario"></a>Escenario  
 En este ejemplo se muestra que el servicio de enrutamiento puede administrar capacidades de mensajería avanzadas, como las transacciones y el contexto de recepción, y que puede utilizar estas capacidades como una parte de la administración correcta de los escenarios de error.  
  
### <a name="real-world-scenario"></a>Escenario real  
 Contoso desea utilizar las recepciones transaccionales a través del servicio de enrutamiento para asegurarse de que todos los servicios necesarios reciben información incluso durante condiciones de error. Además, desean administrar los errores de forma correcta y automática, y los errores que se van a notificar en el caso de que un mensaje no pueda entregarse ni siquiera cuando se utiliza la lógica de control de errores. Para este propósito, configuran el servicio de enrutamiento para conmutar por error a puntos de conexión concretos según se prevea y para que el servicio del enrutamiento administre las situaciones de error, lo que incluye crear, completar y recuperar o anular los contextos de recepción y transacciones según convenga.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplos de persistencia y el hospedaje de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
