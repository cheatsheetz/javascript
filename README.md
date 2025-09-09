# JavaScript Cheat Sheet

Essential JavaScript syntax, methods, and modern ES6+ features for web development.

---

## Table of Contents
- [Basic Syntax](#basic-syntax)
- [Variables & Data Types](#variables--data-types)
- [Functions](#functions)
- [Objects & Arrays](#objects--arrays)
- [Control Structures](#control-structures)
- [ES6+ Features](#es6-features)
- [DOM Manipulation](#dom-manipulation)
- [Async Programming](#async-programming)
- [Built-in Methods](#built-in-methods)

---

## Basic Syntax

| Concept | Syntax | Example |
|---------|--------|---------|
| Variables | `let`, `const`, `var` | `let name = "Alice";` |
| Comments | `//` or `/* */` | `// Single line` |
| Semicolons | Optional but recommended | `let x = 5;` |
| Console output | `console.log()` | `console.log("Hello");` |
| String interpolation | Template literals | `\`Hello \${name}\`` |
| Type checking | `typeof` | `typeof 42` |

## Variables & Data Types

### Variable Declarations
```javascript
// let - block scoped, reassignable
let age = 25;
age = 26;  // OK

// const - block scoped, not reassignable  
const name = "Alice";
// name = "Bob";  // Error

// var - function scoped (avoid in modern JS)
var old_style = "legacy";
```

### Primitive Types
```javascript
// Numbers
let integer = 42;
let float = 3.14;
let scientific = 1e6;  // 1,000,000

// Strings
let single = 'Hello';
let double = "World";
let template = `Hello ${name}`;  // Template literals

// Boolean
let isActive = true;
let isComplete = false;

// Special values
let empty = null;
let notDefined = undefined;
let notANumber = NaN;
let infinite = Infinity;
```

### Type Conversion
```javascript
// To string
String(123)        // "123"
(123).toString()   // "123"
123 + ""          // "123"

// To number
Number("123")      // 123
parseInt("123")    // 123
parseFloat("3.14") // 3.14
+"123"            // 123

// To boolean
Boolean(1)         // true
Boolean(0)         // false
!!value           // Convert to boolean
```

## Functions

### Function Declarations
```javascript
// Function declaration
function greet(name) {
    return `Hello, ${name}!`;
}

// Function expression
const greet = function(name) {
    return `Hello, ${name}!`;
};

// Arrow functions (ES6)
const greet = (name) => {
    return `Hello, ${name}!`;
};

// Short arrow function
const greet = name => `Hello, ${name}!`;
const add = (a, b) => a + b;
```

### Function Features
```javascript
// Default parameters
function greet(name = "World") {
    return `Hello, ${name}!`;
}

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}

// Destructuring parameters
function createUser({name, age, email}) {
    return {name, age, email, active: true};
}

// Higher-order functions
function createMultiplier(factor) {
    return (num) => num * factor;
}

const double = createMultiplier(2);
```

## Objects & Arrays

### Objects
```javascript
// Object creation
const person = {
    name: "Alice",
    age: 30,
    city: "NYC"
};

// Accessing properties
person.name          // Dot notation
person['name']       // Bracket notation
person['full-name']  // For special characters

// Adding/updating properties
person.email = "alice@example.com";
person['phone'] = "123-456-7890";

// Object methods
const user = {
    name: "Alice",
    greet() {
        return `Hello, I'm ${this.name}`;
    }
};

// Object destructuring
const {name, age} = person;
const {name: fullName} = person;  // Rename
```

### Arrays
```javascript
// Array creation
const fruits = ['apple', 'banana', 'orange'];
const numbers = [1, 2, 3, 4, 5];
const mixed = [1, 'hello', true, {name: 'Alice'}];

// Array methods
fruits.push('grape');          // Add to end
fruits.pop();                  // Remove from end
fruits.unshift('kiwi');        // Add to beginning
fruits.shift();                // Remove from beginning
fruits.splice(1, 1, 'mango');  // Remove/add at index

// Array searching
fruits.indexOf('apple');       // Find index
fruits.includes('banana');     // Check existence
fruits.find(item => item.startsWith('a'));  // Find element
fruits.findIndex(item => item === 'banana'); // Find index

// Array iteration
fruits.forEach(fruit => console.log(fruit));
fruits.map(fruit => fruit.toUpperCase());
fruits.filter(fruit => fruit.length > 5);
fruits.reduce((acc, fruit) => acc + fruit.length, 0);
```

## Control Structures

### Conditionals
```javascript
// If statements
if (age >= 18) {
    console.log("Adult");
} else if (age >= 13) {
    console.log("Teenager");
} else {
    console.log("Child");
}

// Ternary operator
const status = age >= 18 ? "Adult" : "Minor";

// Switch statement
switch (day) {
    case 'Monday':
        console.log('Start of work week');
        break;
    case 'Friday':
        console.log('TGIF!');
        break;
    default:
        console.log('Regular day');
}

// Logical operators
if (age >= 18 && hasLicense) {
    console.log("Can drive");
}

if (age < 18 || !hasPermission) {
    console.log("Cannot enter");
}
```

### Loops
```javascript
// For loop
for (let i = 0; i < 5; i++) {
    console.log(i);
}

// For...of loop (ES6) - values
for (const fruit of fruits) {
    console.log(fruit);
}

// For...in loop - keys/indices
for (const index in fruits) {
    console.log(index, fruits[index]);
}

// While loop
let count = 0;
while (count < 5) {
    console.log(count);
    count++;
}

// Do...while loop
do {
    console.log(count);
    count++;
} while (count < 5);
```

## ES6+ Features

### Destructuring
```javascript
// Array destructuring
const [first, second, ...rest] = [1, 2, 3, 4, 5];

// Object destructuring
const {name, age, city = "Unknown"} = person;

// Nested destructuring
const {address: {street, city}} = user;

// Function parameter destructuring
function greet({name, age}) {
    return `Hello ${name}, you are ${age}`;
}
```

### Spread Operator
```javascript
// Array spread
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];  // [1, 2, 3, 4, 5]

// Object spread
const obj1 = {a: 1, b: 2};
const obj2 = {...obj1, c: 3};  // {a: 1, b: 2, c: 3}

// Function arguments
function sum(a, b, c) {
    return a + b + c;
}
sum(...[1, 2, 3]);  // Same as sum(1, 2, 3)
```

### Classes
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, I'm ${this.name}`;
    }
    
    static species() {
        return "Homo sapiens";
    }
}

class Student extends Person {
    constructor(name, age, major) {
        super(name, age);
        this.major = major;
    }
    
    study() {
        return `${this.name} is studying ${this.major}`;
    }
}
```

### Modules
```javascript
// Exporting (export.js)
export const PI = 3.14159;
export function add(a, b) {
    return a + b;
}
export default class Calculator {
    // class definition
}

// Importing (main.js)
import Calculator, { PI, add } from './export.js';
import * as MathUtils from './export.js';
```

## DOM Manipulation

### Selecting Elements
```javascript
// Single elements
document.getElementById('myId');
document.querySelector('.myClass');
document.querySelector('#myId');

// Multiple elements
document.getElementsByClassName('myClass');
document.getElementsByTagName('div');
document.querySelectorAll('.myClass');
```

### Manipulating Elements
```javascript
// Content manipulation
element.innerHTML = '<p>New content</p>';
element.textContent = 'Plain text';
element.innerText = 'Visible text';

// Attribute manipulation
element.getAttribute('src');
element.setAttribute('src', 'image.jpg');
element.removeAttribute('disabled');

// Style manipulation
element.style.color = 'red';
element.style.backgroundColor = 'blue';
element.classList.add('active');
element.classList.remove('hidden');
element.classList.toggle('selected');

// Creating and adding elements
const newDiv = document.createElement('div');
newDiv.textContent = 'Hello World';
parent.appendChild(newDiv);
parent.removeChild(childElement);
```

### Event Handling
```javascript
// Adding event listeners
button.addEventListener('click', function() {
    console.log('Button clicked!');
});

// Arrow function event handler
button.addEventListener('click', (event) => {
    event.preventDefault();
    console.log('Clicked:', event.target);
});

// Event delegation
document.addEventListener('click', (event) => {
    if (event.target.matches('.button')) {
        console.log('Button clicked');
    }
});
```

## Async Programming

### Promises
```javascript
// Creating a promise
const promise = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('Success!');
        // or reject('Error!');
    }, 1000);
});

