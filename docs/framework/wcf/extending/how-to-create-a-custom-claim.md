---
title: "C&#243;mo crear una notificaci&#243;n personalizada | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# C&#243;mo crear una notificaci&#243;n personalizada
La infraestructura del modelo de identidad en [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] proporciona un conjunto de derechos y tipos de demanda integradas con las funciones auxiliares para crear <xref:System.IdentityModel.Claims.Claim> instancias con esos tipos y derechos. Estas demandas integradas están diseñadas para modelar información en los tipos de credencial de un cliente que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] admite de forma predeterminada. En muchos casos, las demandas integradas son suficientes; sin embargo, algunas aplicaciones pueden exigir demandas personalizadas. Una demanda está compuesta por el tipo de demanda, el recurso para el que la demanda se aplica y el derecho que se impone sobre ese recurso. En este tema se describe cómo crear una demanda personalizada.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Para crear una demanda personalizada que está basada en un tipo de datos primitivo  
  
1.  Cree una demanda personalizada pasando el tipo de notificación, el valor de recurso y el derecho a la <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.  
  
    1.  Seleccione un valor único para el tipo de demanda.  
  
         El tipo de demanda es un identificador de cadena único. Es la responsabilidad del diseñador de la demanda personalizada asegurar que el identificador de cadena que se usa para el tipo de demanda sea único. Para obtener una lista de tipos de notificación que se definen mediante [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte el <xref:System.IdentityModel.Claims.ClaimTypes> clase.  
  
    2.  Elija el tipo de datos primitivo y el valor para el recurso.  
  
         Un recurso es un objeto. El tipo CLR del recurso puede ser un tipo primitivo, como <xref:System.String> o <xref:System.Int32>, o cualquier tipo serializable. El tipo CLR del recurso debe ser serializable, porque las demandas se serializan en varios puntos a través de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Los tipos primitivos son serializables.  
  
    3.  Elija un derecho definido por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] o un valor único para un derecho personalizado.  
  
         Un derecho es un identificador de cadena único. Los derechos que se definen mediante [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se definen en el <xref:System.IdentityModel.Claims.Rights> clase.  
  
         Es la responsabilidad del diseñador de la demanda personalizada asegurar que el identificador de cadena que se usa para el derecho sea único.  
  
         En el ejemplo de código siguiente se crea una demanda personalizada con un tipo de notificación `http://example.org/claims/simplecustomclaim`, un recurso denominado `Driver's License`y con el <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> derecho.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Para crear una demanda personalizada basada en un tipo de datos no primitivo  
  
1.  Cree una demanda personalizada pasando el tipo de notificación, el valor de recurso y el derecho a la <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.  
  
    1.  Seleccione un valor único para el tipo de demanda.  
  
         El tipo de demanda es un identificador de cadena único. Es la responsabilidad del diseñador de la demanda personalizada asegurar que el identificador de cadena que se usa para el tipo de demanda sea único. Para obtener una lista de tipos de notificación que se definen mediante [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte el <xref:System.IdentityModel.Claims.ClaimTypes> clase.  
  
    2.  Elija o defina un tipo no primitivo serializable para el recurso.  
  
         Un recurso es un objeto. El tipo CLR del recurso debe ser serializable, porque las demandas se serializan en varios puntos a través de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Los tipos primitivos ya son serializables.  
  
         Cuando se define un nuevo tipo, aplique el <xref:System.Runtime.Serialization.DataContractAttribute> a la clase. También se aplican los <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a todos los miembros del nuevo tipo que deba serializarse como parte de la notificación.  
  
         El ejemplo de código siguiente define un tipo de recurso personalizado denominado `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]  
  
    3.  Elija un derecho definido por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] o un valor único para un derecho personalizado.  
  
         Un derecho es un identificador de cadena único. Los derechos que se definen mediante [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se definen en el <xref:System.IdentityModel.Claims.Rights> clase.  
  
         Es la responsabilidad del diseñador de la demanda personalizada asegurar que el identificador de cadena que se usa para el derecho sea único.  
  
         En el ejemplo de código siguiente se crea una demanda personalizada con un tipo de notificación `http://example.org/claims/complexcustomclaim`, un tipo de recurso personalizado `MyResourceType`y con el <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> derecho.  
  
     [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
     [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente muestra cómo crear una demanda personalizada con un tipo de recurso primitivo y una demanda personalizada con un tipo de recurso no primitivo.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.IdentityModel.Claims.Claim>   
 <xref:System.IdentityModel.Claims.Rights>   
 <xref:System.IdentityModel.Claims.ClaimTypes>   
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>   
 [Administración de notificaciones y autorización con el modelo de identidad](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [Administración de notificaciones y autorización con el modelo de identidad](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)