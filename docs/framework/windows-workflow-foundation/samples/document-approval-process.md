---
title: "Proceso de aprobación de un documento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 345fb44bed207d5d5e2c30bf4dd6e6ace27d7511
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="document-approval-process"></a>Proceso de aprobación de un documento
En este ejemplo se muestra el uso de varias características de [!INCLUDE[wf](../../../../includes/wf-md.md)] y [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] al mismo tiempo. Juntas implementan un escenario de proceso de aprobación de un documento. Una aplicación cliente puede enviar documentos para su aprobación y aprobar documentos. Existe una aplicación de administrador de aprobaciones para facilitar las comunicaciones entre los clientes y aplicar las reglas del proceso de aprobación. El proceso de aprobación es un flujo de trabajo que puede ejecutar varios tipos de aprobación. Existen actividades para obtener una aprobación única, una aprobación de quórum (un porcentaje de un conjunto de aprobadores) y un proceso de aprobación compleja que consta de una aprobación de quórum y una aprobación única en una secuencia.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) [Ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4] para descargar todos los ejemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>Detalles del ejemplo  
 El siguiente gráfico muestra el flujo de trabajo del proceso de aprobación de un documento.  
  
 ![Un flujo de trabajo del proceso de aprobación de documentos](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")  
  
 Desde la perspectiva del cliente, el proceso de aprobación funciona del siguiente modo:  
  
1.  Un cliente realiza una suscripción para convertirse en usuario en el sistema del proceso de aprobación.  
  
2.  Un cliente de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] la envía a un servicio de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedado por la aplicación de administrador de aprobaciones.  
  
3.  Se devuelve un Id. de usuario único al cliente. El cliente puede participar ahora en los procesos de aprobación.  
  
4.  Una vez admitido, un cliente puede enviar un documento para su aprobación mediante un proceso de aprobación única, de quórum o compleja.  
  
5.  Al hacer clic en un botón de la interfaz del cliente, se inicia una instancia de flujo de trabajo en un host de servicio de flujo de trabajo del cliente.  
  
6.  El flujo de trabajo envía una solicitud de aprobación a la aplicación de administrador de aprobaciones.  
  
7.  El administrador del flujo de trabajo inicia un flujo de trabajo por su parte para representar un proceso de aprobación.  
  
8.  Una vez ejecutado el flujo de trabajo de aprobación del administrador, los resultados se devuelven al cliente.  
  
9. El cliente muestra los resultados.  
  
10. Un cliente puede recibir una solicitud de aprobación y responder a la solicitud en cualquier momento.  
  
11. Un servicio de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedado en el cliente puede recibir una solicitud de aprobación procedente de la aplicación de administrador de aprobaciones.  
  
12. La información del documento se presenta en el cliente para revisión.  
  
13. El usuario puede aprobar o rechazar el documento.  
  
14. Se utiliza un cliente de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para devolver una respuesta de aprobación a la aplicación de administrador de aprobaciones.  
  
 Desde el punto de vista de la aplicación de administrador de aprobaciones, el proceso de aprobación funciona del siguiente modo:  
  
1.  Un cliente solicita al sistema del proceso de aprobación participar.  
  
2.  Un servicio de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en el administrador de aprobaciones recibe una solicitud para formar parte del sistema del proceso de aprobación.  
  
3.  Se genera un identificador único para el cliente. La información sobre el usuario se almacena en una base de datos.  
  
4.  El identificador único se envía al usuario.  
  
5.  Se recibe una solicitud de aprobación. El administrador de aprobaciones ejecuta un proceso de aprobación.  
  
6.  El administrador de aprobaciones recibe una solicitud de aprobación, lo que inicia un nuevo flujo de trabajo.  
  
7.  Según el tipo de solicitud (simple, quórum o compleja), se ejecuta una actividad diferente.  
  
8.  Las actividades Send y Receive con correlación se utilizan para enviar la solicitud de aprobación al cliente para su revisión y recibir la respuesta.  
  
9. El resultado del flujo de trabajo del proceso de aprobación se envía al cliente.  
  
## <a name="using-the-sample"></a>Utilizar el ejemplo  
  
##### <a name="to-set-up-the-database"></a>Para configurar la base de datos  
  
1.  Desde un símbolo del sistema de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] abierto con privilegios de administrador, navegue a esta carpeta DocumentApprovalProcess y ejecute Setup.cmd.  
  
