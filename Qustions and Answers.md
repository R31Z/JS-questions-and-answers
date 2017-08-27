# JavaScript Questions and Answers.

## 1. What happens when you don’t declare a variable in Javascript?

If you don’t explicitly declare a variable, you risk creating an implied global variable. This is a problem, as you will be unable to create multiple instances of that object, as each new instance will overwrite the data from the last.
In general, global variables should be used only in very specific situations and are typically not recommended, as they can lead to a lot of odd side effects that may be difficult to track down.

## 2. What will the code below output? Explain your answer.

    console.log(0.1 + 0.2); 

    console.log(0.1 + 0.2 == 0.3);
  
An educated answer to this question would simply be: “You can’t be sure. it might print out “0.3” and “true”, or it might not. 
Numbers in JavaScript are all treated with floating point precision, and as such, may not always yield the expected results.” 
The example provided above is classic case that demonstrates this issue. 

Surprisingly, it will print out:

    0.30000000000000004 false

## 3. Write a simple function (less than 80 characters) that returns a boolean indicating whether or not a string is a palindrome.

The following one line function will return true if str is a palindrome; otherwise, it returns false.

      function isPalindrome(str) {
      str = str.replace(/\W/g, '').toLowerCase();
      return (str == str.split('').reverse().join(''));
      }
  
For example:

      console.log(isPalindrome("level")); // logs 'true'
      console.log(isPalindrome("levels")); // logs 'false'
      console.log(isPalindrome("A car, a man, a maraca")); // logs 'true'
    
## 4.a

    (function(){
        return typeof arguments;
    })();
    
Answer a: 
The answer is "object"; the arguments object accessible in a function is, well, an object. 
There are two things to watch out for here:
Arguments is not an array. It is an array-like object. 
You can thus access its elements with square brackets and integer indices, 
but methods usually available on an array such as push do not exist on arguments.

Even if arguments were a true array, the answer would still be "object". 
The typeof operator returns "object" when given an array, because arrays are objects too.
      
## 4.b

    var f = function g(){ return 44; };
    typeof g(); 
            
Answer b:
The answer is that an error will occur.
This is because function g(){ return 44; } is a function expression (a named one, in fact), not a function declaration.      The function is actually bound to the variable f, not g. 

Specifying an identifier in a function expression does have its use though: stack traces are clearer instead of being        littered with nameless functions, and you can have an anonymous function recursively call itself without using     
arguments.callee. kangax has a very detailed post on function expressions.
            
 ## 5. What would be the result? 3+2+"7"
      
  Answer: 
  
      Since 3 and 2 are integers, they will be added numerically. 
      And since 7 is a string, its concatenation will be done. So the result would be 57.
      
## 6. In what order will the numbers 1-4 be logged to the console when the code below is executed? Why?
(function() {
console.log(1); 
setTimeout(function(){console.log(2)}, 1000); 
setTimeout(function(){console.log(3)}, 0); 
console.log(4);
})();

Answer: The values will be logged in the following order:
    
    1 4 3 2 

Let’s first explain the parts of this that are presumably more obvious:
1 and 4 are displayed first since they are logged by simple calls to console.log() without any delay
2 is displayed after 3 because 2 is being logged after a delay of 1000 msecs (i.e., 1 second) whereas 3 is being logged after a delay of 0 msecs.

OK, fine. But if 3 is being logged after a delay of 0 msecs, doesn’t that mean that it is being logged right away? And, if so, shouldn’t it be logged before 4, since 4 is being logged by a later line of code?

The answer has to do with properly understanding JavaScript events and timing.

The browser has an event loop which checks the event queue and processes pending events. For example, if an event happens in the background (e.g., a script onload event) while the browser is busy (e.g., processing an onclick), the event gets appended to the queue. When the onclick handler is complete, the queue is checked and the event is then handled (e.g., the onload script is executed). Similarly, setTimeout() also puts execution of its referenced function into the event queue if the browser is busy.

When a value of zero is passed as the second argument to setTimeout(), it attempts to execute the specified function “as soon as possible”. Specifically, execution of the function is placed on the event queue to occur on the next timer tick. Note, though, that this is notimmediate; the function is not executed until the next tick. That’s why in the above example, the call to console.log(4) occurs before the call to console.log(3) (since the call to console.log(3) is invoked via setTimeout, so it is slightly delayed). 

## 7. What is the output of "10"+20+30?
102030 because after a string all the + will be treated as string concatenation operator (not binary +).

