//solution-1

const numbers:number[]=[1, 2, 3, 4, 5, 6];
const filterEvenNumbers= numbers.filter(num=> num %2 === 0);



//solutions-2

const str = "typescript";
const reverseString=(text:string): string =>{
 return text.split("").reverse().join("");
};


// solution-3

type StringorNumber= string | number ;
const checkValue=(value:StringorNumber):string => {
    if(typeof value === "string"){
        return "String"
    }
    else {
        return "Number"
    }
}
// solutions-4

  function getProperty<T, K extends keyof T>(obj: T, key:K):T[K]{
    return obj[key];
  }
  
const user = { id: 1, name: "John Doe", age: 21 };

const result = getProperty(user, "name");



// solutions-5


interface Book{
    title: string;
    author: string;
    publishedYear: number;
}
const toggleReadStatus =(book : Book): Book & {isRead: boolean} => {
    return {
        ...book,
        isRead:true};
}
const myBook = {
  title: "TypeScript Guide",
  author: "Jane Doe",
  publishedYear: 2024
};

const updatedBook = toggleReadStatus(myBook);



// solution-6
class Person{
    name:string;
    age:number;

    constructor(name: string, age: number){
        this.name=name;
        this.age=age;
    }
}

class Student extends Person{
    grade: string; 
    constructor(name:string, age:number, grade:string ){
        super(name, age);
        this.grade=grade;
    }
    getDetails():string {
    return `Name: ${this.name}, Age: ${this.age}, Grade: ${this.grade}`;
}
}
const student= new Student("Alice", 20, "A");

//solution-7

function getIntersection<T>(arr1:T[], arr2:T[]):T[]{
    const set2 = new Set(arr2);
    return arr1.filter(item=>set2.has(item));
}
const result1=getIntersection([1, 2, 3, 4, 5], [3, 4, 5, 6,7]);
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

# Blog 4: The Four Pillars of OOP in TypeScript

## Introduction

As applications grow, managing code complexity becomes one of the biggest challenges software engineers face. Without proper structure, code quickly turns into "spaghetti code"—difficult to read, terrifying to modify, and prone to bugs. Object-Oriented Programming (OOP) provides a time-tested blueprint to solve this. In TypeScript, combining the four pillars of OOP (Encapsulation, Abstraction, Inheritance, and Polymorphism) with strict type-checking allows us to build scalable, predictable, and clean enterprise applications.

## Body

### 1. Encapsulation
Encapsulation is the practice of bundling data (properties) and methods that operate on that data into a single unit (a class), while restricting direct access to some of the object's components.

In large projects, letting any part of the codebase arbitrarily change an object's internal state causes unpredictable side effects. TypeScript manages this beautifully using access modifiers: `public`, `protected`, and `private`.


``` ts
class BankAccount {
  private balance: number = 0;
// Private properties cannot be accessed or modified outside this class
  deposit(amount: number) {
    this.balance += amount;
  }

  getBalance() {
    return this.balance;
  }
}
```

### 2. Inheritance
Inheritance allows a new class (subclass) to adopt the properties and behaviors of an existing class (superclass). This promotes the DRY (Don't Repeat Yourself) principle, heavily reducing code duplication across massive codebases.

TypeScript supports single class inheritance using the extends keyword, ensuring that child classes remain fully typed based on their parent structure
``` ts
class Animal {
  speak() {
    console.log("Animal sound");
  }
}

class Dog extends Animal {
  bark() {
    console.log("Dog barks");
  }
}
```

### 3. Polymorphism
Polymorphism literally means "many forms." It allows different classes to implement the same methods or interfaces in their own unique way.
In large-scale architectures, polymorphism enables you to write highly flexible code. Instead of writing endless if/else or switch statements to handle different data types, you write a single function that interacts with a common interface or parent class. At runtime, TypeScript dynamically runs the correct method version based on the object provided.

``` ts
class Cat extends Animal {
  speak() {
    console.log("Meow");
  }
}
```

### 4. Abstraction 
Abstraction means hiding the complex internal implementation details of a system and only exposing a simple, clean interface to the outside world. Think of a car: you only need to interact with the steering wheel and pedals; you don't need to know how the engine manages fuel injection under the hood.

In TypeScript, we achieve abstraction using Abstract Classes and Interfaces. This reduces cognitive load because developers only need to understand what a component does, not how it does it.

``` ts
abstract class Shape {
  abstract getArea(): number;
}

class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }

  getArea() {
    return Math.PI * this.radius * this.radius;
  }
}
```

## Conclusion
The four pillars of OOP are not just theoretical ideas; they are practical tools for survival in large codebases.

• Encapsulation protects your data from corruption.

• Abstraction lowers mental fatigue by hiding messy details.

• Inheritance eliminates copy-pasting code.

• Polymorphism makes your systems modular and easy to extend.

When combined with TypeScript’s compilation-time checks, OOP changes software development from a constant fight against chaotic bugs into an organized, predictable architectural assembly line

