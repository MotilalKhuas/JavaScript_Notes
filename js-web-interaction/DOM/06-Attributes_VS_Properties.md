- The browser parses HTML and generates DOM objects.
- HTML attributes often map to DOM properties, but not always.





## DOM Properties
- DOM nodes are regular JavaScript objects. We can alter them.
#### exp :
```js
document.body.myData = {
  name: 'Caesar',
  title: 'Imperator'
};

document.body.sayTagName = function(){
    alert(this.tagName);
}

console.log(document.body.myData.title); // Imperator
console.log(document.body.sayTagName()); // BODY
```

DOM Properties Are Typed. Not always a string.





## HTML Attributes
When DOM Objects are created for the tags, properties are created for the standard attributes. But that doesn’t happen for non-standard attribute.
#### exp : 
```html
<body id="test" something="non-standard">
  <script>
    alert(document.body.id); // test
    // non-standard attribute does not yield a property
    alert(document.body.something); // undefined
  </script>
</body>
```
standard attribute for one element can be unknown for another one.
#### exp : 
```html
<body id="body" type="...">
  <input id="input" type="text">
  <script>
    alert(input.type); // text
    alert(body.type); // undefined: DOM property not created, because it's non-standard
  </script>
</body>
```
- #### Methods to work with attributes:
   These methods are working for both `standard` and `non-standard` attributes.
    - <mark><ins>**elem.hasAttribute(name)**</ins></mark> : checks for existence.
    -  <mark><ins>**elem.getAttribute(name)**</ins></mark> : gets the value. `There values always a string`.
    -  <mark><ins>**elem.setAttribute(name, value)**</ins></mark> : sets the value
    -  <mark><ins>**elem.removeAttribute(name)**</ins></mark> : removes the attribute.
    -  <mark><ins>**elem.attributes**</ins></mark> : read all attributes. a collection of objects with `name` and `value` properties

Attributes values are always a string.





## Property-Attribute Synchronization
Changes in attributes reflect in properties and vice versa (with exceptions)`(only true for standard attributes)`.
#### code : 
```js
input.setAttribute('id', 'id');
alert(input.id); // id (updated)

input.id = 'newId';
alert(input.getAttribute('id')); // newId (updated)

```
#### Exception: 
input.value syncs only from attribute → property.






