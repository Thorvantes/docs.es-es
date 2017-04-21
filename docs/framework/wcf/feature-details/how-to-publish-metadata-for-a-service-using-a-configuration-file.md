---
title: "C&#243;mo publicar metadatos para un servicio mediante un archivo de configuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: 24
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# C&#243;mo publicar metadatos para un servicio mediante un archivo de configuraci&#243;n
Este es uno de los dos temas de instrucciones para la publicación de metadatos para un servicio de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Hay dos maneras de especificar cómo debería publicar metadatos un servicio: mediante un archivo de configuración y mediante código. En este tema se muestra cómo publicar metadatos para un servicio mediante un archivo de configuración.  
  
> [!CAUTION]
>  En este tema se muestra cómo publicar metadatos de forma no segura. Cualquier cliente puede recuperar los metadatos del servicio. Si necesita el servicio para publicar metadatos de forma segura, vea [extremo seguro de metadatos personalizado](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]publicación de metadatos en el código, vea [Cómo: Publicar metadatos para un servicio mediante código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). La publicación de metadatos permite a los clientes recuperar los metadatos mediante una solicitud GET WS-Transfer o mediante una solicitud HTTP/GET usando la cadena de solicitud `?wsdl`. Para estar seguro de que el código funciona, cree un servicio básico de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Para simplificar, se proporciona un servicio autohospedado básico en el código siguiente.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 Este servicio es un servicio autohospedado que se configura usando un archivo de configuración. El archivo de configuración siguiente sirve de punto de partida.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Publicación de metadatos para un servicio WCF mediante un archivo de configuración  
  
1.  Dentro del archivo App.config, después del elemento `</services>` de cierre, cree un elemento `<behaviors>`.  
  
  
  
2.  Dentro del elemento `<behaviors>`, agregue un nuevo elemento `<serviceBehaviors>`.  
  
  
  
3.  Agregue un elemento `<behavior>` al elemento `<serviceBehaviors>` y especifique un valor para el atributo `name` del elemento `<behavior>`.  
  
  
  
4.  Agregue un elemento `<serviceMetadata>` al elemento `<behavior>`. Establezca el atributo `httpGetEnabled` en `true` y el atributo `policyVersion` en Policy15. `httpGetEnabled` permite que el servicio responda a las solicitudes de metadatos realizadas por una solicitud HTTP GET. `policyVersion` indica al servicio que se ajuste a WS-Policy 1.5 al generar los metadatos.  
  
  
  
5.  Agregue un atributo `behaviorConfiguration` al elemento `<service>` y especifique el atributo `name` del elemento `<behavior>` agregado en el paso 1, como se muestra en el siguiente código de ejemplo.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6.  Agregue uno o varios elementos `<endpoint>` con el contrato establecido en `IMetadataExchange`, como se muestra en el código de ejemplo siguiente.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7.  Para los extremos de metadatos agregados en el paso anterior, establezca el atributo `binding` en uno de los siguientes valores:  
  
    -   `mexHttpBinding` para la publicación HTTP.  
  
    -   `mexHttpsBinding` para la publicación HTTPS.  
  
    -   `mexNamedPipeBinding` para la publicación de la canalización con nombre.  
  
    -   `mexTcpBinding` para la publicación TCP.  
  
8.  Para los extremos de metadatos agregados en un paso anterior, establezca la dirección en:  
  
    -   Una cadena vacía para utilizar la dirección base de la aplicación host como el punto de publicación si la dirección base es igual que el enlace de los metadatos.  
  
    -   Una dirección relativa si la aplicación host tiene una dirección base.  
  
    -   Una dirección absoluta.  
  
9. Compile y ejecute la aplicación de consola.  
  
10. Utilice Internet Explorer para ir a la dirección base del servicio (http://localhost:8001/MetadataSample en este ejemplo) y comprobar que la publicación de los metadatos está activada. Si no, un mensaje en la parte superior de la página resultante muestra: "La publicación de metadatos para este servicio está deshabilitad actualmente".  
  
### <a name="to-use-default-endpoints"></a>Para usar puntos de conexión predeterminados  
  
1.  Para configurar los metadatos en un servicio que usa extremos predeterminados, especifique el <xref:System.ServiceModel.Description.ServiceMetadataBehavior> en la configuración de archivos como en el ejemplo anterior, pero no se especifica ningún extremo. El archivo de configuración debería tener el aspecto siguiente.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Dado que el servicio tiene un <xref:System.ServiceModel.Description.ServiceMetadataBehavior> con el `httpGetEnabled` establecido en `true`, el servicio tiene habilitada la publicación de metadatos y porque no se agregó ningún extremo explícitamente, el tiempo de ejecución agrega los extremos predeterminados. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]extremos predeterminados, enlaces y comportamientos, vea [configuración simplificada](../../../../docs/framework/wcf/simplified-configuration.md) y [configuración simplificada para los servicios WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código muestra la implementación de un servicio [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] básico y el archivo de configuración que publica los metadatos del servicio.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>   
 [Cómo: hospedar un servicio WCF en una aplicación administrada](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)   
 [Autohospedaje](../../../../docs/framework/wcf/samples/self-host.md)   
 [Introducción a la arquitectura de metadatos](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)   
 [Uso de metadatos](../../../../docs/framework/wcf/feature-details/using-metadata.md)   
 [Cómo: Publicar metadatos para un servicio mediante código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)