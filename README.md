# reactDarling

About

Javascript is a single threaded, non-blocking, concurrent and synchronous language. It has a single call stack and executes the program concurrently.

It is  asynchronous only in the ajax case.

Everything in javascript happens in an execution context.

Execution context is like a big box and has two components:
Memory component ( variable environment )
Code component ( thread of execution )

Memory Component => In memory component, all the variables or functions used in the js file are allocated and this is the first component. And memory allocations are done first when a program or file compiles.

Code component => In code component, code executions are done which are written in that file. 

Lazy loading

Once an app runs and all the components are loaded then when we click on any link or buttons then that particular component loads that is called lazy loading.

is a design pattern for optimizing web and mobile apps. The concept of lazy loading is simple: initialize objects that are critical to the user interface first and quietly render noncritical items later
React.lazy() is a function that enables you to render a dynamic import as a regular component. Dynamic imports are a way of code-splitting, which is central to lazy loading. A core feature as of React 16.6, React.lazy() eliminates the need to use a third-party library such as react-loadable.
React.Suspense enables you to specify the loading indicator in the event that the components in the tree below it are not yet ready to render.


Reconciliation in react

The reconciliation process makes React work faster. Reconciliation is the process through which React updates the Browser DOM. Important concepts behind the working of the Reconciliation process are: Virtual DOM ; Diffing Algorithm. The term rendering in React can closely be identified as making or becoming.
<script async>

Async scripts are executed as soon as the script is loaded, so it doesn't guarantee the order of execution (a script you included at the end may execute before the first script file )
<script defer>

Defer scripts guarantee the order of execution in which they appear in the page.
 
Hooks (functional component)

Basic hooks (3): 

useState()
useEffect()
useContext()
Basic hooks (7):

useReducer()
useCallback()
useMemo()
useRef()
useImperativeHandle()
useLayoutEffect()
useDebugValue()

Hooks (class component) - React Component Lifecycle

Initial Phase

It is the birth phase of the lifecycle of a ReactJS component. Here, the component starts its journey on a way to the DOM. In this phase, a component contains the default Props and initial State. These default properties are done in the constructor of a component. The initial phase only occurs once and consists of the following methods.
getDefaultProps()
It is used to specify the default value of this.props. It is invoked before the creation of the component or any props from the parent is passed into it.
getInitialState()
It is used to specify the default value of this.state. It is invoked before the creation of the component.
Mounting Phase
In this phase, the instance of a component is created and inserted into the DOM. It consists of the following methods.
componentWillMount()
This is invoked immediately before a component gets rendered into the DOM. In this case, when you call setState() inside this method, the component will not re-render.
componentDidMount()
This is invoked immediately after a component gets rendered and placed on the DOM. Now, you can do any DOM querying operations.
render()
This method is defined in each and every component. It is responsible for returning a single root HTML node element. If you don't want to render anything, you can return a null or false value.
Updating Phase
componentWillReceiveProps()
It is invoked when a component receives new props. If you want to update the state in response to prop changes, you should compare this.props and nextProps to perform state transition by using this.setState() method.
shouldComponentUpdate()
It is invoked when a component decides any changes/updation to the DOM. It allows you to control the component's behavior of updating itself. If this method returns true, the component will update. Otherwise, the component will skip the updating.
componentWillUpdate()
It is invoked just before the component updating occurs. Here, you can't change the component state by invoking this.setState() method. It will not be called, if shouldComponentUpdate() returns false.
render()
It is invoked to examine this.props and this.state and return one of the following types: React elements, Arrays and fragments, Booleans or null, String and Number. If shouldComponentUpdate() returns false, the code inside render() will be invoked again to ensure that the component displays itself properly.
componentDidUpdate()
It is invoked immediately after the component updating occurs. In this method, you can put any code inside this which you want to execute once the updating occurs. This method is not invoked for the initial render.

Unmounting Phase

It is called when a component instance is destroyed and unmounted from the DOM.
componentWillUnmount()
This method is invoked immediately before a component is destroyed and unmounted permanently. It performs any necessary cleanup related task such as invalidating timers, event listeners, canceling network requests, or cleaning up DOM elements. If a component instance is unmounted, you cannot mount it again.
Context in React

