-                   JAVASCRIPT

- 1) What is your favourite new javascript feature and why?

Most of javascript's new feature are my favorite, mainly ```Promise``` and ```spread operator```are my favorite.

 - A) ```Promise```

 Let me explain why and how I use them.
consider the following Api call with callback

```
export function getList() {
  return fetch('http://localhost:3333/list')
    .then(data => data.json())
}
```
and see here the api call transformed to async/await using promise

```
export async function getListAsync () {
  return await new Promise(resolve => {
    fetch('http://localhost:3333/list')
      .then(data => resolve(data.json()))
  })
}
```

 ```
 getList().then(jsonData => {
  // jsonData is available only in the callback
})
```
 The following line depends on ```jsonData```,
but will not get it, and will error some way, since it's outside the callback

```console.log(jsonData)```

But look the following line of code

```const jsonData = await getListAsync()```

The following line depends on jsonData,
and gets it, and will run as intended, since the await in the above line
waits until jsonData is available

```console.log(jsonData)```

For the above reason promise is one of my favourite new features of javascript. 



- B) ```Spread operator```
This is used to easly concaitnate two different states with out overriding problems. 

``` 
var myState = {name : 'Dawit', age : 26}
var myNewState = {...myState,residence : 'Addis Ababa'}

console.log(myNewState) // {name: "Dawit", age: 26, residence: "Addis Ababa"}
```

- 2) I usually use the above two features based on the use case I would be faced.



- 3)Is there any difference between regular function syntax and the shorter arrow function syntax? (Write the answer in your own words)? 
Yes there are some diffrences. Let us see some differences.The first difference is there way of signature as follows.
```
//Regular function declaration

 function myRegularFunc (x,y){
      return x + y
}

//Arrow function declaration

const myArrowFunc = (x,y) =>{
return x + y 
}
```
The second difference is the value of ```this``` keyword.
The value ```this``` keyword in regular function is different from that of arrow function.
Consider the following example.
```
var myGlobalName = "Dawit"
let myObject = {
    name : "me",
    arrowFunc: () => {
        console.log(this.name);  // prints Dawit
    },
    regularFunc() {
        console.log(this.name); // prints me
    }   
}
```
So, ```this``` inside an arrow function always refers to the outer context, whereas in regular function, ```this``` changes according to the way that function is invoked.


Third difference arrow functions don't know the ```arguments``` keyword but regular functions do.

```

function regularFunction(a,b) {
  console.log(arguments)
}
regularFunction(1,2) // {0: 1, 1: 2}

const arrowFunction = (a,b) => {
  console.log(arguments)
}
arrowFunction(1,2) // arguments is not defined
```
Forth difference is in regular function, we have to use ```return``` keyword to return any value. If we don’t return anything then the function will return undefined.
```
function regularFunc() {
  return "my name"
}
console.log(regularFunc()) // prints my name

const arrowFunc = () => "my name";
console.log(arrowFunc()) //prints my name
```
if we remove the return keyword in the regrular function it will not work as expected. But arrow function works with out saying return. 
In addition to that, if the arrow function contains one expression, we can omit the curly braces, and then the expression will be implicitly returned.
The fifth differnce is that arrow functions can never be used as constructor functions.
The above differnces are not the only diffrences.

- 4) What is the difference between ‘myFunctionCall(++foo)’   and  ‘myFunctionCall(foo++)’
When we call myFunctionCall with ```++foo``` first ```foo``` is increamented then the increamented ```foo``` is used by the function but when we call myFunctionCall with ```foo++``` the function is called first with ```foo``` then the variable ```foo``` is increamented. 

-5 In your own words, explain what a javascript ‘class’ is and how it differs from a function.
In javascript class is a template to create an object.Class contains data that explains the general behavior of a certain thing Whereas function does a certain specific thing. And functions in javascript are first class citizens because we can treat them as values and we can return functions from another function.



-                           CSS

- 6) In your own words, explain css specificity.
Css Specificity is a mechanism that we give priority for css selectors when there are two or more CSS rules that point to the same element, that means the selector with the highest specificity value will override, and its style declaration will be applied to that element.

