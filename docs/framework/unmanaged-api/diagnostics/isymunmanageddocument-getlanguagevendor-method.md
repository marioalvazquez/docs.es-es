---
title: "ISymUnmanagedDocument::GetLanguageVendor (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguageVendor
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 72fffae9995f44be9a9359c16bb876d79c9a8242
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a>ISymUnmanagedDocument::GetLanguageVendor (Método)
Obtiene el proveedor de lenguaje de este documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Un puntero a una variable que recibe el proveedor de lenguaje.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si el método tiene éxito.  
  
## <a name="see-also"></a>Vea también  
 [ISymUnmanagedDocument (interfaz)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
