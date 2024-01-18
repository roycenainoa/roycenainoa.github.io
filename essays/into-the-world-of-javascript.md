---
layout: essay
type: essay
title: "Into the World of Javascript"
# All dates must be YYYY-MM-DD format!
date: 2024-01-17
published: true
labels:
  - Engineering
---

*"JavaScript is the only language that I'm aware of that people feel they don't need to learn before they start using it." - Douglas Crockford*

Since I began learning JavaScript, much of what I learned from other programming languages such as C, C++, and Python came to mind while working through FreeBootCamp. Variable assignments, functions, arrays, objects, loops, and much more. There are many similarities that I could recognize from other programming languages. This is the first time using JavaScript, but after using C for years, it didn't take long for me to become comfortable with the syntax. In fact, in many ways so far, JavaScript simplifies the syntax while improving the functionality of coding. Some lines, like in C, still need to end with a semicolon. However, creating objects and functions has never felt so intuitive. 

### Example: JavaScript Function

```javascript
function greet(name) {
    return `Hello, ${name}!`;
}
```

### Example: C Function

```c
#include <stdio.h>

void greet(char* name) {
    printf("Hello, %s!\n", name);
}
```
In my opinion, the syntax is straightforward. In the JavaScript code block, you don't have to specify the type of the name parameter. Plus, the function directly returns the formatted string. In C, you must include standard libraries (like stdio.h for input/output functions) and explicitly declare the type of each parameter (char* name in this case). So setting up the function in C can take more time.

## Features in Javascript

I've talked about some of the syntax JavaScript has that I enjoy, but there are many other features that I appreciate in JavaScript (also features that I'm not aware of yet). In the ES6 tutorial for the JavaScript FreeBootCamp, ES6 introduced arrow functions. They are a more concise way to write functions. They allow for shorter syntax compared to original function expressions, which I find useful in callbacks and methods. There are also the `let` and `const` variable declarations. `let` allows for block-scoped variables, reducing the problems associated with the global scope of `var`. Although each language that I've learned thus far has its strengths and weaknesses, I don't think JavaScript is particularly "better" than another programming language; maybe in some areas, but it depends on the application. Speaking of features, I haven't been able to utilize tools such as arrow functions in the WODs due to crunch time, but that brings me to the next topic.

## Athletic Software Engineering

In the software engineering course, it is believed that problem-solving and programming skills are improved through time and practice. This practice with the workout-of-the-day (WOD), where we solve a timed programming problem, is proven to improve one's problem-solving skills, not to mention nailing those job interviews. I find the WODs to be useful. It's rewarding to solve the problem, but at the same time, they're a bit stressful because I have often run into a DNF, which is a "Did-not-finish". The WODs are pass or fail, with no leniency for moderate mistakes, so there is a bit of pressure to ensure the code solves the problem. It might be too early for me to have an impression of the practice WODs since, at the time of writing this, I haven't done an in-class graded WOD. However, I do think the process will work for me as long as I put in the time and practice.

## Wrapping up

Overall, JavaScript is a nice tool that I would like to become efficient in. There are many skills in software engineering I would like to hone throughout the semester, and I believe there will be many opportunities to do so.
