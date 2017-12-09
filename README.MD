# Polymer Training
## Objective
- Training
- Build Components
- Build App
- Hackathon

---
## Day 1
### Intro to ES6
- Let, Const
- Template Literals
- Object Oriented JS
- Arrow Functions
- Classes & Instance
- Methods

### Web Components
- Custom Elements
- Shadow DOM
- HTML Imports
- Templates
- Polyfills

Node.js, Bower, Web Server

---
## Day 2
### Intro to Polymer
- Elements / Components
- Custom Component
- Extending Element

### Custom Element Creation
- Imports & APIs
- Legacy Elements / Behaviors
- Attribute Mapping
- Attribute Deserialisation
- Property Configuration

---
## Day 3
### Binding Concepts & Styling
- Observable / Unobservable
- Data Path
- Material Design
- Custom Styling
- Layouts - Grid / Tab

### Polymer Elements Catalog
- App
- IronPaper
- Gold
- Others

---
## Day 4
### Performance & Testing
- PRPL Pattern
- Lighthouse
- Lazy Load
- Web / Offline Storage
- WCT

### Best Practices
- HTML
- CSS
- JS
- Polymer

---
https://goo.gl/PwYgBa

## JS fundamentals  -  es 6

### Basic js concepts.
Literals
* string
    * `'Single Quote'`
    * `"Double Quote"`
    * `` Template
* number
* boolean
* object
* null
* undefined
* functions
* NaN

``` js
// number
var x = 20;
//string
var firstName = 'Jack';
var lastName = "Sparrow";
var location = 'Caribbean';
var workLocation = `${name} is
                    from ${mylocation}`;
var isWorking = true;
var salary;

console.log(`${x} ${name} ${workLocation} ${isWorking}`);
console.log(`Salary is ${salary}`)//undefined variable does not have valid literal.
```
---
### Functions
Functions are building blocks of js

Flav 1
``` js
function sayHello() {
    console.log('Hello!');
}
sayHello();
```
Flav 2.1 - Function as literal.
```js
// function is assigned to a variable
// variable is used to invoke function
function sayHai() {
    console.log('Hai');
}
var hai = sayHai;
hai();
```
Flav 2.2
```js
var greet = function sayGreet() {
    console.log('greet!');
};
greet();
```
Flav 2.3
```js
var display = function () {
    console.log('display!');
};
display();
```
---
## ES 6 Function Pattern.
### Arrow function / Lamdas Expression

```js
var displayArrow = () => console.log('display Arrow!');
displayArrow();
```
### Parameters and return types.
Function can take any literal, return any literal
```js
var getName = function (name) {
    console(`Name is ${name}`);
    return name;
};
```
```js
var getName = (name)=> console(`Name is ${name}`);
```
```js
var getName = name=> console(`Name is ${name}`);
```
```js
var getName = name => name;
```
```js
var getName = (fName,lName) => {
    return `${fName} ${lName}`
}
console.log(getName('Jack','Sparrow'));
```
---
## Initialize object property

Direct
```js
function Employee() {
    //object variable - properties
    this.id = 1;
    this.name = 'Jack Sparrow';
    //methods
    this.calculateSalary = function () {
        return 1000;
    }
}
```
After object creation
```js
var emp = new Employee();
emp.id = 9000;
```
During object creation.

constructor overloading

### Property Access

instance variable inside class.

Access property
```js
//read
variable.propertyname
//write
variable.propertyname ='value'
```

```js
function Employee() {
    this.id = 1;
}
var emp = new Employee();

//get api is called
console.log(emp.id);

//set api is called
emp.id = 9000;

console.log(emp);
```

```js
class GetThings{
    constructor(length) {
        this._length = length;
    }
    //overriding
    set length(val) {
        this._length = val *10;
    }
    get length() {
        return this._length;
    }
}
let things = new GetThings(10);
things.length = 20;
console.log(things.length);
console.log(GetThings.display());
```
```html
<input type="text" value="hello">
```
```js
class HTMLInputElement{
     constructor(){
       this.type='';
       this.value=''
    }
    set type(val){
       this.setAttribute('type',val)
       }
    get type(){
        if(type==='text'){
            return this.type[value];
        }
    }

}
var input=new HTMLInputElement();
input.type='text'
```

### static methods:
```js
static display() {
    return 'Static api!';
}
console.log(GetThings.display());
```

### let, const

Your code
```js
function sayHai(name) {
    if (name) {
        console.log('if is called!');
        var message = 'Welcome' + name;
    }
    return message;
}
```
parser generated code
```js
function sayHai(name) {
 var message;
    if (name) {
        console.log('if is called!');
         message= 'Welcome' + name;
    }
    return message;
}
```

const
```js
const pi = 3.14
pi = 99.99
console.log(pi)
```

let has block scope,which var does not have.
scope:visibility of variable, function, class.

