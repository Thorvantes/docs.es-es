---
title: "Mitigaci&#243;n: Deserializaci&#243;n de objetos en distintos dominios de aplicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# Mitigaci&#243;n: Deserializaci&#243;n de objetos en distintos dominios de aplicaci&#243;n
En algunos casos, cuando una aplicación usa dos o más dominios de aplicación con distintas bases de aplicación, un intento de deserializar objetos en el contexto de llamada lógico entre dominios de aplicación produce una excepción.  
  
## Diagnóstico del problema  
 El problema se produce bajo la secuencia siguiente de condiciones:  
  
1.  Una aplicación usa dos o más dominios de aplicación con distintas bases de aplicación.  
  
2.  Algunos tipos se agregan explícitamente a la clase <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> llamando a métodos como <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=fullName> o <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=fullName>.  Estos tipos no están marcados como serializables y no se almacenan en la caché global de ensamblados.  
  
3.  Después, el código que se ejecuta en el dominio de aplicación no predeterminado intenta leer un valor de un archivo de configuración o usar XML para deserializar un objeto.  
  
4.  Para leer de un archivo de configuración o deserializar el objeto, un objeto <xref:System.Xml.XmlReader> intenta tener acceso al sistema de configuración.  
  
5.  Si aún no se ha inicializado el sistema de configuración, deberá completarse dicha inicialización.  Esto significa, entre otras cosas, que el runtime tiene que crear una ruta de acceso estable para un sistema de configuración, lo que hace de la forma siguiente:  
  
    1.  Busca evidencia para el dominio de aplicación no predeterminado.  
  
    2.  Intenta calcular la evidencia para el dominio de aplicación no predeterminado basándose en el dominio de aplicación predeterminado.  
  
    3.  La llamada para obtener evidencia del dominio de aplicación predeterminado desencadena una llamada de dominio de aplicación cruzado desde el dominio de aplicación no predeterminado al dominio de aplicación predeterminado.  
  
    4.  Como parte del contrato de dominio de aplicación cruzado de .NET Framework, el contenido del contexto de llamada lógico también tiene que calcularse en los límites de dominio de aplicación.  
  
6.  Dado que los tipos incluidos en el contexto de llamada lógico no se pueden resolver en el dominio de aplicación predeterminado, se produce una excepción.  
  
## Mitigación  
 Para solucionar este problema, haga lo siguiente  
  
1.  Busque la llamada a `get_Evidence` en la pila de llamadas cuando se produce la excepción.  La excepción puede ser cualquiera de las existentes en un gran subconjunto de excepciones, incluidas <xref:System.IO.FileNotFoundException> y <xref:System.Runtime.Serialization.SerializationException>.  
  
2.  Identifique el lugar de la aplicación donde no se agrega ningún objeto al contexto de llamada lógico y agregue el código siguiente:  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## Vea también  
 [Cambios en tiempo de ejecución](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)