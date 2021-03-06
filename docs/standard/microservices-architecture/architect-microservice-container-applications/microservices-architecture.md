---
title: Arquitectura de microservicios
description: Arquitectura de microservicios de .NET para aplicaciones .NET en contenedor | Arquitectura de microservicios
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bcaacce323ed9afa482660f409312f9a1b82cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="microservices-architecture"></a>Arquitectura de microservicios

Como su nombre indica, una arquitectura de microservicios es un enfoque para la generación de una aplicación de servidor como un conjunto de servicios pequeños. Cada servicio se ejecuta en su propio proceso y se comunica con otros procesos mediante protocolos como HTTP/HTTPS, WebSockets o [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Cada microservicio implementa un dominio de un extremo a otro específico o una capacidad empresarial dentro de un determinado límite de contexto, y cada uno se debe desarrollar de forma autónoma e implementar de forma independiente. Por último, cada microservicio debe poseer su modelo de datos de dominio relacionado y su lógica del dominio (soberanía y administración de datos descentralizada) sobre la base de diferentes tecnologías de almacenamiento de datos (SQL, NoSQL) y lenguajes de programación.

¿Qué tamaño debe tener un microservicio? Al desarrollar un microservicio, el tamaño no debe ser lo más importante. En su lugar, el punto importante debe ser crear libremente servicios acoplados para que tenga autonomía de desarrollo, implementación y escala, para cada servicio. Por supuesto, al identificar y diseñar microservicios, debe intentar que sean lo más pequeños posible, siempre y cuando no tenga demasiadas dependencias directas con otros microservicios. Más importante que el tamaño del microservicio es la cohesión interna que debe tener y su independencia respecto a otros servicios.

¿Por qué se debe tener una arquitectura de microservicios? En resumen, proporciona agilidad a largo plazo. Con los microservicios puede crear aplicaciones basadas en muchos servicios que se pueden implementar de forma independiente y que tienen ciclos de vida granulares y autónomos, lo que permite un mejor mantenimiento en sistemas complejos, grandes y altamente escalables.

Como ventaja adicional, los microservicios se pueden escalar horizontalmente de forma independiente. En lugar de disponer de una sola aplicación monolítica que debe escalar horizontalmente como una unidad, puede escalar horizontalmente microservicios concretos. De esa forma, puede escalar solo el área funcional que necesita más potencia de procesamiento o ancho de banda para admitir la demanda, en lugar de escalar horizontalmente otras partes de la aplicación que no hace falta escalar. Así, puede ahorrar en costes porque necesita menos hardware.

![](./media/image6.png)

**Figura 4-6**. Implementación monolítica frente al enfoque de los microservicios

Tal y como se muestra en la figura 4-6, el enfoque de los microservicios permite modificaciones ágiles e iteraciones rápidas de cada microservicio, ya que puede cambiar áreas específicas y pequeñas de aplicaciones complejas, grandes y escalables.

Diseñar la arquitectura de aplicaciones específicas basadas en microservicios habilita una integración continua y prácticas de entrega continua. También acelera la entrega de nuevas funciones en la aplicación. La composición específica de las aplicaciones también le permite ejecutar y probar los microservicios de manera aislada y hacerlos evolucionar de forma autónoma a la vez que mantiene contratos claros entre ellos. Siempre y cuando no cambie las interfaces o los contratos, puede cambiar la implementación interna de cualquier microservicio o agregar nuevas funciones sin que ello interrumpa otros microservicios.

Después se indican aspectos importantes para habilitar el éxito de pasar a producción con un sistema basado en microservicios:

-   Supervisión y comprobaciones de estado de los servicios y la infraestructura.

-   Infraestructura escalable para los servicios (es decir, la nube y orquestadores).

-   Diseño de seguridad e implementación en varios niveles: autenticación, autorización, administración de secretos, comunicación segura, etc.

-   Entrega rápida de aplicaciones, en que normalmente distintos equipos que centran en microservicios diferentes.

-   Infraestructura y prácticas de DevOps y CI/CD.

En esta guía solo se cubren o introducen los tres primeros aspectos. Los dos últimos puntos, que están relacionados con el ciclo de vida de la aplicación, se tratan en el libro electrónico adicional [Ciclo de vida de aplicaciones de Docker en contenedor con la plataforma y las herramientas de Microsoft](https://aka.ms/dockerlifecycleebook).

## <a name="additional-resources"></a>Recursos adicionales

-   **Mark Russinovich. Microservices: An application revolution powered by the cloud (Microservicios: una revolución de las aplicaciones con la tecnología de la nube)**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler. Microservices (Microservicios)**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler. Microservice Prerequisites (Requisitos previos de microservicios)**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson. Chunk Cloud Computing (Informática en la nube de fragmentos)**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (Ciclo de vida de aplicaciones de Docker en contenedor con la plataforma y las herramientas de Microsoft; libro electrónico descargable) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)
