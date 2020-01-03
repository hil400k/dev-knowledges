> ZoneJS Patches few browser low level APIs (DOM events, ajax, setTimeout, setInterval)

> By default Angular checks if the value of template has changed & takes into account only props that are 
> used within a template
> (no deep comparison)

>When using OnPush detectors, then the framework will check an OnPush component when any of its input
> properties changes (check by reference), when it fires an event, or when an Observable fires an event

> Angular always running change detection twice. In production mode change detection is only run once.

>
