# Bootstrap4:
  ==============

+ Bootstrap is the most popular front end framework to build responsive websites faster and easily
+ It includes html,css based design templates and optional js plugins(jquery and popper js files)
+ It is compatable with all moder browsers


# Colors:
=========
  class       |  color
  ------------|--------
   primary      |  blue
   secondary    |  gray 
   info | sky blue
   success | green
   warning | orange
   dange | red
   dark | black
   light |  text as light gray(white background)
   white |  text as white (white background)


# Gird system:
==============

+ Gridsystem involve main role for responsiveness of an application
+ Grid system has 5 default classes with respective devices to achieve responsive of a web page
+ 12 columns for each row in a page

    .         | Exatra small  (<576px) | small    (>=576px)   |Medium  devices (>=768px)  |  Large devices  (>=992px)   |Extra large devices (>=1200px)
    ------------------| -----------------------|----------------------|---------------------------|-----------------------------|-------------------------------         
    class prefix      | .col                   |         .col-sm      |           .col-md         |     .col-lg                 |.col-xs     
    No of columns  |12|12|12|12|12

# Tables:
==========
 - .table table-bordered
    - table-striped
    - table-dark
    - thead-dark
    - table-hover
    - table-borderless
 - We can apply contextual class for table
    
    
# JSON:
  + **JSON** - JavaScript Object Notation
  + Json mainly used to store and transfer data between the webapplications and servers
  + JSon filename extension is **.json**
  + Json data is a pair of key and value( Key is a string,value is any datatype)
  + Data should be separated by cammas
 
### JSON Datatypes:
===================
+ Number
+ String
+ Object
+ Array
+ Boolean
+ Null

Example:
========
```
{
	"profile":{
		"name":"Kalyan",
		"Age":25,
		"Collegues":["Sam","Ankith","Jack"],
		"Education":{
			"SSC":"St.Marys High School in Vijayawada",
			"Inter":"Nri junior college at guntur",
			"B.tech":"Universal college"
		}
	}
}
```

# Fetch API:
=============

+ fetch method return a promise to the response to that request
+ fetch method has one argument is must and it is a path for the resourse file
+ it returns a response and it may be text or blob or json
+ We have to use a server(Here we are using a web server for chrome)


Example for response text:
==========================
```
fetch('data.txt')
.then(response=> response.text())
.then(function(data){
	console.log(data);
})
```
Example for fetch blob(image):
===============================
```
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
<img src="" id="image1">
<script type="text/javascript">
	fetch('images/admin.png').then(
		function(response) {
	// return response.blob()
	console.log(response);
	return response.blob();
}).then(blob =>{
	console.log(blob);
	document.getElementById("imkage1").src=URL.createObjectURL(blob);
}).catch(error=>{
	console.error(error);
	console.log("error!");
})
</script>
</body>
</html>
```
Example for fetch json to html page:
====================================
```
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
<img src="" id="image1">
<div class="main">
	<div class="left">
		
	</div>
	<div class="right">
		
	</div>
</div>
<script type="text/javascript">
	fetch('data.json').then(
		function(response) {
	// return response.blob()
	console.log(response);
	return response.json();
}).then(data =>{
	console.log(data);
	profile(data.profile)
}).catch(error=>{
	console.error(error);
	console.log("error!");
})

var main=document.querySelector('.main');
var left=document.querySelector('.left');

var profile= function (info){

	var h2=document.createElement("h2");
	h2.textContent=info.name;
	left.appendChild(h2);
}

	main.appendChild(left);
</script>
</body>
</html>
```

# forEach and map functions

+ Both are applicable for arrays
### foreach:
+ the data can return in the form of normal elements ,when array is not const
```
 let myAwesomeArray = [1, 2, 3, 4, 5]
myAwesomeArray.forEach(x =>console.log( x*2))

o/p: 2
4
6
8
10
```
+ If array is const foreEach returns undefined
```
 const myAwesomeArray = [1, 2, 3, 4, 5]
const demo=myAwesomeArray.forEach(x => x*2)
console.log(demo);
o/p: is undefined
```

