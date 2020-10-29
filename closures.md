 ## Closure & Variable Binding Examples

 * Starting with a closure as an IIFE in the snippet below.
 * The outer function is run and it returns the inner function to ```uniqueIntegerInner```.
 * The variable, ```counter``` becomes bound to the inner function when it is returned.  
 * The execution of the outer function is where  ```counter``` is declared and initialized.  
 * The inner function is returned with ```counter``` bound to it.
```
let uniqueIntegerInner = (function() {
  let counter = 0;
  return function() {return counter++; };
}());
```

 * Invoking the inner function multiple times, illustrates the closure over the outer function's variable.  
```
uniqueIntegerInner();   0
uniqueIntegerInner();   1
uniqueIntegerInner();   2
```
 * Same results here, not using an IIFE  
```
let uniqueIntegerOuter = function() { 
  let counter = 0;
  return function() {return counter++; };
};
```
 * There is one invocation of the outer function causing the variable, ```counter``` to be initialized and bound once.  
```
let uniqueIntegerInner2 = uniqueIntegerOuter();
uniqueIntegerInner2();   0
uniqueIntegerInner2();   1
uniqueIntegerInner2();   2
```

 * Below the inner function is immediately invoked after the outer function is called.   
 * ```counter``` is declared and initialized with each call to the outer function.  
 * The inner function is returned and immediately invoked. 
```
uniqueIntegerOuter()();   0
uniqueIntegerOuter()();   0
uniqueIntegerOuter()();   0
```

 ## Free and Bound Variables
 * Free variables are variables that are neither passed in as parameters nor local.
 * Above ```counter``` is a free variable relative to the inner function. 
 * When the inner function is returned it becomes a bound variable.
 * A bound variable is a variable that was previously free.