- 7) In your own words, explain what is ‘!important’ in css.  Also how does it work?  Are there any special circumstances when using it, where its behavior might not be what you expect?
The ```!important``` is a rule that overrides all previous styling rules for a specific property on an element. It works by overriding all the previous styles applied to an element and it forces the element to maintain its  style declaration without considering the specificity of the selector.

Yes there are some occasions that we do not get the expected output from ```!important```.
Example consider the following scenario.
```
#AppId {
 background-color: yellow !important;
}

.App {
 background-color: red !important;
}
```
In the above css snippet we expect the background color to be red but finally we get yellow.

- 8) What is your prefered layout system: inline-block, floating + clearing, flex, grid, other?  And why?
I prefer flex and grid for most of my layouts. When I need the content to shape the layout, I use flex And when I want the layout to shape the content and also to make it responsive I use grid. I prefer a grid for tabular content.

- 9) Are negative margins legal and what do they do (margin: -20px)?

Yes, as long as we use them to bring elements closer together than their box model properties would allow.
But if we misuse negative margins like when it is used to make up incorrect layouts elsewhere on the site it is bad practice. Because it will make it difficult to debug and harder to read our CSS. Generally negative margin shifts the boundary of an element in the opposite direct So if an element has a margin of -20px, it will have the effect of squeezing the boundary of the element by 20px from all directions. Elements above it will move down by -20 and elements below it will move up by -20, possibly overlapping if the height of the element is less than 40px. Elements to the left will appear to have shifted by 20px to the right, and elements to the right will appear to have shifted by 20px to the left, so again possibly overlapping if the width of the element is less than 40px.


- 10) If a ```div``` has no margin or other styling and a ```p``` tag inside of it has a margin top of some kind, the margin from the ```p``` tag will show up on the div instead (the margin will show above the div not inside of it), why is this?  What are the different things that can be done to prevent it?

Margin does not affect the child's position in relation to its parent, unless the parent has padding, in which case most browsers will then add the child's margin to the parent's padding.
To prevent this we can use the following two solutions.
Solution one, giving top margin value zero for the child component and giving the amount of margin value as a padding value for the parent component.
Solution two, simply adding a style ```display:inline-block``` to child element prevents that issue. 

-                      UNIT TESTS

- 11) What technologies do you use to unit test your react components?
I use RTL + Jest.

- 12) Are there any pitfalls associated with this technology that have caused you difficulty in the past?
No pitfalls.

- 13) How do you test in your unit tests to see if the correct properties are being passed to child components.


-                       REACT TEST

The folloing code comporises all the react test steps

```
import React, { useEffect, useState } from "react";

const getWindowSize = () => {              // 
  const { innerWidth, innerHeight } = window;
  return { innerWidth, innerHeight };
};

let divHeight;
window.setDivHeight = (height) => (divHeight = height);

function LiveWidthContainer({ newHeight }) {
  const [windowWidth, setWindowWidth] = useState(getWindowSize()); //state for step one
  const [divHeight, setDivHeight] = useState(0);

  useEffect(() => {
    const handleResize = () => {
      setWindowWidth(getWindowSize());
    };

    window.addEventListener("resize", handleResize);
    return () => {
      window.removeEventListener("resize", handleResize);
    };
  }, []);

  useEffect(() => {
    setDivHeight(newHeight);
  }, [newHeight]);

  const onKeyPress = (event) => {
    // arrow function keeps scope
    setTimeout(() => {
      // now it is the value after the keypress, because at the time of key press the value is not found
      setDivHeight(event.target.value);
    }, 0);
  };

  return (
    <div
      className="widthContainer"
      style={{
        border: "1px red solid",
        height: `${divHeight}px`
      }}
    >
      <span>{windowWidth.innerWidth}</span>
      <input onKeyPress={onKeyPress} value={divHeight} type="text" />
    </div>
  );
}

// HOC
const withHeight = (WrappedComponent) => (props) => {
  const [newHeight, setHeight] = useState();
  setInterval(() => {
    setHeight(divHeight);
  }, 50);
  return <WrappedComponent {...props} newHeight={newHeight} />;
};

export default withHeight(LiveWidthContainer);
```















