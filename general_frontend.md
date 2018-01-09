## DOM (Document Object Model)
 - When a webpage is loaded, the browser creates a DOM
 - HTML DOM model is a tree of objects - document -> root element (html) -> element (head or body) -> element (a, h1) -> attribute
    - Standard for getting, changing, adding, deleting HTML elements
 - All HTML elements are defined as objects with properties
 
### DOM Methods
  - `document.getElementById(id)`
  - `document.getElementsByTagName(name)`
  - `document.getElementsByClassName(name)`
  
  - `element.innerHTML = new html content`
  - `element.attribute = new value`
  - `element.setAttribute(attribute, value)`
  - `element.style.property = new style`
  
```html 
<html>
<body>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = "Hello World!";
</script>

</body>
</html>
```

### Collections

#### HTMLCollection
 - HTMLCollection object is like an array
   - Access elements by index number, name, or id
   - Can't use array methods pop, push, join...
   
```javascript 
var myCollection = document.getElementsByTagName("p");
var i;
for (i = 0; i < myCollection.length; i++) {
    myCollection[i].style.backgroundColor = "red";
}
```
#### NodeList
 - Collection of document nodes like an array
   - Can only be accessed by their index number
   - Objects can contain attribute nodes and text nodes
 - All browsers return a NodeList object for the property childNodes. 
 - Most browsers return a NodeList object for the method querySelectorAll().
 
