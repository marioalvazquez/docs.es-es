---
title: "Usar actividades de colección"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be7615441f29046fc1a469e3cace86267fc6c031
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="using-collection-activities"></a>Usar actividades de colección
En este ejemplo se muestra cómo utilizar las actividades de colección (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>y <xref:System.Activities.Statements.RemoveFromCollection%601>) con una clase que implementa la interfaz <xref:System.Collections.ICollection> y cómo crear una actividad personalizada que recorra en iteración la colección para imprimir el contenido de cada elemento de la colección. La actividad personalizada, que se denomina `PrintCollection`, imprime en la consola los miembros de elemento de una colección llamada `Numbers`.  
  
 En la siguiente tabla se describen las cuatro actividades que ofrecen a los flujos de trabajo manipulación de colecciones.  
  
|Nombre de actividad|Descripción|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Agrega un elemento a una colección.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Borra todos los elementos de una colección.|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Devuelve `true` si el elemento especificado ya existe en la colección.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Quita un elemento de una colección.|  
  
 El ejemplo se compone de dos soluciones, una bajo el directorio CodedWorkflow y la otra bajo el directorio DesignerWorkflow. Muestran dos maneras diferentes de utilizar las actividades para conseguir los mismos fines.  
  
|Soluciones|Descripción|Archivos principales|  
|-|-|-|  
|CodedWorkflow|Aplicación cliente de ejemplo que muestra cómo invocar las actividades de colección mediante programación.|**PrintCollection.cs**: actividad de aplicación auxiliar para imprimir en la consola de todos los elementos de una colección.<br /><br /> **Program.cs**: compila mediante programación una actividad de secuencia que contiene una serie de actividades de colección y lo ejecuta.|  
|DesignerWorkflow|Aplicación cliente de ejemplo que muestra cómo utilizar las actividades de colección en el diseñador de flujo de trabajo mediante declaración.|**CollectionWorkflow.xaml**: un flujo de trabajo creado mediante declaración con el diseñador que utiliza las actividades de colección.<br /><br /> **PrintCollection.cs**: actividad de aplicación auxiliar para imprimir en la consola de todos los elementos de una colección.<br /><br /> **Program.cs**: invoca el flujo de trabajo descrito en CollectionWorkflow.xaml.|  
  
 En la demostración, los miembros de elemento de la colección `Numbers` se imprimen en la consola mediante una actividad definida de forma personalizada denominada `PrintCollection`.  
  
#### <a name="to-use-this-sample"></a>Para utilizar este ejemplo  
  
1.  Abra el archivo de solución Collection.sln con [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para compilar la solución, presione Ctrl+MAYÚS+B.  
  
3.  Para ejecutar la solución, presione CTRL+F5.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) [Ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4] para descargar todos los ejemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`