---
title: "Configuración"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86a6e12f-73b5-450e-8725-f4ca5fe0702c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3eee9f955ca75d799b9e5384e47df527934a595f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="configuration"></a>Configuración
En este tema se enumeran todas las excepciones que genera la configuración [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="exception-list"></a>Lista de excepciones  
  
|Código de recurso|Cadena de recurso|  
|-------------------|---------------------|  
|ConfigBindingCannotBeConfigured|No se puede configurar el enlace en el extremo de servicio.|  
|ConfigElementKeyNull|La clave de elemento de configuración concreta no puede ser NULL.|  
|ConfigExtensionTypeNotRegisteredInCollection|El tipo de extensión concreto no está registrado en la colección de extensiones concreta.|  
|ConfigIndexOutOfRange|El valor para el atributo concreto está fuera del intervalo.|  
|ConfigInvalidBindingConfigurationName|La configuración concreta no tiene un enlace con el nombre específico.|  
|ConfigInvalidBindingName|La configuración concreta no tiene un enlace con el nombre específico. Éste es un valor no válido para el enlace.|  
|ConfigInvalidCommonEndpointBehaviorType|No pueda agregar la extensión de comportamiento concreta al comportamiento del extremo común porque no implementa el tipo específico.|  
|ConfigInvalidCommonServiceBehaviorType|No pueda agregar la extensión de comportamiento concreta al comportamiento del servicio común porque no implementa el tipo específico.|  
|ConfigInvalidEndpointBehaviorType|No pueda agregar la extensión de comportamiento concreta al comportamiento del extremo concreto porque el tipo de comportamiento subyacente no implementa la interfaz IServiceBehavior.|  
|ConfigInvalidExtensionType|El tipo específico debe derivar de la extensión concreta para que se utilice en la colección.|  
|ConfigInvalidServiceBehaviorType|No pueda agregar la extensión de comportamiento al comportamiento de servicio con el nombre específico porque el tipo de comportamiento subyacente no implementa la interfaz IServiceBehavior.|  
|ConfigMessageEncodingAlreadyInBinding|No puede agregar el elemento de codificación de mensajes concreto. Otro elemento de codificación de mensajes ya existe en el enlace concreto. Solo puede haber un elemento de codificación de mensajes para cada enlace.|  
|ConfigNoExtensionCollectionAssociatedWithType|No puede encontrar la colección de extensiones asociada a la extensión del tipo específico.|  
|ConfigSectionNotFound|No se puede crear la sección de configuración concreta. Al archivo Machine.config le falta información. Compruebe que esta sección de configuración esté correctamente registrada y que ha escrito correctamente el nombre de sección. Para las secciones Windows Communication Foundation, ejecute ServiceModelReg.exe -i para corregir este error.|  
|ConfigTransportAlreadyInBinding|No puede agregar el elemento de transporte concreto. Otro elemento de transporte ya existe en el enlace concreto. Solo puede haber un elemento de codificación de mensajes para cada enlace.|
