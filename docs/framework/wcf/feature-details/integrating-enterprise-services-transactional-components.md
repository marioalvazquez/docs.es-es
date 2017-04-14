---
title: "Integraci&#243;n de los componentes transaccionales de Enterprise Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Integraci&#243;n de los componentes transaccionales de Enterprise Services
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] proporciona un mecanismo automático para integrar con Enterprise Services \(vea [Integración en aplicaciones COM\+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)\).Sin embargo, puede querer flexibilidad para desarrollar servicios que utilicen internamente componentes transaccionales hospedados en Enterprise Services.Dado que la característica Transacciones de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se crea en la infraestructura <xref:System.Transactions>, el proceso para integrar Enterprise Services con [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] es idéntico a la especificación de interoperabilidad entre <xref:System.Transactions> y Enterprise Services, tal y como se describe en [Interoperabilidad con Enterprise Services y transacciones de COM\+](http://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Para proporcionar el nivel deseado de interoperabilidad entre la transacción fluida entrante y la transacción de contexto de COM\+, la implementación del servicio debe crear una instancia <xref:System.Transactions.TransactionScope> y utilizar el valor adecuado de la enumeración <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## Integración de Enterprise Services con una operación de servicio  
 El código siguiente muestra una operación, con flujo de transacción permitido, que crea un <xref:System.Transactions.TransactionScope> con la opción <xref:System.Transactions.EnterpriseServicesInteropOption>.Las condiciones siguientes se aplican en este escenario:  
  
-   Si el cliente fluye una transacción, la operación, incluida la llamada al componente Enterprise Services, se ejecuta dentro del ámbito de esa transacción.El uso de <xref:System.Transactions.EnterpriseServicesInteropOption> asegura que la transacción se sincroniza con el contexto <xref:System.EnterpriseServices>, lo que significa que la transacción ambiente para <xref:System.Transactions> y <xref:System.EnterpriseServices> es la misma.  
  
-   Si el cliente no fluye una transacción, al establecer <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> en `true` se crea un nuevo ámbito de transacción para la operación.De igual forma, utilizar <xref:System.Transactions.EnterpriseServicesInteropOption> garantiza que la transacción de la operación es igual que la transacción utilizada dentro del contexto del componente <xref:System.EnterpriseServices>.  
  
 Cualquier llamada adicional al método también se produce dentro del ámbito de la transacción de la misma operación.  
  
```  
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 Si no se necesita ninguna sincronización entre la transacción actual de la operación y las llamadas a los componentes transaccionales de Enterprise Services, después utilice la opción <xref:System.Transactions.EnterpriseServicesInteropOption> cuando cree instancias de la instancia <xref:System.Transactions.TransactionScope>.  
  
## Integración de Enterprise Services con un cliente  
 El código siguiente muestra código de cliente utilizando una instancia <xref:System.Transactions.TransactionScope> con el valor <xref:System.Transactions.EnterpriseServicesInteropOption>.En este escenario, las llamadas a las operaciones de servicio que admiten el flujo de la transacción se producen dentro del ámbito de la misma transacción como las llamadas a los componentes de Enterprise Services.  
  
```  
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## Vea también  
 [Integración en aplicaciones COM\+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [Integración en aplicaciones COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)