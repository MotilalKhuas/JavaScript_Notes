# Browser environment, specs
There is a "root" object called <mark>window</mark>. It has two roles:
- First, it is a <mark>global object</mark> for Javascript Code.
- Second, it represents the <mark>browser window</mark> and provides methods to control it.

<div style = "display : flex; justify-content : center">
    <img src="./assets/window-obj.png" alt="window-object" style="height: 200px; width:200px;"/>
</div>

## DOM (Document Object Model)
Represnts all page content as an <mark>object</mark> that can be modified.
That object is called <mark><ins>***document***</ins></mark>. The document is the main entry point to the page. We can change or create anything on the page by using it.

> [!NOTE]
> Non-Browser instruments also uses DOM too. <br>
>   - exp : Server-side script that download HTML pages and process them can also use the DOM.


## BOM (Browser Object Model)
Represents additional objects provided by the browser(host environment) for working with everything <mark>except the document</mark>.
