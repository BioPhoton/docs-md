---
kind: FunctionDeclaration
name: ɵɵinvalidFactoryDep
module: core
---

# ɵɵinvalidFactoryDep

## description

Throws an error indicating that a factory function could not be generated by the compiler for a
particular class.

This instruction allows the actual error message to be optimized away when ngDevMode is turned
off, saving bytes of generated code while still providing a good experience in dev mode.

The name of the class is not mentioned here, but will be in the generated factory function name
and thus in the stack trace.

```ts
function ɵɵinvalidFactoryDep(index: number): never;
```

[Link to repo](https://github.com/timdeschryver/angular/blob/master/packages/core/src/di/injector_compatibility.ts#L131-L141)

## codeGenApi

## Parameters

| Name  | Type     | Description |
| ----- | -------- | ----------- |
| index | `number` |             |
