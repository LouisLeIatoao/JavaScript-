## A. Boolean values

A JavaScript Boolean value represents one of two values: **true** or **false**. 

Boolean() function is used to find out if an expression (or a variable) is true: 

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Booleans</h2>
<p>Display the value of Boolean(10 > 9):</p>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = Boolean(10 > 9);
</script>

</body>
</html>

// Output
// Display the value of Boolean(10 > 9)
// true
```

## B. Comparisons and Logical Operators

### Comparison Operators

1. Syntax:
    
    Given that `x = 5`, the table below explains the comparison operators:
    
    <img width="695" alt="Screen Shot 2022-03-27 at 16 13 48" src="https://user-images.githubusercontent.com/99850332/160285903-e50e9ff7-c70b-4006-ba20-6ae4cb32c1cc.png">

    
2. Coding Example:
    
    ```java
    <!DOCTYPE html>
    <html>
    <body>
    
    <h2>JavaScript Comparison</h2>
    
    <p>Assign 5 to x, and display the value of the comparison (x == 8):</p>
    
    <p id="demo"></p>
    
    <script>
    let x = 5;
    document.getElementById("demo").innerHTML = (x == 8);
    </script>
    
    </body>
    </html>
    ```
    
3. Application:
    
    Comparison operators can be used in conditional statements to compare values and take action depending on the result.
    
    Example:
    
    ```java
    if (age < 18) text = "Too young to buy alcohol";
    // this line of code check if the value of the variable age is less
    // than 18. If it's the case, then return the value of varibale text.
    ```
    

### Logical Operator

1. Syntax:
    
    Given that `x = 6` and `y = 3`, the table below explains the logical operators
    
    <img width="545" alt="Screen Shot 2022-03-27 at 16 18 54" src="https://user-images.githubusercontent.com/99850332/160285931-68c872ec-2684-4864-a827-5cd99a212813.png">

    
2. Coding Example
    
    ```java
    <!DOCTYPE html>
    <html>
    <body>
    
    <h2>JavaScript Comparison</h2>
    
    <p>The AND operator (&&) returns true if both 
    expressions are true, otherwise it returns false.</p>
    
    <p id="demo"></p>
    
    <script>
    let x = 6;
    let y = 3;
    
    document.getElementById("demo").innerHTML = 
    (x < 10 && y > 1) + "<br>" + 
    (x < 10 && y < 1);
    </script>
    
    </body>
    </html>
    ```
    
3. Application
    
    Logical operators are used to determine the logic between variables or values.
    

### Conditional (Ternary) Operator

JavaScript also contains a conditional operator that assigns a value to a variable based on some condition.

Example:

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Comparison</h2>

<p>Input your age and click the button:</p>

<input id="age" value="18" />

<button onclick="myFunction()">Try it</button>

<p id="demo"></p>

<script>
function myFunction() {
  let age = document.getElementById("age").value;
  let voteable = (age < 18) ? "Too young":"Old enough";
  document.getElementById("demo").innerHTML = voteable + " to vote.";
}
</script>

</body>
</html>
```

### **Data Type Comparison**

1. String comparison 
    
    JavaScript uses unicode order to determine whether a string is greater than another.
    
    Example:
    
    ```java
    alert( 'Z' > 'A' ); // true
    alert( 'Glow' > 'Glee' ); // true
    alert( 'Bee' > 'Be' ); // true
    ```
    
    The process:
    
    - Compare the first character of both strings.
    - If the first character from the first string is greater (or less) than the other string’s, then the first string is greater (or less) than the second. We’re done.
    - Otherwise, if both strings’ first characters are the same, compare the second characters the same way.
    - Repeat until the end of either string.
    - If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.
    
    Note
    
    <aside>
    💡 Unicode order is case sensitive because capital letter `"A"` is not equal to the lowercase `"a"` . "a” is greater because it has a greater index in the internal encoding table JavaScript uses (Unicode).
    
    </aside>
    

### Comparison between different types

When comparing values of different types, JavaScript converts the values to numbers.

For example:

```java
alert( '2' > 1 ); // true, string '2' becomes a number 2
alert( '01' == 1 ); // true, string '01' becomes a number 1
```

For boolean values, `true` becomes `1` and `false` becomes `0`.

For example:

```java
alert( true == 1 ); // true
alert( false == 0 ); // true
```

### Strict Equality

**A strict equality operator `===` checks the equality without type conversion.**

```java
alert( 0 == false ); // true
alert( 0 === false ); // false, because the types are different
```

## C. JavaScript Condition (if, else and else if)

### The if Statement

Use the `if` statement to specify a block of JavaScript code to be executed if a condition is true.

Syntax

```java
if (condition) {
  //  block of code to be executed if the condition is true
}
```

Example:

```java
if (hour < 18) {
  greeting = "Good day";
}
```

### **The else Statement**

Use the `else` statement to specify a block of code to be executed if the condition is false.

Syntax:

```java
if (condition) {
  //  block of code to be executed if the condition is true
} else {
  //  block of code to be executed if the condition is false
}
```

Example:

```java
const hour = 15; 
let greeting;

if (hour < 18) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}

// Output: Good day
```

### **The else if Statement**

Use the `else if` statement to specify a new condition if the first condition is false.

Syntax:

```java
if (condition1) {
  //  block of code to be executed if condition1 is true
} else if (condition2) {
  //  block of code to be executed if the condition1 is 
  //  false and condition2 is true
} else {
  //  block of code to be executed if the condition1 is 
  //  false and condition2 is false
}
```

Example:

```java
const time = 9;
let greeting;
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
// Output: Good Morning
```

## D. Short-circuit evaluation in JavaScript

### Short-circuit Evaluation

```java
function A() { console.log('called A'); return false; }
function B() { console.log('called B'); return true; }

console.log( A() && B() );
// logs "called A" to the console due to the call for function A,
// && evaluates to false (function A returns false), then false is logged to the console;
// the AND operator short-circuits here and ignores function B
```

### Operator precedence

The AND operator has a higher precedence than the OR operator, meaning the `&&`
 operator is executed before the `||` operator

```java
true || false && false           // returns true
true && (false || false)         // returns false
(2 == 3) || (4 < 0) && (1 == 1)  // returns false
```

## E. JavaScript deal with “dangling else" problem

Using braces and indentation.

```java
if (hour < 18) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

Using *the “if – else if – else”* format so as to specifically indicate which “*else”* belongs to which “*if”*.

```java
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

## F. Switch Statement

Use the `switch` statement to select one of many code blocks to be executed.

Syntax:

```java
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```

This is how it works:

- The switch expression is evaluated once.
- The value of the expression is compared with the values of each case.
- If there is a match, the associated block of code is executed.
- If there is no match, the default code block is executed.

When JavaScript reaches a `break` keyword, it breaks out of the switch block.

This will stop the execution inside the switch block.

It is not necessary to break the last case in a switch block. The block breaks (ends) there anyway.

The `continue` statement breaks one iteration (in the loop), if a specified condition occurs, and continues with the next iteration in the loop.

This example skips the value of 3:
```java
for (let i = 0; i < 10; i++) {
  if (i === 3) { continue; }
  text += "The number is " + i + "<br>";
}
```
