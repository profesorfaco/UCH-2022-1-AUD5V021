# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 21 de abril → sesion_06 →  Bootstrap v5 y Datos en JavaScript

- - - - - - - - 

#### Teoría

En esta sesión pasaremos a otra biblioteca de JavaScript. Partimos por [p5.js](https://p5js.org/es/), una biblioteca que busca hacer que programar sea accesible e inclusivo para artistas, diseñadores, educadores, principiantes y cualquier otra persona. Ahora vamos a "un clásico": [jQuery](https://jquery.com/). 

**[jQuery](https://jquery.com/) es una biblioteca que por muchos años ha simplificado la redacción de instrucciones en JavaScript, sobre todo cuando se busca manipular el [DOM](https://desarrolloweb.com/articulos/que-es-el-dom.html) y hacer transiciones animadas**. Su primera versión estable fue lanzada el año 2006, lo que es anterior a la primera revisión importante del [estándar de JavaScript](https://en.wikipedia.org/wiki/ECMAScript), la [ES5 del 2009](https://www.w3schools.com/js/js_es5.asp), con la que se comenzó a simplificar la redacción del mismo lenguaje.

La versión estable más reciente de [jQuery es la 3.6.0](https://blog.jquery.com/2021/03/02/jquery-3-6-0-released/); versión lanzada en marzo de 2021.

Para entender la utilidad de [jQuery](https://jquery.com/), conviene partir con un ejemplo: En una página web podríamos tener varios elementos con una clase a la que denominamos `tal`. Para afectar a todos los elementos que tienen esa clase con un cambio de color desde JavaScript hace algunos años habríamos escrito la siguiente instrucción:

```
var elementos = Array.from(document.getElementsByClassName("tal"));
elementos.forEach(function(elemento){
  elemento.style.color="red";
});
```

Con el [estándar de JavaScript actual](https://www.w3schools.com/js/js_versions.asp) se simplifica un poco:

```
var elementos = document.querySelectorAll(".tal");
elementos.forEach(elemento => elemento.style.color="red");
```

Pero usando [jQuery](https://jquery.com/), por años ha sido suficiente escribir:

```
$(".tal").css("color","red");
```

Para la primera década del 2000, [jQuery](https://jquery.com/) ofrecía una simplificación radical en el trabajo con JavaScript. Pero ya en la segunda década, no conviene perder de vista al lenguaje original que ha evolucionado para ser más amigable en la medida que los desafíos de programación para la interacción se complejizan; por quedarnos "muy pegados" en [jQuery](https://jquery.com/), podríamos obligar a cada navegador a leer [90kb de código fuente](https://code.jquery.com/jquery-3.6.0.min.js) para interpretar una instrucción que ya se resuelve con menos de 1kb de puro JavaScript, o podríamos tener muchas dificultades dando el primer paso a una biblioteca de JavaScript para construir interfaces de usuario ([Vue.js](https://v3.vuejs.org/) o [React.js](https://es.reactjs.org/)).

Hecha la advertencia, agreguemos un nivel más al ejemplo para poder entender el uso de la biblioteca: 

```
function enrojece() {
  $(".tal").css("color","red");
}
$("#cambio").on("click", enrojece);
```

Tal instrucción está abreviando, mediante [jQuery](https://jquery.com/), lo que se podría escribir en JavaScript actual y puro de la siguiente manera:

```
function enrojece(){
  var elementos = document.querySelectorAll(".tal");
  elementos.forEach(elemento => elemento.style.color="red");  
}
document.querySelector("#cambio").addEventListener("click", enrojece);
```

Con la última instrucción redactada, el cambio de color sobre todos los elementos de clase `tal` se aplica con el click en aquello que tenga identidad `cambio`. Y con este segundo ejemplo ya resulta evidente que la clave del uso de [jQuery](https://jquery.com/) está en la concatenación de un selector y una acción, antecedida de un signo peso: `$(selector).action()`. 

Las opciones de selectores y acciones son descritas detalladamente en https://api.jquery.com/, y de manera muy abreviada en https://htmlcheatsheet.com/jquery/

- - - - - - -

#### Exploración

Con jQuery puedo ir a buscar datos a un JSON. 

A partir de los datos encontrados, puedo agregar párrafos al cuerpo del documento:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <title>jQuery y JSON</title>
    </head>
    <body>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
        <script>
            $(document).ready(function () {
                $.getJSON("https://myjson.dit.upm.es/api/bins/1wo6", function (data) {
                    console.log(data);
                    var singularplural;
                    data.forEach(function (d) {
                        if (d.children.length > 1) {
                            singularplural = "bendiciones";
                        } else {
                            singularplural = "bendición";
                        }
                        $("body").append("<p>" + d.mom + " y " + d.dad + " tienen " + d.children.length + " " + singularplural + ".</p>");
                    });
                });
            });
        </script>
    </body>
</html>
```

Sin jQuery puedo hacer lo mismo: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <title>JavaScript y JSON (sin bibliotecas)</title>
    </head>
    <body>
        <script>
            fetch("https://myjson.dit.upm.es/api/bins/1wo6")
                .then(response => response.json())
                .then(data => {
                    console.log(data);
                    var singularplural;
                    data.forEach(function (d) {
                        if (d.children.length > 1) {
                            singularplural = "bendiciones";
                        } else {
                            singularplural = "bendición";
                        }
                        document.body.innerHTML += "<p>" + d.mom + " y " + d.dad + " tienen " + d.children.length + " " + singularplural + ".</p>";
                    });
                })
                .catch((error) => console.log("¡PLW!", error));
        </script>
    </body>
</html>
```

Sin usar jQuery, me quedé en las 25 líneas y le ahorré al navegador la lectura de [90kb de código fuente](https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js). Esto porque los navegadores actuales soportan la [Fetch API](https://levelup.gitconnected.com/using-the-fetch-api-in-javascript-1de7c2fe673b) de [JavaScript](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch), que vino a reemplazar [formas más complejas](https://stackoverflow.com/questions/1973140/parsing-json-from-xmlhttprequest-responsejson).

Ya podrían estar preguntándose: ¿Por qué seguir insistiendo con jQuery? La respuesta es sencilla: Porque los [efectos `Hide/Show` y `Fade`](https://htmlcheatsheet.com/jquery/) aún son útiles útiles, y si ya estoy obligando al navegador a leer 90kb para hacer sólo eso, bien viene aprovecharse de lo demás. Pero no perdamos de vista las maneras más "puristas" y actuales de manipular el DOM, para no quedarnos atrapados en el pasado.

- - - - - - -

#### Práctica

https://profesorfaco.github.io/interaccion/sesion_06/

- - - - - - - 


[← CLASE ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_05) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/front-end/tree/main/sesion_07)
