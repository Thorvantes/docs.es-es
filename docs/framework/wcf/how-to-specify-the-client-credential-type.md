---
title: 'Cómo: Especificar el tipo de credencial de cliente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 5e1ff85d8a0bd45c87786f98c2cafe06472052b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-client-credential-type"></a>Cómo: Especificar el tipo de credencial de cliente
Después de establecer un modo de seguridad (ya sea transporte o mensaje), tiene la opción de establecer el tipo de credencial de cliente. Esta propiedad especifica qué tipo de credencial debe proporcionar el cliente al servicio para la autenticación. Para obtener más información acerca de cómo establecer el modo de seguridad (es decir, un paso necesario antes de establecer tipo de credencial de cliente), consulte [Cómo: establecer el modo de seguridad](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Para establecer el tipo de credencial de cliente en el código  
  
1.  Cree una instancia del enlace que el servicio va a usar. En el ejemplo siguiente se utiliza el enlace <xref:System.ServiceModel.WSHttpBinding>.  
  
2.  Establezca la propiedad <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> en un valor apropiado. Este ejemplo utiliza el modo de mensaje.  
  
3.  Establezca la propiedad <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> en un valor apropiado. Este ejemplo establece el uso de la autenticación de Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Para establecer el tipo de credencial en la configuración  
  
1.  Agregar un [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento al archivo de configuración.  
  
2.  Como un elemento secundario, agregue un [ \<enlaces >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.  
  
3.  Agregue un enlace adecuado. Este ejemplo se utiliza la [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.  
  
4.  Agregar un [ \<enlace >](../../../docs/framework/misc/binding.md) y establezca el `name` de atributo en un valor adecuado. Este ejemplo utiliza el nombre "SecureBinding".  
  
5.  Agregue un enlace `<security>`. Establezca el atributo `mode` en un valor adecuado. Este ejemplo lo define en `"Message"`.  
  
6.  Agregue un `<message>` o `<transport>` elemento, según lo determinado por el modo de seguridad. Establezca el atributo `clientCredentialType` en un valor adecuado. Este ejemplo usa `"Windows"`.  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad de servicios](../../../docs/framework/wcf/securing-services.md)  
 [Cómo establecer el modo de seguridad](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
