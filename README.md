# From Bugs to Brilliance, Leveling Up JavaScript with TypeScript

By Felipe Garcia


## Why should we look into TypeScript?
Imagine JavaScript injected with steroids, that’s TypeScript. While JavaScript offers flexibility and freedom, it also leaves plenty of room for bugs and silent failures. TypeScript, on the other hand, brings structure and type safety, which becomes especially valuable when working in teams. In this blog, we’ll explore why more developers are making the switch from JavaScript to TypeScript and why you might want to consider it too.

## What is TypeScript?
TypeScript is a statically typed superset of JavaScript created by Microsoft It adds optional type annotations, interfaces, and modern JavaScript features, then compiles (transpiles) down to plain JavaScript that runs in any browser or JavaScript environment.

**What does it mean to transpile code?**
If you’ve decided to transition from JavaScript to TypeScript, chances are you already understand what it means to compile code. But you might still be wondering: “What in the world does it mean to transpile code?”

It’s actually nothing far-fetched or complicated. The key difference is that transpiling means converting your code to a different version of the same or a similar language, like TypeScript to JavaScript, or ES6 to ES5. Unlike compiling, which transforms code from a high-level language into a lower-level one (like C to machine code). To help visualize the difference: think of transpiling as two similar languages, like Spanish and Italian which are rooted in Latin and compiling as comparing a language like English with Chinese which have completely different structures and roots. I'll share a few code snippets below to help solidify our understanding of transpilation.
**TypeScript (before transpilation)**

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}

const user: string = "Alice";
console.log(greet(user));
```
**Transpiled JavaScript (after running `tsc`)**

```js
function greet(name) {
  return "Hello, " + name;
}

var user = "Alice";
console.log(greet(user));
```
With a clear grasp of TypeScript and how transpilation works, it’s time to explore why this language leaves JavaScript in the dust.
<span>
<span>
## How TypeScript Outshines JavaScript in Real Projects

![JavaScript left in the dust by TypeScript](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3x18rh8mj0g2p27l89o8.png)

TypeScript offers many advantages that address common pitfalls in JavaScript. In this section, we’ll walk through each benefit using clear analogies and code examples to show exactly how TypeScript helps solve the pain points JavaScript developers often face.

### Type Safety
Type safety is a common feature in statically typed languages that allows developers to declare variables with specific types. At first, this may feel restrictive or even inconvenient, especially coming from JavaScript’s flexibility. But as we grow as developers and begin working on larger, more complex codebases, the benefits of type safety become clear: 
- fewer runtime errors.
- better code completion. 
- stronger collaboration across teams.

Let’s look at a few code snippets that demonstrate how enforcing type safety can make a real difference and why this extra step pays off in the long run.

**Type Safety in Action (TypeScript Example)**

```ts
// Define an array of numbers
const scores: number[] = [95, 87, 76];

// Push a valid number
scores.push(100); // OK

// Try to push a string
scores.push("high"); 
// ^Error: Argument of type 'string' is not assignable
```
Let's start with a simple example where we declare a variable intended to store an array of numerical values only. At first, this might seem restrictive or like extra work. But imagine you're working on a team, and someone accidentally tries to push a string into that array.

In JavaScript, this kind of mistake could easily go unnoticed and cause hard-to-debug errors later.

With TypeScript, this isn’t a problem. It will immediately flag the issue and refuse to transpile the file until the type mismatch is fixed. TypeScript doesn’t just whisper, it screams when something’s wrong.

## Tuples
At this point, you might still have some doubts about TypeScript. Maybe you're someone who enjoys working on solo projects and values the flexibility that JavaScript offers. The good news is, TypeScript doesn’t take that freedom away, it simply gives you more control when you need it.

In fact, if you want to work with arrays that hold different types of values, TypeScript has a perfect solution: tuples. Let’s take a look at how they work.
 
**Tuple Example in TypeScript**

```ts

// Create a tuple value
const person: [string, number] = ["Alice", 30];

// Access tuple elements
console.log(person[0]); // "Alice"
console.log(person[1]); // 30

