---
title: Sección &lt;extensions&gt;
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 09cabfc6c03602c3b6de343a29b5b25755f2cf0f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ltextensionsgt-section"></a>Sección &lt;extensions&gt;
Esta sección de configuración contiene una colección de extensiones, que le permiten al usuario crear los enlaces definidos por el usuario, comportamientos y otros aspectos de las extensiones.  
  
\<system.ServiceModel>  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Esta sección contiene elementos secundarios que especifican extensiones de comportamiento, que permiten al usuario personalizar el servicio o los comportamientos del punto de conexión.|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|En esta sección se habilita el uso de un elemento de enlace personalizado de un equipo o archivo de configuración de la aplicación.|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Esta sección contiene elementos secundarios que especifican extensiones de enlace, que le permiten al usuario personalizar los enlaces.|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Esta sección contiene elementos secundarios que registran los puntos de conexión estándar.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|system.ServiceModel|Elemento raíz de todos los elementos de configuración de WCF.|
