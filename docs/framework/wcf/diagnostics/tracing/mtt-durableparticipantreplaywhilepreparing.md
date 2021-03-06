---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 830a55a9f82c38b0a58783c49d3f58f64d5afdb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
El servicio de protocolo WS-AT recibió un mensaje de reproducción desde un participante duradero, que no respondió a la instrucción para preparar. Por consiguiente, se anuló la transacción.  
  
## <a name="description"></a>Descripción  
 Se realiza un seguimiento si se recibe un mensaje de reproducción mientras un participante duradero se está preparando. Se trata de un mensaje no válido para este estado y se va a anular la transacción.  
  
## <a name="troubleshooting"></a>Solución de problemas  
 Recibir este error puede indicar que un participante duradero (incluidos los administradores de transacciones subordinados) se ha recuperado del error, aunque no se sabe a ciencia cierta el resultado de la transacción y solicita su estado.  
  
## <a name="see-also"></a>Vea también  
 [Seguimiento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uso del seguimiento para solucionar problemas de la aplicación](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administración y diagnóstico](../../../../../docs/framework/wcf/diagnostics/index.md)