// Invalid order or types cause errors
const wrong: [string, number] = [30, "Alice"]; 
// ^Error: type mismatch

// Invalid length cause errors
const alsoWrong: [string, number] = ["Alice", 30, "Bob"]
// ^Error: array only expects two values
```
Using tuples, we can explicitly define what types of values a variable should hold, the exact order they should appear in, and even how many elements the array should contain. Pretty cool, right?

## Type Aliases
By now, many of you might be convinced that switching to TypeScript is worth it and honestly, you should be!

But there's still one issue that some of you might have already spotted.
You might be wondering: What if I need 50 or even 100 different tuples with the same structure?
Do I really have to declare the same tuple type over and over again?

Instead of repeating the tuple type every time, we can follow the DRY principle by creating a reusable type alias.

Before we dive into an example of type aliases, let’s do a quick refresher on the DRY principle, a key concept for improving the maintainability of our codebases.

**DRY principle**
DRY stands for Don't Repeat Yourself — a core software engineering principle that emphasizes having a single, clear source of truth for each piece of knowledge in a system. This improves maintainability and helps avoid unnecessary duplication.

In React, we apply the DRY principle through a component-based architecture. By creating reusable, customizable components, we can use the same logic and UI in multiple parts of a project — reducing repetition and making our codebase easier to manage.

**Type Alias Example in TypeScript**
Now let's take a look at how type aliases help us enforce the DRY principle in our code.

```ts
// Not DRY: repeating the same tuple structure
const person1: [string, number] = ["Alice", 30];
const person2: [string, number] = ["Bob", 25];
const person3: [string, number] = ["Charlie", 40];

// DRY: use a reusable tuple type alias
type NameAge = [string, number];

const user1: NameAge = ["Alice", 30];
const user2: NameAge = ["Bob", 25];
const user3: NameAge = ["Charlie", 40];
```
In the example above, we used a type alias. A popular TypeScript feature that allows developers to define reusable type structures.

Let’s say we want to reuse an object structure in multiple parts of our code. Instead of rewriting the type each time, we can define it once using a type and then reference it wherever needed. This not only speeds up development but also helps prevent assigning incorrect values to variables, whether by others or by ourselves.

## Enums
I’ll drop a link to a TypeScript course at the end of this blog so you can dive into learning this amazing language as soon as possible.

But for now, let’s keep going with a few more key advantages that TypeScript offers.

You might already be convinced and that’s great but remember: the title of this section doesn’t just claim that TypeScript is better than JavaScript.
We boldly stated that it leaves it in the dust.

So let’s continue until there’s not even a millimeter of doubt left.

**What are Enums in TypeScript?**
Enums is short for enumerations and is a feature in TypeScript that allows us to define a set of named constants, essentially giving human-readable names to numeric or string values.

They help describe a fixed set of possible options for a value.

**TypeScript Enum Example**
```ts
// Define enum for order status
enum OrderStatus {
  Pending = "PENDING",
  Shipped = "SHIPPED",
  Delivered = "DELIVERED"
}

// Valid enum value
const status: OrderStatus = OrderStatus.Shipped;

// Invalid value not in enum
const invalidStatus: OrderStatus = "CANCELLED";
// Error: "CANCELLED" is not assignable to OrderStatus

// Accessing undefined key
const cancelled = OrderStatus.Cancelled;
// Error: Property Cancelled does not exist
```
TypeScript doesn’t just prevent us (or others) from assigning values of the wrong type to existing variables, it also stops us from adding properties that were never part of the original design.

Ladies and gentlemen, this isn’t just a language.
This is a tool built to give you full control over your code.

## Conclusion
It’s now clear why TypeScript completely leaves JavaScript behind.

Curious to dive in? Check out this awesome resource: [TypeScript Course](https://www.codecademy.com/courses/learn-typescript/lessons/typescript-custom-types/exercises/function-types) 

Good luck on your TypeScript journey! Stay patient and as your projects grow, you'll consistently reap the benefits of this powerful transition.
