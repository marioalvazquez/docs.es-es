---
title: "ICorDebugHeapValue::IsValid (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue.IsValid
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df7105c94a6f88c9c196f1d9d6be6f4a62f7c258
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid (Método)
Obtiene un valor que indica si el objeto representado por este ICorDebugHeapValue es válido.  
  
 Este método está en desuso en la versión 2.0 de .NET Framework.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbValid`  
 [out] Un puntero a un valor booleano que indica si este valor en el montón es válido.  
  
## <a name="remarks"></a>Comentarios  
 El valor no es válido si se ha recuperado por el recolector de elementos no utilizados.  
  
 Este método está en desuso. En la versión 2.0 de .NET Framework, todos los valores son válidos hasta [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) se llama, en cuyo momento se invalidan los los valores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
