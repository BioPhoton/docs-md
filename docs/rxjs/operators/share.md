---
kind: FunctionDeclaration
name: share
module: operators
---

# share

## description

Returns a new Observable that multicasts (shares) the original Observable. As long as there is at least one
Subscriber this Observable will be subscribed and emitting data. When all subscribers have unsubscribed it will
unsubscribe from the source Observable. Because the Observable is multicasting it makes the stream `hot`.
This is an alias for `multicast(() => new Subject()), refCount()`.

![](share.png)

## Example

Generate new multicast Observable from the source Observable value

```typescript
import { interval } from "rxjs";
import { share, map } from "rxjs/operators";

const source = interval(1000).pipe(
  map((x: number) => {
    console.log("Processing: ", x);
    return x * x;
  }),
  share()
);

source.subscribe((x) => console.log("subscription 1: ", x));
source.subscribe((x) => console.log("subscription 1: ", x));

// Logs:
// Processing:  0
// subscription 1:  0
// subscription 1:  0
// Processing:  1
// subscription 1:  1
// subscription 1:  1
// Processing:  2
// subscription 1:  4
// subscription 1:  4
// Processing:  3
// subscription 1:  9
// subscription 1:  9
// ... and so on
```

```ts
function share<T>(): MonoTypeOperatorFunction<T>;
```

[Link to repo](https://github.com/ReactiveX/rxjs/blob/master/src/internal/operators/share.ts#L60-L62)

## see

{@link api/index/function/interval}
{@link map}

## return

{Observable<T>} An Observable that upon connection causes the source Observable to emit items to its Observers.

## name

share
