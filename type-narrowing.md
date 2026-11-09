# Type Narrowing in TypeScript

## Introduction
Type narrowing is the process of refining a broad type into a more specific one inside a block of code. It lets us work safely with union types without risky type assertions. TypeScript analyzes our checks and updates the type automatically.

## Using typeof
The `typeof` operator is perfect for primitives such as string, number, and boolean.

```ts
function format(value: string | number): string {
  return typeof value === "string" ? value.trim() : value.toFixed(2);
}
```

## Using instanceof
For class instances, `instanceof` tells the compiler which class we are dealing with.

```ts
function getMessage(error: Error | string): string {
  return error instanceof Error ? error.message : error;
}
```

## Using the in operator
The `in` operator checks whether a property exists on an object, which is ideal for distinguishing object shapes.

```ts
type Cat = { meow: () => void };
type Dog = { bark: () => void };

function speak(pet: Cat | Dog): void {
  if ("meow" in pet) {
    pet.meow();
  } else {
    pet.bark();
  }
}
```

Inside each branch, the compiler knows the exact type, so autocomplete and error checking work correctly.

## Conclusion
Type narrowing makes union types safe and practical to use. Prefer it over type assertions so the compiler keeps protecting your code.