## map:
=======
+ If array is const map returns new array with transmission of data
```
 const myAwesomeArray = [1, 2, 3, 4, 5]
const demo=myAwesomeArray.map(x => x*2)
console.log(demo);
```


#Props :
========

+ Props is like arguments in function
+ Props can be passed from parent component to child component(uni directional flow)
+ Data from props is read only

## props with Finctional component:
===================================
+ letus consider Banks as parent Component,  Andhra(func) and Corp(class) as ChildComponent

Banks.js:
=========
```
import React from 'react';
import Andhra from './Andhra';
import Corp from './Corp';

const Banks = () =>{
return (
	<div>
	<h1>Banks is a Parent Component</h1>

       <Andhra name="Andhra bank"/>
       <Corp name="Corporation Bank" />
	</div>);
}

export default Banks;
```

Andhra.js:
=========
```
import React from 'react';

const Andhra =(props)=>{
	console.log(props.name);
	return <div> 
	
	<h2>Name is:{props.name}</h2>

	</div>
}

export default Andhra;
```
Corp.js:
========
```
import React,{Component} from 'react';


class Corp extends Component{
          
         render(props){
                // console.log(this.props);
         	return (

         		<div>

                   {this.props.name}
         		</div>);
         }
}

export default Corp;

```
# States:

+  States are initialized and managed by Component
+  By using series of constructor(),super() method and state object we can initalized data (we can also take data directly as state object)
+  Data can be updated by using setState() method

Example:
========
```
import React,{Component} from 'react';



class Employee extends Component{
     
     constructor(){
     	super();
     	this.state={name:"Kalyan"};
     }
     // state={name:"Kalyan"};

render(){
	setTimeout(()=>this.setState({name:"Sam"}),3000)
	return  ( 
		<div> 
		    {this.state.name}
		</div>);
}

}

export default Employee;
```

Example2:
=========
```
import React,{Component} from 'react';



class Employees extends Component{
     constructor(){
     	super();
    this.state={
    	Users:[
    	{name:"Kalyan",age:20},
    	{name:"Kalyan ram",age:25},
    	{name:"Jack",age:21},
    	]
    }

}

changeAge=()=>{
	this.setState({
		Users:[
    	{name:"Kalyan",age:15},
    	{name:"Kalyan ram",age:20},
    	{name:"Jack Sparrow",age:20},
    	]
	})
}
render(){
	// setTimeout(()=>this.setState({name:"Sam"}),3000)
	return  ( 
		<div> 
		    {this.state.Users[0].name} age is {this.state.Users[0].age}
		    
		    {this.state.Users[1].name}age is{this.state.Users[1].age}
	         {this.state.Users[2].name}age is{this.state.Users[2].age}
		    
		    
		    <button onClick={this.changeAge}>Change age of employee </button>
		</div>);
}

}

export default Employees;
```

# Hooks
  + Hooks are new addition to React V16.8
  + They let you use state and other React features without writing a class
  + Hooks don't work in classes
  + Basic Hooks
  	- useState
	- useEffect
	- useContext

## useState
+  useState returns a pair: the current state value and a function that lets you update it
+  value may be integer or string or object
	+ const [age, setAge] = useState(42);
	+ const [fruit, setFruit] = useState('banana');
        + const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);

Example:
==========

```import React, { useState } from 'react';  
  
function CountApp() {  
  // Declare a new state variable, which we'll call "count"  
  
  const [count, setCount] = useState(0);  
  
  return (  
    <div>  
      <p>Score : </p>  
      <button onClick={() => setCount(count + 1)}>  
       {count} 
      </button>  
    </div>  
  );  
}  
export default CountApp; 
```

## useEffect

+ When you call useEffect, you’re telling React to run your “effect” function after flushing changes to the DOM
+ Adds the ability to perform side effects from a function component
+ It serves the same purpose as componentDidMount, componentDidUpdate, and componentWillUnmount in React classes, but unified into a single API

Example:
=========

```
import React, { useState, useEffect } from 'react';

function CountApp() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

export default CountApp;
```


  
