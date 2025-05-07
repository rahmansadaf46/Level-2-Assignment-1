# TypeScript Types, Interfaces, and keyof: A Quick Guide

Welcome to this simple blog on TypeScript's **types**, **interfaces**, and the **keyof** keyword. This Blog is written for beginners to quickly grasp these concepts with a clear, easy explanation and examples.

## Types vs. Interfaces

Both **types** and **interfaces** in TypeScript define the shape of data (e.g., objects or variables), but they differ in flexibility and use cases. Here's a comparison:

| Aspect           | Type                                                  | Interface                                             |
|------------------|-------------------------------------------------------|-------------------------------------------------------|
| **Purpose**      | Defines data structure for variables, objects, unions. | Defines a contract for objects or classes.            |
| **Extension**    | Uses `&` for intersection. <br> `type Admin = User & { role: string }` | Uses `extends`. <br> `interface Admin extends User { role: string }` |
| **Merging**      | Same-named types can't merge.                         | Same-named interfaces merge automatically.            |
| **Example**      | `type Person = { name: string; age: number };`        | `interface Person { name: string; age: number }`      |

**When to use?**
- **Types**: For flexible scenarios like unions or complex data.
- **Interfaces**: For object-oriented designs, classes, or when merging is needed.

## What is `keyof`?

The **keyof** keyword generates a union of an object's property keys. It’s super useful for safely accessing or restricting object properties dynamically.

### Example

```typescript
interface Person {
  name: string;
  age: number;
  city: string;
}

type PersonKeys = keyof Person; // "name" | "age" | "city"

function getProperty(obj: Person, key: keyof Person) {
  return obj[key];
}

const person: Person = { name: "Tony Stark", age: 59, city: "New York" };
console.log(getProperty(person, "name")); // Output: Tony Stark
console.log(getProperty(person, "age"));  // Output: 59
```

Here, `keyof Person` ensures `key` is only `"name"`, `"age"`, or `"city"`. Trying `getProperty(person, "address")` will cause a TypeScript error since `"address"` isn’t a valid key.

## Why It Matters

Using **types**, **interfaces**, and **keyof** makes your TypeScript code safer and more maintainable. Types and interfaces provide clear data structures, while `keyof` ensures dynamic but type safe property access.
