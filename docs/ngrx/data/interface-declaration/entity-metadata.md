---
kind: InterfaceDeclaration
name: EntityMetadata
module: data
---

# EntityMetadata

```ts
interface EntityMetadata<T = any, S extends object = {}> {
  entityName: string;
  entityDispatcherOptions?: Partial<EntityDispatcherDefaultOptions>;
  filterFn?: EntityFilterFn<T>;
  noChangeTracking?: boolean;
  selectId?: IdSelector<T>;
  sortComparer?: false | Comparer<T>;
  additionalCollectionState?: S;
}
```

[Link to repo](https://github.com/ngrx/platform/blob/master/modules/data/src/entity-metadata/entity-metadata.ts#L13-L21)

## Properties

| Name                      | Type                                      | Description |
| ------------------------- | ----------------------------------------- | ----------- |
| entityName                | `string`                                  |             |
| entityDispatcherOptions   | `Partial<EntityDispatcherDefaultOptions>` |             |
| filterFn                  | `EntityFilterFn<T>`                       |             |
| noChangeTracking          | `boolean`                                 |             |
| selectId                  | `any`                                     |             |
| sortComparer              | `any`                                     |             |
| additionalCollectionState | `S`                                       |             |
