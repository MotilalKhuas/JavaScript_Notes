## Node Type
<mark><ins>**nodeType**</ins></mark> provides a numeric value representing the type of a node:
- `1` : Element Node
- `2` : Attribute Node
- `3` : Text Node
- `8` : Comment Node
- `9` : Document Node
- `11` :  Document Fragment
#### exp :
```html
<body>
  <script>
    let elem = document.body;
 
    alert(elem.nodeType);             // 1 => element
    alert(elem.firstChild.nodeType);  // 3 => text
    alert( document.nodeType );       // 9
  </script>
</body>
```
 
 
 
 
 
## Node Name and Tag Name
- <mark><ins>**tagName**</ins></mark> : returns tag name(applies to only element node)
- <mark><ins>**nodeName**</ins></mark> : returns name of any node (applies to any type of nodes)
    - for elements it means the same as `tagName`.
    - for other node types (text, comment, etc.) it has a string with the node type.
 
#### exp :
```html
    <body><!-- This is a comment -->
        <script>
            console.log(document.body.tagName); //BODY
            console.log(document.body.nodeName); // BODY
 
            console.log(document.body.firstChild.tagName); //undefined
            console.log(document.body.firstChild.nodeName); //#comment
 
            console.log(document.tagName); //undefined
            console.log(document.nodeName); //#document
        </script>
    </body>
````
 
## HTML content of an Element
<mark><ins>**innerHTML**</ins></mark> property allows to <ins>`get or set`</ins> the HTML inside the element as a string.
 
#### exp :
```js
console.log(document.body.innerHTML); // read the current contents
document.body.innerHTML = "<h1>Updated Content</h1>"; //replace it
```
> [!NOTE]
> ### Scripts don't execute
> If innerHTML inserts a `<script>` tag into the document – it becomes a part of HTML, but doesn’t execute.
 
> [!NOTE]
> ### Beware: “innerHTML+=” does a full overwrite
> Appending using innerHTML += is inefficient because it causes the entire HTML content to reload.
> #### exp :
> ```js
> div.innerHTML += "<p>New paragraph</p>"; // Causes full overwrite & re-render
> ```
> innerHTML+= does this
> - The old contents is removed.
> - The new innerHTML is written instead (a concatenation of the old and the new one).
> - As the content is “zeroed-out” and rewritten from the scratch, all images and other resources will be reloaded.
 
 
 
 
 
 
## Full HTML content of an element
<mark><ins>**outerHTML**</ins></mark> returns : HTML structure of an element  +  the element itself.

> [!CAUTION]
> ### unlike innerHTML, writing to outerHTML does not change the element. Instead, it replaces it in the DOM.
> #### exp : 
> ```html
> <div>Hello, world!</div>
> <script>
>  let div = document.querySelector('div');
>
>  // replace div.outerHTML with <p>...</p>
>  div.outerHTML = '<p>A new element</p>'; // (*)
>
>  // Wow! 'div' is still the same!
>  alert(div.outerHTML); // <div>Hello, world!</div> (**)
> </script>
> ```
> - `div` was removed from the document.
> - Another piece of HTML `<p>A new element</p>` was inserted in its place.
> - `div` still has its old value. The new HTML wasn’t saved to any variable.
>
> The outerHTML assignment does not modify the DOM element (the object referenced by, in this case, the variable ‘div’), but removes it from the DOM and inserts the new HTML in its place.






## Text node content
The `innerHTML` property is only valid for `element nodes`.
<br><br>
<mark><ins>**nodeValue**</ins></mark>, <mark><ins>**data**</ins></mark> : used to get the content from a text or comment nodes.
#### exp : 
```html
<body>
  Hello
  <!-- Comment -->
  <script>
    let text = document.body.firstChild;
    console.log(text.data);         // '\n        Hello\n        '

    let comment = text.nextSibling;
    console.log(comment.data);      // ' Comment '

    console.log(document.body.data) // undefined
  </script>
</body>
```





## Text Content of any Node
<mark><ins>**textContent**</ins></mark> : returns the text inside an node, ignoring any HTML tags.
#### exp : 
```html
<div id="news">
    <h1>Headline!</h1>
    <p>Martians attack people!</p>
</div>
        
<script>
    console.log(document.getElementById("news").textContent);
    //      Headline!
    //      Martians attack people!

    console.log(document.getElementById("news").innerHTML);
    //      <h1>Headline!</h1>
    //      <p>Martians attack people!</p>
</script>
```
- With `innerHTM`L` we’ll have it inserted “as HTML”, with all HTML tags.
- With `textContent` we’ll have it inserted “as text”, all symbols are treated as string.





## Hidden Property
The hidden property controls the visibility of an element, similar to display: none in CSS.
<br>
Useful for toggling UI elements dynamically.

#### exp : 
```js
document.getElementById("elem").hidden = true;
setTimeout(() => document.getElementById("elem").hidden = false, 2000); // Show after 2 seconds
```