// Using promises
promise
    .then(result => console.log(result))
    .catch(error => console.error(error))
    .finally(() => console.log('Done'));

// Promise.all - wait for all
Promise.all([promise1, promise2, promise3])
    .then(results => console.log(results));

// Promise.race - first to complete
Promise.race([promise1, promise2])
    .then(result => console.log(result));
```

### Async/Await
```javascript
// Async function
async function fetchData() {
    try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error:', error);
        throw error;
    }
}

// Using async function
fetchData()
    .then(data => console.log(data))
    .catch(error => console.error(error));
```

### Fetch API
```javascript
// GET request
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => console.log(data));

// POST request
fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json',
    },
    body: JSON.stringify({name: 'Alice', age: 30})
})
.then(response => response.json())
.then(data => console.log(data));
```

## Built-in Methods

### String Methods
| Method | Description | Example |
|--------|-------------|---------|
| `charAt(index)` | Character at index | `"hello".charAt(1)` |
| `slice(start, end)` | Extract substring | `"hello".slice(1, 4)` |
| `substring(start, end)` | Extract substring | `"hello".substring(1, 4)` |
| `toLowerCase()` | Convert to lowercase | `"HELLO".toLowerCase()` |
| `toUpperCase()` | Convert to uppercase | `"hello".toUpperCase()` |
| `trim()` | Remove whitespace | `" hello ".trim()` |
| `split(separator)` | Split into array | `"a,b,c".split(',')` |
| `replace(old, new)` | Replace text | `"hello".replace('l', 'x')` |
| `includes(substring)` | Check if contains | `"hello".includes('ell')` |

### Array Methods
| Method | Description | Example |
|--------|-------------|---------|
| `push(item)` | Add to end | `arr.push('item')` |
| `pop()` | Remove from end | `arr.pop()` |
| `shift()` | Remove from start | `arr.shift()` |
| `unshift(item)` | Add to start | `arr.unshift('item')` |
| `slice(start, end)` | Extract portion | `arr.slice(1, 3)` |
| `splice(index, count)` | Remove/add items | `arr.splice(1, 2, 'new')` |
| `join(separator)` | Join to string | `arr.join(',')` |
| `reverse()` | Reverse array | `arr.reverse()` |
| `sort()` | Sort array | `arr.sort()` |

---

## Resources
- [MDN JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [ES6 Features](https://github.com/lukehoban/es6features)
- [JavaScript.info](https://javascript.info/)

---
*Originally compiled from various sources. Contributions welcome!*