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

## 🔁 Using Callback Functions in TypeScript

In TypeScript, you can specify the type of a **callback function** to ensure it receives the correct arguments and returns the expected type.

---

### ✅ Example

```ts
function greet(name: string, callback: (message: string) => void): void {
  const message = `Hello, ${name}!`;
  callback(message);
}

greet("Devanshu", (msg) => {
  console.log(msg); // Output: Hello, Devanshu!
});
```

## 🆚 `unknown` vs `any` in TypeScript

Both `unknown` and `any` are used when you don't know the type of a value ahead of time — but they behave differently.

---

### 🔓 `any`

- Disables type checking.
- You can perform any operation without errors.
- **Unsafe**, because TypeScript skips all checks.

```ts
let value: any = "Hello";
value.toFixed(); // ✅ No error, but will crash at runtime
```

## 🔐 `unknown` in TypeScript

The `unknown` type tells TypeScript that you don’t know the exact type **yet**, but unlike `any`, it **requires type checking** before you use it — making it **safer**.

---

### ✅ Example

```ts
let value: unknown = "Hello";

// ❌ Error: Object is of type 'unknown'
// value.toFixed();

if (typeof value === "string") {
  console.log(value.toUpperCase()); // ✅ Safe
}
```

## 🚫 `never` in TypeScript

The `never` type represents **values that never occur**.

It’s used when a function **never returns** (like it always throws an error or has an infinite loop), or when you’re handling **exhaustive checks**.

---

### ✅ Example 1: Function that never returns

```ts
function throwError(message: string): never {
  throw new Error(message);
}
```

## Using TypeScript with Classes

TypeScript enhances classes by allowing you to define **types for properties**, **constructor parameters**, and **methods** — making your object-oriented code safer and more maintainable.

---

### ✅ Basic Example

```ts
class Person {
  constructor(public name: string, public age: number) {}

  greet(): void {
    console.log(`Hi, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const devanshu = new Person("Devanshu", 22);
devanshu.greet(); // Output: Hello, my name is Devanshu and I'm 22 years old.
```

## 🔐 TypeScript Class with Access Modifiers

TypeScript provides **access modifiers** to control the visibility of class members:

- `public`: accessible from anywhere (default)
- `private`: accessible only within the class
- `protected`: accessible within the class and subclasses

---

### ✅ Example: Access Modifiers in Action

```ts
class Employee {
  constructor(
    public name: string,
    private salary: number,
    protected department: string
  ) {}

  public getDetails(): string {
    return `Name: ${this.name}, Department: ${this.department}`;
  }

  private getSalary(): number {
    return this.salary;
  }
}

class Manager extends Employee {
  constructor(name: string, salary: number, department: string) {
    super(name, salary, department);
  }

  public getDepartment(): string {
    return this.department; // ✅ allowed because it's protected
  }

  // getSalary() ❌ Not accessible here (private)
}

const emp = new Employee("Devanshu", 50000, "IT");

console.log(emp.name); // ✅ public - accessible
console.log(emp.getDetails()); // ✅ public method

// console.log(emp.salary);   // ❌ Error: 'salary' is private
// console.log(emp.department); // ❌ Error: 'department' is protected
```

## 🔐 TypeScript Class with `readonly` and Optional Property

TypeScript provides special property modifiers to enhance the safety and flexibility of your classes:

- **`readonly`**: The property cannot be reassigned after its initial value is set (usually in the constructor).
- **`?` (optional)**: The property is not required; it may or may not be present.

---

### ✅ Example: `Book` Class with `readonly` and Optional Properties

```ts
class Book {
  readonly id: number; // cannot be modified after initialization
  title: string;
  author?: string; // optional property

  constructor(id: number, title: string, author?: string) {
    this.id = id;
    this.title = title;
    if (author) this.author = author;
  }
}

const book = new Book(1, "Atomic Habits");
console.log(book.id); // ✅ 1

book.title = "New Title"; // ✅ OK
// book.id = 2;               // ❌ Error: Cannot assign to 'id' because it is a read-only property
```

## 🧬 TypeScript Class Inheritance

Inheritance allows one class to extend another, sharing and reusing code.

- Use the `extends` keyword for inheritance.
- Use `super()` to call the parent class constructor.
- Subclasses inherit public and protected members.

---

### ✅ Example: Inheritance with `Employee` and `Manager`

```ts
class Employee {
  constructor(
    public name: string,
    private salary: number,
    protected department: string
  ) {}

  public getDetails(): string {
    return `Name: ${this.name}, Department: ${this.department}`;
  }

  private getSalary(): number {
    return this.salary;
  }
}

class Manager extends Employee {
  constructor(name: string, salary: number, department: string) {
    super(name, salary, department);
  }

  public getDepartment(): string {
    return this.department; // ✅ allowed because it's protected
  }

  // getSalary() ❌ Not accessible here (private)
}

const emp = new Employee("Devanshu", 50000, "IT");

console.log(emp.name); // ✅ public - accessible
console.log(emp.getDetails()); // ✅ public method

// console.log(emp.salary);      // ❌ Error: 'salary' is private
// console.log(emp.department); // ❌ Error: 'department' is protected
```

## ⚙️ TypeScript Getters and Setters

TypeScript allows you to use **get** and **set** accessors to control how properties are accessed or mutated in a class.

- `get`: Used to access a property.
- `set`: Used to modify a property with custom logic (e.g. validation).

---

### ✅ Example: Getters and Setters in a Class

```ts
class Person {
  private _age: number;

  constructor(private name: string, age: number) {
    this._age = age;
  }

  get age(): number {
    return this._age;
  }

  set age(value: number) {
    if (value < 0) {
      throw new Error("Age cannot be negative");
    }
    this._age = value;
  }

  get info(): string {
    return `${this.name} is ${this._age} years old.`;
  }
}

const p = new Person("Devanshu", 22);

console.log(p.age); // ✅ Getter: 22
p.age = 25; // ✅ Setter works
console.log(p.info); // ✅ Getter: Devanshu is 25 years old

// p.age = -5;       // ❌ Throws error: Age cannot be negative
```

## ⚡ TypeScript `static` Keyword

In TypeScript (and JavaScript), the `static` keyword defines a method or property that belongs to the **class itself**, rather than instances of the class.

- You **don't need to create an object** to access static members.
- Access them using the class name directly.

---

### ✅ Example: Using `static` Property and Method

```ts
class MathUtil {
  static PI: number = 3.14159;

  static calculateCircumference(radius: number): number {
    return 2 * MathUtil.PI * radius;
  }
}

console.log(MathUtil.PI); // ✅ 3.14159
console.log(MathUtil.calculateCircumference(10)); // ✅ 62.8318

// const obj = new MathUtil();
// obj.PI ❌ Error: PI is static and should be accessed via the class name
```
