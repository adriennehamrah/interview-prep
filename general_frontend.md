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
  
```html <html>
<body>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = "Hello World!";
</script>

</body>
</html>
```
  
