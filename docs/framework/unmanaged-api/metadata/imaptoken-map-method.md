---
title: "IMapToken::Map (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e3a9701bab27764803442a3cd0c24c4e412deaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="imaptokenmap-method"></a>IMapToken::Map (Método)
Asigna una relación entre los ensamblados utilizando firmas de metadatos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `tkImp`  
 [in] El token de metadatos que representa el objeto de código importado.  
  
 `tkEmit`  
 [in] El token de metadatos que representa el objeto de código emitido.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el token volver a asignar se produce durante una mezcla, el token original tiene un ámbito en el ámbito de metadatos importados (origen) y el nuevo token tiene un ámbito en el ámbito de metadatos emitido (destino).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Cor.h  
  
 **Biblioteca:** usada como recurso en MsCorEE.dll  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [IMapToken (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
