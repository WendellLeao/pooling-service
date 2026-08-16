# Changelog

All notable changes to this package are documented in this file.

## [1.0.0] - 2026-08-16

### Added

- Initial release: `PoolingService` with `TryGetObjectFromPool` and `ReleaseObjectToPool`, backed by `UnityEngine.Pool.ObjectPool`.
- `PoolData` and `PoolDataCollection` ScriptableObjects for configuring pools.
- `IPooledObject` and `IPoolingService` abstractions.
