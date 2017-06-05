---
title: "Elemento &lt;security&gt; de &lt;basicHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# Elemento &lt;security&gt; de &lt;basicHttpBinding&gt;
Define todas las funciones de seguridad de [\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
## Sintaxis  
  
```  
  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|modo|Opcional.  Especifica el tipo de seguridad que se utiliza.  De manera predeterminada, es `None`.  Este atributo es del tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## Atributo de modo  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Ninguna|-   Los mensajes no se protegen durante la transferencia.|  
|Transporte|La seguridad se proporciona utilizando transporte HTTPS.  Los mensajes SOAP se protegen utilizando HTTPS.  El servicio se autentica al cliente utilizando el certificado X.509 del servicio.  El cliente se autentica utilizando el ClientCredentialType proporcionado.  Vea [\<transporte\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).|  
|Mensaje|La seguridad se proporciona mediante la seguridad del mensaje SOAP.  De forma predeterminada, el cuerpo se cifra y firma.  Para este enlace, el sistema requiere que el certificado de servidor se proporcione al cliente fuera de la banda.  El único `ClientCredentialType` válido para este enlace es `Certificate`.|  
|TransportWithMessageCredential|La seguridad de transporte proporciona integridad, confidencialidad y autenticación del servidor.  La autenticación del cliente se proporciona por medio de la seguridad del mensaje SOAP.  Este modo es pertinente cuando el usuario está autenticando utilizando el nombre de usuario\/contraseña y existe una implementación del HTTP existente para proteger la transferencia del mensaje.|  
|TransportCredentialOnly|Este modo no proporciona integridad del mensaje y confidencialidad.  Proporciona la autenticación del cliente basada en http.  Este modo se debe utilizar con precaución.  Se debería utilizar en entornos donde otros recursos \(como IPSec\) están proporcionando la seguridad de transporte y la infraestructura [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] proporciona sólo la autenticación del cliente.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[\<transporte\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|Define los valores de seguridad de transporte para un servicio HTTP básico.  Este elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|Define los valores de modo de seguridad para un servicio HTTP básico.  Este elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|enlace|El elemento de enlace del [\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## Comentarios  
 De forma predeterminada, no se protege el mensaje SOAP y no se autentica el cliente.  Este elemento le permite establecer la configuración de seguridad adicional para el elemento `basicHttpBinding`.  
  
## Vea también  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>   
 <xref:System.ServiceModel.BasicHttpSecurity>   
 [Protección de servicios y clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Selección de tipos de credenciales](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Enlaces](../../../../../docs/framework/wcf/bindings.md)   
 [Configuración de enlaces proporcionados por el sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/es-es/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<enlace\>](../../../../../docs/framework/misc/binding.md)