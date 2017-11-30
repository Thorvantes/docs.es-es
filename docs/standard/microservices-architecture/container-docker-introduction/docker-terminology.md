---
title: "Terminología de docker"
description: "Arquitectura de Microservicios de .NET para aplicaciones .NET en contenedores | Terminología de docker"
keywords: Docker, microservicios, ASP.NET, contenedor
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 885b1fbd3369dec54ebde21a5378630c764f852d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="docker-terminology"></a><span data-ttu-id="57996-104">Terminología de docker</span><span class="sxs-lookup"><span data-stu-id="57996-104">Docker terminology</span></span>

<span data-ttu-id="57996-105">Esta sección enumera los términos y definiciones que debe conocer antes de obtener un poco más en Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-105">This section lists terms and definitions you should be familiar with before getting deeper into Docker.</span></span> <span data-ttu-id="57996-106">Para obtener más definiciones, vea el amplio [glosario](https://docs.docker.com/v1.11/engine/reference/glossary/) proporcionada por Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-106">For further definitions, see the extensive [glossary](https://docs.docker.com/v1.11/engine/reference/glossary/) provided by Docker .</span></span>

<span data-ttu-id="57996-107">**Imagen de contenedor**: un paquete con todas las dependencias y la información necesaria para crear un contenedor.</span><span class="sxs-lookup"><span data-stu-id="57996-107">**Container image**: A package with all the dependencies and information needed to create a container.</span></span> <span data-ttu-id="57996-108">Una imagen incluye todas las dependencias (por ejemplo, marcos) además de la implementación y ejecución de configuración que se usará en tiempo de ejecución de un contenedor.</span><span class="sxs-lookup"><span data-stu-id="57996-108">An image includes all the dependencies (such as frameworks) plus deployment and execution configuration to be used by a container runtime.</span></span> <span data-ttu-id="57996-109">Normalmente, una imagen se deriva de varias imágenes de base que se apilan unos encima de otros para formar el sistema de archivos del contenedor de capas.</span><span class="sxs-lookup"><span data-stu-id="57996-109">Usually, an image derives from multiple base images that are layers stacked on top of each other to form the container’s filesystem.</span></span> <span data-ttu-id="57996-110">Una imagen es inmutable, una vez que se ha creado.</span><span class="sxs-lookup"><span data-stu-id="57996-110">An image is immutable once it has been created.</span></span>

<span data-ttu-id="57996-111">**Contenedor**: una instancia de una imagen de Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-111">**Container**: An instance of a Docker image.</span></span> <span data-ttu-id="57996-112">Un contenedor representa la ejecución de una sola aplicación, proceso o servicio.</span><span class="sxs-lookup"><span data-stu-id="57996-112">A container represents the execution of a single application, process, or service.</span></span> <span data-ttu-id="57996-113">Está formada por el contenido de una imagen de Docker, un entorno de ejecución y un conjunto estándar de instrucciones.</span><span class="sxs-lookup"><span data-stu-id="57996-113">It consists of the contents of a Docker image, an execution environment, and a standard set of instructions.</span></span> <span data-ttu-id="57996-114">Al escalar un servicio, cree varias instancias de un contenedor de la misma imagen.</span><span class="sxs-lookup"><span data-stu-id="57996-114">When scaling a service, you create multiple instances of a container from the same image.</span></span> <span data-ttu-id="57996-115">O bien, un proceso por lotes puede crear varios contenedores de la misma imagen, pasar parámetros diferentes para cada instancia.</span><span class="sxs-lookup"><span data-stu-id="57996-115">Or a batch job can create multiple containers from the same image, passing different parameters to each instance.</span></span>

<span data-ttu-id="57996-116">**Etiqueta**: una marca o una etiqueta que se puede aplicar a las imágenes para que se pueden identificar los diferentes imágenes o las versiones de la misma imagen (según el número de versión o el entorno de destino).</span><span class="sxs-lookup"><span data-stu-id="57996-116">**Tag**: A mark or label you can apply to images so that different images or versions of the same image (depending on the version number or the target environment) can be identified.</span></span>

<span data-ttu-id="57996-117">**Dockerfile**: un archivo de texto que contiene instrucciones sobre cómo crear una imagen de Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-117">**Dockerfile**: A text file that contains instructions for how to build a Docker image.</span></span>

<span data-ttu-id="57996-118">**Compilación**: la acción de creación de una imagen de contenedor en función de la información y el contexto proporcionado por su Dockerfile, además de archivos adicionales en la carpeta donde se crea la imagen.</span><span class="sxs-lookup"><span data-stu-id="57996-118">**Build**: The action of building a container image based on the information and context provided by its Dockerfile, plus additional files in the folder where the image is built.</span></span> <span data-ttu-id="57996-119">Puede crear imágenes con el comando de compilación de docker de Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-119">You can build images with the Docker docker build command.</span></span>

<span data-ttu-id="57996-120">**Repositorio (repositorio)**: una colección de imágenes de Docker relacionadas, etiquetada con una etiqueta que indica la versión de la imagen.</span><span class="sxs-lookup"><span data-stu-id="57996-120">**Repository (repo)**: A collection of related Docker images, labeled with a tag that indicates the image version.</span></span> <span data-ttu-id="57996-121">Algunos repositorios contienen varias variantes de una imagen específica, como una imagen que contiene SDK (más compleja), una imagen que contiene solo tiempos de ejecución (más claro), etcetera. Las variantes se pueden marcar con etiquetas.</span><span class="sxs-lookup"><span data-stu-id="57996-121">Some repos contain multiple variants of a specific image, such as an image containing SDKs (heavier), an image containing only runtimes (lighter), etc. Those variants can be marked with tags.</span></span> <span data-ttu-id="57996-122">Un repositorio único puede contener las variantes de la plataforma, como una imagen de Linux y una imagen de Windows.</span><span class="sxs-lookup"><span data-stu-id="57996-122">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span>

<span data-ttu-id="57996-123">**Registro**: un servicio que proporciona acceso a los repositorios.</span><span class="sxs-lookup"><span data-stu-id="57996-123">**Registry**: A service that provides access to repositories.</span></span> <span data-ttu-id="57996-124">El registro predeterminado para las imágenes más públicas es [Docker Hub](https://hub.docker.com/) (propiedad de Docker como una organización).</span><span class="sxs-lookup"><span data-stu-id="57996-124">The default registry for most public images is [Docker Hub](https://hub.docker.com/) (owned by Docker as an organization).</span></span> <span data-ttu-id="57996-125">Normalmente, un registro contiene repositorios de varios equipos.</span><span class="sxs-lookup"><span data-stu-id="57996-125">A registry usually contains repositories from multiple teams.</span></span> <span data-ttu-id="57996-126">Las empresas suelen tengan registros privados para almacenar y administrar imágenes que se hayan creado.</span><span class="sxs-lookup"><span data-stu-id="57996-126">Companies often have private registries to store and manage images they’ve created.</span></span> <span data-ttu-id="57996-127">Registro de contenedor de Azure es otro ejemplo.</span><span class="sxs-lookup"><span data-stu-id="57996-127">Azure Container Registry is another example.</span></span>

<span data-ttu-id="57996-128">**Centro de docker**: un registro público para cargar imágenes y trabajar con ellos.</span><span class="sxs-lookup"><span data-stu-id="57996-128">**Docker Hub**: A public registry to upload images and work with them.</span></span> <span data-ttu-id="57996-129">Docker Hub proporciona Docker imagen hospedaje, registros públicos o privados, los desencadenadores de compilación y enlaces web e integración con GitHub y Bitbucket.</span><span class="sxs-lookup"><span data-stu-id="57996-129">Docker Hub provides Docker image hosting, public or private registries, build triggers and web hooks, and integration with GitHub and Bitbucket.</span></span>

<span data-ttu-id="57996-130">**Registro de contenedor Azure**: un recurso público para trabajar con imágenes de Docker y sus componentes en Azure.</span><span class="sxs-lookup"><span data-stu-id="57996-130">**Azure Container Registry**: A public resource for working with Docker images and its components in Azure.</span></span> <span data-ttu-id="57996-131">Esto proporciona un registro que está cerca de las implementaciones en Azure y que proporciona control sobre el acceso, lo que permite utilizar los grupos de Active Directory de Azure y los permisos.</span><span class="sxs-lookup"><span data-stu-id="57996-131">This provides a registry that is close to your deployments in Azure and that gives you control over access, making it possible to use your Azure Active Directory groups and permissions.</span></span>

<span data-ttu-id="57996-132">**Registro de confianza de docker (DTR)**: servicio de registro de Docker A (a través de Docker) que puede ser instalado de forma local, por lo que se encuentra en el centro de datos y la red de la organización.</span><span class="sxs-lookup"><span data-stu-id="57996-132">**Docker Trusted Registry (DTR)**: A Docker registry service (from Docker) that can be installed on-premises so it lives within the organization’s datacenter and network.</span></span> <span data-ttu-id="57996-133">Es conveniente para imágenes privadas que deben administrarse dentro de la empresa.</span><span class="sxs-lookup"><span data-stu-id="57996-133">It is convenient for private images that should be managed within the enterprise.</span></span> <span data-ttu-id="57996-134">Registro de confianza de docker se incluye como parte de los productos de centros de datos de Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-134">Docker Trusted Registry is included as part of the Docker Datacenter product.</span></span> <span data-ttu-id="57996-135">Para obtener más información, consulte [del registro de confianza de Docker (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).</span><span class="sxs-lookup"><span data-stu-id="57996-135">For more information, see [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).</span></span>

<span data-ttu-id="57996-136">**Docker Community Edition (CE)**: herramientas de desarrollo para Windows y Mac OS para compilar, ejecutar y probar contenedores localmente.</span><span class="sxs-lookup"><span data-stu-id="57996-136">**Docker Community Edition (CE)**: Development tools for Windows and macOS for building, running, and testing containers locally.</span></span> <span data-ttu-id="57996-137">CE de docker para Windows proporciona entornos de desarrollo para contenedores de Windows y Linux.</span><span class="sxs-lookup"><span data-stu-id="57996-137">Docker CE for Windows provides development environments for both Linux and Windows Containers.</span></span> <span data-ttu-id="57996-138">El host de Linux Docker en Windows se basa en un [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="57996-138">The Linux Docker host on Windows is based on a [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) virtual machine.</span></span> <span data-ttu-id="57996-139">El host para los contenedores de Windows se basa directamente en Windows.</span><span class="sxs-lookup"><span data-stu-id="57996-139">The host for Windows Containers is directly based on Windows.</span></span> <span data-ttu-id="57996-140">Docker CE para Mac se basa en el marco de trabajo de hipervisor de Apple y la [xhyve hipervisor](https://github.com/mist64/xhyve), lo que proporciona una máquina virtual de host de Linux Docker en Mac OS X. Docker CE para Windows y para Mac reemplaza el cuadro de herramientas de Docker, que se basa en Oracle VirtualBox.</span><span class="sxs-lookup"><span data-stu-id="57996-140">Docker CE for Mac is based on the Apple Hypervisor framework and the [xhyve hypervisor](https://github.com/mist64/xhyve), which provides a Linux Docker host virtual machine on Mac OS X. Docker CE for Windows and for Mac replaces Docker Toolbox, which was based on Oracle VirtualBox.</span></span>

<span data-ttu-id="57996-141">**Docker Enterprise Edition (EE)**: una versión de escala empresarial de herramientas de Docker para el desarrollo de Linux y Windows.</span><span class="sxs-lookup"><span data-stu-id="57996-141">**Docker Enterprise Edition (EE)**: An enterprise-scale version of Docker tools for Linux and Windows development.</span></span>

<span data-ttu-id="57996-142">**Crear**: una herramienta de línea de comandos y YAML de formato con metadatos para definir y ejecutar aplicaciones de contenedor de varios archivos.</span><span class="sxs-lookup"><span data-stu-id="57996-142">**Compose**: A command-line tool and YAML file format with metadata for defining and running multi-container applications.</span></span> <span data-ttu-id="57996-143">Definir una sola aplicación en función de varias imágenes con uno o más archivos de .yml que pueden invalidar valores dependiendo del entorno.</span><span class="sxs-lookup"><span data-stu-id="57996-143">You define a single application based on multiple images with one or more .yml files that can override values depending on the environment.</span></span> <span data-ttu-id="57996-144">Después de crear las definiciones, puede implementar la aplicación de todo el contenedor de varios con un solo comando (docker-crear una) que crea un contenedor por imagen en el host de Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-144">After you have created the definitions, you can deploy the whole multi-container application with a single command (docker-compose up) that creates a container per image on the Docker host.</span></span>

<span data-ttu-id="57996-145">**Clúster**: una colección de hosts de Docker que se exponen como si fuera un solo host Docker virtual, para que la aplicación se puede adaptar a varias instancias de los servicios se reparten entre varios hosts del clúster.</span><span class="sxs-lookup"><span data-stu-id="57996-145">**Cluster**: A collection of Docker hosts exposed as if it were a single virtual Docker host, so that the application can scale to multiple instances of the services spread across multiple hosts within the cluster.</span></span> <span data-ttu-id="57996-146">Con Docker Swarm, Mesosphere DC/OS, Kubernetes y Azure Service Fabric, se pueden crear clústeres de docker.</span><span class="sxs-lookup"><span data-stu-id="57996-146">Docker clusters can be created with Docker Swarm, Mesosphere DC/OS, Kubernetes, and Azure Service Fabric.</span></span> <span data-ttu-id="57996-147">(Si usa Docker Swarm para administrar un clúster, se suele hacer referencia al clúster como un *swarm* en lugar de un clúster.)</span><span class="sxs-lookup"><span data-stu-id="57996-147">(If you use Docker Swarm for managing a cluster, you typically refer to the cluster as a *swarm* instead of a cluster.)</span></span>

<span data-ttu-id="57996-148">**Orchestrator**: una herramienta que simplifica la administración de clústeres y hosts de Docker.</span><span class="sxs-lookup"><span data-stu-id="57996-148">**Orchestrator**: A tool that simplifies management of clusters and Docker hosts.</span></span> <span data-ttu-id="57996-149">Orchestrators le permiten administrar sus imágenes, los contenedores y los hosts a través de una interfaz de línea de comandos (CLI) o una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="57996-149">Orchestrators enable you to manage their images, containers, and hosts through a command line interface (CLI) or a graphical UI.</span></span> <span data-ttu-id="57996-150">Puede administrar las redes de contenedor, configuraciones, equilibrio de carga, la detección de servicios, alta disponibilidad, configuración del host de Docker y mucho más.</span><span class="sxs-lookup"><span data-stu-id="57996-150">You can manage container networking, configurations, load balancing, service discovery, high availability, Docker host configuration, and more.</span></span> <span data-ttu-id="57996-151">Organizador es responsable de la ejecución, la distribución, ajuste de escala y la recuperación de las cargas de trabajo a través de una colección de nodos.</span><span class="sxs-lookup"><span data-stu-id="57996-151">An orchestrator is responsible for running, distributing, scaling, and healing workloads across a collection of nodes.</span></span> <span data-ttu-id="57996-152">Normalmente, los productos de orchestrator son el mismo que proporcionan la infraestructura de clúster, como Mesosphere DC/OS, Kubernetes, Docker Swarm y Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="57996-152">Typically, orchestrator products are the same products that provide cluster infrastructure, like Mesosphere DC/OS, Kubernetes, Docker Swarm, and Azure Service Fabric.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="57996-153">[Anterior] (docker-defined.md) [siguiente] (docker contenedores-imágenes registries.md)</span><span class="sxs-lookup"><span data-stu-id="57996-153">[Previous] (docker-defined.md) [Next] (docker-containers-images-registries.md)</span></span>