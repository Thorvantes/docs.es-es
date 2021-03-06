---
title: Operador / (Referencia de C#)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 9d0bbff1fd9f4ab3c93c879d12ccd5fde1187b44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>Operador / (Referencia de C#)
El operador de división (`/`) divide su primer operando por su segundo operando. Todos los tipos numéricos tienen operadores de división predefinidos.
  
## <a name="remarks"></a>Comentarios  
 Los tipos definidos por el usuario pueden sobrecargar el operador `/` (vea [operator](../../../csharp/language-reference/keywords/operator.md)). Una sobrecarga del operador `/` sobrecarga implícitamente el [operador /=](division-assignment-operator.md).  
  
 Cuando se dividen dos números enteros, el resultado siempre es un entero. Por ejemplo, el resultado de 7 / 3 es 2. No debe confundirse con la división por pisos, ya que el operador `/` redondea hacia cero: -7 / 3 es -2.  
  
 Para obtener un cociente como un número racional, use los tipos `float`, `double` o `decimal`. Hay muchas maneras de convertir entre [los tipos numéricos integrados](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 Para determinar el resto, use el [operador de resto](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Referencia de C#](../../../csharp/language-reference/index.md)  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Operadores de C#](../../../csharp/language-reference/operators/index.md)