##### <a name="to-set-up-the-application"></a>Para configurar la aplicación  
  
1.  Con [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra el archivo de solución de DocumentApprovalProcess.sln.  
  
2.  Para compilar la solución, presione Ctrl+MAYÚS+B.  
  
3.  Para ejecutar la solución, inicie la aplicación Administrador de aprobaciones haciendo clic en el proyecto ApprovalManager en el **el Explorador de soluciones** y haga clic en **depurar**->**iniciar**  nueva instancia en el menú contextual.  
  
     Espere a que el resultado del administrador le indique que está listo.  
  
##### <a name="to-run-the-single-approval-scenario"></a>Para ejecutar el escenario de aprobación única  
  
1.  Abra un símbolo del sistema con permisos de administrador.  
  
2.  Navegue al directorio que contiene la solución.  
  
3.  Navegue a la carpeta ApprovalClient\Bin\Debug y ejecute dos instancias de ApprovalClient.exe.  
  
4.  Haga clic en **detectar**, espere hasta que el **suscribirse** botón está habilitado.  
  
5.  Escriba un nombre de usuario y haga clic en **suscribirse**. Para un cliente, use `UserType1` y para el otro, escriba `UserType2`.  
  
6.  En el cliente `UserType1`, seleccione el tipo de aprobación única en el menú desplegable y escriba un nombre de documento y su contenido. Haga clic en **solicitar la aprobación**.  
  
7.  En el cliente `UserType2`, aparecerá un documento a la espera de aprobación. Selecciónelo y presione **aprobar** o **rechazar**. Los resultados deberían mostrarse en el cliente `UserType1`.  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>Para ejecutar el escenario de aprobación de quórum  
  
1.  Abra un símbolo del sistema con permisos de administrador.  
  
2.  Navegue al directorio que contiene la solución.  
  
3.  Navegue a la carpeta ApprovalClient\Bin\Debug y ejecute tres instancias de ApprovalClient.exe.  
  
4.  Haga clic en **detectar**, espere hasta que el **suscribirse** botón está habilitado.  
  
5.  Escriba un nombre de usuario y haga clic en **suscribirse**. Para un cliente, use `UserType1` y para los otros dos, escriba `UserType2`.  
  
6.  En el cliente `UserType1`, seleccione el tipo de aprobación de quórum en el menú desplegable y escriba un nombre de documento y su contenido. Haga clic en **solicitar la aprobación**. Este tipo de aprobación requieres que los dos clientes `UserType2` aprueben o rechacen el documento. Aunque los dos clientes `UserType2` deben responder, solo uno de ellos necesita aprobar el documento para que se considere aprobado.  
  
7.  En los clientes `UserType2`, aparecerá un documento a la espera de aprobación. Selecciónelo y presione **aprobar** o **rechazar**. Los resultados deberían mostrarse en el cliente `UserType1`.  
  
##### <a name="to-run-the-complex-approval-scenario"></a>Para ejecutar el escenario de aprobación compleja  
  
1.  Abra un símbolo del sistema con permisos de administrador.  
  
2.  Navegue al directorio que contiene la solución.  
  
3.  Navegue a la carpeta ApprovalClient\Bin\Debug y ejecute cuatro instancias de ApprovalClient.exe.  
  
4.  Haga clic en **detectar**, espere hasta que el **suscribirse** botón está habilitado.  
  
5.  Escriba un nombre de usuario y haga clic en **suscribirse**. Para un cliente, use `UserType1`, para los otros dos, escriba `UserType2` y en el último, use `UserType3`.  
  
6.  En el cliente `UserType1`, seleccione el tipo de aprobación única en el menú desplegable y escriba un nombre de documento y su contenido. Haga clic en **solicitar la aprobación**.  
  
7.  En los clientes `UserType2`, aparecerá un documento a la espera de aprobación. Selecciónelo y presione **aprobar**, el documento se pasa a la `UserType3` cliente.  
  
     Si el primer quórum `UserType2` aprueba el documento, el documento se pasa al cliente `UserType3`.  
  
8.  Apruebe o rechace el documento en el cliente `UserType3`. Los resultados deberían mostrarse en el cliente `UserType1`.  
  
##### <a name="to-clean-up"></a>Para realizar una limpieza  
  
1.  En un símbolo de sistema de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], navegue a la carpeta DocumentApprovalProcess y ejecute Cleanup.cmd.