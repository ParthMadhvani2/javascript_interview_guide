# Javascript Interview Guide

# A simple guide for javascript if you are preparing for javascript interviews.

# Closure
    
Closure is one of the most confusing topics but I will try to explain this in a very simple way.
    
A closure is a feature that allows inner functions to access scope or variables of the outer functions.
    
    Example

    function outer(){
      function inner(){
        console.log("Parth")
        }
        inner()
      }
    outer()

In the above example, there is an "outer" func and an "inner" func. When we are invoking the "outer" func, we are getting the output as Parth. This means we are able to invoke the 'inner' func by an "outer" func.

    Example 2

    function outer(name, age){
      const myAge = age;
        function inner(){
          console.log(`${name} - ${age}`)
        }

      return inner
    }

    // 2 different ways

    outer("Parth", 21)() // Parth - 21

    const parth = outer("Parth", 21)
    parth() // Parth - 21

    
In the 2nd Example, there are 2 ways to call the function
    
1 -> By calling the outer function followed by bracket.

2 -> By calling the outer function stored in a variable. This is more common than the other.

Real Magic of closure

As you can see myAge variable is defined within the scope of the outer function but the parth variable is able to access this.

This is due to closure that we are able to access myAge outside the scope of outer function.

# Hoisting

- Hoisting is one of the most common questions asked in the interviews.
- Hoisting makes some types of variables accessible in the code before they are actually declared.
- Variables are lifted to the top of their scope due to hoisting.

Normal use case

- We mostly use the functions in the following way.
  
      function name(){
          console.log("Parth");
      }
  
      name() // Parth

Func declarations

- Function declarations are always hoisted i.e we can use them before defining them.

      age()
  
      function age(){
          console.log(21)
      }

      // 21

Function Expressions

- Function expressions are not hoisted i.e you can use them before declaring.

      age()
        
      const age = function(){
          console.log(21)
      }

      // Uncaught ReferenceError : Cannot access age before initialization

Var Variables

- Var variables are hoisted but it comes with a downside. You can access the var variables declaration but not the value i.e it returns undefined.

      console.log(age) // undefined
      console.log(city) // undefined

      var city = "Surat"
      var age = 21

Let Variables

- Let variables are not hoisted

      console.log(name)
      // Uncaught ReferenceError : Cannot access name before initialization
    
      let name = "Parth"

Const Variables

- variables defined with const are also not hoisted.

      console.log(age)
      // Uncaught ReferenceError : Cannot access name before initialization

      const age = 21


# Template Literals

- Template literals allow us to use strings or variables in the form of string.
- The introduction of template literals is one of the most loved features of ES-6
- Before ES-6, we use single or double quotes to wrap a string literals and it offers limited function.

Before Template literals

    const name = "parth";
    const age = 21;

    const info = "My name is " + name + " and my age is " + age;

    console.log(info)
    // My name is parth and my age is 21

After Template literals

    const name = "Parth";
    const age = 21;

    const info_new = `My name is ${name} and my ${age} is age`;

    console.log(info_new)
    // My name is parth and my age is 21


# This Keyword

- The 'this' keyword is a reference variable that refers to the object that is executing the current piece of code.

      const parth = {
          name: "Parth",
          age: 21,
          info(){
              console.log(`My name is ${this.name}`)
          }
      }
      parth.info()
      // My name is Parth

Different values

The 'this' keyword has different values depending upon its use.

- Used Alone
- Used in Regular Function
- Used in Object Method
- Regular function in strict mode

1. Used Alone

