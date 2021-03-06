---
title: "CorMethodSemanticsAttr (Enumeración)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodSemanticsAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodSemanticsAttr
helpviewer_keywords: CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c6dca24aad06b1c07c86cb716f4be344c8458471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr (Enumeración)
Contiene valores que describen la relación entre un método y una propiedad o evento asociados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`msSetter`|Especifica que el método es un `set` descriptor de acceso para una propiedad.|  
|`msGetter`|Especifica que el método es un `get` descriptor de acceso para una propiedad.|  
|`msOther`|Especifica que el método tiene una relación con una propiedad o un evento distintos de los definidos aquí.|  
|`msAddOn`|Especifica que el método agrega métodos de controlador de un evento.|  
|`msRemoveOn`|Especifica que el método quita los métodos de control para un evento.|  
|`msFire`|Especifica que el método genera un evento.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorHdr.h  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones para metadatos](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
