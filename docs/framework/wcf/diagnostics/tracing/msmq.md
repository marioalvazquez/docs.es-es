---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15be4b6bfb84a0aa843e3d62861a9195e125a04e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="msmq"></a>MSMQ
En una aplicación MSMQ, no se transfiere ninguna actividad adicional del canal en cola a MSMQ y de MSMQ al canal en cola.  
  
 Además, se siguen tanto el id. de mensaje de MSMQ como el del mensaje SOAP (junto con el id. de la actividad, si existe) como seguimientos de canal en cola en una operación de envío.  
  
 Se siguen tanto el id. de mensaje de MSMQ como el del mensaje SOAP (junto con el id. de la actividad, si existe) como seguimientos de canal en cola en una operación de recepción.  
  
 Las transferencias necesarias en la operación de recepción se ejecutan de igual forma que en cualquier otro transporte (operación de recepción de bytes ->Procese mensaje ->).
