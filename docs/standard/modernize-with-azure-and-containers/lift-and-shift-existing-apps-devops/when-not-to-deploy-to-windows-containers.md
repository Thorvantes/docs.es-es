---
title: "Cuándo no se debe implementar en los contenedores de Windows"
description: "Arquitectura de Microservicios de .NET para aplicaciones .NET en contenedores | Cuándo no se debe implementar en los contenedores de Windows"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 538cb518cd169f42b3e8b7324ca108a1d366137a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="747bb-103">Cuándo no se debe implementar en los contenedores de Windows</span><span class="sxs-lookup"><span data-stu-id="747bb-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="747bb-104">Algunas tecnologías de Windows no son compatibles con los contenedores de Windows.</span><span class="sxs-lookup"><span data-stu-id="747bb-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="747bb-105">En esos casos, deberá migrar a las máquinas virtuales de estándares, normalmente con solo Windows e IIS.</span><span class="sxs-lookup"><span data-stu-id="747bb-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="747bb-106">No se admite en los contenedores de Windows, a partir de mediados de 2017 los casos:</span><span class="sxs-lookup"><span data-stu-id="747bb-106">Cases not supported in Windows Containers, as of mid-2017:</span></span>

-   <span data-ttu-id="747bb-107">Microsoft Message Queuing (MSMQ) actualmente no se admite en los contenedores de Windows.</span><span class="sxs-lookup"><span data-stu-id="747bb-107">Microsoft Message Queuing (MSMQ) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="747bb-108">Foro de solicitud de UserVoice</span><span class="sxs-lookup"><span data-stu-id="747bb-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="747bb-109">Foro de discusión</span><span class="sxs-lookup"><span data-stu-id="747bb-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="747bb-110">Coordinador de transacciones distribuidas de Microsoft (MSDTC) actualmente no se admite en los contenedores de Windows</span><span class="sxs-lookup"><span data-stu-id="747bb-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers</span></span>

    -   [<span data-ttu-id="747bb-111">Problema de GitHub</span><span class="sxs-lookup"><span data-stu-id="747bb-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="747bb-112">Microsoft Office no admite actualmente los contenedores</span><span class="sxs-lookup"><span data-stu-id="747bb-112">Microsoft Office currently does not support containers</span></span>

    -   [<span data-ttu-id="747bb-113">Foro de solicitud de UserVoice</span><span class="sxs-lookup"><span data-stu-id="747bb-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

<span data-ttu-id="747bb-114">Para las solicitudes de la Comunidad y otros escenarios no admitidos, vea el foro de UserVoice para contenedores de Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="747bb-114">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="747bb-115">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="747bb-115">Additional resources</span></span>

-   <span data-ttu-id="747bb-116">**Máquinas virtuales y contenedores en Azure**</span><span class="sxs-lookup"><span data-stu-id="747bb-116">**Virtual machines and containers in Azure**</span></span>

    [<span data-ttu-id="747bb-117">https://docs.Microsoft.com/Azure/Virtual-Machines/Windows/Containers</span><span class="sxs-lookup"><span data-stu-id="747bb-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="747bb-118">[Anterior](deploy-existing-net-apps-as-windows-containers.md)
[Siguiente](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="747bb-118">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>