---
title: "!= (Distinto de) (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# != (Distinto de) (Entity SQL)
Compara dos expresiones para determinar si la expresión de la izquierda no es igual que la expresión de la derecha. El operador \!\= \(No es igual a\) es funcionalmente equivalente al operador \<\>.  
  
## Sintaxis  
  
```  
  
          expression  
          !=  
          expression  
or  
expression <> expression  
```  
  
## Argumentos  
 `expression`  
 Cualquier expresión válida. Ambas expresiones deben tener tipos de datos convertibles implícitamente.  
  
## Tipos de resultado  
 `true` si la expresión de la izquierda no es igual a la expresión de la derecha; de lo contrario, `false`.  
  
## Ejemplo  
 La consulta de Entity SQL siguiente usa el operador \!\= para comparar dos expresiones con el fin de determinar si la expresión de la izquierda es distinta de la expresión de la derecha. La consulta se basa en el modelo AdventureWorks Sales. Para compilar y ejecutar esta consulta, siga estos pasos:  
  
1.  Siga el procedimiento de [Ejecutar una consulta que devuelve resultados StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Pase la consulta siguiente como argumento al método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## Vea también  
 [Referencia de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)