## className
<mark><ins>**elem.className**</ins></mark> : corresponds to the class attribute.<br>
If we assign something to elem.className, it replaces the whole string of classes.
 
exp :
```html
    <div class="div container" id="div"></div>
    <script>
        console.log(div.className); //op : div container
 
        div.className = "header";
        console.log(div.className); //op : header
    </script>
```
 
 
 
## classList
<mark><ins>**elem.classList**</ins></mark> : special object(iterable) containing all the className applied to an element.<br>
also contains methods to work with single class.
 
methods :
 
- <mark><ins>**elem.classList.add/remove("class")**</ins></mark> : adds/removes the class.
- <mark><ins>**elem.classList.toggle("class")**</ins></mark> – adds the class if it doesn’t exist, otherwise removes it.
- <mark><ins>**elem.classList.contains("class")**</ins></mark> : checks for the given class, returns true/false.
 
 
 
 
## Element Style
- <mark><ins>**elem.style**</ins></mark> : an object that corresponds to what’s written in the `"style"` attribute.<br>
 If the property is made of several words, separated by dashes, the dashes are removed and it is converted to camel case: `background-color` becomes `backgroundColor`.

    exp : 
    ```html
    <div id="div">Hello World!</div>
    <script>
        div.style.backgroundColor = "red" //Set background color to red
    </script>
    ```
- <mark><ins>**elem.style.cssText**</ins></mark> : To set the full style as a string.
    exp : 

    ```html
    <div id="div">Hello World!</div>
    <script>
        div.style.cssText = "color : red; background-color : green; text-align : center"
    </script>
    ```

    - This property is rarely used, because such assignment removes all existing styles: it does not add, but replaces them. 
    - The same can be achieved by setting an attribute : `div.setAttribute('style', 'color: red...')`.






 ## Resetting the style property
 Sometimes we want to assign a style property, and later remove it.

 - Setting the `Style property` to <mark>Empty string<mark> removes that property from the element.

    exp :
    ```html
        <div id="div" style="color : red">Hello World!</div>
        <script>
            div.style.color = "" //remove color property from div.
        </script>
    ```
- <mark><ins>**elem.style.removeProperty('style property')**</ins></mark> : can also remove a property like this.

    exp :
    ```html
        <div id="div" style="background-color : red">Hello World!</div>
        <script>
            div.style.removeProperty("background-color") //remove color property from div.
        </script>
    ```




## Computed Styles
<mark><ins>**getComputedStyle(element, [pseudo])**</ins></mark> : used to get a perticular style applied to an element.

- <ins>element</ins> :  Element to read the value for.
- <ins>pseudo</ins> : A pseudo-element if required, for instance ::before. An empty string or no argument means the element itself.

getComputedStyle requires the full property name like `paddingLeft` or `paddingTop` not `padding`. 

exp : <br>
```html
<div id="div" style="color : red">Hello World!</div>
<script>
    div.style.padding = "10px";

    computedStyle  = getComputedStyle(div);
    console.log(computedStyle.color); // op : red
    console.log(computedStyle.paddingTop); // op : 10px
</script>
```