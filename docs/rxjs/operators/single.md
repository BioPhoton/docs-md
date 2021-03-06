---
kind: FunctionDeclaration
name: single
module: operators
---

# single

## description

Returns an observable that asserts that only one value is
emitted from the observable that matches the predicate. If no
predicate is provided, then it will assert that the observable
only emits one value.

In the event that the observable is empty, it will throw an
{@link EmptyError}.

In the event that two values are found that match the predicate,
or when there are two values emitted and no predicate, it will
throw a {@link SequenceError}

In the event that no values match the predicate, if one is provided,
it will throw a {@link NotFoundError}

## Example

Expect only name beginning with 'B':

```ts
import { of } from "rxjs";
import { single } from "rxjs/operators";

const source1 = of(
  { name: "Ben" },
  { name: "Tracy" },
  { name: "Laney" },
  { name: "Lily" }
);

source1
  .pipe(single((x) => x.name.startsWith("B")))
  .subscribe((x) => console.log(x));
// Emits "Ben"

const source2 = of(
  { name: "Ben" },
  { name: "Tracy" },
  { name: "Bradley" },
  { name: "Lincoln" }
);

source2
  .pipe(single((x) => x.name.startsWith("B")))
  .subscribe((x) => console.log(x));
// Error emitted: SequenceError('Too many values match')

const source3 = of(
  { name: "Laney" },
  { name: "Tracy" },
  { name: "Lily" },
  { name: "Lincoln" }
);

source3
  .pipe(single((x) => x.name.startsWith("B")))
  .subscribe((x) => console.log(x));
// Error emitted: NotFoundError('No values match')
```

```ts
function single<T>(
  predicate: (
    value: T,
    index: number,
    source: Observable<T>
  ) => boolean = defaultPredicate
): MonoTypeOperatorFunction<T>;
```

[Link to repo](https://github.com/ReactiveX/rxjs/blob/master/src/internal/operators/single.ts#L92-L96)

## see

{@link first}
{@link find}
{@link findIndex}
{@link elementAt}

## throws

{NotFoundError} Delivers an NotFoundError to the Observer's `error`
callback if the Observable completes before any `next` notification was sent.
{SequenceError} Delivers a SequenceError if more than one value is emitted that matches the
provided predicate. If no predicate is provided, will deliver a SequenceError if more
that one value comes from the source

## Parameters

| Name       | Type                                                          | Description                                                                          |
| ---------- | ------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| {Function} | ``                                                            | predicate - A predicate function to evaluate items emitted by the source Observable. |
| predicate  | `(value: T, index: number, source: Observable<T>) => boolean` |                                                                                      |

## return

{Observable<T>} An Observable that emits the single item emitted by the source Observable that matches
the predicate or `undefined` when no items match.
