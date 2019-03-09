# Namespaces-Interfaces-Classes

- ## Namespaces

first-file.ts
```ts
namespace App {
    export const version = '0.1';
}
```
second-file.ts
```ts
///<reference path="first-file.ts"/>

console.info(App.version);
```
in terminal to compile
```
tsc --outFile sample.js Test.ts
```

- ## Interfaces

```ts
interface Point {
    readonly x: number;
    readonly y: number;
}

let p1: Point = { x: 10, y: 20 };
p1.x = 5; // error!
```
```ts
let a: number[] = [1, 2, 3, 4];
let ro: ReadonlyArray<number> = a;
ro[0] = 12; // error!
```
> as any
```ts
interface SquareConfig {
    color: string;
    width: number;
}

function createSquare(config: SquareConfig): void {
    // ...
    console.info('hello');
}

createSquare({} as any);
```
> Function Interface
```ts
interface SearchFunc {
    (source: string, subString: string): boolean;
}

let mySearch: SearchFunc;
mySearch = function(source: string, subString: string) {
    let result = source.search(subString);
    return result > -1;
}
```
> indexable type
```ts
interface StringArray {
    [index: number]: string;
}

let myArray: StringArray;
myArray = ["Bob", "Fred"];
```
> Class Types
```ts
interface ClockInterface {
    currentTime: Date;
    setTime(d: Date);
}

class Clock implements ClockInterface {
    currentTime: Date;
    setTime(d: Date) {
        this.currentTime = d;
    }
    constructor(h: number, m: number) { }
}
```
> ClockConstructor Interface for Constructor & ClockInterface Interface for class methods
```ts
interface ClockConstructor {
    new (hour: number, minute: number): ClockInterface;
}
interface ClockInterface {
    tick(): void;
}

class DigitalClock implements ClockInterface {
    constructor(h: number, m: string) { }
    tick() {
        console.log("beep beep");
    }
}

function create(ctor: ClockConstructor): DigitalClock {
    return new ctor(10, 20);
}
```
> Extending interfaces
```ts
interface Shape {
    color: string;
}

interface Square extends Shape {
    sideLength: number;
}

let square = <Square>{};
square.color = "blue";
square.sideLength = 10;
```
- ## Classes
> Class declaration creates two things: a type representing instances of the class and a constructor function. Because classes create types, you can use them in the same places you would be able to use interfaces.

> variable to use static methods of a class and to access to class 
```ts
class Greeter {
    static standardGreeting = "Hello, there";
    greeting: string;
    greet() {
        if (this.greeting) {
            return "Hello, " + this.greeting;
        }
        else {
            return Greeter.standardGreeting;
        }
    }
}

let greeter1: Greeter;
greeter1 = new Greeter();
console.log(greeter1.greet());

let greeterMaker: typeof Greeter = Greeter;
greeterMaker.standardGreeting = "Hey there!";

let greeter2: Greeter = new greeterMaker();
console.log(greeter2.greet());
```