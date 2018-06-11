---
title: Introducción al lenguaje C# y .NET Framework
description: Conozca los conceptos básicos de C# y .NET. Obtenga información general sobre el lenguaje C# y el ecosistema .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: ab2d3042aff51e85b50296ce6f4382f588e1af71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Introducción al lenguaje C# y .NET Framework
C# es un lenguaje elegante, con seguridad de tipos y orientado a objetos, que permite a los desarrolladores crear una gran variedad de aplicaciones seguras y sólidas que se ejecutan en [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] .NET. Puede usar C# para crear aplicaciones cliente de Windows, servicios web XML, componentes distribuidos, aplicaciones cliente-servidor, aplicaciones de base de datos y muchas, muchas más cosas. Visual C# proporciona un editor de código avanzado, prácticos diseñadores de interfaz de usuario, un depurador integrado y muchas otras herramientas que facilitan el desarrollo de aplicaciones basadas en el lenguaje C# y [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
> En la documentación de Visual C# se supone que comprende los conceptos básicos de programación. Si es principiante, puede que quiera examinar Visual C# Express, que está disponible en Internet. También puede aprovechar los libros y recursos web sobre C# para aprender sobre habilidades prácticas de programación.  
  
## <a name="c-language"></a>Lenguaje C#  
 La sintaxis de C# es muy expresiva, pero también sencilla y fácil de aprender. Cualquier persona familiarizada con C, C++ o Java, reconocerá al instante la sintaxis de llaves de C#. Los desarrolladores que conocen cualquiera de estos lenguajes pueden empezar normalmente a trabajar en C# de forma productiva en un espacio muy corto de tiempo. La sintaxis de C# simplifica muchas de las complejidades de C++ y proporciona características eficaces, como tipos de valor que aceptan valores NULL, enumeraciones, delegados, expresiones lambda y acceso directo a memoria, que no se encuentran en Java. C# admite métodos y tipo genéricos, que proporcionan una mayor seguridad de tipos y rendimiento, e iteradores, que permiten a los implementadores de clases de colecciones definir comportamientos de iteración personalizados que son fáciles de usar por el código de cliente. Las expresiones [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] convierten la consulta fuertemente tipada en una construcción de lenguaje de primera clase.  
  
 En cuanto lenguaje orientado a objetos, C# admite los conceptos de encapsulación, herencia y polimorfismo. Todas las variables y métodos, incluido el método `Main`, el punto de entrada de la aplicación, se encapsulan dentro de las definiciones de clase. Una clase puede heredar directamente de una clase primaria, pero puede implementar cualquier número de interfaces. Los métodos que invalidan los métodos virtuales en una clase primaria requieren la palabra clave `override` como una manera de evitar redefiniciones accidentales. En C#, un struct es como una clase sencilla; es un tipo asignado en la pila que puede implementar interfaces pero que no admite herencia.  
  
 Además de estos principios básicos orientados a objetos, C# facilita el desarrollo de componentes de software mediante varias construcciones de lenguaje innovadoras, incluidas las siguientes:  
  
-   Signaturas de método encapsulado llamadas *delegados*, que permiten notificaciones de eventos con seguridad de tipos.  
  
-   Propiedades, que actúan como descriptores de acceso para variables miembro privadas.  
  
-   Atributos, que proporcionan metadatos declarativos sobre tipos en tiempo de ejecución.  
  
-   Comentarios de doc.umentación XML insertados  
  
-   [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] que proporciona funcionalidades de consulta integradas en diversos orígenes de datos.  
  
 Si tiene que interactuar con otro software de Windows, como objetos COM o archivos DLL nativos de Win32, puede hacerlo en C# mediante un proceso denominado "Interoperabilidad". La interoperabilidad permite que los programas de C# hagan casi todo lo que puede hacer una aplicación C++ nativa. C# admite incluso el uso de punteros y el concepto de código "no seguro" en los casos en los que el acceso directo a memoria es absolutamente crítico.  
  
 El proceso de compilación de C# es simple en comparación con C y C++ y más flexible que en Java. No hay ningún archivo de encabezado independiente y ningún requisito de declaración de métodos y tipos en un orden en particular. Un archivo de código fuente de C# puede definir cualquier número de clases, structs, interfaces y eventos.  
  
 Los siguientes son recursos adicionales de C#:  
  
-   Para obtener una buena introducción general al lenguaje, consulte el capítulo 1 de la [especificación del lenguaje C#](../../csharp/language-reference/language-specification/index.md).  
  
-   Para más información sobre aspectos específicos del lenguaje C#, consulte la [referencia de C#](../../csharp/language-reference/index.md).  
  
-   Para más información sobre [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], consulte [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Arquitectura de la plataforma .NET Framework  
 Los programas de C# se ejecutan en [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], un componente integral de Windows que incluye un sistema de ejecución virtual llamado Common Language Runtime (CLR) y un conjunto unificado de bibliotecas de clases. El CLR es la implementación comercial de Microsoft de Common Language Infrastructure (CLI), un estándar internacional que es la base para la creación de entornos de ejecución y desarrollo en los que los lenguajes y las bibliotecas trabajan juntos sin problemas.  
  
 El código fuente escrito en C# se compila en un lenguaje intermedio (IL) que guarda conformidad con la especificación de CLI. El código y los recursos IL, como mapas de bits y cadenas, se almacenan en disco en un archivo ejecutable denominado ensamblado, normalmente con la extensión .exe o .dll. Un ensamblado contiene un manifiesto que proporciona información sobre los tipos, la versión, la referencia cultural y los requisitos de seguridad del ensamblado.  
  
 Cuando se ejecuta el programa de C#, el ensamblado se carga en el CLR, el cual podría realizar diversas acciones en función de la información en el manifiesto. Luego, si se cumplen los requisitos de seguridad, el CLR realiza la compilación Just in time (JIT) para convertir el código IL en instrucciones máquina nativas. El CLR también proporciona otros servicios relacionados con la recolección de elementos no utilizados, el control de excepciones y la administración de recursos. El código que se ejecuta en el CLR se conoce a veces como "código administrado", a diferencia del "código no administrado" que se compila en lenguaje de máquina nativo destinado a un sistema específico. En el siguiente diagrama se ilustran las relaciones de tiempo de compilación y tiempo de ejecución de archivos de código fuente de C#, las bibliotecas de clases de .NET Framework, los ensamblados y el CLR.  
  
 ![De código fuente de C&#35; a ejecución de máquina](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 la interoperabilidad entre lenguajes es una característica principal de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Debido a que el código IL generado por el compilador de C# cumple la especificación de tipo común (CTS), este código puede interactuar con el código generado a partir de las versiones .NET de Visual Basic, Visual C++ o cualquiera de los más de 20 lenguajes compatibles con CTS. Un solo ensamblado puede contener varios módulos escritos en diferentes lenguajes .NET y los tipos se pueden hacer referencia mutuamente igual que si estuvieran escritos en el mismo lenguaje.  
  
 Además de los servicios de tiempo de ejecución, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] también incluye una amplia biblioteca de más de 4000 clases organizadas en espacios de nombres que proporcionan una gran variedad de funciones útiles para todo, desde la entrada y la salida de archivos, pasando por la manipulación de cadenas para el análisis XML, hasta controles de formularios Windows Forms. La aplicación de C# típica usa la biblioteca de clases [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] de forma extensa para administrar tareas comunes de infraestructura.  
  
 Para más información sobre .NET Framework, consulte [Introducción a Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Vea también  
 [C#](../../csharp/index.md) [Introducción a Visual C# y Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
