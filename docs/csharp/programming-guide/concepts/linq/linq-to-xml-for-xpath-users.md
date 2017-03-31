---
title: LINQ to XML para usuarios de XPath (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 91774511-1dca-4f06-ac0b-913746f104fe
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ff9490d7eb89e1503763060dbd123d59308a512d
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-for-xpath-users-c"></a>LINQ to XML para usuarios de XPath (C#)
En este conjunto de temas se muestran varias expresiones XPath y sus equivalentes de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Todos los ejemplos usan la funcionalidad XPath en [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] que está disponible con los métodos de extensión de <xref:System.Xml.XPath.Extensions?displayProperty=fullName>. Los ejemplos ejecutan la expresión XPath y la expresión [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. A continuación, cada ejemplo compara los resultados de ambas consultas, validando que la expresión XPath sea funcionalmente equivalente a la consulta de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Como ambos tipos de consultas devuelven nodos del mismo árbol XML, la comparación del resultado de las consultas se realiza mediante identidad referencial.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Comparación de XPath y LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Proporciona información general de las similitudes y diferencias entre XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].|  
|[Cómo: Buscar un elemento secundario (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Compara el eje del elemento secundario XPath con el método <xref:System.Xml.Linq.XContainer.Element%2A> de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"DeliveryNotes"`.|  
|[How to: Find a List of Child Elements (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md) (Cómo: Buscar una lista de elementos secundarios (XPath-LINQ to XML) [C#])|Compara el eje de elementos secundarios XPath con el eje <xref:System.Xml.Linq.XContainer.Elements%2A> de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"./*"`|  
|[How to: Find the Root Element (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md) (Cómo: Buscar el elemento raíz (XPath-LINQ to XML) [C#])|Compara cómo obtener el elemento raíz con XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"/PurchaseOrders"`|  
|[How to: Find Descendant Elements (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md) (Cómo: Buscar elementos descendientes (XPath-LINQ to XML) [C#])|Compara cómo obtener los elementos descendientes con un nombre específico con XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"//Name"`|  
|[How to: Filter on an Attribute (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md) (Cómo: Filtrar por un atributo (XPath-LINQ to XML) [C#])|Compara cómo obtener los elementos descendientes con un nombre especificado y con un atributo con un valor especificado con XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`".//Address[@Type='Shipping']"`|  
|[Cómo: Buscar elementos relacionados (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Compara cómo obtener un elemento seleccionando en un atributo al que hace referencia el valor de otro elemento con XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Cómo: Buscar elementos de un espacio de nombres (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace-xpath-linq-to-xml.md)|Compara el uso de la clase <xref:System.Xml.XmlNamespaceManager> de XPath con la propiedad <xref:System.Xml.Linq.XName.Namespace%2A> de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] de la clase <xref:System.Xml.Linq.XName> para trabajar con espacios de nombres XML.<br /><br /> La expresión XPath asociada es:`"./aw:*"`|  
|[How to: Find Preceding Siblings (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md) (Cómo: Buscar elementos anteriores del mismo nivel (XPath-LINQ to XML) [C#])|Compara el eje `preceding-sibling` de XPath con el eje <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> secundario de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"preceding-sibling::*"`|  
|[Cómo: Buscar descendientes de un elemento secundario (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Compara cómo obtener los elementos descendientes de un elemento secundario con un nombre específico con XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"./Paragraph//Text/text()"`|  
|[Cómo: Buscar la unión de dos rutas de acceso a ubicaciones (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml.md)|Compara el uso del operador de unión, `&#124;`, en XPath con el operador de consulta estándar <xref:System.Linq.Enumerable.Concat%2A> en [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"//Category&#124;//Price"`|  
|[Cómo: Buscar nodos del mismo nivel (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Compara cómo buscar todos los elementos del mismo nivel de un nodo que tiene un nombre específico con XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"../Book"`|  
|[Cómo: Buscar un atributo del elemento principal (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Compara cómo desplazarse al elemento primario y buscar un atributo asociado usando XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"../@id"`|  
|[Cómo: Buscar atributos de elementos del mismo nivel con un nombre específico (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml.md)|Compara cómo buscar atributos específicos de los elementos del mismo nivel del nodo de contexto con XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"``../Book/@id``"`|  
|[Cómo: Buscar elementos con un atributo específico (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml.md)|Compara cómo buscar todos los elementos que contienen un atributo específico usando XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"./*[@Select]"`|  
|[Cómo: Buscar elementos secundarios en función de la posición (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position-xpath-linq-to-xml.md)|Compara cómo buscar un elemento basándose en su posición relativa usando XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"Test[position() >= 2 and position() <= 4]"`|  
|[Cómo: Buscar el nodo del mismo nivel inmediatamente anterior (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Compara cómo buscar el elemento del mismo nivel inmediatamente anterior de un nodo usando XPath y [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> La expresión XPath asociada es:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Xml.XPath?displayProperty=fullName>   
 [Consultar árboles XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)   
 [Procesamiento de datos XML con el modelo de datos XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081)