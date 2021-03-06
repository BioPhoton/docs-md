---
kind: ClassDeclaration
name: EntityDispatcherDefaultOptions
module: data
---

# EntityDispatcherDefaultOptions

## description

Default options for EntityDispatcher behavior
such as whether `add()` is optimistic or pessimistic by default.
An optimistic save modifies the collection immediately and before saving to the server.
A pessimistic save modifies the collection after the server confirms the save was successful.
This class initializes the defaults to the safest values.
Provide an alternative to change the defaults for all entity collections.

```ts
class EntityDispatcherDefaultOptions {
  optimisticAdd = false;
  optimisticDelete = true;
  optimisticUpdate = false;
  optimisticUpsert = false;
  optimisticSaveEntities = false;
}
```

[Link to repo](https://github.com/ngrx/platform/blob/master/modules/data/src/dispatchers/entity-dispatcher-default-options.ts#L10-L22)

## Properties

| Name                   | Type      | Description                                                                                                |
| ---------------------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| optimisticAdd          | `boolean` | True if added entities are saved optimistically; false if saved pessimistically.                           |
| optimisticDelete       | `boolean` | True if deleted entities are saved optimistically; false if saved pessimistically.                         |
| optimisticUpdate       | `boolean` | True if updated entities are saved optimistically; false if saved pessimistically.                         |
| optimisticUpsert       | `boolean` | True if upsert entities are saved optimistically; false if saved pessimistically.                          |
| optimisticSaveEntities | `boolean` | True if entities in a cache saveEntities request are saved optimistically; false if saved pessimistically. |
