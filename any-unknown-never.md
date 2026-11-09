\*\*Any, Unknown, and Never: Understanding TypeScript's Type Hierarchy

Introduction

TypeScript's types form a hierarchy. The type unknown sits at the top, never sits at the bottom, and any is a special escape hatch outside the normal rules. This hierarchy explains how assignability works. It also shows why unknown is the safer choice.

The Three Types

unknown is the top type, so every value can be assigned to it. However, you cannot use an unknown value until you narrow its type.

ts
let value: unknown = "hello";
if (typeof value === "string") {
value.toUpperCase();
}

any disables type checking completely. It accepts every value and allows every operation, so mistakes only appear at runtime.

ts
let data: any = 5;
data.foo.bar(); // compiles, crashes at runtime

never is the bottom type: it represents values that never occur. It is assignable to every type, but nothing is assignable to it. Functions that always throw return never.

ts
function fail(msg: string): never {
throw new Error(msg);
}
Why Prefer unknown?

Both any and unknown accept every value, but unknown forces you to check before using it. In contrast, any silently spreads, because values derived from it also lose type safety. With unknown, the compiler keeps protecting you.

Conclusion

Think of unknown as "I don't know yet" and any as "stop checking". Use unknown for uncertain data such as API responses, and reserve any for rare migration cases.