Context allows passing data through the component tree without passing props down manually at every level.
In React application, we passed data in a top-down approach via props

Context API

React.createContext()
	
const MyContext = React.createContext(defaultValue);  

Context.Provider

	<MyContext.Provider value={/* some value */}>  

Context.Consumer

	<MyContext.Consumer>  
       {value => /* render something which is based on the context value */}  
</MyContext.Consumer> 

Class.contextType

	const BtnColorContext = React.createContext('btn btn-darkyellow');  
	static contextType = BtnColorContext;  








Var vs Let vs Const keywords

var is function scoped
	
Available within the function
If we declare them outside the function, then they are available everywhere i.e. they are a global variable.
	
	Example :  
{ var a = 1 }  
		console.log(a)  //output -> 1 (can access from outside)

Let and Const  are  block scoped
	
They are scoped to the block in which they are declared
If we declare them outside the function, then they are available everywhere i.e. they are a global variable.
	
	Example :  
{ let a = 1 }   or { const a = 1 }
		console.log(a)  // error  -> a is not defined

Question 1 : 

Const obj1 = {
	a: 2,
	b: 3,
};


Const obj2 = obj1;
obj2.b  = 10
console.log(obj1) // output = ?
console.log(obj2) // output = ?

Answer:

	Let address of obj1 in memory is 2000 and it’s value is { a : 2, b: 3 }
	Let address of obj2 in memory is 3000 and it’s value is nothing yet (suppose that)
	
	Const obj2 = obj1; means obj2 stores the address of the obj1 so value at 3000 (obj2) will be the address of obj1 (i.e. 2000). That is 3000 holds address 2000.

obj2.b  = 10; means value of obj2.b = 10; that is value at (2000 address).b = 10; that means updating the value in obj1 { a: 2, b: 10 } 

console.log(obj1) // output = { a: 2, b: 10 }
console.log(obj2) // output = { a: 2, b: 10 }  same output for both obj1 and obj2


Difference between ‘null’ and ‘undefined’

Undefined is a special keyword which has separate memory space.This is kept as placeholder to the variables until the variables assigned by some values.

typeof undefined is undefined

Ex: Number, function these are also keywords so if we console their typeof so output will be itself.


Why is Javascript a loosely/weakly typed language?

Reason: Javascript does not attach it’s variables to any specific data types.

var a = 10;
	a = “text”;

Value of a can be anything. Like text, number, object, undefined, null, boolean etc.

Call Stacks in javascript

CallStack is generally a data structure which consists of active sub-routines in the computer program. So when a program executes, if it sees a function call, then it is pushed onto the stack and once the function finishes the execution or returns a value, then it will be popped out from the stack.

Hoisting

Hoisting means moving the declaration part of the variable at the top of the code.

It is the process whereby the compiler allocated the memory for variable and function declaration prior to the execution of code.

Lexical Environment

It is the local memory along with the lexical environment of its parent.

Var a = 10;
Function add() { console.log(a) }  //accessing the variable a inside the function add
Temporal Dead Zone

Time between the ‘let’ and ‘const’ variable hoisted and initialized by some value is called a temporal dead zone.
When we try to access these variables in a temporal dead zone then it gives us a reference error.
Block 

Block is also called a compound statement. It is denoted by {}.
A block is used to combine the multiple javascript statements into a group.
Block Scope

Scope determines the accessibility (visibility) of variables.
Block scope
Function scope
Global scope

Before ES6 (2015), JavaScript had only Global Scope and Function Scope.
ES6 introduced two important new JavaScript keywords: let and const.
These two keywords provide Block Scope in JavaScript.
Variables declared inside a { } block cannot be accessed from outside the block.

Destructuring of Props in ReactJs
What is Destructuring?

