Source: 

1. https://www.programiz.com/javascript/operators.

2. https://www.javascripttutorial.net/es-next/javascript-bigint/#:~:text=The%20BigInt%20supports%20the%20following,the%20unary%20operator%20(%20%2B%20).

3. JavaScript for impatient programmers (ES2022 edition).

4. https://en.hexlet.io/courses/intro_to_programming/lessons/types/theory_unit.

## 1. **Keywords**

JavaScipt keywords:

await break case catch class const continue debugger default delete do else export extends finally for function if import in instanceof let new return static super switch this throw try typeof var void while with yield

The following tokens are also keywords, but currently not used in the language:

enum implements package protected interface private public

## 2. **Reserved words**

- All keywords are reserved words
- Literals: true false null
- Should not use the names of global variables (String, Math, etc.) for your own variables and parameters, either.

## 3. **Valid Identifiers**

First character:

- Unicode letter (including accented characters such as é and ü and characters from
non-latin alphabets, such as α)
- $
- _

Subsequent characters:

- Legal first characters
- Unicode digits (including Eastern Arabic numerals)
- Some other Unicode marks and punctuations

For example: 

**const** ε = 0.0001;

**const** строка = '';

**let** _tmp = 0;

**const** $foo2 = **true**;

## 4. **Weak Typing, implicitly typed language **
JavaScript is a weakly typed language. It has a notion of types, but it's relaxed about them, and can treat values somewhat arbitrary. 
Coding example: 

```jsx
4 + '7';      // '47'
4 * '7';      // 28
2 + true;     // 3
false - 3;    // -3
```

In the 1st line of code, JavaScript converted number 4 into a string '4' and concatenated two strings — glued them together. JavaScript just took the liberty of assuming this is what users wanted.

In the 2nd line of code, JavaScript converted string ‘7’ into number 7 and did the normal multiplication. 

So, JavaScript does a lot of implicit conversions, but it also gives users tools to do explicit conversion ourselves. We can convert strings to numbers and numbers to strings, boolean to string etc like this:

```jsx
Number('590');    // 590
Number('aaa!!');  // NaN

Boolean(1);       // true
Boolean(0);       // false

String(true);     // 'true'
String(false);    // 'false'

String('44843');  // '44843'
```

## 5. **Primitive types vs. Reference Types**

**5.1 Primitive Types**

Primitive types are simple atomic pieces of data in JavaScript. Primitive types are always saved and accessed by the variable's value and not as a reference to another object. There are six primitive types in JavaScript:

- undefined
- null
- boolean
- number
- string
- symbol

**5.2 Reference Types**

Reference types are not simple atomic values but are objects that are made up of multiple properties assigned to them. They are stored as a reference in memory and not as independent values assigned to variables. There are three reference types in JavaScript:

- objects
- arrays
- functions

**5.3 How Primitive Types and Reference Types are Stored in Memory**

5.3.1 Primitive type

Primitive types are stored as single atomic value assigned to a variable in the memory. 

```jsx
let name1 = 'tuan';
let name2 = name; // the value of name2 now is 'john'

name2 = "le"; 
// the value of name1 is still 'tuan'
// the value of name2 now is "le"
```

Look at the 1st line of code, JavaScript will save this as a single atomic value in the memory. 

For the 2nd line of code, if we create create a new variable called `name2` ****and assigned the value of the variable `name1` to it. In this step, JavaScript will go ahead and create a new space in the memory and allocate the same value as the variable `name1` and assign it to the variable `name2`

**The new value assigned to the variable `name2`, is entirely separate from the variable `name`  and does not have any reference to it whatsoever.**

5.3.1 Reference type

Reference values are objects stored in memory and references to objects instead of dedicated places in memory like primitive types. 

