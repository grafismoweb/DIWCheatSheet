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


# Selectores

* Puedes consultar: [https://www.w3schools.com/Jquery/jquery_selectors.asp](https://www.w3schools.com/Jquery/jquery_selectors.asp)


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
| :only-child) | $("div:only-child") | todos los elementos que sean el único hijo del div |
| elemento ~ hermano  | $("h3 ~ p") | los p que estén al mismo nivel que los h3 |
| elemento + hermanoAdyacente | $("h3 + p") | los p que estén junto a un h3 y al mismo nivel que ese h3 |
| padre > hijo | $("div > p") | todos los p que sean hijos directos de un div |
| padre descendiente | $("div p") | todos los p descendientes de un div (directos o no) |
| :eq(index) | $("ul li:eq(2)") | el tercer elemento de la lista (index empieza en 0) |
| :contains(text) | $(":contains('cosa')") | todos los elementos que contienen el texto 'cosa' |
| [atributo] | $("src") | todos los elementos que tengan un atributo src |
| :input | $(":input") | todos los elementos input |
| :text | $(":text") | todos los elementos con el type="text" |
| :enabled | $("input:enabled") | todos los elementos que estén activos |
| :disabled | $("input:disabled") | todos los elementos que NO estén activos |
| elemento[atributo='valor']") | $("a[href='http://www.google.es']") | todos los elementos de tipo a que tengan ese enlace en href |
| elemento[atributo^='valor']") | $("a[href^='http://www.google.es/']") | todos los elementos de tipo a en los que el ese enlace de href empiece por la cadena indicada |


## Métodos selectores para conjuntos de elementos (arrays, colecciones)

