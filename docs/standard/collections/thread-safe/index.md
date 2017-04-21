---
title: "Colecciones seguras para subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "colecciones seguras para subprocesos, introducción"
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
caps.latest.revision: 24
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 24
---
# Colecciones seguras para subprocesos
[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] introduce el espacio de nombres <xref:System.Collections.Concurrent?displayProperty=fullName>, que incluye varias clases de colección que son a la vez seguras para subprocesos y escalables.  Varios subprocesos pueden agregar o quitar elementos de estas colecciones sin ningún riesgo y de un modo eficaz, sin requerir una sincronización adicional en código de usuario.  Al escribir un nuevo código, utilice las clases de colección simultáneas siempre que la colección se escriba en varios subprocesos simultáneamente.  Si solo está leyendo en una colección compartida, puede utilizar las clases en el espacio de nombres <xref:System.Collections.Generic?displayProperty=fullName>.  Recomendamos no utilizar clases de colección 1.0 a menos que estén destinadas a .NET Framework 1.1. o un runtime de una versión anterior.  
  
## Sincronización de subprocesos en las colecciones de .NET Framework 1.0 y 2.0  
 Las colecciones introducidas en .NET Framework 1.0 se encuentran en el espacio de nombres <xref:System.Collections?displayProperty=fullName>.  Estas colecciones, que incluyen <xref:System.Collections.ArrayList> y <xref:System.Collections.Hashtable> utilizados habitualmente, proporcionan cierta seguridad para subprocesos mediante la propiedad `Synchronized`, que devuelve un contenedor seguro para subprocesos en torno a la colección.  El contenedor funciona bloqueando toda la colección en cada operación de agregar o quitar.  Por consiguiente, cada subproceso que intenta tener acceso a la colección debe esperar su turno para tomar el único bloqueo.  Esto no es escalable y puede producir una degradación significativa del rendimiento en las colecciones grandes.  Asimismo, el diseño no está totalmente protegido de las condiciones de carrera.  Para obtener más información, vea [Synchronization in Generic Collections](http://go.microsoft.com/fwlink/?LinkID=161130) en el sitio web de MSDN.  
  
 Las clases de colección introducidas en .NET Framework 2.0 se encuentran en el espacio de nombres <xref:System.Collections.Generic?displayProperty=fullName>.  Éstas incluyen <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, etc.  Estas clases proporcionan una seguridad de tipos y un rendimiento mejorados comparados con las clases de .NET Framework 1.0.  Sin embargo, las clases de colección de .NET Framework 2.0 no proporcionan ninguna sincronización de subprocesos; el código de usuario debe proporcionar toda la sincronización cuando se agregan o quitan elementos en varios subprocesos simultáneamente.  
  
 Recomendamos las clases de colección simultáneas en [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] porque proporcionan no solo la seguridad de tipos de las clases de colección de .NET Framework 2.0, sino también una seguridad de subprocesos más eficaz y completa que las colecciones de [!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)].  
  
## Mecanismos de bloqueo específico y sin bloqueos  
 Algunos de los tipos de colección simultáneos utilizan mecanismos de sincronización ligeros como <xref:System.Threading.SpinLock>, <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim> y <xref:System.Threading.CountdownEvent>, que son nuevos en [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  Estos tipos de sincronización utilizan normalmente *giro de ocupado* durante breves períodos antes de colocar el subproceso en un verdadero estado de espera.  Cuando se prevé que los tiempos de espera sean muy cortos, el giro es técnicamente menos costoso que la espera, que implica una costosa transición del kernel.  Para las clases de colección que utilizan el giro, esta eficacia significa que se pueden agregar y quitar varios subprocesos con una tasa muy alta.  Para obtener más información sobre el giro frente al bloqueo, vea [SpinLock](../../../../docs/standard/threading/spinlock.md) y [SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 Las clases <xref:System.Collections.Concurrent.ConcurrentStack%601> y <xref:System.Collections.Concurrent.ConcurrentQueue%601> no utilizan bloqueos en absoluto.  En su lugar, dependen de las operaciones <xref:System.Threading.Interlocked> para lograr la seguridad para subprocesos.  
  
> [!NOTE]
>  Como las clases de colección simultáneas son compatibles con <xref:System.Collections.ICollection>, proporcionan implementaciones para las propiedades <xref:System.Collections.ICollection.SyncRoot%2A> y <xref:System.Collections.ICollection.IsSynchronized%2A>, aunque estas propiedades sean irrelevantes.  `IsSynchronized` devuelve siempre `false` y `SyncRoot` es siempre `null` \(`Nothing` en Visual Basic\).  
  
 La siguiente tabla enumera los tipos de colección en el espacio de nombres <xref:System.Collections.Concurrent?displayProperty=fullName>.  
  
|Tipo|Descripción|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Proporciona funcionalidad de límite y bloqueo para cualquier tipo que implemente <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.  Para obtener más información, vea [Información general sobre BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Implementación segura para subprocesos de un diccionario de pares clave\-valor.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Implementación segura para subprocesos de una cola FIFO \(primero en entrar, primero en salir\).|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Implementación segura para subprocesos de una pila LIFO \(último en entrar, primero en salir\).|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Implementación segura para subprocesos de una colección no ordenada de elementos.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Interfaz que debe implementar un tipo para su uso en `BlockingCollection`.|  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Información general sobre BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|Describe la funcionalidad proporcionada por el tipo <xref:System.Collections.Concurrent.BlockingCollection%601>.|  
|[Cómo: Agregar y quitar elementos de ConcurrentDictionary](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Describe cómo agregar y quitar los elementos de <xref:System.Collections.Concurrent.ConcurrentDictionary%602>|  
|[Cómo: Agregar y tomar elementos de forma individual en una clase BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Describe cómo agregar y recuperar elementos de una colección de bloqueo sin utilizar el enumerador de solo lectura.|  
|[Cómo: Agregar la funcionalidad de límite y bloqueo a una colección](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Describe cómo utilizar cualquier clase de colección como mecanismo de almacenamiento subyacente para una colección <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.|  
|[Cómo: Utilizar ForEach para quitar elementos de BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Describe cómo utilizar `foreach`, \(`For Each` en Visual Basic\) para quitar todos los elementos en una colección de bloqueo.|  
|[Cómo: Usar matrices de colecciones de bloqueo en una canalización](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Describe cómo utilizar varias colecciones de bloqueo para implementar una canalización al mismo tiempo.|  
|[Cómo: Crear un grupo de objetos usando ConcurrentBag](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Muestra cómo usar un controlador simultáneo para mejorar el rendimiento en escenarios donde puede reutilizar objetos en lugar de crear continuamente otros nuevos.|  
  
## Reference  
 <xref:System.Collections.Concurrent?displayProperty=fullName>