Destructuring is a characteristic of JavaScript, It is used to take out sections of data from an array or objects, We can assign them to new variables created by the developer.
In destructuring, It does not change an array or any object, it makes a copy of the desired object or array element by assigning them in its own new variables, later we can use this new variable in React (class or functional) components.
It makes the code more clear. When we access the props using this keyword, we have to use this/ this.props throughout the program, but by the use of restructuring, we can discard this/ this.props by assigning them in new variables.
How to pass data from a child component to its parent in ReactJS ?

In the parent component, create a callback function. This callback function will retrieve the data from the child component.
Pass the callback function to the child as a props from the parent component.
The child component calls the parent callback function using props and passes the data to the parent component.
Cloning of Array
1. Spread Operator (Shallow copy)
Ever since ES6 dropped, this has been the most popular method. It’s a brief syntax and you’ll find it incredibly useful when using libraries like React and Redux.
numbers = [1, 2, 3];
numbersCopy = [...numbers];
2. Good Old for() Loop (Shallow copy)
I imagine this approach is the least popular, given how trendy functional programming’s become in our circles.
Pure or impure, declarative or imperative, it gets the job done!
numbers = [1, 2, 3];
numbersCopy = [];
 
for (i = 0; i < numbers.length; i++) {
  numbersCopy[i] = numbers[i];
}
3. Good Old while() Loop (Shallow copy)
Same as for—impure, imperative, blah, blah, blah…it works! ?
numbers = [1, 2, 3];
numbersCopy = [];
i = -1;
 
while (++i < numbers.length) {
  numbersCopy[i] = numbers[i];
}
4. Array.map (Shallow copy)
Back in modern territory, we’ll find the map function. Rooted in mathematics, map is the concept of transforming a set into another type of set, while preserving structure.
In English, that means Array.map returns an array of the same length every single time.
To double a list of numbers, use map with a double function.
numbers = [1, 2, 3];
double = (x) => x * 2;
 
numbers.map(double);
5. Array.filter (Shallow copy)
This function returns an array, just like map, but it’s not guaranteed to be the same length.
What if you’re filtering for even numbers?
[1, 2, 3].filter((x) => x % 2 === 0);
// [2]
6. Array.reduce (Shallow copy)
I almost feel bad using reduce to clone an array, because it’s so much more powerful than that. But here we go…
numbers = [1, 2, 3];
numbersCopy = numbers.reduce((newArray, element) => {
  newArray.push(element);
 return newArray;
}, []);
7. Array.slice (Shallow copy)
slice returns a shallow copy of an array based on the provided start/end index you provide.
If we want the first 3 elements:
[1, 2, 3, 4, 5].slice(0, 3);
// [1, 2, 3]
// Starts at index 0, stops at index 3
8. JSON.parse and JSON.stringify (Deep copy)
JSON.stringify turns an object into a string.
JSON.parse turns a string into an object.
Combining them can turn an object into a string, and then reverse the process to create a brand new data structure.
Note: This one safely copies deeply nested objects/arrays!
nestedNumbers = [[1], [2]];
numbersCopy = JSON.parse(JSON.stringify(nestedNumbers));
numbersCopy[0].push(300);
console.log(nestedNumbers, numbersCopy);
// [[1], [2]]
// [[1, 300], [2]]
// These two arrays are completely separate!
9. Array.concat (Shallow copy)
concat combines arrays with values or other arrays.
[1, 2, 3].concat(4); // [1, 2, 3, 4]
[1, 2, 3].concat([4, 5]); // [1, 2, 3, 4, 5]
10. Array.from (Shallow copy)
This can turn any iterable object into an array. Giving an array returns a shallow copy.
numbers = [1, 2, 3];
numbersCopy = Array.from(numbers);
// [1, 2, 3]
What is React?
React is a JavaScript library created for building fast and interactive user interfaces for web and mobile applications. It is an open-source, component-based, front-end library responsible only for the application’s view layer. In Model View Controller (MVC) architecture, the view layer is responsible for how the app looks and feels. React was created by Jordan Walke, a software engineer at Facebook. 
 