iife function pattern ```(function(){}())```;

```js
//global scope
var x = 10;

//local scope or function scope
function sayHello() {
    var name = 'test';
}
sayHello();
console.log(name);

//block scope - if(){ var x=100;}
function sayHai(name) {
    if (name) {
        console.log('if is called!');
        var message = 'Welcome' + name;
        //let message = 'Welcome' + name;
    }
    return message;
}
//console.log(sayHai('ram'));
console.log(sayHai());
//undefined - the variable is there but not having value
```
### Concurrency

doing multiple things at the same time.
Non-blocking

OS -----> Multi process.
Process ----> Sub process (threads)

How to implement application level concurrency?

1. Threads
2. Event loop, Event Queue

Concurrency, also called as async

Javascript is single threaded and does not support multi threading

Callbacks / Async / Concurrency

1. pass the function to another function as parameter

```js
let greetMe = (greeter) => {
    //invoke function
    //bind event
    setTimeout(() => {
        let result = greeter('Jack Sparrow');
        console.log(result);
    }, 1000); //here 1000(timeout) ms is event
}

//variable way
let hai = name => 'Hai' + name;
greetMe(hai);

//direct way
greetMe(name => {
    return 'Hello' + name;
});
//greetMe(function (name) { })
```

```js
function add(a, b) {
    return a+b
}
add(10, 10); //passing literal directly
var x = 10, y = 20;
add(x, y); //via variable
```
---

## WebComponents

- Object which represents GUI elements,and reusable.

- Create WebComponent by extending existing HTML Elements.

### Standard / Spec (W3C)
1. Custom elements
 ```<ns-header>, <hcl-app>```

2. Shadow DOM
    - Light DOM  -  Document DOM
    - Shadow DOM -  Document Fragment

3. HTML imports
    - Linking html with html.

4. Templates
    - Describe elements structure

Generally the spec not implemented fully in all browsers.

### Polyfill
Runtime wrapper for older browsers.

### Webcomponents.js
- Webcomponents -v 0  - ES 5 Standard
- Webcomponents -v 1  - ES 6 Standard.

1. create custom element.
```document.registerElement('ns-header')```

2. create class which extends HTMLElement

```js
// extend HTMLElement
var HeaderComponentProto = Object.create(HTMLElement.prototype);
// add template using lifecycle
HeaderComponentProto.createdCallback = function() {
this.innerHTML = '<h1>Weclome to WebComponents</h1>';
};
var HeaderComponent = document.registerElement('ns-header', {prototype: HeaderComponentProto});
// insert in current body
document.body.appendChild(new HeaderComponent());
```

### Shadow DOM
Encapsulated DOM

1. Enable Shadow DOM
```js
var shadow = this.createShadowRoot();
```

2. Encapulate Your Template
```js
shadow.innerHTML = '<h1>Welcome To webComponents</h1>';
```

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>WebComponent</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
    </head>
    <body>
        <h1>Wecomponents</h1>
        <script>
            //Create Our Object  by extending HTMLElement
            const HeaderComponentProto = Object.create(HTMLElement.prototype);
            //Add /Override Element Callback to stamp template
            HeaderComponentProto.createdCallback = function() {
            //create Shadow dom tree
            const shadow = this.createShadowRoot();
            //template is basically defined through innerHTML property
            shadow.innerHTML = `
                <style>
                    div{
                    width:100%;
                    height:100px;
                    background:#333;
                    color:#FFF;
                    }
                </style>
                <div>
                    <h1>Weclome to WebComponents</h1>
                    <h2>Welcome to HCL </h2>
                </div>
                `;
          };
          //register element
          const HeaderComponent = document.registerElement('ns-header',
                           {prototype: HeaderComponentProto});
          //create HeaderComponent Object
          const headerelement =new HeaderComponent();
          //attach element to body.
          document.body.appendChild(headerelement);
      </script>
    </body>
</html>
```

### Templates

```html
<template id="headertemplate"></template>
```
.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title></title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
    </head>
    <body>
   <template id="header-tpl">
   <style>
          h1 { color: orange; }
   </style>
       <h1>Introduction to WebComponents</h1>
   </template>
   <script>
   const HeaderComponentProto = Object.create(HTMLElement.prototype);
    HeaderComponentProto.createdCallback = function() {
        //Template
       const template=document.querySelector("#header-tpl");
       console.dir(template);
       const clone = document.importNode(template.content, true);
       this.createShadowRoot().appendChild(clone);
    };
    var HeaderComponent = document.registerElement('ns-header',
    {prototype: HeaderComponentProto});
        const headerelement =new HeaderComponent();
          //attach element to body.
          document.body.appendChild(headerelement);
   </script>


</body>
</html>
```
**HTML imports spec**
```html
<link rel="import" href="header-element.html">
```
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>WebCompoents</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <!--Include Polyfil-webComponent !-->
        <script src="/bower_components/webcomponentsjs/webcomponents-loader.js"></script>
        <!--lnclude component-->
        <link rel="import" href="header-element.html">
    </head>
    <body>
      <ns-header></ns-header>
    </body>
