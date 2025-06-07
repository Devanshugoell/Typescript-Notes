## Why Use TypeScript?

TypeScript helps catch many potential bugs **during development** through static type checking, even before the code runs. This reduces the chances of runtime errors and makes the codebase more reliable.

### Example

#### JavaScript:

```js
function add(a, b) {
  return a + b;
}

add("5", 10); // ✅ No error, but result is "510" (string), which is incorrect
```

In JavaScript, this won't throw any error, but it gives the wrong result — which can cause major problems in large-scale applications.

#### Typescript:

```ts
function add(a: number, b: number): number {
  return a + b;
}

add("5", 10); // ❌ Error: Argument of type 'string' is not assignable to parameter of type 'number'
```

## How to Use TypeScript with Objects

```ts
interface Product {
  id: number;
  title: string;
  price: number;
}

const product: Product = {
  id: 1,
  title: "Laptop",
  price: 1500,
};
```

## How to Use TypeScript with Array

```ts
const mixedArray: (number | string)[] = [1, "hello", 42, "world"];
```

## What is `enum` in TypeScript?

An `enum` (enumeration) is a special TypeScript feature that lets you define a set of **named constants** — making your code more **readable and manageable**.

---

### 🔢 Custom Values

```ts
enum Status {
  Pending = 1,
  InProgress = 2,
  Done = 3,
}

const taskStatus: Status = Status.InProgress;
console.log(taskStatus); // Output: 2
```
