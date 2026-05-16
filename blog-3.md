# Blog 3: How Generics Enable Reusable and Type-Safe Code in TypeScript

## Introduction

Generics in TypeScript allow developers to write reusable and flexible
code while maintaining strict type safety. Instead of duplicating logic
for different data types, generics help create a single implementation
that works for multiple types.

## Body

### Problem Without Generics

``` ts
function getFirstNumber(arr: number[]): number {
  return arr[0];
}

function getFirstString(arr: string[]): string {
  return arr[0];
}
```

This approach duplicates logic and breaks the DRY principle.

### Solution Using Generics

``` ts
function getFirst<T>(arr: T[]): T {
  return arr[0];
}
```

### Usage Example

``` ts
const num = getFirst<number>([1, 2, 3]);
const str = getFirst<string>(["a", "b"]);
```

### Generic Interface Example

``` ts
interface Box<T> {
  value: T;
}

const numberBox: Box<number> = { value: 10 };
const stringBox: Box<string> = { value: "Hello" };
```

### API Example

``` ts
interface ApiResponse<T> {
  data: T;
  status: number;
}
```

## Conclusion

Generics make code reusable, maintainable, and type-safe. They are
essential for building scalable TypeScript applications.