---
title: 'Cómo: Consultar una base de datos usando LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: f17e0dc6956c5465f8269562705eb0f754f1585c
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827266"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a>Cómo: Consultar una base de datos usando LINQ (Visual Basic)
Language-Integrated Query (LINQ) facilita el acceso a la información de la base de datos y ejecutar consultas.  
  
 En el ejemplo siguiente se muestra cómo crear una nueva aplicación que realiza consultas en una base de datos de SQL Server.  
  
 Los ejemplos de este tema usan la base de datos de ejemplo Northwind. Si no tiene esta base de datos en el equipo de desarrollo, puede descargarlo desde Microsoft Download Center. Para obtener instrucciones, consulte [descargar bases de datos de ejemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a>Para crear una conexión a una base de datos  
  
1.  En Visual Studio, abra **Explorador de servidores**/**el Explorador de base de datos** haciendo clic en **Explorador de servidores**/**base de datos El Explorador de** en el **vista** menú.  
  
2.  Haga clic en **las conexiones de datos** en **Explorador de servidores**/**el Explorador de base de datos** y, a continuación, haga clic en **Agregar conexión**.  
  
3.  Especifique una conexión válida a la base de datos de ejemplo Northwind.  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para agregar un proyecto que contiene un archivo LINQ to SQL  
  
1.  En el menú **Archivo** de Visual Studio, apunte a **Nuevo** y haga clic en **Proyecto**. Seleccione Visual Basic **aplicación de Windows Forms** como el tipo de proyecto.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**. Seleccione el **clases LINQ to SQL** plantilla de elemento.  
  
3.  Asigne al archivo el nombre `northwind.dbml`. Haga clic en **Agregar**. Se abre el Object Relational Designer (Object Relational Designer) para el archivo northwind.dbml.  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a>Para agregar tablas a una consulta para el Object Relational Designer  
  
1.  En **Explorador de servidores**/**el Explorador de base de datos**, expanda la conexión a la base de datos Northwind. Expanda el **tablas** carpeta.  
  
     Si ha cerrado el Object Relational Designer, puede volver a abrirlo haciendo doble clic en el archivo northwind.dbml que agregó anteriormente.  
  
2.  Haga clic en la tabla Customers y arrástrelo hasta el panel izquierdo del diseñador. Haga clic en la tabla Orders y arrástrelo hasta el panel izquierdo del diseñador.  
  
     El diseñador crea nuevos `Customer` y `Order` objetos para el proyecto. Observe que el diseñador automáticamente detecta las relaciones entre las tablas y crea a secundarios propiedades de objetos relacionados. Por ejemplo, IntelliSense mostrará que el `Customer` objeto tiene una `Orders` propiedad para todos los pedidos relacionados con ese cliente.  
  
3.  Guarde los cambios y cierre el diseñador.  
  
4.  Guarde el proyecto.  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Para agregar código para consultar la base de datos y mostrar los resultados  
  
1.  Desde el **cuadro de herramientas**, arrastre un <xref:System.Windows.Forms.DataGridView> control en el formulario Windows Forms predeterminado para el proyecto, Form1.  
  
2.  Haga doble clic en Form1 para agregar código a la `Load` evento del formulario.  
  
3.  Cuando agrega tablas a Object Relational Designer, el diseñador agrega un <xref:System.Data.Linq.DataContext> objeto para el proyecto. Este objeto contiene el código que necesita para tener acceso a esas tablas, además de los objetos individuales y colecciones de cada tabla. La <xref:System.Data.Linq.DataContext> objeto para el proyecto se denomina según el nombre del archivo dbml. Para este proyecto, el <xref:System.Data.Linq.DataContext> se denomina objeto `northwindDataContext`.  
  
     Puede crear una instancia de la <xref:System.Data.Linq.DataContext> en el código y consultar las tablas especifican por el Object Relational Designer.  
  
     Agregue el código siguiente a la `Load` eventos para consultar las tablas que se exponen como propiedades de su contexto de datos.  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]  
  
4.  Presione F5 para ejecutar el proyecto y ver los resultados.  
  
5.  Estos son algunas consultas adicionales que puede probar:  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]  
  
## <a name="see-also"></a>Vea también  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Métodos de DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