- Whenever 'this' keyword is used alone, it always refers to the global window object.
     
       console.log(this);
       /* Window { window: Window, self: Window,
          document: document, name: '', location: Location..., ...}

2. Used in Regular Function

- In the case of a regular function the 'this' keyword also refers to the global window object.

        function parth(){
              console.log("Parth")
              console.log(this)
        }

        parth();

       // parth
       /* Window { window: Window, self: Window,
          document: document, name: '', location: Location..., ...}

3. Used in Object Method

- Function within an object is called Method. In such a case, the 'this' keyword refers to the object itself.

        const about = {
          name: "Parth",
          age: 21,
          more(){
              const country = "India"
              console.log(country);
              console.log(this);
          }
       }

       about.more()

       // India
      // { name: 'Parth', age: 21 }

4. Regular Function Strict Mode

- If you are using strict mode, the 'this' keyword used in the regular function will be undefined.

          "use strict"

          function mohit(){
              console.log("Parth")
              console.log(this)
          }

          parth()

# Array Destructuring

- In simple words, destructuring means to break down a complex structure into smaller parts.
- Destructuring in Js is a simplified method for extracting multiple properties from an array.
- The concept of destructuring is widely used in a React App.

Before Destructuring 

 - Before Array Destructuring, If we wanted to extract data from arrays we had to define one variable for a separate array index.

        const lang = ['JavaScript', 'Python', 'Java', 'Rust'];

        const easy = lang[0];
        const supereasy = lang[1];
        const hard = lang[2];
        const superhard = lang[3];

        console.log(easy, supereasy, hard, superhard);
        // output -> JavaScript Python Java Rust

Using Destructuring 

- We can reduce the hectic work of storing eash array index separately by using the concept of destructuring.

        const lang = ['JavaScript', 'Python', 'Java', 'Rust'];

        // Array Destructuring
        const [easy, supereasy, hard, superhard] = lang;

        // Arrays are index based so the order of the variables matter.
        // 0 (easy) 1 (supereasy) 2 (hard) 3 (superhard)

        console.log(easy, supereasy, hard, superhard);
        // output -> JavaScript Python Java Rust

Syntax

- We can not use numbers for destructuring, numbers will throw an error because numbers can not be variables.
  
        const lang = ['JavaScript', 'Python', 'Java', 'Rust'];

        const [1,2,3,4] = lang;
    
        // output -> Invalid destructuring assignment target.

- We can also skip a variable by using comma.

        const lang = ['JavaScript', 'Python', 'Java', 'Rust'];

        // Array destructuring
        const [easy, ,hard, superhard] = lang;

        console.log(easy, hard, superhard)
        // output -> JavaScript Java Rust

# String Methods

    const text = "Hello, I am Parth";
    console.log(text.length) // 17
    console.log(text.toUpperCase()); // HELLO, I AM PARTH
    console.log(text.indexOf("Mohit")) // 12
    console.log(text.slice(7, 12)); // I am
    console.log(text.replace("Hello", "Hi")) // Hi, I am Parth

# Array Methods

    const numbers = [1, 2, 3, 4, 5];
    console.log(numbers.length) // 5
    console.log(numbers.join("-") // "1-2-3-4-5"
    console.log(numbers.indexOf(3)) // 2
    console.log(numbers.slice(1,3)) // [2, 3]
    console.log(numbers.map(num => num * 2)) // [2, 4, 6, 8, 10]

# Object Methods

    const person = { name: "Parth", age: 21 }
    const keys = Object.keys(person); // ["name", "age"]
    const value = Object.values(person); // ["Parth", 21]
    const entries = Object.entries(person); // [["name", "Parth"], ["age", 21]]
    const hasName = Object.hasOwnProperty("name"); // true

# Date Methods

    const currentDate = new Date();
    console.log(currentDate.getFullYear()) // Current Year
    console.log(currentDate.getMonth()) // Current month
    console.log(currentDate.getDay()) // Current day of the month
    console.log(currentDate.getHours()) // Current hour
    console.log(currentDate.getMinutes()) // Current minute

# Math functions

    console.log(Math.random()) // Random number between 0 - 1
    console.log(Math.round(3.7)) // 4
    console.log(Math.floor(5.9)) // 5 ( rounds down value )
    console.log(Math.max(3, 7, 1, 9)) // 9
    console.log(Math.sqrt(16)) // 4
    console.log(Math.abs(-5)) // 5 ( absolute value )
    console.log(Math.pow(2, 3)) // 8 ( 2 raised to the power 3 )
    console.log(Math.ceil(2.1)) // 3 ( rounds up value )
    console.log(Math.min(3, 7, 1, 9)) // 3 ( smallest number )

# some() & every()

Array.some()

- The some( method was introduced in ES6 version of JavaScript. This method checks whether at least one of the elements of an array satisfies the given condition.

Syntax

        let numbers = [2, 3, 4, 5, 6, 7, 23];

        numbers.some(callback func, this)

Parameters

- Callback func, the function that works on every element in an array. This callback func takes following arguments.
- Current element, the element being passed from the array.
- this, which is an optional parameter

The some() method returns

- true, if one of the elements of the array passes the given test function.
- false, if no element of the array satisfies the condition.

Example

        let numbers = [2, 3, 4, 5, 6, 7, 23];
        let smallNum = numbers.some((item) => item > 10);

        console.log(smallNum) // true

The some() will return true if one of the elements of the array passes the given test function.


Array.every()

- The every() method was introduced in ES6 version of JavaScript, it does the following things.
- Loops over the element from left to right.
- For each iteration, it calls the given function with the current array element as its 1st argument.
- The loop continues until the function returns a falsy value.

Syntax 

    let numbers = [2, 3, 4, 5, 6, 7, 23];
    let bigNumbers = numbers.every(callBack(currentValue), this);

Parameters

- Callback func, the function that works on every element in an array. This callback func takes following arguments.
- Current element, the element being passed from the array.
- this, which is an optional parameter

The some() method returns

- true, if all the elements of the array pass the given test function.
- false, if any element of the array fails the given test function.

Example

        let numbers = [2, 3, 4, 5, 6, 7, 23];
        let bigNumbers = numbers.every((item) => item > 1);

        console.log(bigNumbers) // true

        let smallNumber = number.every((item) => {
            return item < 10;
        })
        console.log(smallNumber); // false

The some() will return true if one of the elements of the array passes the given test function.
    

# Array Methods

.forEach()

- Executes a provided function once for each array element.

      const emojis = ['🤣', '🥲', '🥹'];

      emojis.forEach(emoji => {
      console.log(`I love ${emoji}`);
      }

      // Console
      I love 🤣
      I love 🥲
      I love 🥹

.map()

- Creates a new array populated with the results of calling a provided function on every element.

        const emojis = ['👽', '🎃', '🤖'];

        const result = emojis.map(emoji => {
            return emoji + emoji
        })

        console.log(result)

        // Console
        ['👽👽', '🎃🎃', '🤖🤖']
