---
title: IEnumIDENTITY_ATTRIBUTE (Interfaz)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumIDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords: IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f88e400556421e0908e0a0b115f66ec3221124c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="ienumidentityattribute-interface"></a>IEnumIDENTITY_ATTRIBUTE (Interfaz)
Actúa como un enumerador para los atributos del objeto de código en el ámbito actual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Obtiene un puntero de interfaz a una nueva `IEnumIDENTITY_ATTRIBUTE` que contiene los mismos miembros que esto `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Escribe los datos contenidos en los elementos de esta `IEnumIDENTITY_ATTRIBUTE` al búfer de datos especificado.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Obtiene el número especificado de atributos, comenzando en la posición actual.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Mueve el puntero de instrucción al principio de este `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Mueve el puntero de instrucción hacia delante el número especificado de elementos, empezando en la posición actual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Isolation.h  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de Fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
