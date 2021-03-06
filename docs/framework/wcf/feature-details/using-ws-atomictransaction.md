---
title: "Utilización de WS-AtomicTransaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12e6e2be3e01ea920b45cce7a27814dd19c00935
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="using-ws-atomictransaction"></a>Utilización de WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) es un protocolo de transacción interoperable. Permite fluir las transacciones distribuidas utilizando los mensajes de servicio web y coordinar de una manera interoperable entre las infraestructuras de transacción heterogéneas. WS-AT utiliza el protocolo de confirmación en dos fases para controlar un resultado atómico entre las aplicaciones distribuidas, administradores de transacciones y administradores de recursos.  
  
 La implementación de WS-AT que [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] proporciona incluye un servicio de protocolo integrado en el administrador de transacciones de Microsoft DTC (Coordinador de transacciones distribuidas, MSDTC). Con WS-AT, las aplicaciones [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pueden fluir transacciones a otras aplicaciones, incluidos los servicios web creados con tecnología de otro fabricante.  
  
 Al fluir una transacción entre una aplicación cliente y una aplicación de servidor, el protocolo de transacción utilizado está determinado por el enlace que el servidor expone en el extremo del cliente seleccionado. Algunos enlaces proporcionados por el sistema [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] especifican el protocolo `OleTransactions` como formato de propagación de transacción de manera predeterminada, mientras otros especifican WS-AT. También puede modificar mediante programación la opción de protocolo de transacción dentro de un enlace determinado.  
  
 La opción del protocolo influye en lo siguiente:  
  
-   El formato de los encabezados del mensaje utilizado para fluir la transacción desde el cliente al servidor.  
  
-   El protocolo de red utilizado para ejecutar el protocolo de confirmación en dos fases entre el administrador de transacciones del cliente y la transacción del servidor para resolver el resultado de la transacción.  
  
 Si el servidor y el cliente se escriben utilizando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], no necesita utilizar WS-AT. En su lugar, puede utilizar la configuración predeterminada de `NetTcpBinding` con el atributo `TransactionFlow` habilitado, que utilizará en su lugar el protocolo `OleTransactions`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). De lo contrario, si está fluyendo las transacciones a los servicios web creados con tecnologías de otro fabricante, deberá utilizar WS-AT.  
  
## <a name="see-also"></a>Vea también  
 [Configurar la compatibilidad con WS-AtomicTransaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
