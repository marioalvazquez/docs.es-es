---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da0bc2ac9a4283ec9b23a1d4767f664de071ef47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Métodos  
 La clase OperationBehaviorAttribute no define ningún método.  
  
## <a name="properties"></a>Propiedades  
 La clase OperationBehaviorAttribute tiene las propiedades siguientes:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 El estado de la característica de eliminación automática para parámetros.  
  
### <a name="impersonation"></a>Suplantación  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Indica el nivel de suplantación del llamador que la operación admite.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Indica cuándo durante el curso de una invocación de la operación debe reciclarse el objeto.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 Indica si confirmar automáticamente la transacción actual si no se produce ninguna excepción no controlada.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 Indica si la operación requiere una transacción.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Se declara en Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espacio de nombres|Se define en root\ServiceModel|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
