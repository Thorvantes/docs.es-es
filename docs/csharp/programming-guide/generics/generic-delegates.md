---
title: Delegados genéricos (Guía de programación de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: a9f06dcf608a83b53e894310f20810182cf6daa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="generic-delegates-c-programming-guide"></a>Delegados genéricos (Guía de programación de C#)
Un [delegado](../../../csharp/language-reference/keywords/delegate.md) puede definir sus propios parámetros de tipo. El código que hace referencia al delegado genérico puede especificar el tipo de argumento para crear un tipo construido abierto, igual que al crear una instancia de una clase genérica o al llamar a un método genérico, como se muestra en el siguiente ejemplo:  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C# 2.0 tiene una nueva característica denominada conversión de grupo de métodos, que se aplica a los tipos delegados concretos y genéricos, y permite escribir la línea anterior con esta sintaxis simplificada:  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Los delegados definidos dentro de una clase genérica pueden usar los parámetros de tipo de la clase genérica de la misma manera que lo hacen los métodos de clase.  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 El código que hace referencia al delegado debe especificar el argumento de tipo de la clase contenedora, de la siguiente manera:  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Los delegados genéricos son especialmente útiles para definir eventos basados en el patrón de diseño habitual porque el argumento del remitente puede estar fuertemente tipado y ya no tiene que convertirse a y de <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Collections.Generic>  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Introducción a los genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Métodos genéricos](../../../csharp/programming-guide/generics/generic-methods.md)  
 [Clases genéricas](../../../csharp/programming-guide/generics/generic-classes.md)  
 [Interfaces genéricas](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [Delegados](../../../csharp/programming-guide/delegates/index.md)  
 [Genéricos](~/docs/standard/generics/index.md)
