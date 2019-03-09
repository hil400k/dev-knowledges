# Advanced Types
> All Members of all three types 
```ts
interface A {
    name: string;
}

interface B {
    age: number;
}

let a: A & B = {
    name: 'name',
    age: 11
}
```
> #### Union Types
> - A union type describes a value that can be one of several types. We use the vertical bar (|) to separate each type, so number | string | boolean is the type of a value that can be a number, a string, or a boolean.
> - If a value has the type A | B, we only know for certain that it has members that both A and B have. (About interfaces)

> #### Type Guards
```ts
function isFish(pet: Fish | Bird): pet is Fish {
    return (<Fish>pet).swim !== undefined;
}

// Both calls to 'swim' and 'fly' are now okay.

if (isFish(pet)) {
    pet.swim();
}
else {
    pet.fly();
}
```
> We can use ! to avoid explicit checking if null or undefined ↓
```ts
function fixed(name: string | null): string {
  function postfix(epithet: string) {
    return name!.charAt(0) + '.  the ' + epithet; // ok
  }
  name = name || "Bob";
  return postfix("great");
}
```
#### Types
```ts
type Name = string;
type NameResolver = () => string
type NameOrResolver = Name | NameResolver;
function getName(n: NameOrResolver): Name {
    return typeof n === "string" ? n : n();
}
```
```ts
type Tree<T> = {
    value: T;
    left: Tree<T>;
    right: Tree<T>;
}
```
#### Interfaces vs. Type Aliases
> Difference is that type aliases cannot be extended or implemented from. And Editor doc displaying for Alias return type and for Interface return type will differ.

---
> String Literal Types (Number can be too)
```ts
interface Interface {
    name: 'inter' | 'face'
}

const item: Interface = {
    name: 'name'
};
```
> Never type is for values that never occur
```ts
// Function returning never must have unreachable end point
function error(message: string): never {
    throw new Error(message);
}
```

