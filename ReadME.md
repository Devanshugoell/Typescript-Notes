## Why Use TypeScript?

TypeScript catches many potential runtime errors **at compile time**, before the code moves to production. This helps prevent bugs early in the development process.

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
