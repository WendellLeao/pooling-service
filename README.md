# Pooling Service

Generic component-based object pooling service for Unity projects.

## Installation

Add the package via the Unity Package Manager using a git URL:

```
https://github.com/WendellLeao/pooling-service.git
```

To pin a specific version, append `#v1.0.0` (or any tag) to the URL.

Depends on [WendellLeao.ServiceLocator](https://github.com/WendellLeao/service-locator).

## Usage

1. Create a `PoolData` asset per prefab (`Create > WendellLeao > Pooling > Pool Data`), setting its `id`, `prefab`, and pool sizing.
2. Create a `PoolDataCollection` asset and assign the `PoolData` entries to it.
3. Add a `PoolingService` component to a persistent GameObject and assign the `PoolDataCollection`.
4. Implement `IPooledObject` on any prefab you want to pool.

```csharp
using WendellLeao.Pooling;
using WendellLeao.ServiceLocator;

IPoolingService poolingService = Locator.Get<IPoolingService>();

if (poolingService.TryGetObjectFromPool(poolId: "Bullet", parent: null, out BulletPickup bullet))
{
    // use bullet
}

poolingService.ReleaseObjectToPool(bullet);
```

`PoolingService` registers itself as `IPoolingService` on `Awake` and unregisters on `OnDestroy`.
