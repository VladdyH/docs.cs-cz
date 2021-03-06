---
title: Implementace odolných připojení Entity Framework Core SQL
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace odolných připojení Entity Framework Core SQL. Tato technika je zvlášť důležité při používání Azure SQL Database v cloudu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 0df375737c0e079baba426f3c97b95edcb9aca75
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127183"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementace odolných připojení Entity Framework Core SQL

Pro službu Azure SQL DB Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku. Ale je potřeba povolit strategie provádění Entity Framework pro každé připojení kontext databáze. Pokud chcete mít [odolnost připojení EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

Například následující kód na úrovni připojení EF Core umožňuje odolnost připojení SQL, které se zopakují, pokud se nepovede.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts

Pokud opakované pokusy jsou povolené v EF Core připojení, bude každé operace, které můžete provádět pomocí EF Core vlastní opakovatelné operace. Každý dotaz a každé volání SaveChanges bude zopakován jako celek, pokud dojde k přechodnému selhání.

Ale pokud váš kód zahájí transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je potřeba za jednotku považuje – všechno, co je uvnitř transakce se vrátila zpět, pokud dojde k chybě. Výjimku vypadat asi takto se zobrazí, pokud se pokusíte spustit transakci, při použití strategie provádění EF (zásady opakování) a zahrnují několik SaveChanges volání z více DbContexts v transakci.

> System.InvalidOperationException: Strategie provádění nakonfigurované "SqlServerRetryingExecutionStrategy" nepodporuje transakce iniciované uživatelem. Použití strategie provádění vrácený "DbContext.Database.CreateExecutionStrategy()" provádět všechny operace v transakci jako vyvolaly jednotky.

Řešením je vyvolat strategie provádění EF s všechno, co představuje delegáta, který je nutné spustit ručně. Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta. Například následující kód zobrazí, jak je implementován v aplikaci eShopOnContainers se dvěma více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a potom uložení ProductPriceChangedIntegrationEvent objektu, který je potřeba použít jiné DbContext.

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

Je první objekt DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu. Provedení akce potvrzení napříč více DbContexts použitím strategie provádění EF.

## <a name="additional-resources"></a>Další zdroje

-   **Odolnost připojení EF** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Odolnost připojení a zachycení příkazů s rozhraním Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **De la Torre Cesarovi. Pomocí odolné Entity Framework Core Sql připojení a transakce**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Předchozí](implement-retries-exponential-backoff.md)
>[další](explore-custom-http-call-retries-exponential-backoff.md)