Why React?
Easy creation of dynamic applications: React makes it easier to create dynamic web applications because it requires less coding and offers more functionality, as opposed to JavaScript, where coding often gets complex very quickly.
Improved performance: React uses Virtual DOM, thereby creating web applications faster. Virtual DOM compares the components’ previous states and updates only the items in the Real DOM that were changed, instead of updating all of the components again, as conventional web applications do. 
Reusable components: Components are the building blocks of any React application, and a single app usually consists of multiple components. These components have their logic and controls, and they can be reused throughout the application, which in turn dramatically reduces the application’s development time.
Unidirectional data flow: React follows a unidirectional data flow. This means that when designing a React app, developers often nest child components within parent components. Since the data flows in a single direction, it becomes easier to debug errors and know where a problem occurs in an application at the moment in question.
Small learning curve: React is easy to learn, as it mostly combines basic HTML and JavaScript concepts with some beneficial additions. Still, as is the case with other tools and frameworks, you have to spend some time to get a proper understanding of React’s library.
It can be used for the development of both web and mobile apps: We already know that React is used for the development of web applications, but that’s not all it can do. There is a framework called React Native, derived from React itself, that is hugely popular and is used for creating beautiful mobile applications. So, in reality, React can be used for making both web and mobile applications.
Dedicated tools for easy debugging: Facebook has released a Chrome extension that can be used to debug React applications. This makes the process of debugging React web applications faster and easier.
 
Closure

Function along with its lexical scope forms a closure.
A closure is the combination of a function and the lexical environment (scope) within which that function was declared. Closures are a fundamental and powerful property of Javascript

Bubbling And Capturing

Beginning from the target and moving towards the top is the bubbling i.e. starting from the child to its parent, it moves straight upwards. But a handler can also take the decision to stop the bubbling when the event has been processed completely. In JavaScript, we use the event.stopPropagation () method.

if an element has more than one event handler on a single event, all the event handlers bubbling will get stopped using this event.stopImmediatePropagation() method

 parent.addEventListener('click', function(){  
      console.log("Parent is invoked");  
   }); 
 child.addEventListener('click', function(){  
      console.log("Child is invoked");  
   });

//output ====> child is invoked  and then Parent is invoked


 parent.addEventListener('click', function(){  
      console.log("Parent is invoked");  
    },true); 

 child.addEventListener('click', function(){  
      console.log("Child is invoked");  
   });

//output ====> Parentis invoked  and then Child is invoked

third argument of addEventListner () to true in order to enable event capturing in the parent div.

Note: Due to event capturing, the event of the parent element executes first, and then the event of the target element gets executed.

What is virtual DOM?

Virtual DOM is a representation of the DOM. The creation of a real dom will be handled by browsers. Modern frameworks like react, vue, etc.., will create a tree of elements similar to real dom in memory this is called virtual DOM.
 
Virtual DOM is a representation of real DOM. Whenever states are changed a new virtual DOM will be created and will be compared with the previous virtual DOM. And then DOM operations will be applied for those specific changes. The cost of virtual DOM is calculating diff with another virtual DOM. For a big project with lots of components, diff calculation will take time.
 
What is HOC’s in ReactJS?

HOC’s are the components in reactJS that return new components with some new logic.
HOC’s are used when some components in the project have some common logic and share the same state values.
In such a case, we can put common logic (functions and state) inside HOC’s and return an “ enhanced ”new component that will have that logic in its props.
 
What is prop drilling?
Prop drilling is the process in a React app where props are passed from one part of a tree to another by going through other parts that do not need the da ta, but only help in passing it through the tree.
 
The Solution: React Context
What is React Context?
React Context can help remove this cumbersome process of explicitly passing props around to every component in the tree for props that are required by many components in the application. So what is React Context?
 
bubbling : child to parent (upward)
capturing : parent to child (downwards)
anonymous function
IIFE
setTimeOut vs setInterval 
tap
useCallback vs useMemo
useRef 
promise (definition and usage)
shift vs unshift(practise all array property)
map,filter,reduce
store in redux
switch eslint error
how to create store
Date.toLocalString()
Unit Testing
Test driven development
 
 
Why we should hire
What is your strength
What is your weakness
How you handle argument
What is your hobby
 






