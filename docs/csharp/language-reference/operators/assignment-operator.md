---
title: Operador = (Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 979250c91cfe2abdf7295ae3866cd6b4294285cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>Operador = (Referencia de C#)
El operador de asignación (`=`) almacena el valor de su operando de la derecha en la ubicación de almacenamiento, propiedad o indexador indicado por su operando de la izquierda y devuelve el valor como su resultado. Los operandos deben ser del mismo tipo (o el operando de la derecha debe poder convertirse implícitamente en el tipo del operando de la izquierda).  
  
## <a name="remarks"></a>Comentarios  
 El operador de asignación no se puede sobrecargar. En cambio, puede definir operadores de conversión implícitos para un tipo, que le permiten usar el operador de asignación con esos tipos. Para obtener más información, vea [Usar operadores de conversión (Guía de programación de C#)](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Referencia de C#](../../../csharp/language-reference/index.md)  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Operadores de C#](../../../csharp/language-reference/operators/index.md)
