---
title: 'Introducción al almacenamiento de tabla de Azure con F #'
description: Almacenar datos estructurados en la nube con el almacenamiento de tabla de Azure o base de datos de Azure Cosmos.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: ac81bc88db1436aa4d5f576da61a90839df04b99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Introducción a almacenamiento de tabla de Azure y la API de tabla de base de datos de Azure Cosmos con F # # 

El almacenamiento de tabla es un servicio que almacena datos estructurados de NoSQL en la nube. Almacenamiento de tabla es un almacén de clave/atributo con un diseño schemaless. Dado que el almacenamiento de tabla es schemaless, es fácil adaptar los datos como las necesidades de su evolucionar de la aplicación. Acceso a los datos es rápido y rentable para todos los tipos de aplicaciones. Almacenamiento de tabla suele ser significativamente menor costo que SQL tradicional para similar volúmenes de datos.

Puede usar el almacenamiento de tabla para almacenar conjuntos de datos flexible, como datos de usuario para aplicaciones web, libretas de direcciones, información del dispositivo y cualquier otro tipo de metadatos que necesite el servicio. Puede almacenar cualquier número de entidades en una tabla y una cuenta de almacenamiento puede contener cualquier número de tablas, hasta el límite de capacidad de la cuenta de almacenamiento.

Base de datos de Azure Cosmos proporciona la API de tabla para las aplicaciones escritas para el almacenamiento de tabla de Azure y que requieren capacidades premium como:

- Distribución global llave en mano.
- Rendimiento dedicado en todo el mundo.
- Latencias de milisegundos de un solo dígito en el percentil 99.
- Garantiza la alta disponibilidad.
- Secundario la indexación automática.

Las aplicaciones escritas para el almacenamiento de tabla de Azure pueden migrar a base de datos de Azure Cosmos mediante la API de tabla sin realizar ningún cambio en el código y aprovechar las capacidades premium. La API de tabla tiene el SDK de cliente disponible para. NET, Java, Python y Node.js.

