---
title: Crear un objeto DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: c5073a553926fdfdd78b0b6837cdc07b58ac7faf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-datareader"></a>Crear un objeto DataReader
Las clases <xref:System.Data.DataTable> y <xref:System.Data.DataSet> tienen un método <xref:System.Data.DataTable.CreateDataReader%2A> que devuelve el contenido de la <xref:System.Data.DataTable> o el contenido de la colección <xref:System.Data.DataSet> del objeto <xref:System.Data.DataSet.Tables%2A> como uno o más conjuntos de resultados de solo lectura y solo avance.  
  
## <a name="example"></a>Ejemplo  
 La siguiente aplicación de consola crea una instancia de <xref:System.Data.DataTable>. En el ejemplo a continuación, pasa el relleno <xref:System.Data.DataTable> a un procedimiento que llama el <xref:System.Data.DataTable.CreateDataReader%2A> método, que recorre en iteración los resultados incluidos en el <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 En el ejemplo se muestra el siguiente resultado en la ventana de consola:  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [Objetos DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [Proveedores administrados de ADO.NET y Centro para desarrolladores de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
