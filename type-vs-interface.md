# Type Alias vs Interface in TypeScript: Which One Should You Choose?

## Introduction

TypeScript offers two ways to describe the shape of data: `type` aliases and `interface`. They look similar and often work interchangeably. However, a few important differences affect how you design your code. Knowing them helps you choose the right tool confidently.

## Core Differences

The biggest difference is flexibility. An interface describes only object shapes, while a type alias can name any type, including unions, tuples, and primitives.

```ts
type ID = string | number;
type Point = [number, number];

interface User {
  name: string;
}
```

Interfaces also support declaration merging. If you declare the same interface twice, TypeScript combines them, but a duplicate type alias causes an error.

interface User {
age: number;
}

Extending works differently too. Interfaces use `extends`, while type aliases use intersections with `&`.

interface Admin extends User {
role: string;
}
type Staff = User & { role: string };

Classes can implement both, as long as they describe an object shape.

## When to Choose Which

Use `interface` for object contracts, public APIs, and anything that others might extend or a class might implement. Use `type` for unions, tuples, function types, and advanced features such as mapped and conditional types. Whichever you prefer, stay consistent across the project.

## Conclusion

Both tools are powerful, and the difference is small for simple objects. Choose interface for extendable object shapes and type for everything more complex. Consistency matters more than the choice itself.
