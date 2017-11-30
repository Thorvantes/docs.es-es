---
title: Estado y los datos en aplicaciones de Docker
description: Arquitectura de Microservicios de .NET para aplicaciones .NET en contenedores | Estado y los datos en aplicaciones de Docker
keywords: Docker, Microservicios, ASP.NET, contenedor, SQL, CosmosDB, Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 36d0fb9f27ef56b36c380e2fc972c79cff77003e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2017
---
# <a name="state-and-data-in-docker-applications"></a><span data-ttu-id="019b7-104">Estado y los datos en aplicaciones de Docker</span><span class="sxs-lookup"><span data-stu-id="019b7-104">State and data in Docker applications</span></span>

<span data-ttu-id="019b7-105">En la mayoría de los casos, se puede considerar un contenedor como una instancia de un proceso.</span><span class="sxs-lookup"><span data-stu-id="019b7-105">In most cases, you can think of a container as an instance of a process.</span></span> <span data-ttu-id="019b7-106">Un proceso no mantiene el estado persistente.</span><span class="sxs-lookup"><span data-stu-id="019b7-106">A process does not maintain persistent state.</span></span> <span data-ttu-id="019b7-107">Aunque puede escribir un contenedor para su almacenamiento local, suponiendo que una instancia será indefinidamente alrededor sería como suponiendo que una sola ubicación en memoria será duradera.</span><span class="sxs-lookup"><span data-stu-id="019b7-107">While a container can write to its local storage, assuming that an instance will be around indefinitely would be like assuming that a single location in memory will be durable.</span></span> <span data-ttu-id="019b7-108">Imágenes del contenedor, como procesos, deben suponer tener varias instancias o que finalmente se terminará; Si administra que se encuentra con un orquestador del contenedor, se debe suponer que se podría obtener mover desde un nodo o la máquina virtual a otro.</span><span class="sxs-lookup"><span data-stu-id="019b7-108">Container images, like processes, should be assumed to have multiple instances or that they will eventually be killed; if they’re managed with a container orchestrator, it should be assumed that they might get moved from one node or VM to another.</span></span>

<span data-ttu-id="019b7-109">Docker ofrece una característica denominada la *superposición de sistema de archivos*.</span><span class="sxs-lookup"><span data-stu-id="019b7-109">Docker provides a feature named the *overlay file system*.</span></span> <span data-ttu-id="019b7-110">Esto implementa una tarea de copia en escritura que almacena información actualizada en el sistema de archivos de la raíz del contenedor.</span><span class="sxs-lookup"><span data-stu-id="019b7-110">This implements a copy-on-write task that stores updated information to the root file system of the container.</span></span> <span data-ttu-id="019b7-111">Esta información es además la imagen original en el que se basa el contenedor.</span><span class="sxs-lookup"><span data-stu-id="019b7-111">That information is in addition to the original image on which the container is based.</span></span> <span data-ttu-id="019b7-112">Si se elimina el contenedor del sistema, estos cambios se perderán.</span><span class="sxs-lookup"><span data-stu-id="019b7-112">If the container is deleted from the system, those changes are lost.</span></span> <span data-ttu-id="019b7-113">Por lo tanto, si es posible guardar el estado de un contenedor dentro de su almacenamiento local, diseñar un sistema de resolver este problema entrarían en conflicto con la idea de diseño de contenedor, cuyo valor predeterminado es sin estado.</span><span class="sxs-lookup"><span data-stu-id="019b7-113">Therefore, while it is possible to save the state of a container within its local storage, designing a system around this would conflict with the premise of container design, which by default is stateless.</span></span>

<span data-ttu-id="019b7-114">Las soluciones siguientes se usan para administrar datos persistentes en aplicaciones de Docker:</span><span class="sxs-lookup"><span data-stu-id="019b7-114">The following solutions are used to manage persistent data in Docker applications:</span></span>

