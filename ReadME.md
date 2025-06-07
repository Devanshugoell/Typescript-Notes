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
