---
title: 'Cómo: Usar el diseño automático para crear un botón'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Cómo: Usar el diseño automático para crear un botón
En este ejemplo se describe cómo usar el enfoque de diseño automático para crear un botón en una aplicación localizable.  
  
 Localización de un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] puede ser un proceso lento. A menudo, los localizadores tienen que cambiar el tamaño y la posición de los elementos, además de traducir el texto. En el pasado cada idioma que un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se ha adaptado para el ajuste necesario. Ahora con las capacidades de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] puede diseñar elementos que reducen la necesidad de ajuste. El enfoque para escribir aplicaciones que pueden resultar más fácilmente cuyo tamaño ha cambiado y cambia de posición se denomina `automatic layout`.  
  
 Las dos siguientes [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ejemplos crean aplicaciones que crean instancias de un botón: uno con texto en inglés y otro con texto en español. Observe que el código es el mismo, salvo para el texto; el botón se ajusta para adaptarse al texto.  
  
## <a name="example"></a>Ejemplo  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 En el gráfico siguiente se muestra la salida de los ejemplos de código.  
  
 ![El mismo botón con texto en diferentes idiomas](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Botón ajustable automáticamente  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el uso del diseño automático](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Usar una cuadrícula para el diseño automático](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
