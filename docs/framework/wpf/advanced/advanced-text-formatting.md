---
title: Formato de texto avanzado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1828b6ffe2d24c2bfb98b4668a9540adf5978e5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="advanced-text-formatting"></a>Formato de texto avanzado
El [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ofrece un potente conjunto de [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] para incluir texto en la aplicación. Diseño y [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], como <xref:System.Windows.Controls.TextBlock>, proporcione los más comunes y elementos de uso general para la presentación de texto. Dibujo [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], como <xref:System.Windows.Media.GlyphRunDrawing> y <xref:System.Windows.Media.FormattedText>, proporcionan un medio para incluir texto con formato en dibujos. El nivel avanzado, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] proporciona un motor para controlar todos los aspectos de presentación de texto, como la administración de almacén de texto, administración de formato de texto y administración de los objetos incrustados de formato de texto extensible.  
  
 Este tema proporciona una introducción a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] el formato de texto. Se centra en la implementación del cliente y el uso de la [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] motor de formato de texto.  
  
> [!NOTE]
>  Todos los ejemplos de código dentro de este documento pueden encontrarse en el [Advanced Text Formatting Sample](http://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Requisitos previos  
 En este tema se da por supuesto que está familiarizado con el nivel más alto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] usa para la presentación de texto. La mayoría de los escenarios de usuario no requerirá el formato de texto avanzada [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] tratados en este tema. Para obtener una introducción a las diferencias del texto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], consulte [documentos en WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Formato de texto avanzado  
 El diseño del texto y [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controla en [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] proporcionan propiedades de formato que permiten incluir con facilidad texto con formato en la aplicación. Estos controles exponen varias propiedades para controlar la presentación de texto, como las de tipo de letra, tamaño y color. En circunstancias normales, estos controles pueden controlar la mayoría de las características de presentación de texto en la aplicación. Sin embargo, algunos escenarios avanzados requieren el control del almacenamiento de texto, así como su presentación. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] proporciona un motor de formato de texto extensible para este fin.  
  
 Características de formato de texto avanzado se encuentra en [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consisten en un formato de texto motor, un almacén de texto, ejecuciones de texto y propiedades de formato. El motor de formato de texto <xref:System.Windows.Media.TextFormatting.TextFormatter>, crea las líneas de texto que se utilizará para la presentación. Esto se logra al iniciar el proceso de formato de línea y el formateador de texto de llamada <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. El formateador de texto recupera las ejecuciones de su almacén de texto mediante una llamada a la tienda <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> método. El <xref:System.Windows.Media.TextFormatting.TextRun> objetos, a continuación, se forman en <xref:System.Windows.Media.TextFormatting.TextLine> objetos por el formateador de texto y entrega a la aplicación para inspección o presentación.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Uso del formateador de texto  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>es el [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dar formato al texto del motor y proporciona servicios para dar formato e interrumpir las líneas de texto. El formateador de texto puede controlar los distintos formatos de caracteres de texto y estilos de párrafo, e incluye compatibilidad para el diseño de texto internacional.  
  
 A diferencia de un texto tradicional [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], el <xref:System.Windows.Media.TextFormatting.TextFormatter> interactúa con un cliente de diseño de texto a través de un conjunto de métodos de devolución de llamada. Requiere que el cliente proporcione estos métodos en una implementación de la <xref:System.Windows.Media.TextFormatting.TextSource> clase. El siguiente diagrama ilustra la interacción de diseño de texto entre la aplicación cliente y <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagrama de TextFormatter y cliente de diseño de texto](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interacción entre la aplicación y TextFormatter  
  
 El formateador de texto se utiliza para recuperar las líneas de texto con formato del almacén de texto, que es una implementación de <xref:System.Windows.Media.TextFormatting.TextSource>. Esto se hace creando primero una instancia del formateador de texto usando el <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> método. Este método crea una instancia del formateador de texto y establece los valores máximos de alto y ancho de línea. En cuanto se crea una instancia del formateador de texto, el proceso de creación de la línea se inicia mediante una llamada a la <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> método. <xref:System.Windows.Media.TextFormatting.TextFormatter>vuelve a llamar a la fuente de texto para recuperar el texto y los parámetros de formato de las ejecuciones de texto que forman una línea.  
  
 En el ejemplo siguiente, se muestra el proceso para formatear un almacén de texto. El <xref:System.Windows.Media.TextFormatting.TextFormatter> objeto se usa para recuperar las líneas de texto desde el almacén de texto y, a continuación, dar formato a la línea de texto para dibujar en el <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementación del almacén de texto de cliente  
 Al ampliar el motor de formato de texto, es necesario que implemente y administre todos los aspectos del almacén de texto. Esta no es una tarea trivial. El almacén de texto es responsable del seguimiento de las propiedades de las ejecuciones de texto, las propiedades de párrafo, los objetos incrustados y otro contenido similar. También proporciona el formateador de texto con individuo <xref:System.Windows.Media.TextFormatting.TextRun> objetos que utiliza el formateador de texto para crear <xref:System.Windows.Media.TextFormatting.TextLine> objetos.  
  
 Para controlar la virtualización de la tienda de texto, el almacén de texto se debe derivar de <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>define el método usado por el formateador de texto para recuperar ejecuciones de texto desde el almacén de texto. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>es el método utilizado por el formateador de texto para recuperar texto ejecuta usado en el formato de la línea. La llamada a <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> se realiza varias veces por el formateador de texto hasta que se produce una de las condiciones siguientes:  
  
-   Un <xref:System.Windows.Media.TextFormatting.TextEndOfLine> o se devuelve una subclase.  
  
-   El ancho acumulado de ejecuciones de texto supera el ancho de línea máximo especificado en la llamada para el formateador de texto o de a la llamada para crear el formateador de texto <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> método.  
  
-   Un [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] secuencia de nueva línea, como "CF", "LF" o "CRLF", se devuelve.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Abastecimiento de ejecuciones de texto  
 La esencia del proceso de formato de texto es la interacción entre el formateador de texto y el almacén de texto. La implementación de <xref:System.Windows.Media.TextFormatting.TextSource> proporciona el formateador de texto con el <xref:System.Windows.Media.TextFormatting.TextRun> objetos y las propiedades que se va a dar formato se ejecuta el texto. Esta interacción se controla mediante el <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> método, que es llamado por el formateador de texto.  
  
 En la tabla siguiente muestra algunas de las predefinidas <xref:System.Windows.Media.TextFormatting.TextRun> objetos.  
  
|Tipo TextRun|Uso|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Ejecución de texto especializada que se usa para devolver una representación de glifos de caracteres al formateador de texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Ejecución de texto especializada que se usa para proporcionar contenido donde la medida, la prueba de posicionamiento y el dibujo se ejecutan de forma global, como un botón o una imagen dentro del texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Ejecución de texto especializada que se usa para marcar el final de una línea.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Ejecución de texto especializada que se usa para marcar el final de un párrafo.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|La ejecución de texto especializada que se usa para marcar el final de un segmento, por ejemplo, al final del ámbito afectado por una anterior <xref:System.Windows.Media.TextFormatting.TextModifier> ejecutar.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Ejecución de texto especializada que se usa para marcar un intervalo de caracteres ocultos.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Ejecución de texto especializada que se usa para modificar las propiedades de las ejecuciones de texto en su ámbito. El ámbito se extiende a la coincidencia siguiente <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> ejecución de texto o la próxima <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Cualquiera de las predefinidas <xref:System.Windows.Media.TextFormatting.TextRun> pueden crear subclases de objetos. Esto permite que el origen del texto proporcione al formateador de texto ejecuciones de texto que incluyan datos personalizados.  
  
 En el ejemplo siguiente se muestra un <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> método. Este almacén de texto devuelve <xref:System.Windows.Media.TextFormatting.TextRun> objetos para el formateador de texto para su procesamiento.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  En este ejemplo, el almacén de texto proporciona las mismas propiedades de texto para todo el texto. Los almacenes de texto avanzados tendrían que implementar su propia administración de intervalos para permitir que caracteres individuales tengan propiedades diferentes.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Especificación de las propiedades de formato  
 <xref:System.Windows.Media.TextFormatting.TextRun>se da formato a objetos mediante las propiedades proporcionadas por el almacén de texto. Estas propiedades son de dos tipos, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> y <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>Administrar propiedades de inclusión de párrafo como <xref:System.Windows.TextAlignment> y <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>son propiedades que pueden ser diferentes para cada ejecución de texto de un párrafo, por ejemplo, el pincel de primer plano, <xref:System.Windows.Media.Typeface>y el tamaño de fuente. Para implementar el párrafo personalizado y tipos de propiedades de ejecución de texto personalizado, la aplicación debe crear clases que derivan de <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> y <xref:System.Windows.Media.TextFormatting.TextRunProperties> respectivamente.  
  
## <a name="see-also"></a>Vea también  
 [Tipografía en WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Documentos en WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
