---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89aff21ed916e1b486a191f86dde5ed8b3e4ba22
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>Métodos  
 La clase ServiceCredentials no define ningún método.  
  
## <a name="properties"></a>Propiedades  
 La clase ServiceCredentials posee las siguientes propiedades:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 La autenticación del certificado de cliente y la configuración de aprovisionamiento para este servicio.  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Los valores actuales de autenticación de token emitido para este servicio.  
  
### <a name="peer"></a>Del mismo nivel  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 La autenticación de la credencial actual y la configuración de aprovisionamiento que van a utilizar los extremos de transporte del mismo nivel.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Especifica los valores de conversación seguros actuales.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 El certificado asociado a este servicio.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Los valores de nombre de usuario/contraseña para este servicio.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Los valores de autenticación de Windows para este servicio.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Se declara en Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espacio de nombres|Se define en root\ServiceModel|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Description.ServiceCredentials>
