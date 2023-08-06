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

## Array
> array of numbers
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

## Array
> array of numbers
```js
let arr: number[] = [1, 2, 3, 4];
console.log(arr, "Array of Numbers");
```
