# Typescript w/Code Coach Mike

## What is typescript?

- `TypeScript` is a superset of JavaScript, meaning that all valid JavaScript code is also valid TypeScript code.
- TypeScript adds optional static typing to JavaScript, which can help to catch errors early and make code more readable and maintainable.
- Typescript is dynamically typed.

![alt text](https://img.icons8.com/fluency/128/typescript--v1.png)

_`Would you rather have "silly" errors during development, or insanity-inducing errors in production?`_

---

### Benefits of using typescript

- **_Catch errors early_**: Error catching can occur in typescript before your code is executed.
- **_More readable and maintainable code_**: TypeScript can help you to write more readable and maintainable code by providing type information to your code editor and other tools.

- **_Improved documentation:_**: TypeScript can help you to generate better documentation for your code, which can be helpful for other developers who need to understand your code.

---

### Typescript basics

- **_Type annotations_**: Type annotations are used to tell TypeScript the type of a variable, function, or class member.
- **_Interfaces_**: Interfaces are used to define the shape of an object, without specifying how the object is implemented.
- **_Classes_**: Classes are used to create reusable blueprints for objects.

---

### Getting Started

![NPM](https://img.icons8.com/color/125/npm.png)

### Using NPM (**Node Package Manager**)

- The World's Largest Software Registry (Library)

- npm is the world's largest Software Registry.

- The registry contains over 800,000 code packages.

- Open-source developers use npm to share software.

- All npm packages are defined in files called package.json.

- The content of package.json must be written in JSON.

**`package.json` Example:**

```bash

{
"name" : "myPkg",
"version" : "1.2.3",
"description" : "A package for some things",
"main" : "pkg.js",
"keywords" : ["pkg", "pack", "package"],
"author" : "Mike",
"license" : "ISC"
}

```

### Adding a TS package

Create an empty `package.json` file:

```bash
npm init -y
```

Within your npm project, run the following command to install the compiler:

```bash
npm install typescript --save-dev
```

To use the TS compiler we want to run the command:

```bash
npx tsc "name of your main.ts file"
```

You can have TypeScript create `tsconfig.json` with the recommended settings with:

```bash
npx tsc --init
```

Inside of the `tsconfig.json` header : `JavaScript Support` allowJs:

```json
/* JavaScript Support */
    // "allowJs": true, //uncomment this <~~~            /* Allow JavaScript files to be a part of your program. Use the 'checkJS' option to get errors from these files. */
    // "checkJs": true,                                  /* Enable error reporting in type-checked JavaScript files. */
    // "maxNodeModuleJsDepth": 1,                        /* Specify the maximum folder depth used for checking JavaScript files from 'node_modules'. Only applicable with 'allowJs'. */

```

### Basic Syntax

[TypeScript Simple Types](https://www.w3schools.com/typescript/typescript_simple_types.php)

### **Primitives**

- numbers
  - whole numbers and floating point values
- strings
  - text values like "TypeScript is cool"
- booleans
  - true or false values

```typescript
let num: number = 8;

let str: string = "Hello, World";

let bool: boolean = false | true; // using union types allow you to define flexible type values.

let strOrNum: string | number; // union types | define all types
strOrNum = "Hello, World";
strOrNum = 10;
```

---

### **Variable Assignment**

**Explicit Type**:

```typescript
let firstName: string = "nolan"; // type string
```

**Implicit Type**:

```typescript
let firstName = "andrew"; // inferred to type string
```

---

### **Array & Object Types**

**Arrays:**

```typescript
let ourClass: string[];

ourClass = ["caroline", "joe", "mike"];
```

**Objects:**

```typescript
let student: {
  name: string;
  age: number;
  isStudent: boolean;
}; // define the

student = {
  name: "James",
  age: 33,
  isStudent: true,
  //   hasPets: true
};
```

---

### **Generics**

- To create type-safe generics, you will need to use `Type` parameters. `Type` parameters are defined by `T` or `<T>`.
- They denote the data type of passed parameters to a class, interface, and functions.

```typescript
function fun<T>(args: T): T {
  return args;
}
```

- As a result, `fun` is now a type-safe generic function.
- To test this type-safe generic function, create a variable named `result` and set it equal to `fu`n`with a`string`type parameter. The argument will be the`Hello World` string:

```typescript
let result = fun<string>("Hello World");
```

- Try using the `fun` function with the `number` type. Set the argument equal to `200`:

```typescript
let result2 = fun<number>(200);
```

- If you would like to see the results of this code, you can include `console.log` statements to print `result` and `result2` to the console:

```typescript
console.log(result);
console.log(result2);
```

- In the end, your code should look like this:

```typescript
function fun<T>(args: T): T {
  return args;
}

let result = fun<string>("Hello World");
let result2 = fun<number>(200);

//////Output\\\\\\\\

console.log(result); // Hello World
console.log(result2); // 200
```

---

### **Type Aliases & Interfaces**

Type Aliases allow defining types with a custom name **_(an Alias)_**.

- Type Aliases can be used for primitives like string or more complex types such as objects and arrays:

### **_Aliases_**

```typescript
type CodeCoach = {
  name: string;
  roomAssign: number;
  isCoach: boolean;
};

let coachMike: CodeCoach = {
  name: Michael,
  roomAssign: 10,
  isCoach: true,
};

console.log(coachMike.name);
```

### **_Interfaces_**

Interfaces are similar to type aliases, except they **_only_** apply to **object types\***.

```typescript
interface Rectangle {
  height: number;
  width: number;
}

const rectangle: Rectangle = {
  height: 20,
  width: 10,
};
```

---

### **_Using Interfaces with a Class_**

We defined an interface `Rectangle`:

```typescript
interface Rectangle {
  height: number;
  width: number;
}
```

To use the interface Rectangle in TypeScript in a class, you can use the **_`implements`_** keyword. This tells the TypeScript compiler that the class must implement all of the properties and methods that are defined in the interface.

```typescript
interface Rectangle {
  height: number;
  width: number;
}

class RectangleImpl implements Rectangle {
  height: number;
  width: number;

  constructor(height: number, width: number) {
    this.height = height;
    this.width = width;
  }
}

const rectangle: Rectangle = new RectangleImpl(10, 20);

const height = rectangle.height; //Accessing the properties on our rectangle obj.
const width = rectangle.width;
```

Lets define a method on our **`RectangleImpl`** Class:

```typescript
class RectangleImpl implements Rectangle {
  height: number;
  width: number;

  constructor(height: number, width: number) {
    this.height = height;
    this.width = width;
  }

  calculateArea(): number {
    return this.height * this.width;
  }
}

const rectangle: Rectangle = new RectangleImpl(10, 20);
const area = rectangle.calculateArea(); // our area is 200.
```

---

### That's Basic Typescript folks

![alt text](https://media.giphy.com/media/xT9IgFXbD1smKi1IHe/giphy.gif)