```jsx
let person = {
    name: 'tuan',
    age: 20,
};

let person2 = person;
```
![image](https://user-images.githubusercontent.com/99850332/156924892-a362c2c6-1096-4516-a03b-30d60892d1f5.png)

Look at the code example above, we can see the variable `person` contains an object that contains 2 attributes name and ages. 

When we declare the 2nd variable called `person02` and assign it the same `person` object, JavaScript will save the `person02` object as a reference to the `person` object.

****Immutability and Mutability****

Primitive values in JavaScript cannot have anything added upon to them, they can only be re-assigned, and hence all primitive values in JavaScript are immutable.

```jsx
// Example 
let name1 = 'tuan';
let name2 = name1; 

console.log(name1);
console.log(name2);

/*
 * john
 * john 
 */

let name2 = 'doe';

console.log(name1);
console.log(name2);

/*
 * john
 * doe 
 */
```

As the code example above, we can see that the when reassigning the value of `name2` to ‘doe’, the value of the variable `name1` did not change. 

With reference types: 

```jsx
// Example with objects
let person = {
    name: 'john',
    age: 22,
};

let person2 = person; 

console.log(person);
console.log(person2);

/*
* {
* name: 'john',
* age: 22,
* }
*
* {
* name: 'john',
* age: 22,
* }
*/

let person2.name = 'doe'; 

console.log(person);
console.log(person2);

/*
* {
* name: 'doe',
* age: 22,
* }
*
* {
* name: 'doe',
* age: 22,
* }
*/
```

You see that JavaScript has changed person as well as `person2`. This is because the `person2`
 object was created by referencing the `person`object. With reference types, JavaScript creates a reference to the same object, and the object remains mutable. This shows that the reference types are mutable, those can be changed.

## 6. JavaScript Operator available for each data type

**6.1 String:**

`+` operator to concatenate (join) two or more strings.

```jsx
// concatenation operator
console.log('hello' + 'world');

let a = 'JavaScript';

a += ' tutorial';  // a = a + ' tutorial';
console.log(a);

/*
* helloworld
* JavaScript tutorial
*/
```

**6.2 Number** 

Arithmetic Operators

![image](https://user-images.githubusercontent.com/99850332/156926247-a309af3f-f438-4aa5-9285-7453c387f8b4.png)

![image](https://user-images.githubusercontent.com/99850332/156926399-555e4dd8-7c02-4ef4-9e4f-140892102ae7.png)

**6.3 BigInt** 

The BigInt supports the following operator +, *, -, **, %, bitwise operators except >>> (zero-fill right shift). It doesn’t support the unary operator (+).

The / operator will also work with the whole numbers. However, the result will not return any fractional digits. For example:
```jsx
let result = 3n / 2n;
console.log(result); // 1n, not 1.5n
```

A BigInt is not strictly equal (===) to a Number:
```jsx
console.log(1n === 1); // false
```

However, a BigInt is loosely equal to a number when you use the == operator:
```jsx
console.log(1n == 1); // true    
```

You can use the <, <=, >, >= to compare a BigInt with a Number:
```jsx
console.log(1n < 2); // true
console.log(2n > 1); // true
console.log(2n >= 2); // true
```

**6.4 JavaScript Assignment Operators** 
Assignment operators are used to assign values to variables. 

![image](https://user-images.githubusercontent.com/99850332/156926839-3d182b44-d5e5-41c0-b0ae-314b92b984a0.png)


**6.5 JavaScript Logical Operators** 
Logical operators perform logical operations and return a boolean value, either true or false. 

![image](https://user-images.githubusercontent.com/99850332/156926874-a1009be2-774c-44a5-a987-0be717ee1f22.png)


**6.6 JavaScript Bitwise Operators** 
Bitwise operators perform operations on binary representations of numbers.

![image](https://user-images.githubusercontent.com/99850332/156926896-6a1d822d-35a4-4bbb-abb3-f6fd74f943f2.png)

Operator	Description

**6.7 JavaScript Other Operators** 

![image](https://user-images.githubusercontent.com/99850332/156926914-44287913-6d68-4be7-8cbb-de8a145218f5.png)

## 7. Dynamically typed languages
JavaScript is dynamically typed languages. If use the incorrect type, your program does run, and the error occurs only when that particular line of code is executed. So, the types are checked during runtime.