## 8 Difference between Client side JavaScript and Server side JavaScript?
Client side JavaScript comprises the basic language and predefined objects which are relevant to running java script in a browser. The client side JavaScript is embedded directly by in the HTML pages. This script is interpreted by the browser at run time.

Server side JavaScript also resembles like client side java script. It has relevant java script which is to run in a server. The server side JavaScript are deployed only after compilation.

## 9. What are the advantages of using JavaScript?

Lightweight: 
JavaScript can be executed within the user’s browser without having to communicate with the server, saving on bandwidth.

Versatile: 
JavaScript supports multiple programming paradigms—object-oriented, imperative, and functional programming and can be used on both front-end and server-side technologies.

Sleek Interactivity: 
Because tasks can be completed within the browser without communicating with the server, JavaScript can create a smooth “desktop-like” experience for the end user.

Rich Interfaces: 
From drag-and-drop blocks to stylized sliders, there are numerous ways that JavaScript can be used to enhance a website’s UI/UX.

Prototypal Inheritance: 
Objects can inherit from other objects, which makes JavaScript so simple, powerful, and great for dynamic applications.

## 10. What are the disadvantages of using JavaScript?

Experienced coders won’t just be able to rave about their favorite language’s strengths—they will also be able to talk about its weaknesses. JavaScript’s main weakness is security. Look for answers on how it can be exploited. A secondary weakness is JavaScript’s ubiquity and versatility—it can be a double-edged sword in that there’s a lot of room for programming quirks that can lead to inconsistent performance across different platforms.

## 11. What’s An Object In JavaScrpt And How Do We Create Them?

A JavaScript object is an entity having state and behavior (properties and method). Since JavaScript is an object-based language, it treats everything as an object.

JavaScript is a template-based language not class based. It supports to create the object directly, there is no need to define a class for this.

JavaScript supports following three ways to create objects.

### 1. By Object Literal.

The syntax of creating an object using object literal is as follows.
           
    object={property1:value1, property2:value2.....propertyN:valueN}
    
Here, property and value are separated by “:”.

Let’s take an example of creating an object using object literal technique.

    <script> 

    std={id:1114, name:"Albert Einstein", subject:"Physics"} 

    document.write(std.id+" "+std.name+" "+std.subject); 

    </script> 
    
### 2. By Creating An Instance Of The Object (Using New Keyword).

The syntax of creating an object directly is as follows.
     
    var objectname=new Object();
    
Here, the new keyword is used to create the object.
Let’s take an example of creating an object directly.
   
    <script> 

    var std=new Object(); 

    std.id=1114; 

    std.name="Albert Einstein"; 

    std.subject="Physics"; 

    document.write(std.id+" "+std.name+" "+std.subject); 

    </script>

### 3. By Using An Object Constructor.

In this method, we create a function with arguments. The value of each of these arguments can be assigned to the current object by using this keyword.

This keyword refers to the current object.
Let’s take an example of creating an object using object constructor technique.

    <script> 

    function std(id,name,subject){ 

    this.id=id; 

    this.name=name; 

    this.subject=subject; 

    } 

    s=new std(1114,"Albert Einstein","Physics"); 

    document.write(s.id+" "+s.name+" "+s.subject); 

    </script>
  
## 12. What Is Scope In JavaScript?

The scope determines the accessibility of variables, objects, and functions in particular part of your code.

In JavaScript, the scope is of two types.

### 1. Global Scope.

A variable defined outside a function comes under the Global scope. Variables defined inside the Global scope are accessible from any part of the code. Let’s see an example.
        
        var name = 'TechBeamers';

        console.log(name); // logs 'TechBeamers'

        function logName() {

        console.log(name); // 'name' is accessible here and everywhere else

        }

        logName(); // logs 'TechBeamers'
        
### 2. Local Scope.

Variables defined inside a function comes under the Local scope. Different functions can use a variable with the same name. It is because these variables are strictly bound to the function that defines it (each having different scopes) and is not accessible in other functions. Let’s see an example.

    // Global Scope

    function sampleFunction() {

        // Local Scope #1

        function sample2Function() {

            // Local Scope #2

        }
    }

    // Global Scope

    function sample3Function() {

        // Local Scope #3

    }

    // Global Scope
## 13. What Is <This> In JavaScript?

All the prime languages use ‘this’ keyword to refer to an object that is currently instantiated by the class. However, in JavaScript, ‘this’ refers to an object which ‘owns’ the method. Though this varies, with how a function call happens.

Global Scope.

