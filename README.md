# TypeScript Cheat Sheet

> Follow my channel - [https://www.youtube.com/channel/UCvE-1xbTsOH_Kstd8PJdiXQ](https://www.youtube.com/@martialcoding3297)

## Table of Contents
- [String](#string)
- [Number](#number)
- [Boolean](#boolean)
- [Any](#any)
- [Array](#array)
- [Union](#union)
- [Number](#number)
- [Number](#number)
- [Number](#number)
- [Number](#number)
- [Number](#number)
- [Number](#number)
- [Number](#number)
- [Number](#number)
- [Number](#number)


## String
```typescript
const username: string = "Jon"; // String
console.log(username, typeof username);
```

## Number
```typescript
const num: number = 1; // Number
console.log(num, typeof num);
```

## Boolean
```typescript
const bool: boolean = false; // Boolean
console.log(bool, typeof bool);
```

## Any
```typescript
let anyVal: any = "Dex"; // Any
anyVal = 12;
console.log(anyVal, "Any");
```

## Array
> array of numbers
```typescript
let arr: number[] = [1, 2, 3, 4];
console.log(arr, "Array of Numbers");
```

## Union
> Union Types in TypeScript allow you to specify multiple possible types for a single variable or parameter.
> A union type is written as a vertical bar | separated list of types.
```typescript
let id: string | number = 22; // Union
id = "id_12";
console.log(id, "Union of string and number");
```

## Tuple
> A tuple type is another sort of Array type that knows exactly how many elements it contains,
>  and exactly which types it contains at specific positions.
```typescript
let tupleData: [number, string, boolean] = [1, "str", true];
console.log(tupleData, "Tuple");
```
> Array of Tuples
```typescript
let tupleArr: [number, string][] = [
  [1, "str"],
  [2, "str"],
];
console.log(tupleArr, "Tuple Array");
```

## Type Assertion
>Type assertions in TypeScript are a way to tell the compiler to treat a value as a specific type, regardless of its inferred type.
>There are two syntaxes for type assertions in TypeScript:
> - The “angle-bracket” syntax: <T>value
> - The “as” syntax: value as T
```typescript
// Type Assertion
let uid: any = 1;
let userId = <number>uid;
let userId2 = uid as number;
```
> as const is a type assertion in TypeScript that allows you to assert that an expression has a specific type,
> and that its value should be treated as a read-only value.
```typescript
const colors = ['red', 'green', 'blue'] as const;
```

## Enum
> Enums is not a type-level extension of JavaScript. It allow a developer to define a set of named constants.
> Using enums can make it easier to document intent, or create a set of distinct cases.
> TypeScript provides both numeric and string-based enums.
```typescript
enum Direction1 {
  UP,
  DOWN,
  LEFT,
  RIGHT,
}
console.log(Direction1, "Enum");

enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT",
}
```

## Typing Functions 
> In TypeScript, functions can be typed in a few different ways to indicate the input parameters and return type of the function.
```typescript
function isString(value: unknown): value is string {
  return typeof value === "string";
}

function example(x: unknown) {
  if (isString(x)) {
    // We can now call any 'string' method on 'x'.
    x.toUpperCase();
  } else {
    console.log(x);
  }
}
```

## Interface
> Interfaces in TypeScript provide a way to define a contract for a type, which includes a set of properties, methods, and events.
> It’s used to enforce a structure for an object, class, or function argument.
> Interfaces are not transpiled to JavaScript and are only used by TypeScript at compile-time for type-checking purposes.
```js
interface User {
  readonly id: number;
  name: string;
  age?: number; // optional
}

interface StringObject {
  [index: string]: string | number; // any index of object and its type
  defaultIndex1: string;
  defaultIndex2: string;
}

const stringObj: StringObject = {
  defaultIndex1: "Default value",
  defaultIndex2: "Default value 2",
  key1: "Key 1",
  key2: 12,
};
```

> Extending Interfaces
> In TypeScript, you can extend an interface by creating a new interface that inherits from the original interface using the “extends” keyword.
> The new interface can include additional properties, methods, or redefine the members of the original interface.
```typescript
interface Shape {
  width: number;
  height: number;
}

interface Rectangle extends Shape {
  sideLength: number;
}
```

## keyof Operator
> The keyof operator in TypeScript is used to get the union of keys from an object type. Here’s an example of how it can be used:
```typescript
interface StringObject {
  [index: string]: string | number; // any index of object and its type
  defaultIndex1: string;
  defaultIndex2: string;
}

const stringObj: StringObject = {
  defaultIndex1: "Default value",
  defaultIndex2: "Default value 2",
  key1: "Key 1",
  key2: 12,
};

for (const key in stringObj) {
  console.log(`${key}: ${stringObj[key as keyof StringObject]}`);
  console.log(`${key}: ${stringObj[key as keyof typeof stringObj]}`);
}

interface Account {
  name: string;
  age: number;
  location: string;
}

type AccountKeys = keyof Account; // "name" | "age" | "location"
const key: AccountKeys = "name";
```

## Class
> In TypeScript, a class is a blueprint for creating objects with specific properties and methods.
> Classes are a fundamental concept in object-oriented programming. 
```js
class Car {
  make: string;
  model: string;
  year: number;

  constructor(make: string, model: string, year: number) {
    this.make = make;
    this.model = model;
    this.year = year;
  }

  drive() {
    console.log(`Driving my ${this.year} ${this.make} ${this.model}`);
  }
}

class Person implements PersonInterface {
  id: number;
  name: string;

  constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }

  register(): string {
    return `${this.name} is now registered`;
  }
}

const brad = new Person(1, "Brad Traversy");
const mike = new Person(2, "Mike Jordan");

class Employee extends Person {
  position: string;

  constructor(id: number, name: string, position: string) {
    super(id, name);
    this.position = position;
  }
}

const emp = new Employee(3, "Shawn", "Developer");
```

## Array
> array of numbers
```js
let arr: number[] = [1, 2, 3, 4];
console.log(arr, "Array of Numbers");
```

## Array
> array of numbers
```js
let arr: number[] = [1, 2, 3, 4];
console.log(arr, "Array of Numbers");
```