</html>

<template id="header-tpl">
      <h1>Weclome to WebComponents</h1>
 </template>
 <script>
    const doc = this.document.currentScript.ownerDocument;
    const HeaderComponentProto = Object.create(HTMLElement.prototype);
    HeaderComponentProto.createdCallback = function() {
       var template=doc.querySelector("#header-tpl");
       console.log(template)
       var clone = document.importNode(template.content, true);
       this.createShadowRoot().appendChild(clone);
    };
    var HeaderComponent = document.registerElement('ns-header',
    {prototype: HeaderComponentProto});
</script>
```
### Custom Elements V1 -ES 6 implementation:

Pattern 1
```js
class  MyElement extends HTMLElement{

}
window.customElements.define('ns-header',MyElement);
```
Pattern2
```js
window.customElements.define('ns-header',class HeaderComponent extends
HTMLElement{

});
```
header-element.js
```js
class HeaderComponent extends HTMLElement {
    constructor() {
        super();
        console.log('Element is created!');
    }
}
window.customElements.define('ns-header',HeaderComponent)
```
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>WebCompoents -ES 6</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <!--Include Polyfil-webComponent !-->
        <script src="/bower_components/webcomponentsjs/webcomponents-loader.js"></script>
     </head>
    <body>
     <script src="/componentsjs/header-component.js"></script>
     <ns-header></ns-header>
    </body>
</html>
```

### Rules on creating custom elements

1. The name of a custom element must contain a dash (-). So ```<x-tags>```, ```<my-element>``` and ```<my-awesome-app>``` are all valid names, while ```<tabs>``` and ```<foo_bar>``` are not. This requirement is so the HTML parser can distinguish custom elements from regular elements. It also ensures forward compatibility when new tags are added to HTML.

2. You can't register the same tag more than once. Attempting to do so will throw a DOMException. Once you've told the browser about a new tag, that's it. No take backs.

3. Custom elements cannot be self-closing because HTML only allows a few elements to be self-closing. Always write a closing tag ```<app-drawer></app-drawer>```.

ps: element name - projectname/productname ing-header

### Element Inheritance:

Element can inherit other Elements.
```js
class HeaderComponent extends HTMLElement {
    constructor() {
        super();
        console.log('Element is created!');
    }
}
window.customElements.define('ns-header', HeaderComponent)

class HeaderFancyComponent extends HeaderComponent {
    constructor() {
        super();
        console.log('HeaderFancy Component')
    }
}
window.customElements.define('ns-fancy-header', HeaderFancyComponent)
```
Inherit HTML specif elements like button,div,h1
```js
class FancyButton extends HTMLButtonElement{

}
customElements.define('fancy-button', FancyButton, {extends: 'button'});
```
### Custom Element Reactions

### Callback APIs
1. **constructor**
An instance of the element is created or upgraded. Useful for initializing state, settings up event listeners, or creating shadow dom. See the spec for restrictions on what you can do in the constructor.

2. **connectedCallback**
Called every time the element is inserted into the DOM. Useful for running setup code, such as fetching resources or rendering. Generally, you should try to delay work until this time.

3. **disconnectedCallback**
Called every time the element is removed from the DOM. Useful for running clean up code (removing event listeners, etc.).

4. **attributeChangedCallback(attrName, oldVal, newVal)**
An attribute was added, removed, updated, or replaced. Also called for initial values when an element is created by the parser, or upgraded. Note: only attributes listed in the observedAttributes property will receive this callback

5. **adoptedCallback**
The custom element has been moved into a new document (e.g. someone called document.adoptNode(el)).

### Observing changes to attributes

<ns-header name="Jack"></ns-header>

1. Elements can react to attribute changes by defining a   attributeChangedCallback.

2. The browser will call this method for every change to
  attributes listed in the "observedAttributes" array.

3. Override set / get methods for each attribute.
```js
get name() {
  return this.hasAttribute('name');
}
set name(val) {
  if (val) {
    this.setAttribute('name', val);
  } else {
    this.removeAttribute('name');
  }
}
```
### Template Registration:
```js
constructor(){
 // Attach a shadow root to the element.
    let shadowRoot = this.attachShadow({mode: 'open'});
    shadowRoot.innerHTML = `
      <style>:host { ... }</style> <!-- look ma, scoped styles -->
      <b>I'm in shadow dom!</b>
}
```

### Slot

Place holder for child content injection.

```html
<ns-header>
   <img slot="pictureslot" src=""></img>
   <h1 slot="title">Awesome</h1>
</ns-header>
```
