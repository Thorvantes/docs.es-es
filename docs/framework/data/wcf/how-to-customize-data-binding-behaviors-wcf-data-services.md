---
title: 'Cómo: Personalizar comportamientos de enlace de datos (Data Services de WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 6ebc50a4a4ed2c91db0dcbcb53d3965757a94f9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Cómo: Personalizar comportamientos de enlace de datos (Data Services de WCF)
Con [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], puede proporcionar lógica personalizada a la que <xref:System.Data.Services.Client.DataServiceCollection%601> llama cuando se agrega o se quita un objeto de la colección de enlaces o cuando se detecta un cambio en una propiedad. Esta lógica personalizada se proporciona como métodos, al que hace referencia como <xref:System.Func%602> delegados, que devuelven un valor de `false` cuando el comportamiento predeterminado aún se debe ejecutar cuando se completa el método personalizado y `true` cuando subsiguientes de procesamiento de la debe detenerse el evento.  
  
 Los ejemplos de este tema proporcionan métodos personalizados para los parámetros `entityChanged` y `entityCollectionChanged` de la clase <xref:System.Data.Services.Client.DataServiceCollection%601>. En los ejemplos de este tema se usa el servicio de datos de ejemplo Northwind y las clases del servicio de datos del cliente generadas automáticamente. Se crean este servicio y las clases de datos de cliente al completar la [inicio rápido de WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Ejemplo  
 La siguiente página de codigos subyacente para el archivo XAML crea una instancia de <xref:System.Data.Services.Client.DataServiceCollection%601> con métodos personalizados a los que se llama cuando se producen cambios en los datos enlazados a la colección de enlaces. Cuando se produce el evento <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged>, el método proporcionado evita que se elimine del servicio de datos un elemento que se ha quitado de la colección de enlaces. Cuando se produce el evento <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged>, se valida el valor de `ShipDate` para asegurarse de que no se realizan cambios en los pedidos que ya han enviado.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Ejemplo  
 El código XAML siguiente define la ventana del ejemplo anterior.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca cliente de Servicios de datos de WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
