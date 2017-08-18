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
## 4.
   Question a. 
            (function(){
                return typeof arguments;
            })();
      
    Question b. 
            var f = function g(){ return 44; };
            typeof g(); 
            
     Answer a: 
     The answer is "object"; the arguments object accessible in a function is, well, an object. 
     There are two things to watch out for here:
     Arguments is not an array. It is an array-like object. 
     You can thus access its elements with square brackets and integer indices, 
     but methods usually available on an array such as push do not exist on arguments.
     
     Even if arguments were a true array, the answer would still be "object". 
     The typeof operator returns "object" when given an array, because arrays are objects too.

     Answer b:
     The answer is that an error will occur.
     This is because function g(){ return 44; } is a function expression (a named one, in fact), not a function declaration.      The function is actually bound to the variable f, not g. 
     
     Specifying an identifier in a function expression does have its use though: stack traces are clearer instead of being        littered with nameless functions, and you can have an anonymous function recursively call itself without using     
     arguments.callee. kangax has a very detailed post on function expressions.
            
