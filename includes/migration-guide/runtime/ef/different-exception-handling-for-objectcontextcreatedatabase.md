### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="30769-101">Control de excepciones diferente para los métodos ObjectContext.CreateDatabase y DbProviderServices.CreateDatabase</span><span class="sxs-lookup"><span data-stu-id="30769-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

|   |   |
|---|---|
|<span data-ttu-id="30769-102">Detalles</span><span class="sxs-lookup"><span data-stu-id="30769-102">Details</span></span>|<span data-ttu-id="30769-103">A partir de .NET Framework 4.5, si se produce un error de creación de base de datos, los métodos <code>CreateDatabase</code> tratarán de eliminar la base de datos vacía.</span><span class="sxs-lookup"><span data-stu-id="30769-103">Beginning in .NET 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="30769-104">Si la operación se realiza correctamente, se propagará el elemento <xref:System.Data.SqlClient.SqlException?displayProperty=name> original (en lugar del elemento <xref:System.InvalidOperationException?displayProperty=name>, que ya se iniciaba siempre en .NET Framework 4.0).</span><span class="sxs-lookup"><span data-stu-id="30769-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=name> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=name> that was always thrown in .NET 4.0)</span></span>|
|<span data-ttu-id="30769-105">Sugerencia</span><span class="sxs-lookup"><span data-stu-id="30769-105">Suggestion</span></span>|<span data-ttu-id="30769-106">Cuando se detecta una excepción <xref:System.InvalidOperationException?displayProperty=name> al ejecutar <xref:System.Data.Objects.ObjectContext.CreateDatabase> o <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, ahora también se deben detectar las excepciones SQLExceptions.</span><span class="sxs-lookup"><span data-stu-id="30769-106">When catching an <xref:System.InvalidOperationException?displayProperty=name> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>|
|<span data-ttu-id="30769-107">Ámbito</span><span class="sxs-lookup"><span data-stu-id="30769-107">Scope</span></span>|<span data-ttu-id="30769-108">Secundaria</span><span class="sxs-lookup"><span data-stu-id="30769-108">Minor</span></span>|
|<span data-ttu-id="30769-109">Versión</span><span class="sxs-lookup"><span data-stu-id="30769-109">Version</span></span>|<span data-ttu-id="30769-110">4.5</span><span class="sxs-lookup"><span data-stu-id="30769-110">4.5</span></span>|
|<span data-ttu-id="30769-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="30769-111">Type</span></span>|<span data-ttu-id="30769-112">Tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="30769-112">Runtime</span></span>|
|<span data-ttu-id="30769-113">API afectadas</span><span class="sxs-lookup"><span data-stu-id="30769-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
