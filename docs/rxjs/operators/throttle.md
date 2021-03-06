---
kind: FunctionDeclaration
name: throttle
module: operators
---

# throttle

## description

Emits a value from the source Observable, then ignores subsequent source
values for a duration determined by another Observable, then repeats this
process.

<span class="informal">It's like {@link throttleTime}, but the silencing
duration is determined by a second Observable.</span>

![](throttle.png)

`throttle` emits the source Observable values on the output Observable
when its internal timer is disabled, and ignores source values when the timer
is enabled. Initially, the timer is disabled. As soon as the first source
value arrives, it is forwarded to the output Observable, and then the timer
is enabled by calling the `durationSelector` function with the source value,
which returns the "duration" Observable. When the duration Observable emits a
value or completes, the timer is disabled, and this process repeats for the
next source value.

## Example

Emit clicks at a rate of at most one click per second

```ts
import { fromEvent, interval } from "rxjs";
import { throttle } from "rxjs/operators";

const clicks = fromEvent(document, "click");
const result = clicks.pipe(throttle((ev) => interval(1000)));
result.subscribe((x) => console.log(x));
```

```ts
function throttle<T>(
  durationSelector: (value: T) => SubscribableOrPromise<any>,
  config: ThrottleConfig = defaultThrottleConfig
): MonoTypeOperatorFunction<T>;
```

[Link to repo](https://github.com/ReactiveX/rxjs/blob/master/src/internal/operators/throttle.ts#L66-L69)

## see

{@link audit}
{@link debounce}
{@link delayWhen}
{@link sample}
{@link throttleTime}

## Parameters

| Name             | Type                                       | Description                                                                         |
| ---------------- | ------------------------------------------ | ----------------------------------------------------------------------------------- |
| {function(value: | ``                                         | T): SubscribableOrPromise} durationSelector A function                              |
| {Object}         | ``                                         | config a configuration object to define `leading` and `trailing` behavior. Defaults |
| durationSelector | `(value: T) => SubscribableOrPromise<any>` |                                                                                     |
| config           | `ThrottleConfig`                           |                                                                                     |

## return

{Observable<T>} An Observable that performs the throttle operation to
limit the rate of emissions from the source.

## name

throttle
