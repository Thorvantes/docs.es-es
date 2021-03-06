---
title: Referencia de Entity SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: a114bf9b58da255f560564d3fedfee598adb22b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="entity-sql-reference"></a>Referencia de Entity SQL
Esta sección contiene temas de referencia de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. En este tema se resumen y agrupan el [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores por categoría.  
  
## <a name="arithmetic-operators"></a>Operadores aritméticos  
 Los operadores aritméticos realizan operaciones matemáticas con dos expresiones de uno o más tipos de datos numéricos. En la tabla siguiente se enumeran los operadores aritméticos de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Operador|Usar|  
|--------------|---------|  
|[+ (Agregar)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|Adición.|  
|"/ (Dividir)"|División.|  
|[% (Módulo)](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|Devuelve el resto de una división.|  
|[* (Multiplicar)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|Multiplicación.|  
|[- (Negativo)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|Negativo.|  
|[- (Restar)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|Resta.|  
  
## <a name="canonical-functions"></a>Funciones canónicas  
 Las funciones canónicas son admitidas por todos los proveedores de datos y pueden usarse en todas las tecnologías de creación de consultas. En la tabla siguiente se enumeran las funciones canónicas.  
  
|Función|Tipo|  
|--------------|----------|  
|[Funciones canónicas de agregado de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|Describe las funciones canónicas de agregado de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funciones canónicas matemáticas](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|Describe las funciones canónicas matemáticas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funciones canónicas de cadena](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|Describe las funciones canónicas de cadena de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funciones canónicas de fecha y hora](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Describe las funciones canónicas de fecha y hora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funciones canónicas bit a bit](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Describe las funciones canónicas bit a bit de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Otras funciones canónicas](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|Describe las funciones no clasificadas como funciones bit a bit, de fecha y hora, de cadena, matemáticas o de agregado.|  
  
## <a name="comparison-operators"></a>Operadores de comparación  
 Los operadores de comparación se definen para los tipos siguientes: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` y `DateTimeOffset`. La promoción de tipos implícita se produce para los operandos antes de que se aplique el operador de comparación. Los operadores de comparación siempre dan como resultados valores booleanos. Cuando al menos uno de los operandos es `null`, el resultado es `null`.  
  
 La igualdad y desigualdad se definen para cualquier tipo de objeto que tenga identidad, como el tipo `Boolean`. Los objetos no primitivos con identidad se consideran iguales si comparten la misma identidad. En la tabla siguiente se enumeran los operadores de comparación de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[= (Igual que)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|Compara la igualdad de dos expresiones.|  
|[> (Mayor que)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|Compara dos expresiones para determinar si la expresión de la izquierda tiene un valor mayor que el de la expresión de la derecha.|  
|[>= (Mayor o igual que)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|Compara dos expresiones para determinar si la expresión de la izquierda tiene un valor igual o mayor que el de la expresión de la derecha.|  
|[ES &AMP;#91;NO&AMP;#93; NULL](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|Determina si una expresión de consulta es nula.|  
|[< (Menor que)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|Compara dos expresiones para determinar si la expresión de la izquierda tiene un valor menor que el de la expresión de la derecha.|  
|[<= (Menor o igual que)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|Compara dos expresiones para determinar si la expresión izquierda tiene un valor igual o menor que el de la expresión derecha.|  
|[&AMP;#91;NO&AMP;#93; BETWEEN](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|Determina si el resultado de una expresión es un valor incluido en un intervalo especificado.|  
|[\!= (No igual a)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|Compara dos expresiones para determinar si la expresión de la izquierda no es igual que la expresión de la derecha.|  
|[&AMP;#91;NO&AMP;#93; COMO](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|Determina si una cadena de caracteres específica coincide con un patrón especificado.|  
  
## <a name="logical-and-case-expression-operators"></a>Operadores lógicos y de expresión CASE  
 Los operadores lógicos prueban la veracidad de una condición. La expresión CASE evalúa un conjunto de expresiones booleanas para determinar el resultado. En la tabla siguiente se enumeran los operadores lógicos y de expresión CASE.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[& & (AND lógico)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|AND lógico.|  
|[Operador (NOT lógico)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|NOT lógico.|  
|[&#124;&#124;(OR lógico)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|OR lógico.|  
|[CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|Evalúa un conjunto de expresiones booleanas para determinar el resultado.|  
|[THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|El resultado de un [cuando](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) cláusula cuando se evalúa como true.|  
  
## <a name="query-operators"></a>Operadores de consulta  
 Los operadores de consulta se usan para definir expresiones de consulta que devuelven datos de la entidad. En la tabla siguiente se enumeran los operadores de consulta.  
  
|Operador|Usar|  
|--------------|---------|  
|[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|Especifica la colección que se utiliza en [seleccione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrucciones.|  
|[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|Especifica los grupos en los objetos que son devueltos por una consulta ([seleccione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expresión que se van a colocar.|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|Devuelve una colección de valores de argumento que se proyecta a partir de la partición de grupo con la que está relacionado el agregado.|  
|[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|Especifica una condición de búsqueda para un grupo o agregado.|  
|[LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|Usar con el [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula para realizar la paginación física.|  
|[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|Especifica el criterio de ordenación que se usa en los objetos devueltos en una [seleccione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrucción.|  
|[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|Especifica los elementos de la proyección devueltos por una consulta.|  
|[SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|Usar con el [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula para realizar la paginación física.|  
|[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|Especifica que solo se devolverá el primer conjunto de filas del resultado de la consulta.|  
|[WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|Filtra de forma condicional los datos devueltos por una consulta.|  
  
## <a name="reference-operators"></a>Operadores de referencia  
 Una referencia es un puntero lógico (clave externa) a una entidad concreta en un conjunto de entidades específico. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] admite los operadores siguientes para construir, anular la construcción y navegar por las referencias.  
  
|Operador|Usar|  
|--------------|---------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|Crea referencias a una entidad en un conjunto de entidades.|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|Desreferencia un valor de referencia y genera el resultado de dicha desreferenciación.|  
|[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|Extrae la clave de una referencia o de una expresión de entidad.|  
|[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|Permite navegar por la relación de un tipo de entidad a otro|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|Devuelve una referencia a una instancia de entidad.|  
  
## <a name="set-operators"></a>Operadores de conjuntos  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] proporciona varias operaciones de conjuntos muy eficaces. Esto incluye operadores de conjuntos similares a los operadores de Transact-SQL como UNION, INTERSECT, EXCEPT y EXISTS. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] también es compatible con operadores para la eliminación de duplicados (SET), la prueba de pertenencia a un grupo (IN) y las combinaciones (UNION). En la tabla siguiente se enumeran los operadores de conjuntos de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Operador|Usar|  
|--------------|---------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|Extrae un elemento de una colección de varios valores.|  
|[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|Devuelve una colección de los valores distintos de la expresión de consulta situada a la izquierda del operando EXCEPT, que tampoco se devuelven en la expresión de consulta situada a la derecha del operando EXCEPT.|  
|[&AMP;#91;NO&AMP;#93; EXISTS](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|Determina si una colección está vacía.|  
|[FLATTEN](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|Convierte una colección de colecciones en una colección plana.|  
|[&AMP;#91;NO&AMP;#93; IN](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|Determina si un valor determinado coincide con algún valor de una colección.|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|Devuelve una colección de los valores distintos que devuelven las expresiones de consulta situadas a los lados izquierdo y derecho del operando INTERSECT.|  
|[OVERLAPS](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|Determina si dos colecciones tienen elementos comunes.|  
|[SET](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|Convierte una colección de objetos en un conjunto produciendo una colección nueva en la que se han quitado todos los elementos duplicados.|  
|[UNION](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|Combina los resultados de dos o más consultas en una sola colección.|  
  
## <a name="type-operators"></a>Operadores de tipo  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Proporciona operaciones que permiten al tipo de una expresión (valor) para construir, consultar y manipular. En la tabla siguiente se enumeran los operadores usados para trabajar con tipos.  
  
|Operador|Usar|  
|--------------|---------|  
|[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|Convierte una expresión de un tipo de datos a otro.|  
|[COLLECTION](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|Usar en un [función](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operación para declarar una colección de tipos de entidad o tipos complejos.|  
|[ES &AMP;#91;NO&AMP;#93; OF](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|Determina si el tipo de una expresión es del tipo especificado o uno de sus subtipos.|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|Devuelve una colección de objetos de una expresión de consulta de un tipo específico.|  
|[Constructor de tipos con nombre](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|Crea instancias de tipos de entidad o tipos complejos.|  
|[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|Crea una instancia de un conjunto múltiple a partir de una lista de valores.|  
|[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|Crea registros anónimos con tipos asignados estructuralmente a partir de uno o varios valores.|  
|[TREAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|Trata un objeto de un tipo base determinado como un objeto del tipo derivado especificado.|  
  
## <a name="other-operators"></a>Otros operadores  
 En la tabla siguiente se enumera otros [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores.  
  
|Operador|Usar|  
|--------------|---------|  
|[+ (Concatenación de cadenas)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|Concatena cadenas en [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[. (Acceso a miembros)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|Obtiene acceso al valor de una propiedad o campo de una instancia de un tipo de modelo conceptual estructural.|  
|[-- (Comentario)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|Incluye comentarios de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|Define una función insertada que se puede ejecutar en una consulta de Entity SQL.|  
  
## <a name="see-also"></a>Vea también  
 [Lenguaje Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
