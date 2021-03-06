---
title: Maneras de seleccionar un control Button de formularios Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 39696be1286efa68fa70b698ba9623911c90e352
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Maneras de seleccionar un control Button de formularios Windows Forms
Se pueden seleccionar un botón de formularios Windows Forms en las siguientes maneras:  
  
-   Usar un mouse para hacer clic en el botón.  
  
-   Invocar el botón <xref:System.Windows.Forms.Control.Click> evento en el código.  
  
-   Mover el foco al botón presionando la tecla TAB y, a continuación, elija el botón al presionar la barra espaciadora o ENTRAR.  
  
-   Presione la tecla de acceso (ALT + letra subrayada) del botón. Para obtener más información acerca de las teclas de acceso, consulte [Cómo: crear teclas de acceso para controles de formularios Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
-   Si el botón es el botón "Aceptar" del formulario, al presionar ENTRAR, elige el botón, aunque otro control tenga el foco, excepto si ese control es otro botón, un cuadro de texto de varias líneas o un control personalizado que intercepta la tecla ENTRAR.  
  
-   Si el botón es el botón "Cancelar" del formulario, al presionar ESC elige el botón, aunque otro control tenga el foco.  
  
-   Llame a la <xref:System.Windows.Forms.Button.PerformClick%2A> método para seleccionar el botón mediante programación.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el control Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Responder a clics de botones en Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Botón (control)](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
