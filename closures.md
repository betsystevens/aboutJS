 ## Closure & Variable Binding Examples

 * Starting with a closure as an IIFE  
 * The variable, ```counter``` becomes bound to the inner function when it is returned.  
 * The outer function is executed once and  ```counter``` is declared and initialized.  
 * The inner function is returned with ```counter``` bound to it.
```
let uniqueInteger = (function() {
  let counter = 0;
  return function() {return counter++; };
}());
```

 * Invoking the inner function multiple times, illustrates the closure over the outer function's variable.  
```
uniqueInteger();   0
uniqueInteger();   1
uniqueInteger();   2
```
 * Same results here, not using an IIFE  
```
let uniqueInteger2 = function() { 
  let counter = 0;
  return function() {return counter++; };
};
```
 * There is one invocation of the outer function causing the variable, ```counter``` to be bound once.  
```
let unique = uniqueInteger2();
unique();   0
unique();   1
unique();   2
```

 * Below the inner function is immediately invoked after the outer function is called.   
 * The results surprised me as I was experimenting with these functions.
 * ```counter``` is declared and initialized with each call to the outer function.  
 * Then the inner function is immediately invoked. 
```
uniqueInteger2()();   0
uniqueInteger2()();   0
uniqueInteger2()();   0
```

 ## Free and Bound Variables
 * Free variables are variables that are neither passed in as parameters nor local.
 * Above ```counter``` is a free variable relative to the inner function. 
 * When the inner function is returned it becomes a bound variable.
 * A bound variable is a variable that was previously free.
