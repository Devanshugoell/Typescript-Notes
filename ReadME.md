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

## What is a Union in TypeScript?

A **union** in TypeScript allows a variable to hold **more than one type** — using the `|` (pipe) symbol.

---

### ✅ Example

```ts
function printId(id: string | number) {
  console.log("Your ID is: " + id);
}

printId(101); // OK
printId("ABC123"); // OK
```

## What is a Literal Type in TypeScript?

A **literal type** in TypeScript allows a variable to have a **specific, exact value** (not just a general type like `string` or `number`).

Instead of saying a variable is of type `string`, you can say it's exactly `"success"` or `"error"`.

---

### ✅ Example

```ts
type Status = "success" | "error" | "loading";

let currentStatus: Status;

currentStatus = "success"; // ✅ OK
currentStatus = "error"; // ✅ OK
currentStatus = "done"; // ❌ Error: "done" is not assignable to type 'Status'
```

## What is a Type Alias in TypeScript?

A **type alias** in TypeScript is a way to give a **custom name to a type** — whether it's a primitive, object, union, or even a function type.  
It improves **readability** and **reusability**, and helps define complex types more clearly.

---

### ✅ Example

```ts
type Status = "success" | "error" | "loading";

let currentStatus: Status = "loading";
```

## 🔁 Function Return Type in TypeScript

You can explicitly specify the **return type** of a function in TypeScript using a colon (`:`) after the parameter list.

---

### ✅ Example

```ts
function add(num1: number, num2: number): number {
  return num1 + num2;
}
```
