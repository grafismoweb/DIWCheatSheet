# jQuery

jQuery es una librería de JavaScript.

Solo con javascript:
`let el = document.getElementById("start");
el.innerHTML = "Go";`

Lo mismo con jQuery:
`$("#start").html("Go");`


## Cómo usar jQuery

### Descargar y enlazar

Se puede descargar el archivo o apuntar hacia el archivo online, pero siempre hay que referenciarlo en el head del HTML de mi web entre etiquetas `<script></script>`:

`<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
        <script src="https://code.jquery.com/jquery-3.1.1.js"></script>
    </head>
    <body>
    </body>
</html>`


### Funcion de carga de la página (todo dentro).

Versión corta de la función:
`$(function() {
   // jQuery code goes here
});`

Versión larga (ambas hacen lo mismo):
`$(document).ready(function() {
   // jQuery code goes here
});`


