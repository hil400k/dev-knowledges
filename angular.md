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
- shareRaplay is an operator that is used to not create separate stream for eahc subscriber.
It is to use shared one. Useful to handle 2 async pipes for one request. In result app will send only one.
