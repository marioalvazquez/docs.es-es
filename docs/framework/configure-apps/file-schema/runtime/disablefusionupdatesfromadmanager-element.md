---
title: '&lt;disableFusionUpdatesFromADManager&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4aa3343e7f3f60bbf6a57340d858c1ef12197bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disableFusionUpdatesFromADManager&gt; elemento
Especifica si el comportamiento predeterminado, que consiste en permitir el host en tiempo de ejecución para invalidar los valores de configuración de un dominio de aplicación, está deshabilitado.  
  
 \<Configuración > elemento  
\<en tiempo de ejecución > elemento  
\<disableFusionUpdatesFromADManager >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|enabled|Atributo necesario.<br /><br /> Especifica si se deshabilita la capacidad predeterminada de invalidar la configuración de fusión.|  
  
## <a name="enabled-attribute"></a>Atributo enabled  
  
|Valor|Descripción|  
|-----------|-----------------|  
|0|Deshabilitar la capacidad de invalidar la configuración de fusión. Éste es el comportamiento predeterminado, a partir de la [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Deshabilitar la capacidad de invalidar la configuración de fusión. Esto revierte el comportamiento de versiones anteriores de .NET Framework.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|  
|`runtime`|Contiene información del enlace del ensamblado y de la recolección de elementos no utilizados.|  
  
## <a name="remarks"></a>Comentarios  
 A partir de la [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], el comportamiento predeterminado es permitir la <xref:System.AppDomainManager> objeto que se va a invalidar opciones de configuración mediante el uso de la <xref:System.AppDomainSetup.ConfigurationFile%2A> propiedad o el <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método de la <xref:System.AppDomainSetup> objeto que se pasa a la implementación de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método, en su subclase de <xref:System.AppDomainManager>. Para el dominio de aplicación predeterminado, la configuración que cambia invalida la configuración especificada por el archivo de configuración de aplicación. Para otros dominios de aplicación, invalidan los valores de configuración que se pasaron a la <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> o <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.  
  
 Puede pasar nueva información de configuración o pasar null (`Nothing` en Visual Basic) para eliminar la información de configuración que se pasó.  
  
 No pase información de configuración a ambos el <xref:System.AppDomainSetup.ConfigurationFile%2A> propiedad y el <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método. Si se pasa la información de configuración a ambos, la información se pasa a la <xref:System.AppDomainSetup.ConfigurationFile%2A> propiedad se omite porque el <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método invalida la información de configuración desde el archivo de configuración de aplicación. Si usas el <xref:System.AppDomainSetup.ConfigurationFile%2A> propiedad, se puede pasar null (`Nothing` en Visual Basic) a la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método para eliminar los bytes de configuración que se especificaron en la llamada a la <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> o <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.  
  
 Además de información de configuración, puede cambiar la configuración siguiente en el <xref:System.AppDomainSetup> objeto que se pasa a la implementación de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, y <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Como alternativa al uso de la `<disableFusionUpdatesFromADManager>` elemento, puede deshabilitar el comportamiento predeterminado mediante la creación de una configuración del registro o estableciendo una variable de entorno. En el registro, cree un valor DWORD denominado `COMPLUS_disableFusionUpdatesFromADManager` en `HKCU\Software\Microsoft\.NETFramework` o `HKLM\Software\Microsoft\.NETFramework`y establezca el valor en 1. En la línea de comandos, establezca la variable de entorno `COMPLUS_disableFusionUpdatesFromADManager` en 1.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo deshabilitar la capacidad de invalidar la configuración de fusión usando el `<disableFusionUpdatesFromADManager>` elemento.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también  
 [Esquema de la configuración de Common Language Runtime](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de los archivos de configuración](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Cómo el motor en tiempo de ejecución ubica ensamblados](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
