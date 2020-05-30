> ZoneJS Patches few browser low level APIs (DOM events, ajax, setTimeout, setInterval)

> By default Angular checks if the value of template has changed & takes into account only props that are 
> used within a template
> (no deep comparison)

>When using OnPush detectors, then the framework will check an OnPush component when any of its input
> properties changes (check by reference), when it fires an event, or when an Observable fires an event

> Angular always running change detection twice. In production mode change detection is only run once.

---
### Angular Lifecycle
Here are the lifecycle hooks available, in the order in which they are invoked:
> ngOnChanges: Called every time a data-bound input property changes (<component [dataBoundInputProp] />). It’s called a first time before the ngOnInit hook. The hook receives a SimpleChanges object that contains the previous and current values for the data-bound inputs properties. This hook gets called often, so it’s a good idea to limit the amount of processing it does.

> ngOnInit: Called once upon initialization of the component.

> ngDoCheck: Use this hook instead of ngOnChanges for changes that Angular doesn’t detect. It gets called at every change detection cycle, so keeping what it does to a minimum is important for performance.

> ngAfterContentInit: Called after content is projected in the component.

> ngAfterContentChecked: Called after the projected content is checked.

> ngAfterViewInit: Called after a component’s view or child view is initialized.

> ngAfterViewChecked: Called after a component’s view or child view is checked.

> ngOnDestroy: Called once when the component is destroyed and a good hook to use to cleanup and unsubscribe from observables.
---

> Using onPush strategy allows to react only on input reference changes instead of reaction to mutating an object.

> OnPush reacts to reference (Object,Array) or values changes (string,number,boolean); to async pipe; to changeDetector.detectChasnges; to DOM event handlers

> Default change detection strategy: When the state of one of the components changes, no matter where it is in the tree, a change detection pass is triggered for the whole tree (all app). This happens because Angular scans for changes from the top component node, all the way to the bottom leaves of the tree. 

---
### Rx.js
- shareRaplay is an operator that is used to not create separate stream for each subscriber.
It is to use shared one. Useful to handle 2 async pipes for one request. In result app will send only one.
- `from([1,2,3,4]).subscribe(val => console.log(val));` Output: 4 separate 1,2,3,4
- `of([1,2,3,4]).subscribe(val => console.log(val));` Output: array [1,2,3,4]
- `mergeAll`
```ts
const firstSource = of(1);
const secondSource = val => of(`asyncToolPrefix: ${val}`);

const example = firstSource.pipe(
  map(val => secondSource(val)),
  mergeAll()
);

const subscribe = example.subscribe(val => console.log(val));
```
Output: `asyncToolPrefix: 1`. It would log an observable if mergeAll wasn't used.


### Map differences:

- `map` returns not an observable
- `switchMap` returns observable

### Hot and Cold Observables
**Cold observable produces separate stream for each subscriber.** Producers created by the code: `of, from, timer, interval`
**Hot Observables share stream for each subsciber.**
Hot observables producers are independant and external. For example `fromEvent` of `WebSockets` messages.

#### Angular 9 new features
- Ivy compiller by default
- improved debuggeing
- i18n improved
- unit-testing faster

### forkJoin & combineLatest
- forkJoin: waits until last observable completes (completes!!!) and then returns array of value. `forkJoin([obs1, obs2, obs3])` all this
observables runs in parallel;
- combineLatest: returns new value every time new `combineLatest([obs1, obs2, obs3])` obs do. 
You won’t see the result until each of the streams have emitted at least one value.

```ts
const $1 = interval(1000).pipe(take(3));
const $2 = interval(2000).pipe(take(3));

combineLatest([$1, $2]).subscribe((data) => {
  console.info(data);
})
```
output:
```
[1,0]
[2,0]
[2,1]
[2,2]
```
Replace forkjoin with combineLatest will return `[2, 2]`

### filter & takeWhile

```ts
const $1 = from([1,2,3,1,2]);
$1.pipe(takeWhile(val => val < 2)).subscribe(console.info);
$1.pipe(filter(val => val < 2)).subscribe(console.info);
```
output: takewhile: 1; filter 1,1
takeWhile completes after first wrong value

---

### ngModule
declarations: The components, directives, and pipes that belong to this NgModule.

exports: The subset of declarations that should be visible and usable in the component templates of other NgModules.

imports: Other modules whose exported classes are needed by component templates declared in this NgModule.

providers: Creators of services that this NgModule contributes to the global collection of services; they become accessible in all parts of the app. (You can also specify providers at the component level, which is often preferred.)

bootstrap: The main application view, called the root component, which hosts all other app views. Only the root NgModule should set the bootstrap property.

---

### Custom Pipe

ngModule
```angular2
  declarations: [
    CustomPipe
  ],
```
pipe declaration
```angular2
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'customPipe'
})
export class CustomPipe implements PipeTransform {
  transform(value: any, ...args): any {
    return `${value.toString()} ${args[0]}`;
  }
}
```
usage
```html
<div class="col-content">
  {{item.text | customPipe: 'piped'}}
</div>
```
