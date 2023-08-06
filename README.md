# TypeScript Cheat Sheet

> Follow my channel - [https://www.youtube.com/channel/UCvE-1xbTsOH_Kstd8PJdiXQ](https://www.youtube.com/@martialcoding3297)

## Table of Contents
- [String](#string)
- [Number](#number)
- [Boolean](#boolean)
- [Any](#any)
- [Array](#array)
- [Union](#union)
- [Tuple](#tuple)
- [Type Assertion](#type-assertion)
- [Enum](#enum)
- [Typing Functions](#typing-functions)
- [Interface](#interface)
- [keyof Operator](#keyof-operator)
- [Class](#class)
- [instanceOf operator](#instanceof-operator)
- [Never](#never)
- [Intersection Types](#intersection-types)
- [Abstract Classes](#abstract-classes)
- [Generics](#generics)
- [Partial](#partial)
- [Pick](#pick)
- [Omit](#omit)
- [Readonly](#readonly)
- [Record](#number)
- [Satisfies](#satisfies)
- [Exclude](#exclude)
- [Extract](#extract)
- [Non Nullable](#non-nullable)
- [Parameters](#parameters)
- [ReturnType](#returntype)
- [Instance Type](#instance-type)
- [Awaited](#awaited)
- [Mapped Types](#mapped-types)
- [Namespace](#namespace)
- [Multi File Namespaces](#multi-file-namespaces)
- [Ambient Modules](#ambient-modules)
- [Namespace Augmentation](#namespace-augmentation)
- [Declare](#declare)
- [Conditional Types](#conditional-types)


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
```typescript
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
```typescript
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

## Type
```typescript
type Streams = "salary" | "employ";
type Incomes = Record<Streams, number | string>;

const monthlyIncomes: Incomes = {
  salary: 500, // number
  employ: "some string", // string
};
```

## instanceOf operator
> The instanceof operator is a way to narrow down the type of a variable.
> It is used to check if an object is an instance of a class, interface, or type.
```typescript
class Bird {
  fly() {
    console.log("flying...");
  }
  layEggs() {
    console.log("laying eggs...");
  }
}

const pet = new Bird();

// instanceof
if (pet instanceof Bird) {
  pet.fly();
} else {
  console.log("pet is not a bird");
}
```

## Never
> The never type represents the type of values that never occur.
> For instance, never is the return type for a function expression or an arrow function expression
> that always throws an exception or one that never returns.
> Variables also acquire the type never when narrowed by any type guards that can never be true.
> The never type is a subtype of, and assignable to, every type; however, no type is a subtype of, or assignable to, never (except never itself).
> Even any isn’t assignable to never.
```typescript
// Function returning never must not have a reachable end point
function error(message: string): never {
  throw new Error(message);
}

// Inferred return type is never
function fail() {
  return error("Something failed");
}
```

## Intersection Types
> An intersection type creates a new type by combining multiple existing types.
> The new type has all features of the existing types. To combine types, you use the & operator as follows:
```typescript
type UserPerson = User & Person;
// The UserPerson will have all properties from both User and Person.
// Note that the union type uses the | operator that defines a variable which can hold a value of either typeA or typeB
```

## Abstract Classes
```typescript
abstract class Animal {
  abstract makeSound(): void;

  move(): void {
    console.log("moving...");
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log("bark");
  }
}
```

## Generics
> Generics in TypeScript are a way to write code that can work with multiple data types, instead of being limited to a single data type.
> Generics allow you to write functions, classes, and interfaces that take one or more type parameters,
> which act as placeholders for the actual data types that will be used when the function, class, or interface is used.
```typescript
function getArray<T>(items: T[]): T[] {
  return new Array().concat(items);
}

let numArray = getArray<number>([1, 2, 3, 4]);
let strArray = getArray<string>(["brad", "John", "Jill"]);

function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>("Hello"); // type of output will be 'string'

interface Lengthwise {
  length: number;
}

function loggingIdentity<T extends Lengthwise>(arg: T): T {
  // Now we know it has a .length property, so no more error
  console.log(arg.length);

  return arg;
}

loggingIdentity(3); // Error, number doesn't have a .length property
loggingIdentity({ length: 10, value: 3 }); // OK


class GenericNumber<T> {
  zeroValue: T;
  add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function (x, y) {
  return x + y;
};
```

## Partial
> The Partial type in TypeScript allows you to make all properties of a type optional.
> This is useful when you need to create an object with only a subset of the properties of an existing type.
```typescript
interface Person1 {
  name: string;
  age: number;
  email: string;
}

function createUser(user: Partial<Person1>): Person1 {
  return {
    name: "John Doe",
    age: 30,
    email: "john.doe@example.com",
    ...user,
  };
}

const newUser = createUser({ name: "Jane Doe" });

console.log(newUser);
// Output: { name: 'Jane Doe', age: 30, email: 'john.doe@example.com' }
```

## Pick
> Pick constructs a type by picking the set of properties Keys (string literal or union of string literals) from Type.
```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

type TodoPreview = Pick<Todo, "title" | "completed">;

const todo: TodoPreview = {
  title: "Clean room",
  completed: false,
};
```

## Omit
> Omit constructs a type by picking all properties from Type and then removing Keys (string literal or union of string literals).
```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
  createdAt: number;
}

type TodoPreview1 = Omit<Todo, "description">;

const todo1: TodoPreview1 = {
  title: "Clean room",
  completed: false,
  createdAt: 1615544252770,
};

type TodoInfo = Omit<Todo, "completed" | "createdAt">;

const todoInfo: TodoInfo = {
  title: "Pick up kids",
  description: "Kindergarten closes at 5pm",
};
```

## Readonly
> Readonly constructs a type with all properties of Type set to readonly, meaning the properties of the constructed type cannot be reassigned.
```typescript
interface ReadOnlyTodo {
  title: string;
}

const readOnlyTodo: Readonly<ReadOnlyTodo> = {
  title: "Delete inactive users",
};

// Cannot assign to 'title' because it is a read-only property.
// readOnlyTodo.title = 'Hello';
```

## Record
> Record constructs an object type whose property keys are Keys and whose property values are Type.
> This utility can be used to map the properties of a type to another type.
```typescript
interface Values {
  age: number;
  name: string;
}

type Keys = "key1" | "key2" | "key3";

const cats: Record<Keys, Values> = {
  key1: { age: 10, name: "Dexter" },
  key2: { age: 5, name: "Jon Snow" },
  key3: { age: 16, name: "Logan" },
};
```

## satisfies
> The satisfies operator lets us validate that the type of an expression matches some type, without changing the resulting type of that expression.
> As an example, we could use satisfies to validate that all the properties of palette are compatible with string | number[]:
```typescript
type Colors = "red" | "green" | "blue";
type RGB = [red: number, green: number, blue: number];

const palette = {
  red: [255, 0, 0],
  green: "#00ff00",
  blue: [0, 0, 255],
  //  ~~~~ The typo is now caught!
} satisfies Record<Colors, string | RGB>;

// Both of these methods are still accessible!
const redComponent = palette.red[0];
const greenNormalized = palette.green.toUpperCase();
```

## Exclude
> Exclude constructs a type by excluding from UnionType all union members that are assignable to ExcludedMembers.
```typescript
type T0 = Exclude<"a" | "b" | "c", "a">; // "b" | "c"
type T1 = Exclude<"a" | "b" | "c", "a" | "b">; // "c"
type T2 = Exclude<string | number | (() => void), Function>; // string | number
```

## Extract
> Extract constructs a type by extracting from Type all union members that are assignable to Union.
```typescript
type T3 = Extract<"a" | "b" | "c", "a" | "f">;
// type T0 will be equal to "a"
```

## Non Nullable
> Non-Nullable constructs a type by excluding null and undefined from Type.
```typescript
type T4 = NonNullable<string | number | undefined>;
// type T4 = string | number
type T5 = NonNullable<string[] | null | undefined>;
// type T5 = string[]
```

## Parameters
> Parameters constructs a tuple type from the types used in the parameters of a function type Type.
```typescript
type T6 = Parameters<() => string>;
// type T6 = []

type T7 = Parameters<(s: string) => void>;
// type T7 = [s: string]

type T8 = Parameters<<T>(arg: T) => T>;
// type T8 = [arg: unknown]

declare function f1(arg: { a: number; b: string }): void;
type T9 = Parameters<typeof f1>;
// type T9 = [arg: {
//     a: number;
//     b: string;
// }]

type T10 = Parameters<any>;
// type T10 = unknown[]

type T11 = Parameters<never>;
// type T11 = never
```

## ReturnType
> Return type constructs a type consisting of the return type of function Type.
```typescript
type T12 = ReturnType<() => string>;
// type T12 = string

type T13 = ReturnType<(s: string) => void>;
// type T13 = void

type T14 = ReturnType<<T>() => T>;
// type T14 = unknown

type T15 = ReturnType<<T extends U, U extends number[]>() => T>;
// type T15 = number[]

declare function f1(): { a: number; b: string };
type T16 = ReturnType<typeof f1>;
// type T16 = {
//     a: number;
//     b: string;
// }

type T17 = ReturnType<any>;
// type T17 = any

type T18 = ReturnType<never>;
// type T18 = never
```

## InstanceType
> This type constructs a type consisting of the instance type of a constructor function in Type.
```typescript
class C {
  x = 0;
  y = 0;
}

type T19 = InstanceType<typeof C>;
// type T19 = C

type T20 = InstanceType<any>;
// type T20 = any

type T21 = InstanceType<never>;
// type T21 = never
```

## Awaited
> This type is meant to model operations like await in async functions, or the .then() method on
> Promises - specifically, the way that they recursively unwrap Promises.
```typescript
type A = Awaited<Promise<string>>;
// type A = string

type B = Awaited<Promise<Promise<number>>>;
// type B = number

type D = Awaited<boolean | Promise<number>>;
// type D = number | boolean
```

## Mapped Types
> Mapped types in TypeScript are a way to create a new type based on an existing type,
> where each property of the existing type is transformed in some way.
> Mapped types are declared using a combination of the keyof operator and a type that maps each property of the existing type to a new property type.
```typescript
type OnlyBooleansAndString = {
  [key: string]: boolean | string;
};

const onlyBooleansAndString: OnlyBooleansAndString = {
  key1: true,
  key2: "string value",
};

// A mapped type is a generic type which uses a union of PropertyKeys (frequently created via a keyof) to iterate through keys to create a type:
type OptionsFlags<Type> = {
  [Property in keyof Type]: boolean;
};

type Features = {
  darkMode: () => void;
  newUserProfile: () => void;
};

type FeatureOptions = OptionsFlags<Features>;
// type FeatureOptions = {
//   darkMode: boolean;
//   newUserProfile: boolean;
// }

// For example, the following is a mapped type that takes an object type and creates a new type with all properties of the original type but with their type changed to readonly:
type MappedTypeWithNewProperties<Type> = {
  readonly [Property in keyof Type]: Type[Property];
};

// You can leverage features like template literal types to create new property names from prior ones:

type Getters<Type> = {
  [Property in keyof Type as `get${Capitalize<
    string & Property
  >}`]: () => Type[Property];
};

interface Person {
  name: string;
  age: number;
  location: string;
}

type LazyPerson = Getters<Person>;
// type LazyPerson = {
//   getName: () => string;
//   getAge: () => number;
//   getLocation: () => string;
// }

// You can filter out keys by producing never via a conditional type:
// Remove the 'kind' property
type RemoveKindField<Type> = {
  [Property in keyof Type as Exclude<Property, "kind">]: Type[Property];
};

interface Circle {
  kind: "circle";
  radius: number;
}

type KindlessCircle = RemoveKindField<Circle>;

// You can map over arbitrary unions, not just unions of string | number | symbol, but unions of any type:
type EventConfig<Events extends { kind: string }> = {
  [E in Events as E["kind"]]: (event: E) => void;
};

type Square = { kind: "square"; x: number; y: number };
type Disc = { kind: "disc"; radius: number };

type UnionSquareDisc = EventConfig<Square | Circle>;

// type UnionSquareDisc = {
//     square: (event: Square) => void;
//     circle: (event: Circle) => void;
// }
```

## Namespace
> In TypeScript, namespaces are used to organize and share code across multiple files.
> Namespaces allow you to group related functionality into a single unit and prevent naming conflicts.
```typescript
namespace Validation {
  export interface StringValidator {
    isAcceptable(s: string): boolean;
  }
  const lettersRegexp = /^[A-Za-z]+$/;
  const numberRegexp = /^[0-9]+$/;
  export class LettersOnlyValidator implements StringValidator {
    isAcceptable(s: string) {
      return lettersRegexp.test(s);
    }
  }
  export class ZipCodeValidator implements StringValidator {
    isAcceptable(s: string) {
      return s.length === 5 && numberRegexp.test(s);
    }
  }
}
```

## Multi-file namespaces
> Here, we’ll split our Validation namespace across many files. Even though the files are separate,
> they can each contribute to the same namespace and can be consumed as if they were all defined in one place.
> Because there are dependencies between files, we’ll add reference tags to tell the compiler about the relationships between the files.
> Our test code is otherwise unchanged.
```typescript
// Validation.ts
namespace Validation {
  export interface StringValidator {
    isAcceptable(s: string): boolean;
  }
}

// LettersOnlyValidator1.ts
/// <reference path="Validation.ts" />
namespace Validation {
  const lettersRegexp = /^[A-Za-z]+$/;
  export class LettersOnlyValidator1 implements StringValidator {
    isAcceptable(s: string) {
      return lettersRegexp.test(s);
    }
  }
}

// ZipCodeValidator1.ts
/// <reference path="Validation.ts" />
namespace Validation {
  const numberRegexp = /^[0-9]+$/;
  export class ZipCodeValidator1 implements StringValidator {
    isAcceptable(s: string) {
      return s.length === 5 && numberRegexp.test(s);
    }
  }
}
// Test.ts
/// <reference path="Validation.ts" />
/// <reference path="LettersOnlyValidator1.ts" />
/// <reference path="ZipCodeValidator1.ts" />
// Some samples to try
let strings = ["Hello", "98052", "101"];
// Validators to use
let validators: { [s: string]: Validation.StringValidator } = {};
validators["ZIP code"] = new Validation.ZipCodeValidator1();
validators["Letters only"] = new Validation.LettersOnlyValidator1();
// Show whether each string passed each validator
for (let s of strings) {
  for (let name in validators) {
    console.log(
      `"${s}" - ${
        validators[name].isAcceptable(s) ? "matches" : "does not match"
      } ${name}`
    );
  }
}
```

## Ambient Modules
> Ambient modules in TypeScript are used to declare external modules or third-party libraries in a TypeScript program.
> Ambient modules provide type information for modules that have no TypeScript declarations, but are available in the global scope.
```typescript
// node.d.ts
declare module "url";
import * as URL from "url";
let myUrl = URL.parse("https://www.typescriptlang.org");
```

##  Namespace Augmentation
> In TypeScript, namespace augmentation is a way to extend or modify existing namespaces.
> This is useful when you want to add new functionality to existing namespaces or to fix missing or incorrect declarations in third-party libraries.
```typescript
// myModule.d.ts
declare namespace MyModule {
  export interface MyModule {
    newFunction(): void;
  }
}

// main.ts
/// <reference path="myModule.d.ts" />
namespace MyModule {
  export class MyModule {
    public newFunction() {
      console.log("I am a new function in MyModule!");
    }
  }
}

const obj = new MyModule.MyModule();
obj.newFunction(); // Output: "I am a new function in MyModule!"
```

## Declare
> Using the declare keyword to do global augmentation. A developer can also use the declare keyword to add declarations to the global scope.  
```typescript
declare global {
  interface String {
    toSmallString(): string;
  }
}

String.prototype.toSmallString = (): string => {
  // implementation.
  return "";
};
```

## Conditional Types
> At the heart of most useful programs, we have to make decisions based on input. JavaScript programs are no different,
> but given the fact that values can be easily introspected, those decisions are also based on the types of the inputs.
> Conditional types help describe the relation between the types of inputs and outputs.
```typescript
interface Animal {
  live(): void;
}
interface Dog extends Animal {
  woof(): void;
}

type Example1 = Dog extends Animal ? number : string;
// type Example1 = number

type Example2 = RegExp extends Animal ? number : string;
// type Example2 = string

// Conditional types take a form that looks a little like conditional expressions (condition ? trueExpression : falseExpression) in JavaScript:
// SomeType extends OtherType ? TrueType : FalseType;

type MessageOf<T> = T extends { message: unknown } ? T["message"] : never;

interface Email {
  message: string;
}

interface Dog {
  bark(): void;
}

type EmailMessageContents = MessageOf<Email>;
// type EmailMessageContents = string

type DogMessageContents = MessageOf<Dog>;
// type DogMessageContents = never

// Conditional types provide us with a way to infer from types we compare against in the true branch using the infer keyword. For example, we could have inferred the element type in Flatten instead of fetching it out “manually” with an indexed access type:
type Flatten<Type> = Type extends Array<infer Item> ? Item : Type;

// If we plug a union type into ToArray, then the conditional type will be applied to each member of that union.
type ToArray<Type> = Type extends any ? Type[] : never;

type StrArrOrNumArr = ToArray<string | number>;
// type StrArrOrNumArr = string[] | number[]
```
