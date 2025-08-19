# Namaste Javascript 🙏 S1+S2
## 1. How Javascript works - Execution Context

> "Everything In JS happens inside Execution context".
- Execution context is like a container or box in which JS code is executed.
- It has two Components in it - 
    1. Memory Component or Variable Environment
    2. Code Component or Thread of Execution
- **Memory Component** - It is a sort of environment where variables and functions are stored in Key value pairs.
- **Code Component** - This is the place where code is executed line by line (one line at a time).

![alt](./image1.png)

>"Javascript is synchronous single threaded language"
- Javascript can Execute One Command at a time in a specific order.

## 2. How JS code is executed?

### Steps to execute a JS code.

![alt](./image2.png)

1. Gloabal Execution context is created.
2. Execution Context created in two phases 
    - Memory creation Phase
    - Code Execution Phase
3. In Memory Execution phase memory is allocated to variables and functions.
4. Js Skims through the program allocates memory to every varibles and function 
5. for variables a special value undefined is allocated to it.
6. for functions it allocates the whole code. as key value pair.

![alt](./image3.png)

7. Now for the Code Execution Phase JS goes line by line and executes the code now.
8. So, when the function call happens a brand new execution context is created for it.
9. Which will again have a memory component and a code component and will execute in same 2 phases.

![alt](./image4.png)

10. return is a special keyword which sends the returned value to the execution context where function was invoked.
11. Once the function is executed the execution context of the function will be removed.


![alt](./image5.png)

12. *Square4 will get the value 16 and then execution context of the second call will be deleted. 

13. This is how whole code runs.

### How JS manages all these ?

1. this is managed by JS very efficently by using a Stack called as Call Stack.
2. Every time in our stack we have our Global Execution Context at the bottom.
3. Everytime a function is called new execution context is created on top of the other. 
4. once the function is returned the exec. context is popped out of the stack
5. after all the code execution global exec. context is popped out of the stack and call stack will be empty.

> "Call Stack maintains the order of execution of execution contexts"

- Fancy Names for call stack-
    + Execution context stack
    + Program Stack
    + Control Stack
    + Run-time Stack
    + Machine Stack

## 3. Hoisting in JS
- Hoisting is a phenomenon in JS by which we can access the variable and functions even before it was initialized , we can access it without any error.
- for variable due to memory creation phase it will have the value as undefined  
- when you call a function it will automatically will execute with the result because the whole fucntion is already being stored with the function name during the memory creation phase.
- Arrow function act as a variable only it stays undefined until it is called.

![alt](./image6.png)

## 4. How functions execute.(Imp Points only)

![alt](./image7.png)

> Console O/P : 10 100 1

- JS doesnt get confused when there are  x declared times inside our code

- Because each function has their own execution context and they will have thier own memory creation phase so each x will be created inside thier respective execution context.
- after the function call is finished it will remove the execution context and its respective memory allocated variables or functions.
- JS engine and call stack handles this very efficiently. So the funtional x will have thier own value for a() - 10, b() - 100 , and the global x will finally console.log at line number 4 as 1

## 5. Shortest Js Program , Window, This

- Shortest program in JS is the blank JS file or you can say for example blank index.js JS file.

- Even when it is an empty JS still Global context Gets created also sets up the memory space. 

- With Global context it Creates a Global Object window and a keyword this.

- In global scope this points to Global Object, So we can say -
> this===window // true

- window is a object that has many functions and variables in it which is created by JS engine

- Global object in Browsers Js engine is window
- Global space is the code which is not inside the fucntion
- The variables and functions we create in global space gets attached the global object.
- Like in the following image a and b is there in global object not x.

![alt](./image8.png)

- to access this values from global object we can use window.(variable or fucntion name) or simply the (name) Js assumes we are saying window.(name) , or we can also use this.(name)

> console.log(window.a) //10
> console.log(a) //10
> console.log(this.a) //10
> console.log(x) // refrence error as it is not a part of window object.

## 6. undefined vs not-defined
- undefined is a placeholder which is being assigned to a variable when execution context is created and memory creation phase is done.
-not-defined is something for which memory is not allocated.
-undefined is not empty it is a special keyword that acts as placeholder until the variable is assigned some other value

![alt](./image9.png)

- JS is a loosely typed or weakly typed language.
- we can put every data type inside a variable it can be string it can be number or boolean anything.

![alt text](./image10.png)

- Not a best practice assigning a varibale to undefined in code.
>var a = undefined;

- because undefined has specific purpose which is to say that the variable was not assigned with a value. its bad practice.

## 7. Scope chaining and Lexical environment.
- Scope in Js is directly related to lexical environment.

- **Scope** - Scope means where you can access the specific function or a variable. scope of the varible or scope of the function.

- **Global Variables**- Varibales inside global context is called global variables. and it can be accessed from anywhere in program (we will know how).

