---
title: "Seguridad del transporte con la autenticación de Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 68550646f806b30f072b4270a336698011db54d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-with-windows-authentication"></a>Seguridad del transporte con la autenticación de Windows
El escenario siguiente muestra un cliente [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] y el servicio protegido por la seguridad de Windows. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]programación, vea [Cómo: proteger un servicio con credenciales de Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
 Un Servicio Web de la intranet muestra la información de recursos humanos. El cliente es una aplicación de Windows Form. La aplicación se implementa en un dominio con un controlador Kerberos que protege el dominio.  
  
 ![Seguridad de transporte con autenticación de Windows](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Modo de seguridad|Transporte|  
|Interoperabilidad|Solo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]|  
|Autenticación (servidor)<br /><br /> Autenticación (cliente)|Sí (al utilizar la autenticación integrada de Windows)<br /><br /> Sí (al utilizar la autenticación integrada de Windows)|  
|Integridad|Sí|  
|Confidencialidad|Sí|  
|Transporte|NET.TCP|  
|Enlaces|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Servicio  
 El código y la configuración siguientes están diseñados para ejecutarse de forma independiente. Realice una de las siguientes acciones:  
  
-   Cree un servicio independiente mediante el código sin configuración.  
  
-   Cree un servicio mediante la configuración proporcionada, pero sin definir ningún extremo.  
  
### <a name="code"></a>Código  
 El código siguiente muestra cómo crear un punto de conexión de servicio que utilice la seguridad de Windows.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Configuración  
 Se puede usar la configuración siguiente en lugar del código para configurar el extremo de servicio:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
 El código y la configuración siguientes están diseñados para ejecutarse de forma independiente. Realice una de las siguientes acciones:  
  
-   Cree un cliente independiente mediante el código (y el código de cliente).  
  
-   Cree un cliente que no defina direcciones de extremo. En su lugar, utilice el constructor de cliente que adopta el nombre de configuración como un argumento. Por ejemplo:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Código  
 El siguiente código crea el cliente. El enlace se configura para utilizar la seguridad del modo de transporte, con el transporte TCP, con el tipo de credencial de cliente establecido en Windows.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Configuración  
 La configuración siguiente se puede utilizar en lugar del código para crear el cliente.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre seguridad](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Cómo proteger un servicio con credenciales de Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [Modelo de seguridad de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