-   <span data-ttu-id="019b7-115">[Volúmenes de datos](https://docs.docker.com/engine/tutorials/dockervolumes/) que montar en el host.</span><span class="sxs-lookup"><span data-stu-id="019b7-115">[Data volumes](https://docs.docker.com/engine/tutorials/dockervolumes/) that mount to the host.</span></span>

-   <span data-ttu-id="019b7-116">[Contenedores de volúmenes de datos](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) que proporcionan almacenamiento compartido entre todos los contenedores mediante un contenedor externo.</span><span class="sxs-lookup"><span data-stu-id="019b7-116">[Data volume containers](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) that provide shared storage across containers using an external container.</span></span>

-   <span data-ttu-id="019b7-117">[Complementos de volumen](https://docs.docker.com/engine/tutorials/dockervolumes/) que montar los volúmenes a los servicios remotos, proporcionar persistencia a largo plazo.</span><span class="sxs-lookup"><span data-stu-id="019b7-117">[Volume plugins](https://docs.docker.com/engine/tutorials/dockervolumes/) that mount volumes to remote services, providing long-term persistence.</span></span>

-   <span data-ttu-id="019b7-118">[Almacenamiento de Azure](https://docs.microsoft.com/azure/storage/), que proporciona almacenamiento geográfica distribuible, proporcionar una buena solución de persistencia a largo plazo para los contenedores.</span><span class="sxs-lookup"><span data-stu-id="019b7-118">[Azure Storage](https://docs.microsoft.com/azure/storage/), which provides geo-distributable storage, providing a good long-term persistence solution for containers.</span></span>

-   <span data-ttu-id="019b7-119">Bases de datos relacionales remotos como [base de datos de SQL Azure](https://azure.microsoft.com/services/sql-database/) o bases de datos NoSQL, como [base de datos de Azure Cosmos](https://docs.microsoft.com/azure/cosmos-db/introduction), o almacenar en caché servicios como [Redis](https://redis.io/).</span><span class="sxs-lookup"><span data-stu-id="019b7-119">Remote relational databases like [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) or NoSQL databases like [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), or cache services like [Redis](https://redis.io/).</span></span>

<span data-ttu-id="019b7-120">A continuación proporciona más información sobre estas opciones.</span><span class="sxs-lookup"><span data-stu-id="019b7-120">The following provides more detail about these options.</span></span>

<span data-ttu-id="019b7-121">**Volúmenes de datos** directorios asignado desde el sistema operativo del host en los directorios en contenedores.</span><span class="sxs-lookup"><span data-stu-id="019b7-121">**Data volumes** are directories mapped from the host OS to directories in containers.</span></span> <span data-ttu-id="019b7-122">Cuando el código en el contenedor tiene acceso al directorio, que acceso es realmente un directorio en el sistema operativo del host.</span><span class="sxs-lookup"><span data-stu-id="019b7-122">When code in the container has access to the directory, that access is actually to a directory on the host OS.</span></span> <span data-ttu-id="019b7-123">Este directorio no está asociado a la duración del contenedor y el directorio puede tener acceso desde el código que se ejecuta directamente en el sistema operativo del host o por otro contenedor que asigna el mismo directorio de host a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="019b7-123">This directory is not tied to the lifetime of the container itself, and the directory can be accessed from code running directly on the host OS or by another container that maps the same host directory to itself.</span></span> <span data-ttu-id="019b7-124">Por lo tanto, los volúmenes de datos están diseñados para conservar los datos independientemente de la vida del contenedor.</span><span class="sxs-lookup"><span data-stu-id="019b7-124">Thus, data volumes are designed to persist data independently of the life of the container.</span></span> <span data-ttu-id="019b7-125">Si elimina un contenedor o una imagen desde el host Docker, los datos se conserva en el volumen de datos no se elimina.</span><span class="sxs-lookup"><span data-stu-id="019b7-125">If you delete a container or an image from the Docker host, the data persisted in the data volume is not deleted.</span></span> <span data-ttu-id="019b7-126">Pueden tener acceso a los datos en un volumen desde el sistema operativo de host también.</span><span class="sxs-lookup"><span data-stu-id="019b7-126">The data in a volume can be accessed from the host OS as well.</span></span>

<span data-ttu-id="019b7-127">**Contenedores de volúmenes de datos** son una evolución de los volúmenes de datos normal.</span><span class="sxs-lookup"><span data-stu-id="019b7-127">**Data volume containers** are an evolution of regular data volumes.</span></span> <span data-ttu-id="019b7-128">Un contenedor de volúmenes de datos es un contenedor simple que tiene uno o más volúmenes de datos dentro de él.</span><span class="sxs-lookup"><span data-stu-id="019b7-128">A data volume container is a simple container that has one or more data volumes within it.</span></span> <span data-ttu-id="019b7-129">El contenedor de volúmenes de datos proporciona acceso a los contenedores desde un punto de montaje central.</span><span class="sxs-lookup"><span data-stu-id="019b7-129">The data volume container provides access to containers from a central mount point.</span></span> <span data-ttu-id="019b7-130">Este método de acceso a datos es conveniente porque resume la ubicación de los datos originales.</span><span class="sxs-lookup"><span data-stu-id="019b7-130">This method of data access is convenient because it abstracts the location of the original data.</span></span> <span data-ttu-id="019b7-131">Aparte de eso, su comportamiento es similar de un volumen de datos normal, por lo que los datos se guardan en este contenedor dedicado independientemente del ciclo de vida de los contenedores de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="019b7-131">Other than that, its behavior is similar to that of a regular data volume, so data is persisted in this dedicated container independently of the lifecycle of the application’s containers.</span></span>

<span data-ttu-id="019b7-132">Tal como se muestra en la figura 4-5, volúmenes de Docker normales pueden almacenarse fuera de los propios contenedores, pero dentro de los límites físicos del servidor de host o máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="019b7-132">As shown in Figure 4-5, regular Docker volumes can be stored outside of the containers themselves but within the physical boundaries of the host server or VM.</span></span> <span data-ttu-id="019b7-133">Sin embargo, contenedores de Docker no pueden tener acceso a un volumen de servidor de un host o máquina virtual a otro.</span><span class="sxs-lookup"><span data-stu-id="019b7-133">However, Docker containers cannot access a volume from one host server or VM to another.</span></span> <span data-ttu-id="019b7-134">En otras palabras, con estos volúmenes, no es posible administrar los datos que se comparten entre contenedores que se ejecutan en diferentes hosts de Docker</span><span class="sxs-lookup"><span data-stu-id="019b7-134">In other words, with these volumes, it is not possible to manage data shared between containers that run on different Docker hosts</span></span>

![](./media/image5.png)

<span data-ttu-id="019b7-135">**Figura 4-5**.</span><span class="sxs-lookup"><span data-stu-id="019b7-135">**Figure 4-5**.</span></span> <span data-ttu-id="019b7-136">Volúmenes de datos y orígenes de datos externos para aplicaciones basadas en el contenedor</span><span class="sxs-lookup"><span data-stu-id="019b7-136">Data volumes and external data sources for container-based applications</span></span>

<span data-ttu-id="019b7-137">Además, cuando un orchestrator administra contenedores de Docker, contenedores podrían "mover" entre los hosts, dependiendo de las optimizaciones realizadas por el clúster.</span><span class="sxs-lookup"><span data-stu-id="019b7-137">In addition, when Docker containers are managed by an orchestrator, containers might “move” between hosts, depending on the optimizations performed by the cluster.</span></span> <span data-ttu-id="019b7-138">Por lo tanto, no se recomienda utilizar volúmenes de datos para los datos empresariales.</span><span class="sxs-lookup"><span data-stu-id="019b7-138">Therefore, it is not recommended that you use data volumes for business data.</span></span> <span data-ttu-id="019b7-139">Pero son un buen mecanismo para trabajar con archivos de seguimiento, archivos temporales, o similar no afectará a coherencia de los datos empresariales.</span><span class="sxs-lookup"><span data-stu-id="019b7-139">But they are a good mechanism to work with trace files, temporal files, or similar that will not impact business data consistency.</span></span>

<span data-ttu-id="019b7-140">**Complementos de volumen** como [Flocker](https://clusterhq.com/flocker/) proporcionan acceso a datos a través de todos los hosts en un clúster.</span><span class="sxs-lookup"><span data-stu-id="019b7-140">**Volume plugins** like [Flocker](https://clusterhq.com/flocker/) provide data access across all hosts in a cluster.</span></span> <span data-ttu-id="019b7-141">Aunque no todos los complementos de volumen se crean por igual, volumen complementos normalmente proporcionar externalizado almacenamiento confiable persistente de contenedores inmutable.</span><span class="sxs-lookup"><span data-stu-id="019b7-141">While not all volume plugins are created equally, volume plugins typically provide externalized persistent reliable storage from immutable containers.</span></span>

<span data-ttu-id="019b7-142">**Orígenes de datos remotos y caché** herramientas como base de datos de SQL Azure, base de datos de Azure Cosmos o una caché remota como Redis pueden utilizarse en contenedores aplicaciones del mismo modo que se utilizan cuando se desarrolla sin contenedores.</span><span class="sxs-lookup"><span data-stu-id="019b7-142">**Remote data sources and cache** tools like Azure SQL Database, Azure Cosmos DB, or a remote cache like Redis can be used in containerized applications the same way they are used when developing without containers.</span></span> <span data-ttu-id="019b7-143">Se trata de una manera comprobada para almacenar datos de aplicaciones de negocios.</span><span class="sxs-lookup"><span data-stu-id="019b7-143">This is a proven way to store business application data.</span></span>

<span data-ttu-id="019b7-144">**Almacenamiento de Azure.**</span><span class="sxs-lookup"><span data-stu-id="019b7-144">**Azure Storage.**</span></span> <span data-ttu-id="019b7-145">Datos económicos normalmente deberá colocarse en recursos externos o las bases de datos, como el almacenamiento de Azure.</span><span class="sxs-lookup"><span data-stu-id="019b7-145">Business data usually will need to be placed in external resources or databases, like Azure Storage.</span></span> <span data-ttu-id="019b7-146">Almacenamiento de Azure, en concreto, proporciona los siguientes servicios en la nube:</span><span class="sxs-lookup"><span data-stu-id="019b7-146">Azure Storage, in concrete, provides the following services in the cloud:</span></span>

-   <span data-ttu-id="019b7-147">Almacenamiento de blobs almacena datos de objetos no estructurados.</span><span class="sxs-lookup"><span data-stu-id="019b7-147">Blob storage stores unstructured object data.</span></span> <span data-ttu-id="019b7-148">Un blob puede ser cualquier tipo de datos de texto o binarios, como documentos o medios de archivos (imágenes, audio y vídeo).</span><span class="sxs-lookup"><span data-stu-id="019b7-148">A blob can be any type of text or binary data, such as document or media files (images, audio, and video files).</span></span> <span data-ttu-id="019b7-149">Almacenamiento de blobs también se conoce como almacenamiento de objetos.</span><span class="sxs-lookup"><span data-stu-id="019b7-149">Blob storage is also referred to as Object storage.</span></span>

-   <span data-ttu-id="019b7-150">Almacenamiento de archivos ofrece almacenamiento compartido para aplicaciones heredadas mediante el protocolo SMB estándar.</span><span class="sxs-lookup"><span data-stu-id="019b7-150">File storage offers shared storage for legacy applications using standard SMB protocol.</span></span> <span data-ttu-id="019b7-151">Máquinas virtuales de Azure y servicios en la nube pueden compartir datos de archivos a través de los componentes de la aplicación a través de recursos compartidos montados.</span><span class="sxs-lookup"><span data-stu-id="019b7-151">Azure virtual machines and cloud services can share file data across application components via mounted shares.</span></span> <span data-ttu-id="019b7-152">Aplicaciones locales pueden tener acceso a datos de archivos en un recurso compartido a través de la API de REST de servicio de archivo.</span><span class="sxs-lookup"><span data-stu-id="019b7-152">On-premises applications can access file data in a share via the File service REST API.</span></span>

-   <span data-ttu-id="019b7-153">Almacenamiento de tabla almacena conjuntos de datos estructurados.</span><span class="sxs-lookup"><span data-stu-id="019b7-153">Table storage stores structured datasets.</span></span> <span data-ttu-id="019b7-154">Almacenamiento de tabla es un almacén de datos del atributo de clave NoSQL, lo que permite el desarrollo rápido y un acceso rápido a grandes cantidades de datos.</span><span class="sxs-lookup"><span data-stu-id="019b7-154">Table storage is a NoSQL key-attribute data store, which allows rapid development and fast access to large quantities of data.</span></span>

<span data-ttu-id="019b7-155">**Bases de datos relacionales y bases de datos NoSQL.**</span><span class="sxs-lookup"><span data-stu-id="019b7-155">**Relational databases and NoSQL databases.**</span></span> <span data-ttu-id="019b7-156">Existen muchas opciones para bases de datos externas, desde bases de datos relacionales como bases de datos NoSQL, PostgreSQL, Oracle o SQL Server como base de datos de Azure Cosmos, MongoDB, etcetera. Estas bases de datos no se van a explicarse como parte de esta guía puesto que están en un asunto completamente diferente.</span><span class="sxs-lookup"><span data-stu-id="019b7-156">There are many choices for external databases, from relational databases like SQL Server, PostgreSQL, Oracle, or NoSQL databases like Azure Cosmos DB, MongoDB, etc. These databases are not going to be explained as part of this guide since they are in a completely different subject.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="019b7-157">[Anterior] (incluya-monolítico-applications.md) [siguiente] (service-oriented-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="019b7-157">[Previous] (containerize-monolithic-applications.md) [Next] (service-oriented-architecture.md)</span></span>