---
layout: essay
type: essay
title: "Unraveling Coding Standards"
# All dates must be YYYY-MM-DD format!
date: 2024-02-06
published: true
labels:
  - Engineering
---

*"Any fool can write code that a computer can understand. Good programmers write code that humans can understand."― Martin Fowler*

Up until I began taking classes in object-oriented programming, there was only a faint idea of what a coding standard meant for me. I wrote code to solve a problem, but that was all there was to it. In C language, let's say there's an array that I would like to return the sum using a function:

```c
int array(int arr[], int size) {
int sum=0;
for(int i=0; i<size;i++) {
sum+=arr[i];}
return sum;}
```

The code block above will compile normally and correctly calculate the sum of an array when the function is called. However, if someone has been programming for a long time and were to view this code block, there are clearly several mistakes if not errors in the code that do not follow coding standards.

## What is a Coding Standard?

So what is a coding standard? From the website [Codacy](https://blog.codacy.com/coding-standards#:~:text=Coding%20standards%2C%20also%20known%20as,and%20facilitate%20collaboration%20among%20developers.), Coding standards, also known as coding guidelines or programming style guides, are rules and conventions that developers follow when writing code. These rules define the code characteristics necessary to maintain a uniform codebase and facilitate collaboration among developers. Referring to the C code block above again, if a conding standard were enforced on this, here are some issues in the code that would be changed:

1. Naming: The name of function should be descriptive and reflect what the function does, let's rename it to sumArray. Also in Linux Kernel Coding Style, function names typically follow this camelCase convention.
2. Indention: Often overlooked for beginner programmers, having proper indention is important because it organizes the code to be more readable
3. Whitespace: in multiple lines it can also be seen that there is a lack of whitespaces between assignments in the for loop. This should be corrected spaces accordingly so that it's also easier to read.
4. Comments: Although not always enforced, it's very important to comment your code to ensure others who review or read it can understand what a function or subroutine might be there for.

Addressing these problems let's take a look at a corrected version of the code block:

```c
// Function to calculate the sum of elements in an array
int sumArray(int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}
```
Now with a coding standard, the C code block is much more easier to read and understand. 

## Javascript with ESLint

In general, coding standards may be differ according to the type of standard enforced in the language. In my software engineering course, we program using Javascript and at the time of writing, we began learning how to enforce a coding standard using [ESLint](https://eslint.org/). ESLint is a widely used static code analysis tool for identifying problematic patterns found in JavaScript code. At first, when using ESLint, it can be picky about how you write your code. Let's take a look at another code block:

```javascript{1}
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Here, there is a simple for loop that outputs integer from 1 to 5. It may appear to be correctly enforced with indents and whitespaces. However in coding standards using ESLint, there needs to be one newline at the end of the code, past line 3. The newline at the end of a file is a convention followed in many programming languages and file formats, including CSS, and Markdown. While it's not strictly necessary for ESLint, it's often recommended as a best practice for consistency in good coding practice.

## So why go through the trouble
