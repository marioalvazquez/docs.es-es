---
title: "Cómo recuperar la huella digital de un certificado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f66a7003fe712ab482d5237762e2bafffc5a6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Cómo recuperar la huella digital de un certificado
Al escribir una aplicación [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] que usa un certificado X.509 para la autenticación, es a menudo necesario especificar demandas en el certificado. Por ejemplo, debe proporcionar una demanda de huella digital al utilizar la enumeración <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> en el método <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> . Se requieren dos pasos a la hora de buscar un valor de demanda. Primero, abra el complemento de Microsoft Management Console (MMC) para certificados. (Vea [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Segundo, como se describe aquí, busque un certificado adecuado y copie su huella digital (u otros valores de demanda).  
  
 Si usa un certificado para la autenticación del servicio, es importante apuntar el valor de la columna **Emitido para** (la primera columna en la consola). Al utilizar Capa de sockets seguros (SSL) como seguridad de transporte, una de las primeras comprobaciones es la comparación de la dirección base Identificador uniforme de recursos (URI) de un servicio con el valor **Emitido para** . Los valores deben coincidir o se detiene el proceso de autenticación.  
  
 También puede usar la herramienta Makecert.exe de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] de SDK para crear certificados temporales para el uso durante el desarrollo. Una entidad de certificación no emite, sin embargo, de forma predeterminada, este tipo de certificado, y no se puede usar para propósitos de producción. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Cómo: crear certificados temporales para su uso durante el desarrollo](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Para recuperar una huella digital de un certificado  
  
1.  En Microsoft Management Console (MMC), abra el complemento de certificados. (Vea [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2.  En el panel izquierdo de la ventana **Raíz de consola** , haga clic en **Certificados (Equipo local)**.  
  
3.  Haga clic en la carpeta **Personal** para expandirlo.  
  
4.  Haga clic en la carpeta **Certificados** para expandirlo.  
  
5.  En la lista de certificados, tenga en cuenta el encabezado **Propósitos planteados** . Busque un certificado que haga una lista de **Autenticación de cliente** como un propósito intencional.  
  
6.  Haga doble clic en el certificado.  
  
7.  En el cuadro de diálogo **Certificado** , haga clic en la pestaña **Detalles** .  
  
8.  Desplácese a través de la lista de campos y haga clic en **Huella digital**.  
  
9. Copie los caracteres hexadecimales en el cuadro. Si esta huella digital se usa en código para `X509FindType`, quite los espacios entre los números hexadecimales. Por ejemplo, la huella digital "a9 09 50 2d d8 2a e4 14 33 f8 del e6 38 86 0d del b0 que 42 77 a3 2a 7b" se debería especificar como "a909502dd82ae41433e6f83886b00d4277a32a7b" en código.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [Cómo: configurar un puerto con un certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Cómo: ver certificados con el complemento de MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Cómo: crear certificados temporales para su uso durante el desarrollo](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
