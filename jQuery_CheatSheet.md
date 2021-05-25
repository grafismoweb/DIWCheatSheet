# jQuery

jQuery es una librería de JavaScript.

Solo con javascript:
~~~
let el = document.getElementById("start");
el.innerHTML = "Go";
~~~

Lo mismo con jQuery:
~~~
$("#start").html("Go");
~~~


## Cómo usar jQuery

### Descargar y enlazar

Se puede descargar el archivo o apuntar hacia el archivo online, pero siempre hay que referenciarlo en el head del HTML de mi web entre etiquetas `<script></script>`:

~~~
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
        <script src="https://code.jquery.com/jquery-3.1.1.js"></script>
    </head>
    <body>
    </body>
</html>
~~~


### Evento de carga de la página (todo el código jQuery va dentro de la función).

Hay que evitar llamar con jQuery a algún elemento HTML que aún no exista.  
Debemos asegurarnos que la web en html esté acargada completamente antes de usar jQuery, por eso usamos una función como las siguientes, que vienen a decir:  
> "cuando la web esté cargada del todo (evento: **ready**), ejecuta el código que tengo dentro".

Todo el código jQuery ha de ir por tanto dentro de esta función.  
Hay dos versiones de ella que hacen exactamente lo mismo.


- Versión corta de la función:
~~~
$(function() {
   // Todo el código jQuery va aquí dentro.
});
~~~

- Versión larga de la función:
~~~
$(document).ready(function() {
   // Todo el código jQuery va aquí dentro.
});
~~~


## Sintaxis básica

El selector dice sobre qué elemento se ejecuta la acción, va entre comillas y puede ser cualquier selector css.
~~~
$("selector").accion();
~~~


## Selectores

> Recuerda que también puedes combinar selectores.

| Selector | Ejemplo | Selecciona del documento... |
| -- | -- | -- |
| * | $("*") | todos los elementos |
| #id | $("#cosa") | el elemento con id="cosa" |
| .class | $(".cosa") | todos los elementos con clase="cosa" |
| un elemento | $("p") | todos los elementos p |
| varios elementos | $("h1, h2, h3") | todos los elementos h1, h2 y h3 |
| :first | $("p:first") | el primer elemento p |
| :last | $("p:last") | el último elemento p |
| :first-child | $("p:first-child") | todos los p que sean primer hijo de sus padres |
| :last-child | $("p:last-child") | todos los p que sean último hijo de sus padres |
| :nth-child(n) | $("div:nth-child(2)") | todos los p que sean segundo (2) hijo de sus padres |
| padre > hijo | $("div > p") | todos los p que sean hijos directos de un div |
| padre descendiente | $("div p") | todos los p descendientes de un div (directos o no) |
| :eq(index) | $("ul li:eq(2)") | el tercer elemento de la lista (index empieza en 0) |
| :contains(text) | $(":contains('cosa')") | todos los elementos que contienen el texto 'cosa' |
| [atributo] | $("src") | todos los elementos que tengan un atributo src |
| :input | $(":input") | todos los elementos input |
| :text | $(":text") | todos los elementos con el type="text" |


## Obtener o Modificar

Métodos de jQuery para obtener o establecer, el contenido y los atributos de los elementos HTML seleccionados:  

**text()** establece o devuelve el contenido de **texto** de los elementos seleccionados.  
**html()** establece o devuelve el **contenido, incluido el marcado html** de los elementos seleccionados.  
**val()** establece o devuelve el **valor de los campos de formulario** de los elementos seleccionados.  
**attr()** establece o devuelve el valor de los **atributos** de los elementos seleccionados.   


### text()
> **text()** establece o devuelve el contenido de **texto** de los elementos seleccionados.  

HTML
~~~
<div id="test">
   <p>some text</p>
</div>
~~~
JS. Devuelve solo el texto del div, sin etiquetas html: hello!
~~~
$(function() {
    $("#test").text("hello!");
});
~~~


### html()
> **html()** establece o devuelve el **contenido, incluido el marcado html** de los elementos seleccionados.  

HTML
~~~
<p>
  JQuery is <b>fun</b>
</p>
~~~
JS Devuelve p: JQuery is <b>fun</b> (incluidas las etiquetas html).
~~~
$(function() {
    var val = $("p").html();
    alert(val);
});
~~~


### val()
> **val()** establece o devuelve el **valor de los campos de formulario** de los elementos seleccionados.  

HTML. Formulario con un input con el texto: Hola.
~~~
<input type="text" id="name" value="Hola">
~~~
JS. Devuelve un alert con el texto Hola
~~~
$(function() {
    alert($("#name").val());
});
~~~


### attr()
> **attr()** establece o devuelve el valor de los **atributos** de los elementos seleccionados.   

HTML
~~~
<a href="https://www.google.com/">Click here</a> 
~~~
JS 1. Si pasamos 1 parámetros, obtenemos el valor del atributo href: https://www.google.com/
~~~
$(function() {
    $("a").attr("href");
});
~~~
JS 2. Si pasamos 2 parámetros, cambia el valor del atributo href, por el enlace que le hemos pasado como segundo parámetro, ahora nos llevará a http://www.jquery.com/
~~~
$(function() {
    $("a").attr("href", "http://www.jquery.com");
});
~~~


## Borrar

Métodos de jQuery para eliminar el atributo del los elemento HTML seleccionado:  

**removeAttr()** elimina el atributo especificado.

HTML
~~~
<table border="5" class="tbl" >
           <tr>
               <td>one</td>
               <td>two</td>
           </tr>
           <tr>
               <td>three</td>
               <td>four</td>
           </tr>
       </table> 
~~~
JS. Eliminamos el atributo border de la tabla y el atributo class.
~~~
$(function() {
    $("table").removeAttr("border");
    $("table").removeAttr("class"); 
});
~~~


## Crear





