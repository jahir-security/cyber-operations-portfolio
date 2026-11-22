# JavaScript Essentials - [11-21-2026]

## What This Covers

This lab covers the fundamentals of JavaScript from a cybersecurity perspective, including variables, data types, functions, loops, and control flow statements. It explores how JavaScript can be integrated into HTML using internal and external scripts, and how JavaScript interacts with web page elements through the Document Object Model (DOM). I practised executing JavaScript through the Google Chrome Developer Console, creating HTML files with embedded and external JavaScript, and testing interactive dialogue functions such as alert(), prompt(), and confirm(). The lab also demonstrates how client-side JavaScript logic can be inspected and manipulated through login form exercises, how malicious scripts can abuse dialogue functions, and how minified and obfuscated JavaScript can be analysed and deobfuscated.

## Key Concepts

* Understanding JavaScript fundamentals, including variables declared with var, let, and const.
* Understanding JavaScript data types such as strings, numbers, booleans, null, undefined, and objects.
* Using functions to organise reusable blocks of code and accept arguments.
* Understanding loops such as for, while, and do...while to execute repetitive tasks.
* Understanding conditional statements such as if-else to control program execution based on conditions.
* Executing JavaScript directly through the Google Chrome Developer Console.
* Understanding the difference between interpreted JavaScript execution and compiled languages.
* Integrating JavaScript into HTML using internal scripts and external .js files.
* Understanding how the DOM allows JavaScript to access and modify HTML elements using document.getElementById() and innerHTML.
* Inspecting webpage source code to identify internally embedded scripts and externally loaded JavaScript files.
* Understanding JavaScript dialogue functions, including alert(), prompt(), and confirm().
* Understanding how untrusted JavaScript files can abuse alert dialogue boxes through repetitive execution using loops.
* Examining client-side age verification using prompt() and if-else statements.
* Analysing a JavaScript-based login form and understanding the security risks of relying on client-side authentication logic.
* Understanding JavaScript minification and obfuscation and how they make code difficult to read.
* Inspecting JavaScript source files through the Sources tab in Chrome Developer Tools.
* Using online tools to minify, obfuscate, and deobfuscate JavaScript code.
* Understanding why client-side validation alone is insufficient and why sensitive credentials should never be hardcoded in JavaScript.
* Recognising the importance of using trusted JavaScript libraries and external script sources.

## Commands/Tools Used

```javascript
// Browser Console - First JavaScript Program:
console.log("Hello, World!");

// Variables and Data Types:
let age = 25;

// Conditional Statements:
if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}

// Functions:
function greet(name) {
    console.log("Hello, " + name + "!");
}

greet("Bob");

// Addition of Two Numbers:
let x = 5;
let y = 10;
let result = x + y;

console.log("The result is: " + result);
```

```html
<!-- Internal JavaScript - internal.html -->

<script>
    let x = 5;
    let y = 10;
    let result = x + y;

    document.getElementById("result").innerHTML =
        "The result is: " + result;
</script>
```

```javascript
// External JavaScript - script.js:

let x = 5;
let y = 10;
let result = x + y;

document.getElementById("result").innerHTML =
    "The result is: " + result;
```

```html
<!-- Linking External JavaScript - external.html -->

<script src="script.js"></script>
```

```javascript
// JavaScript Dialogue Functions:

// Alert:
alert("Hello THM");

// Prompt:
name = prompt("What is your name?");
alert("Hello " + name);

// Confirm:
confirm("Do you want to proceed?");
```

```javascript
// Repeated Alert Demonstration - invoice.html:

for (let i = 0; i < 3; i++) {
    alert("Hacked");
}
```

```javascript
// Conditional Statements - Age Verification:

age = prompt("What is your age");

if (age >= 18) {
    document.getElementById("message").innerHTML =
        "You are an adult.";
} else {
    document.getElementById("message").innerHTML =
        "You are a minor.";
}
```

```javascript
// JavaScript File Analysis - hello.js:

function hi() {
    alert("Welcome to THM");
}

hi();
```

```bash
# Chrome Developer Tools:
Ctrl + Shift + I

# Browser Developer Tools:
Console
Sources

# File and Script Analysis:
internal.html
external.html
external_test.html
script.js
login.html
hello.html
hello.js

# JavaScript Analysis:
Inspect
View Page Source

# JavaScript Minification and Obfuscation:
Online JavaScript Minification Tool
Online JavaScript Obfuscation Tool
Online JavaScript Deobfuscation Tool
```

## What I learned

I learned how JavaScript works and how it can make web applications interactive. I started by executing JavaScript programs through the Chrome Developer Console and practised variables, data types, functions, loops, and conditional statements. I then created HTML files using both internal and external JavaScript and understood how scripts interact with HTML elements through the DOM. I tested alert(), prompt(), and confirm() and observed how JavaScript dialogue functions can be abused through repetitive execution. I also worked through age verification and a JavaScript-based login authentication exercise to understand the weaknesses of relying on client-side logic for security. Finally, I created and inspected JavaScript files through Chrome Developer Tools, experimented with minification and obfuscation using online tools, and used deobfuscation to recover readable JavaScript code. The lab helped me understand why client-side validation should not be trusted as the only security mechanism and why sensitive information must not be stored in publicly accessible JavaScript files.