| Método selector | Ejemplo | Selecciona del documento... |
| -- | -- | -- |
| find() | $($(".imagenes").find("img")[2]) | Selecciona hijos de un conjunto: la tercera imagen [2] de las imagenes con clase imágenes .imagenes. |
| first() / last() | $(".miniaturas").first() | Selecciona el primer o último componente de un conjunto de elementos. |
| each() | $(".miniaturas").each(function(index){ $(this)} | Itera por el conjunto de elementos seleccionado. En cada iteración el elemento actual se nombra con $(this). Podemos usar su index |
| eq() | $(".miniaturas").eq(1) | Selecciona un elemento de un conjunto por su índice: el segundo elemento [1] que tenga la clase .miniaturas |
| slice() | $(".miniaturas").slice(2,4) | Como eq pero para un conjunto de elementos en vez de uno, se define el inicio y el final: del tercer al quinto elemento [2,4] que tenga la clase .miniaturas |


## Obtener, Sustituir o Añadir contenido/valor

Métodos de jQuery para obtener el contenido o el valor de un elemento, sustituir el contenido o valor de un elemento, o añadir contenido o valor a un elemento que esté vacío.  

| Método | Devolver | Sustituir o Añadir | ¿qué? |
| -- | -- | -- | -- |
| **text()** | text() | text(con parametro) | el **contenido de texto** de los elementos seleccionados |
| **html()** | html() | html(con parametro) | el **contenido, incluido el marcado html** de los elementos seleccionados |
| **val()** | val() | val(con parametro) | el **valor de los campos de formulario** de los elementos seleccionados |
| **attr()** | attr("nombreAtributo") | attr("nombreAtributo", "nuevoValorAtributo") | el **valor del atributo pasado por parámetro** del elemento seleccionado |


### Ejemplos de cómo obtener, sustituir o añadir contenido (si no hay).
HTML:
~~~
<!-- .text() -->
<div id="test">
   <p>esto es un texto</p>
</div>

<!-- .html() -->
<h2>
  JQuery es <b>lo que toca</b>
</h2>

<!-- .val() -->
<input type="text" id="name" value="Hola">

<!-- .attr() -->
<a href="https://www.google.com/">Click aquí</a> 
~~~
JS:
~~~
$(function() {

// .text()
    $("#test").text(); // OBTIENE el texto contenido en el div #text.
    $("#test").text("Buenos dias"); // SUSTITUYE el texto contenido en el div #text por el pasado entre los paréntesis.

// .html()
    let variable1 = $("h2").html(); // OBTIENE: JQuery es <b>lo que toca</b> incluidas las etiquetas html.
    let variable2 = $("h2").html(<ul><li>lista<li></ul>); // SUSTITUYE: el contenido del <h2> por una lista ordenada con un item; lista.

// .val()
    let variable4 $("#name").val(); // OBTIENE: Hola, que es el contenido de dentro del input, su valor.
    let variable5 $("#name").val("Buenos días"); // SUSTITUYE: el contenido de dentro del input, su valor, por Buenos días. Si el input estuviera vacío, lo añadiría.

// .attr()
    $("a").attr("href"); // OBTIENE: Con 1 parámetro devuelve el valor del atributo indicado en el parámetro; https://www.google.com/
    $("a").attr("href", "http://www.jquery.com"); // SUSTITUYE: Con 2 parámetros cambia el valor del atributo href, por el enlace que le hemos pasado como segundo parámetro, ahora nos llevará a http://www.jquery.com/
});
~~~


## Borrar atributos

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


## Añadir contenido, antes o después del que ya existe

>Los métodos html () y text () se pueden usar para obtener y establecer el contenido de un elemento seleccionado. Sin embargo, cuando se utilizan estos métodos para configurar contenido, el contenido existente se pierde.

Métodos para **agregar nuevo contenido** a un elemento seleccionado **sin eliminar el contenido existente**. 
Todos admiten etiquetas html:

| Método | ¿qué hace? |
| -- | -- |
| **append()** | inserta contenido **detrás del último hijo** de los elementos seleccionados, será el último hijo. El contenido se inserta **dentro del selector** es **hijo** del selector|
| **prepend()** | inserta contenido **delante del primer hijo** de los elementos seleccionados, será el primer hijo. El contenido se inserta **dentro del selector** es **hijo** del selector| 
| **after()** | inserta contenido **detrás** de los elementos seleccionados. El contenido se inserta **fuera del selector** es **hermano** del selector| 
| **before()** | inserta contenido **delante** de los elementos seleccionados. El contenido se inserta **fuera del selector** es **hermano** del selector| 


### Ejemplos de cómo **Añadir** contenido, antes o después del que ya existe

HTML:
~~~
<p id="parrafo">Hola</p>
~~~
JS:
~~~
$(function() {

// OJO: Estos ejemplos deben entenderse como código aislado unos de otros.
// Partimos siempre del contenido HTML de arriba donde el contenido del párrafo es: Hola.
// (en realidad si este código fuera seguido, tras cada añadido, el elemento p tendria un contenido diferente, no solo el Hola).

//-------------------------------------------

    $("#parrafo").append("Caracola"); 
    // SALIDA: Hola Caracola

//------------------------------------------

    $("#parrafo").after("Caracola"); 
    // SALIDA: Hola 
    //         Caracola

//-------------------------------------------

    $("#parrafo").before("<b>Saludo:</b>")
    // SALIDA: Saludo: // en negrita
    //         Hola    // sin negrita

//-------------------------------------------

});
~~~

## Crear nuevos elementos y contenido

Los métodos append (), prepend (), before () y after () se pueden usar también para crear nuevos elementos.

HTML:
~~~
<p id="parrafo">Hola</p>
~~~
JS:
~~~
$.function(){

    // Crea un nuevo párrafo.
    let nuevoElemento = $("<p></p>").text("Soy un parrafo nuevo creado con jQuery."); 

    // Añade el nuevo parrafo a continuación del que ya estaba.
    $("#parrafo").after(nuevoElemento); 
}

// SALIDA:
// Hola
// Soy un parrafo nuevo creado con jQuery.
~~~


# Manipulación de estilos CSS

## Añadir y Quitar clases CSS

| Método | ¿qué hace? |
| -- | -- |
| **addClass()** | agrega una o más clases a los elementos seleccionados. |
| **removeClass()** | elimina una o más clases a los elementos seleccionados. |
| **toogleClass()** | alterna entre agregar/eliminar una o más clases de los elementos seleccionados (si la clase existe para el elemento, se elimina, y si no existe, se agrega). Se suele usar con eventos (on/off con un botón por ejemplo). |

~~~
$.function(){

    // Añade las clases CSS: .texto y .menu a todos los parrafos.
    $("p").addClass("texto menu");

    // Quita la clase .menu de todos los parrafos.
    $("p").removeClass("menu");
}
~~~


# ...archivo en elaboración (continuará)