Para obtener más información, consulte [Introducción a la API de tabla de base de datos de Azure Cosmos](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Acerca de este tutorial

Este tutorial muestra cómo escribir código de F # para realizar algunas tareas comunes utilizando la API de tabla de Azure Cosmos DB, incluida la creación y eliminar una tabla e Insertar, actualizar, eliminar y consultar datos de la tabla o de almacenamiento de tabla de Azure.

## <a name="prerequisites"></a>Requisitos previos

Para utilizar esta guía, primero debe [crear una cuenta de almacenamiento de Azure](/azure/storage/storage-create-storage-account) o [cuenta de base de datos de Azure Cosmos](https://azure.microsoft.com/try/cosmosdb/).


## <a name="create-an-f-script-and-start-f-interactive"></a>Crear un Script de F # y el inicio de F # Interactive

Los ejemplos de este artículo pueden usarse en una aplicación de F # o un script de F #. Para crear un script de F #, cree un archivo con el `.fsx` extensión, por ejemplo `tables.fsx`, en el entorno de desarrollo de F #.

A continuación, use un [el Administrador de paquetes](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) o [NuGet](https://www.nuget.org/) para instalar el `WindowsAzure.Storage` paquete y referencia `WindowsAzure.Storage.dll` en el script mediante un `#r`directiva. Hacerlo nuevo para `Microsoft.WindowsAzure.ConfigurationManager` con el fin de obtener el espacio de nombres Microsoft.Azure.

### <a name="add-namespace-declarations"></a>Agregue las declaraciones de espacio de nombres

Agregue el siguiente `open` instrucciones a la parte superior de la `tables.fsx` archivo:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Obtener la cadena de conexión de almacenamiento de Azure

Si se está conectando al servicio de la tabla de almacenamiento de Azure, necesitará la cadena de conexión para este tutorial. Puede copiar la cadena de conexión desde el portal de Azure. Para obtener más información acerca de las cadenas de conexión, vea [configurar cadenas de conexión de almacenamiento](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Obtener la cadena de conexión de base de datos de Azure Cosmos

Si se está conectando a la base de datos de Azure Cosmos, necesitará la cadena de conexión para este tutorial. Puede copiar la cadena de conexión desde el portal de Azure. En el portal de Azure, en la cuenta de base de datos de Cosmos, vaya a **configuración** > **cadena de conexión**y haga clic en el **copia** botón para copiar la conexión principal Cadena. 

En el tutorial, escriba la cadena de conexión en el script, como en el ejemplo siguiente:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Sin embargo, esto es **no recomienda** proyectos de una manera real. La clave de cuenta de almacenamiento es similar a la contraseña raíz para la cuenta de almacenamiento. Tenga siempre cuidado proteger la clave de cuenta de almacenamiento. Evitar la distribución a otros usuarios, codificar de forma rígida, o guardarlo en un archivo de texto sin formato sea accesible a otros usuarios. Puede volver a generar la clave mediante el Portal de Azure si cree que se han comprometido.

Las aplicaciones de una manera real, la mejor manera de mantener la cadena de conexión de almacenamiento está en un archivo de configuración. Para capturar la cadena de conexión de un archivo de configuración, puede hacer esto:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Con el Administrador de configuración de Azure es opcional. También puede utilizar una API como .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analizar la cadena de conexión

Para analizar la cadena de conexión, use:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Esto devuelve un `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Crear al cliente del servicio tabla

La `CloudTableClient` clase le permite recuperar tablas y entidades en el almacenamiento de tabla. Aquí es una manera de crear al cliente del servicio:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Ahora está listo para escribir código que lee datos de y escribe datos en el almacenamiento de tabla.

### <a name="create-a-table"></a>Creación de una tabla

En este ejemplo se muestra cómo crear una tabla si aún no existe:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Agregar una entidad a una tabla

Una entidad debe tener un tipo que hereda de `TableEntity`. Puede extender `TableEntity` en como desee, pero su tipo *debe* tiene un constructor sin parámetros. Solo las propiedades que tienen ambos `get` y `set` se almacenan en la tabla de Azure.

Partición de una entidad y la clave de fila identifican la entidad en la tabla. Entidades con la misma clave de partición se pueden consultar más rápido que aquellos con las claves de partición diferente, pero el uso de las claves de partición diversos permite para una mayor escalabilidad de operaciones en paralelo.

Este es un ejemplo de un `Customer` que usa el `lastName` como la clave de partición y el `firstName` como la clave de fila.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Ahora, agregue `Customer` a la tabla. Para ello, cree un `TableOperation` que se ejecuta en la tabla. En este caso, cree un `Insert` operación.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Insertar un lote de entidades

Puede insertar un lote de entidades en una tabla con una sola operación de escritura. Operaciones por lotes permiten combinar las operaciones en una sola ejecución, pero tienen algunas restricciones:

- Puede realizar actualizaciones, elimina y se inserta en la misma operación por lotes.
- Una operación por lotes puede incluir hasta 100 entidades.
- Todas las entidades de una operación por lotes deben tener la misma clave de partición.
- Aunque es posible realizar una consulta en una operación por lotes, debe ser la única operación en el lote.

Este es un código que combina dos inserciones en una operación por lotes:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Recuperar todas las entidades de una partición

Para consultar una tabla para todas las entidades de una partición, use un `TableQuery` objeto. En este caso, se filtran las entidades donde "Smith" es la clave de partición.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Ahora imprimir los resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Recuperar un intervalo de entidades en una partición

Si no desea consultar todas las entidades en una partición, puede especificar un intervalo combinando el filtro de clave de partición con un filtro de clave de fila. Aquí, se usa dos filtros para obtener todas las entidades de la partición "Smith" en la clave de fila (nombre) comienza con una letra anterior a "M" en el alfabeto.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Ahora imprimir los resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Recuperar una sola entidad

Puede escribir una consulta para recuperar una entidad única, específica. A continuación, use un `TableOperation` para especificar el cliente "Ben Smith". En lugar de una colección, se recibe un `Customer`. Especificar la clave de partición y la clave de fila en una consulta es la manera más rápida de recuperar una entidad única desde el servicio de la tabla.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Ahora imprimir los resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a>Reemplazar una entidad

Para actualizar una entidad, recuperar desde el servicio tabla, modificar el objeto de entidad y, a continuación, guarde los cambios a la tabla de servicio mediante un `Replace` operación. Esto hace que la entidad que se va a reemplazar completamente en el servidor, a menos que la entidad en el servidor ha cambiado desde que se recuperó, en cuyo caso se produce un error en la operación. Este error es evitar que la aplicación se ha sobrescrito accidentalmente cambios de otros orígenes.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Insertar o reemplazar una entidad

A veces, no sabe si existe una entidad en la tabla. Y si lo hace, ya no son necesarios los valores actuales almacenados en ella. Puede usar `InsertOrReplace` para crear la entidad o cámbielo si existe, independientemente de su estado.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Consultar un subconjunto de propiedades de entidad

Una consulta de tabla puede recuperar solo unas pocas propiedades de una entidad en lugar de todos ellos. Esta técnica, denominada proyección, puede mejorar el rendimiento, especialmente para entidades de gran tamaño. En este caso, se devuelven solo correo electrónico aborda el uso de `DynamicTableEntity` y `EntityResolver`. Tenga en cuenta que no se admite proyección en el emulador de almacenamiento local, por lo que este código se ejecuta sólo cuando se usa una cuenta en el servicio de la tabla.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Recuperar entidades en las páginas de forma asincrónica

Si está leyendo un gran número de entidades y desea procesarlas a medida que se recuperan en lugar de esperar a todos los que devuelven, puede utilizar una consulta segmentada. En este caso, se devuelven resultados en páginas mediante el uso de un flujo de trabajo asincrónico para que no la ejecución se bloquea mientras espera para un gran conjunto de resultados para devolver.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Ahora ejecute sincrónicamente este cálculo:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Eliminar una entidad

Puede eliminar una entidad después de que se han recuperado. Al igual que con la actualización de una entidad, esto se produce un error si la entidad ha cambiado desde que recuperó.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Eliminar una tabla

Puede eliminar una tabla de una cuenta de almacenamiento. Una tabla que se ha eliminado no estará disponible para volver a crearse durante un período de tiempo tras la eliminación.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Pasos siguientes

Ahora que conoce los fundamentos del almacenamiento de tabla, siga estos vínculos para obtener información acerca de las tareas más complejas de almacenamiento y la API de tabla de base de datos de Azure Cosmos.

- [Introducción a la API de la tabla de base de datos de Azure Cosmos](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Biblioteca de cliente de almacenamiento para la referencia de .NET](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Proveedor de tipos de almacenamiento de Azure](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog del equipo de almacenamiento de Azure](http://blogs.msdn.com/b/windowsazurestorage/)
- [Configurar cadenas de conexión](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Introducción a almacenamiento de tabla de Azure en .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
