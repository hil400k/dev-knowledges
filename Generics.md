# Generics

```ts
function someFunc<T>(param: T): T {
  return param;
}

let func: <T>(param: T) => T = someFunc;
let func2: {<T>(param: T): T} = someFunc;
```

## Generic Classes

```ts
class GenericNumber<T> {
    zeroValue: T;
    add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function(x, y) { return x + y; };
```

> To have possibility to access .length ptop

```ts
interface Lengthwise {
    length: number;
}

function LoggingIdentity<T extends Lengthwise>(arg: T): T {
    console.info(arg.length);

    return arg;
}
```
## Generic Constrains

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K) {
    return obj[key];
}

let x = { a: 1, b: 2, c: 3, d: 4 };

getProperty(x, "a"); // okay
getProperty(x, "m"); // error: Argument of type 'm' isn't assignable to 'a' | 'b' | 'c' | 'd'.

```
```ts
function create<T>(c: { new(): T }): T {
    return new c;
}

class Boss {
    go() {

    }
}

create(Boss).go();
```