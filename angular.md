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
