---
title: "Terminología de docker"
description: "Ciclo de vida de aplicación de Docker en contenedores con herramientas y plataforma de Microsoft"
keywords: Docker, microservicios, ASP.NET, contenedor
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: c3b4391a839db02d8bad8380013ea916100e4a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="docker-terminology"></a>Terminología de docker

Esta sección enumeran términos y definiciones con la que debería familiarizarse con antes de profundizar un poco más en Docker (para obtener más definiciones, vea el amplio [glosario](https://docs.docker.com/glossary/) proporcionada por Docker en <https:// docs.docker.com/glossary/>:

-   **Imagen de contenedor** un paquete con todas las dependencias y la información necesaria para crear un contenedor. Una imagen incluye todas las dependencias (por ejemplo, marcos) además de implementación y configuración que se usará en tiempo de ejecución de un contenedor. Normalmente, una imagen se deriva de varias imágenes de base que se capas apilan uno sobre otro para formar el sistema de archivos del contenedor. Una imagen es inmutable después de que se ha creado.

-   **Contenedor** una instancia de una imagen de Docker. Un contenedor representa un tiempo de ejecución para una sola aplicación, proceso o servicio. Está formada por el contenido de una imagen de Docker, un entorno en tiempo de ejecución y un conjunto estándar de instrucciones. Al escalar un servicio, cree varias instancias de un contenedor de la misma imagen. O bien, un proceso por lotes puede crear varios contenedores de la misma imagen, pasar parámetros diferentes para cada instancia.

-   **Etiqueta** una marca o una etiqueta que se puede aplicar a las imágenes para que se pueden identificar los diferentes imágenes o las versiones de la misma imagen (según el número de versión o el entorno de destino).

-   **Dockerfile** un archivo de texto que contiene instrucciones sobre cómo crear una imagen de Docker.

-   **Generar** la acción de creación de una imagen de contenedor en función de la información y el contexto proporcionado por su Dockerfile, así como los archivos adicionales en la carpeta donde se crea la imagen. Puede crear imágenes mediante el comando de compilación de docker de Docker.

-   **Repositorio (también conocido como repositorio)** una colección de imágenes de Docker relacionadas con la etiqueta con una etiqueta que indica la versión de la imagen. Algunos repositorios contienen varias variantes de una imagen específica, como una imagen que contiene SDK (más compleja), una imagen que contiene solo los runtimes (más claros), y así sucesivamente. Las variantes se pueden marcar con etiquetas. Un solo repositorio puede contener las variantes de la plataforma, como una imagen de Linux y una imagen de Windows.

-   **Registro** un servicio que proporciona acceso a los repositorios. El registro predeterminado para las imágenes más públicas es [Docker Hub](https://hub.docker.com/) (propiedad de Docker como una organización). Normalmente, un registro contiene repositorios de varios equipos. Las empresas suelen tengan registros privados para almacenar y administrar imágenes que hayan creado. *Registro de contenedor Azure* es otro ejemplo.

-   **Centro de docker** un registro público para cargar imágenes y trabajar con ellos. Docker Hub proporciona Docker imagen hospedaje, registros públicos o privados, los desencadenadores de compilación y enlaces web e integración con GitHub y Bitbucket.

-   **Registro de contenedor Azure** un recurso público para trabajar con imágenes de Docker y sus componentes en Azure. Esto proporciona un registro que está cerca de las implementaciones en Azure y que proporciona control sobre el acceso, lo que permite utilizar los grupos de Active Directory de Azure y los permisos.

-   **Registro de confianza de docker (DTR)** servicio de registro de Docker A (a través de Docker) que se puede instalar en local para que se encuentra en el centro de datos y la red de la organización. Es conveniente para imágenes privadas que deben administrarse dentro de la empresa. Registro de confianza de docker se incluye como parte de los productos de centros de datos de Docker. Para obtener más información, vaya a [https://docs.docker.com/docker-trusted-registry/overview/](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** herramientas de desarrollo para Windows y Mac OS para compilar, ejecutar y probar contenedores localmente. CE de docker para Windows proporciona entornos de desarrollo para contenedores de Windows y Linux. El host de Linux Docker en Windows se basa en un [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) máquina virtual. El host para los contenedores de Windows se basa directamente en Windows. Docker CE para Mac se basa en el marco de trabajo de hipervisor de Apple y la [xhyve hipervisor](https://github.com/mist64/xhyve), lo que proporciona una máquina virtual del host de Linux Docker en Mac OS X. Docker CE para Windows y para Mac reemplaza el cuadro de herramientas de Docker, que se basa en Oracle VirtualBox.

-   **Docker Enterprise Edition (EE)** una versión de escala empresarial de herramientas de Docker para el desarrollo de Linux y Windows.

-   **Crear** una herramienta de línea de comandos y YAML formato con metadatos para definir y ejecutar aplicaciones multicontainer de archivo. Definir una sola aplicación en función de varias imágenes con uno o más archivos de .yml que pueden invalidar valores dependiendo del entorno. Después de crear las definiciones, puede implementar toda la aplicación multicontainer mediante un único comando (docker-crear una) que crea un contenedor por imagen en el host de Docker.

-   **Clúster** una colección de hosts de Docker que se exponen como si fueran un único host virtual de Docker para que la aplicación se puede adaptar a varias instancias de los servicios se reparten entre varios hosts del clúster. Puede crear clústeres de Docker mediante Docker Swarm, Mesosphere DC/OS, Kubernetes y Azure Service Fabric. (Si usa Docker Swarm para administrar un clúster, se suele hacer referencia al clúster como un *swarm* en lugar de un clúster.)

-   **Orchestrator** una herramienta que simplifica la administración de clústeres y hosts de Docker. Orchestrators puede administrar sus imágenes, los contenedores y los hosts a través de una CLI o una interfaz gráfica de usuario. Puede administrar las redes de contenedor, configuraciones, equilibrio de carga, la detección de servicios, alta disponibilidad, configuración del host de Docker y mucho más. Organizador es responsable de la ejecución, la distribución, ajuste de escala y la recuperación de las cargas de trabajo a través de una colección de nodos. Normalmente, los productos de orchestrator son el mismo que proporcionan la infraestructura de clúster, como Mesosphere DC/OS, Kubernetes, Docker Swarm y Azure Service Fabric.


>[!div class="step-by-step"]
[Anterior] (what-es-docker.md) [siguiente] (docker-contenedores-imágenes-y-registries.md)
