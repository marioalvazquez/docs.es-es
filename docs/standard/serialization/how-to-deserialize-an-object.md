---
title: "Cómo: Deserializar un objeto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 651fb2ca3a3ea81a8a4e894c5f6a71bcf9ac3a50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-deserialize-an-object"></a>Cómo: Deserializar un objeto
Al deserializar un objeto, el formato de transporte determina si creará una secuencia u objeto de archivo. Una vez determinado el formato de transporte, puede llamar <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> o los métodos <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, como se requiera.  
  
### <a name="to-deserialize-an-object"></a>Para deserializar un objeto  
  
1.  Construya un<xref:System.Xml.Serialization.XmlSerializer> utilizando el tipo del objeto para deserializar.  
  
2.  Llame al método <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> para generar una réplica del objeto. Al deserializar, debe convertir el objeto devuelto al tipo del original, como se muestra en el ejemplo siguiente, que deserializa el objeto en un archivo (aunque también se pudo deserializar en una secuencia).  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Introducción a la serialización XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Cómo: Serializar un objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)