If no object is currently available, then ‘this’ represents the global object. In a web browser, ‘window’ is the top-level object which represents the document, location, history and a few other useful properties and methods. Let’s take a sample code.

    window.Obj= "I represent the window object";

    alert(window.Obj);

    alert(this.Obj); // I'm the window object

    alert(window === this); // true
    
 ### The Scenario Of A Function Call.

In the case of a function call, ‘this’ refers to the global object.

    window.Obj = "I represent the window object";

    function TestFunction() {

        alert(this.Obj); // I'm the window object

        alert(window === this); // true

    }

    TestFunction();
    
### Call Object Methods.

When an object constructor or any of its methods gets called, ‘this’ refers to an instance of an object. It is similar to any class-based language.

    window.Obj = "I'm the window object";

    function TestFunction() {

        this.Obj = "I'm the Test object";

        this.Verify1 = function() {

            alert(this.Obj); // I'm the Test object

        };

    }

    TestFunction.prototype.Verify2 = function() {

        alert(this.Obj); // I'm the Test object

    };

    var tf= new TestFunction();

    tf.Verify1();

    tf.Verify2();
    
## 14. What Is Prototype Property In JavaScript?

Every JavaScript function has a prototype property (by default this property is null), that is mainly used for implementing inheritance. We add methods and properties to a function’s prototype so that it becomes available to instances of that function. Let’s take an example that calculates the perimeter of a rectangle.

    function Rectangle(x, y) {

        this.x = x;

        this.y = y;

    }

    Rectangle.prototype.perimeter = function() {

       return 2 * (this.x + this.y);

    }

    var rect = new Rectangle(4, 2);

    console.log(rect.perimeter()); // outputs '12'
    
## 15. What Is Closure In JavaScript?

A closure is a JavaScript function defined inside another function. And that’s why it gets a special privilege to access three types of scope which are as follows.

- Internal Scope i.e. the variables defined between its curly brackets.
- Outer Function Scope i.e. the variables of the enclosing function.
- Global Scope i.e. variables defined as globals.

Please note that a closure can not only access the outer function variables but also see its parameters. But it can’t call the outer function’s arguments object. However, it can directly call the outer function’s parameters.

Here is a code example describing closure by adding a function inside another function.

    function outerFunc(arg1, arg2) {
    var param = "I'm closure. ";

    // Inner function accessing outer function variables and parameters
    function innerFunc() { 
     return arg1 + arg2 + " " + param;
    }
        return innerFunc();
    }

    outerFunc("arg1", "arg2");
## 16. Why Is “Self” Needed Instead Of “This"?

Inner functions in JavaScript have access to all of the variables defined in the outer function. However, “this” variable is an exception. Since the nested function is just a regular function and not an object method, it’s “this” refers to the global namespace. To make it more clear, let’s look at the following example.

    var aProperty = 'global';
 
    var myObject = {

      outerFun: function() {

        this.aProperty = 'local';

        setTimeout(function() {

          console.log(this.aProperty); // outputs 'global'

        }, 1);

      }

    };

Thus, we see that inside “setTimeout” function, “this” refers to the global object. We need a way to get a reference to the object, that is available inside the nested function. We assign the object from “this”, to another(non-special) variable, “self”. It is not a special variable and hence cannot be overwritten by other functions(like “this”). Thus on using “self” inside the inner function, we can refer to the local object. Following is the sample code.

    var myObject = {

      outerFun: function() {

        var self = this;

        this.aProperty = 'local';

        setTimeout(function() {

          console.log(self.aProperty); // outputs 'local'

        }, 1);

      }

    };
## 17. Why Is “Self” Needed Instead Of “This” In JavaScript?

Inner functions in JavaScript have access to all of the variables defined in the outer function. However, “this” variable is an exception. Since the nested function is just a regular function and not an object method, it’s “this” refers to the global namespace. To make it more clear, let’s look at the following example.

    var aProperty = 'global';

    var myObject = {

      outerFun: function() {

        this.aProperty = 'local';

        setTimeout(function() {

          console.log(this.aProperty); // outputs 'global'

        }, 1);

      }

    };
    
Thus, we see that inside “setTimeout” function, “this” refers to the global object. We need a way to get a reference to the object, that is available inside the nested function. We assign the object from “this”, to another(non-special) variable, “self”. It is not a special variable and hence cannot be overwritten by other functions(like “this”). Thus on using “self” inside the inner function, we can refer to the local object. Following is the sample code.

    var myObject = {

      outerFun: function() {

        var self = this;

        this.aProperty = 'local';

        setTimeout(function() {

          console.log(self.aProperty); // outputs 'local'

        }, 1);

      }

    };
