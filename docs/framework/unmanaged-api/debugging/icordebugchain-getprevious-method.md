---
title: "ICorDebugChain::GetPrevious (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetPrevious
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1203aa4a6e35574c1d026ddc05cac810fed5b78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetprevious-method"></a>ICorDebugChain::GetPrevious (Método)
Obtiene la cadena anterior de marcos para el subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppChain`  
 [out] Un puntero a la dirección de un objeto ICorDebugChain que representa la cadena anterior de marcos para este subproceso. Si esta cadena es la primera cadena, `ppChain` es null.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