- **Lexical Environment**- Whenever a Execution context is created Lexical environment is also created. Lexical Environment is the local memory and Lexical environment of its parent (lexical means in hierarchy or in sequence).
>Lexical env = local Memory + Lexical env of parent

![alt](./image11.png)

> [!NOTE]
> The c() function is Lexically inside a function.

- Whenever Exec. Context  is created a Lexical Environment reference of parent also get created inside it.

- **Scope Chain** - The way of finding values from own lexical envrioment to its parents lexical environment and this goes on until it reaches the global environment which points to null.

![alt](./image11.png)

![alt](./image12.png)

- So Here we can see the Lexical environment of c( ) points to a( ).
> Sequence of Scope chain- c()->a()->Global->null.


## 8. let, const in JS and Temporal Dead Zone.

> let and const are hoisted but they are hoisted bit differently than var.

- let and const remain in temporal dead zone for time being.

- Whenever we try to access let or const before it is declared we get a reference error that says "RefrenceError: Cannot access (variable_name) before initialization".

![alt](./image13.png)

- So in the below image we can see that let and const are hoisted but they declared in separate memory space not in global memory space like var. that is why they are not accessible before initialization.

![alt](./image15.png)
![alt](./image14.png)

- **Temporal Dead Zone** - it is the time between the let/const was hoisted and  it was initialised with some value.

- Whenever we try to access a variable that is not defined in the code we get a diffrent reference not the same error as let value accessed before initialization.

![alt](./image16.png)

- for window object and this cannot access the value of let and const because they are not part of the global space like vars. so they give undefined like for all the undeclared variables.

![alt](./image17.png)

- let is bit strict than var so if we try to redeclare the same variable using let or var we get a syntax error and it not even executes single line of code.

>let a=10 ; var a=1000 ;let a=200 // these will give error.
![alt](./image18.png)

- const is more strict than let we have to initilize const variable at same line it is declared. it will give syntax error

>const b; b=20; // will give error
![alt](./image19.png)

- if we want to assign any value later in the const it will give a diffrent error called type error.

> const b=100; b=20 // will give error
![alt](./image20.png)

- When to use which variable.
    - **const**- whenever there is a constant value through out the program use const best to use cause it is very strict.
    -  **let**- if the value is changing use let it is less strict than const , it has TDZ  so you wont get into the issues of undefined etc.
    - **var**- Keep var aside normal coding doesnt requires var but there are few special cases where we can use var.

- Always keep your declartions and initialization at top of the scope to avoid TDZ errors.

## 9. Block Scope.

>[!NOTE]
> "let and const are block scoped"

- What is Block?
    - Block is defined by {} these two curly braces this is a perfectly valid JS code.
    - Block is also know n as compound statement it helps to combine multiple JS statements in one group.
    - we need to group the statement because 
    - we group multiple statements in a block so we can use it where JS expects single statement.

    ![alt](./image21.png)

- We use it in loops conditions etc. 
- Block scope means variables or functions we can access inside block.

![alt](./image22.png)

- We can see in the above image that let and const are not part of global scope they are part of Block scope completely separate from global object where as var is inside the global scope.

- let and const are hoisted in a diffrent space that is reserved for this block "{}" and var is hoisted in the Global scope.

-  let and const are not accessible outside this block so that is why they are called block scoped.

- What is Shadowing ?
    - if you have same variable inside the block it shadows the variable outside. executes the value inside.

    ![alt](./image23.png)

    - The above image shows shadowing exapmle.
    - [exclusively for var] even if we get out of the block scope and try to log the value it will show us the value which was inside the block as var is inside the global scope and both are pointing to same memory location inside Global object. 
    - for let and const situations are different.
    
    ![alt](./image24.png)

    - So we can see there are two separate values of ab inside two diffrent scope.
    as we know that let and const are block scopic.
    - inside the block the same variable ab shodowed the value of ab which exists outside the block. 

    - but if we log outside the block where block scope is ended it will take the script scope value of ab.
    - concept of shadowing is not only for block scopes it for functions to remeber functions has this -{}.

- What is illegal Shadowing?
    - if you are shadowing a let variable with var then it is illegal shadowing
    >[!CAUTION]
    > let a=10; {var a=100 } //Illegal Shadwing will give syntax error "a is already been declared"

    - if a variable is shadowing something it should not cross the boundary of its scope as we know var is in the global scope so it persists the value even after the block.
    - var is a function scope if we do this inside a function there wont be any error.

- you can shadow let using let, var using let(inside block)

- Block Scope also follows lexical scope.

- like it checks in its own block if it finds the value it logs or else it checks in its lexical parent.

- examples of scope chaining in block scope.

![alt](./image25.png)

![alt](./image26.png)

![alt](./image27.png)

- scope rules are same for arrow and normal functions.



















