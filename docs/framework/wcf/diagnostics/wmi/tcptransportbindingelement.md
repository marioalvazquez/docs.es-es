---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Métodos  
 La clase TcpTransportBindingElement no define ningún método.  
  
## <a name="properties"></a>Propiedades  
 La clase TcpTransportBindingElement tiene las propiedades siguientes:  
  
### <a name="connectionpoolsettings"></a>connectionPoolSettings  
 Tipo de datos: TcpConnectionPoolSettings  
  
 Tipo de acceso: solo lectura  
  
 Agrupación de conexiones.  
  
### <a name="listenbacklog"></a>ListenBacklog  
 Tipo de datos: sint32  
  
 Tipo de acceso: solo lectura  
  
 El número máximo de solicitudes de conexión en cola que pueden estar pendientes.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 Valor booleano que especifica si el uso compartido de los puertos TCP está habilitado para esta conexión.  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 Un valor booleano que especifica si Teredo (una tecnología para direccionar clientes que están detrás de firewalls) está habilitada.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Se declara en Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espacio de nombres|Se define en root\ServiceModel|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
