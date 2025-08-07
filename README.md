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

-Not a best practice assigning a varibale to undefined in code.
>var a = undefined;

- because undefined has specific purpose which is to say that the variable was not assigned with a value. its bad practice.




