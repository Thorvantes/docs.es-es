---
title: '&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f041cbfb4195b2c649c3af4fa061bf63e227df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a>&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; elemento
Especifica si PerfCounter.dll usa la configuración del Registro CategoryOptions en una aplicación de .NET Framework 1.1 para determinar si se van a cargar los datos del contador de rendimiento desde la memoria compartida específica de la categoría o la memoria global.  
  
 \<configuration>  
\<en tiempo de ejecución >  
\<forcePerformanceCounterUniqueSharedMemoryReads >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`enabled`|Atributo necesario.<br /><br /> Indica si PerfCounter.dll usa el valor del Registro CategoryOptions para determinar si se debe cargar los datos del contador de rendimiento de memoria compartida específica de la categoría o la memoria global.|  
  
## <a name="enabled-attribute"></a>Atributo enabled  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`false`|PerfCounter.dll no utiliza el CategoryOptions esta configuración del registro es el valor predeterminado.|  
|`true`|PerfCounter.dll utiliza el valor del Registro CategoryOptions.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|  
|`runtime`|Contiene información del enlace del ensamblado y de la recolección de elementos no utilizados.|  
  
## <a name="remarks"></a>Comentarios  
 En las versiones de .NET Framework anteriores a la [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], la versión de PerfCounter.dll cargada correspondía al runtime que se cargó en el proceso. Si un equipo tenía tanto la versión de .NET Framework 1.1 y [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] instalado, una aplicación de .NET Framework 1.1 carga la versión 1.1 de .NET Framework de PerfCounter.dll. A partir de la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], se carga la versión más reciente instalada de PerfCounter.dll. Esto significa que una aplicación de .NET Framework 1.1 se cargará el [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] versión de PerfCounter.dll si la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] está instalado en el equipo.  
  
 A partir de la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], al utilizar los contadores de rendimiento, PerfCounter.dll comprueba la entrada del Registro CategoryOptions de cada proveedor para determinar si debe leer desde la memoria compartida específica de la categoría o la memoria compartida global. El PerfCounter.dll de .NET Framework 1.1 no lee esa entrada del registro, porque no es consciente de memoria compartida de específico de la categoría; siempre lee de la memoria compartida global.  
  
 Por compatibilidad con versiones anteriores, el [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll no comprueba la entrada del registro de CategoryOptions al ejecutarse en una aplicación de .NET Framework 1.1. Simplemente utiliza la memoria compartida global, al igual que el PerfCounter.dll de .NET Framework 1.1. Sin embargo, puede indicar la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll para comprobar la configuración del Registro habilitando el `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento.  
  
> [!NOTE]
>  Habilitar la `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento no garantiza que se utilizará memoria compartida específica de la categoría. El valor habilitado para `true` sólo provoca que PerfCounter.dll haga referencia el valor del Registro CategoryOptions. La configuración predeterminada para CategoryOptions es específico de la categoría de memoria compartida; Sin embargo, puede cambiar CategoryOptions para indicar que se debe usar la memoria compartida global.  
  
 La clave del registro que contiene el valor CategoryOptions es HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. De forma predeterminada, CategoryOptions se establece en 3, que indica a PerfCounter.dll usar memoria compartida específica de la categoría. Si CategoryOptions está establecido en 0, PerfCounter.dll usa la memoria compartida global. Datos de instancia se reutilizará solo si el nombre de la instancia que se va a crear es idéntico a la instancia que se va a volver a usar. Todas las versiones podrán escribir en la categoría. Si CategoryOptions está establecido en 1, se utiliza la memoria compartida global, pero se pueden reutilizar los datos de instancia si el nombre de categoría es la misma longitud que la categoría que se va a volver a usar.  
  
 Los valores 0 y 1 pueden provocar pérdidas de memoria y el rellenado de la memoria del contador de rendimiento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo especificar que PerfCounter.dll debería hacer referencia a la entrada del Registro CategoryOptions para determinar si debe utilizar la memoria compartida específica de la categoría.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también  
 [Esquema de la configuración de Common Language Runtime](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de los archivos de configuración](../../../../../docs/framework/configure-apps/file-schema/index.md)
