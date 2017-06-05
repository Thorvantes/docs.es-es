---
title: "C&#243;mo importar WSDL personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# C&#243;mo importar WSDL personalizado
En este tema se describe cómo importar WSDL personalizado.  Para administrar el WSDL personalizado, debe implementar la interfaz <xref:System.ServiceModel.Description.IWsdlImportExtension>.  
  
### Para importar el WSDL personalizado  
  
1.  Implemente <xref:System.ServiceModel.Description.IWsdlImportExtension>.  Implemente el método <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> para modificar los metadatos antes de que se importen.  Implemente los métodos <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> y <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> para modificar contratos y extremos importados de los metadatos.  Para tener acceso al contrato o extremo importados, utilice el objeto de contexto \(<xref:System.ServiceModel.Description.WsdlContractConversionContext> correspondiente o <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>\):  
  
    ```  
    public class WsdlDocumentationImporter : IWsdlImportExtension  
       {  
          public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
    {  
            // Contract documentation  
         if (context.WsdlPortType.Documentation != null)  
         {  
               context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
    if (operation.Documentation != null)  
    {  
    OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
    if (operationDescription != null)  
    {  
                            operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
    }  
    }  
    }  
    }  
  
    public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)   
            {  
                Console.WriteLine("BeforeImport called.");  
            }  
  
    public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)   
            {  
                Console.WriteLine("ImportEndpoint called.");  
            }  
       }  
    ```  
  
2.  Configure la aplicación de cliente para utilizar el importador de WSDL personalizado.  Tenga en cuenta que si está utilizando Svcutil.exe, debería agregar esta configuración al archivo de configuración para Svcutil.exe \(Svcutil.exe.config\):  
  
    ```  
    <system.serviceModel>  
          <client>  
            <endpoint   
              address="http://localhost:8000/Fibonacci"   
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
  
    ```  
  
3.  Cree una nueva instancia <xref:System.ServiceModel.Description.WsdlImporter> \(pasar la instancia <xref:System.ServiceModel.Description.MetadataSet> que contiene los documentos WSDL que desea importar\) y llame a <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
  
    ```  
  
## Vea también  
 [Metadatos](../../../../docs/framework/wcf/feature-details/metadata.md)   
 [Exportación e importación de metadatos](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)   
 [Publicación de WSDL personalizada](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)