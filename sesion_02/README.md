# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 24 de marzo → sesion_02 → HTML5, CSS3 y p5.js

- - - - - - - - 

#### Teoría

En esta sesión vamos a echarle un vistazo al fondo de la pisciona a la que ya nos lanzamos. Lo primero que aparece a la vista es que el código fuente implica describir y/o programar. Hay lenguajes de descripción y lenguajes de programación. En web, se utilizan los siguientes:

- **HTML (HyperText Markup Language)**. Lenguaje estándar que describe la estructura de las páginas web (qué es lo que contiene la página). HTML5 es la versión más reciente de este lenguaje. El bloque constructivo más básico del HTML es el elemento. Cada elemento de HTML se escribe, generalmente, entre etiquetas: `<etiqueta>contenido</etiqueta>` → Puedes complementar esta brevísima introducción a HTML con una revisión de https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/HTML_basics

- **CSS (Cascading Style Sheets)**. Lenguaje estándar que describe la presentación de las páginas web (cómo se muestra lo que contiene la página). CSS3 es la versión más reciente de este lenguaje. Su unidad más básica es la regla. Cada regla se inicia con un selector, seguido de paréntesis de llave `{…}`. Tal paréntesis contiene un bloque de declaraciones. En tal bloque cada declaración se separa de otra mediante punto y coma `;`. Una declaración se compone del par `propiedad: valor`. Con todo lo dicho, una regla se escribirá, generalmente, de la siguiente manera: `selector{ propiedad: valor; }` → Puedes complementar esta brevísima introducción a CSS con una revisión de https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/CSS_basics (no es necesario realizar el ejercicio que allí se propone).

- **JS (JavaScript)**. Lenguaje de programación que controla el comportamiento de las páginas web (qué hace la página). Con JS se pueden escribir secuencias de instrucciones con las que una computadora realizará una tarea determinada en el navegador. Su estructura puede variar dependiendo de la lógica de cada instrucción, la [versión](https://www.w3schools.com/js/js_versions.asp) en uso, la biblioteca (*library*) de JavaScript en la que nos apoyemos, o el *framework* de programación en el que se basa el trabajo; podemos imaginar que una biblioteca es como una selección de ingredientes listos para poder preparar determinado tipo de comida, mientras que el *framework* te permite preparar un banquete si es que ya tienes suficiente experiencia en la cocina → Puedes complementar esta breve introducción a JS con una revisión de https://jsparagatos.com/

[Python](https://www.python.org/), [PHP](https://www.php.net/) y [Ruby](https://www.ruby-lang.org/es/) son otros lenguajes de programación de uso popular en Web.

Y solo para evitar pensar en ellos como lenguajes, conviene mencionar tres *framework* populares para el desarrollo Web: [Angular](https://angular.io/), [React](https://es.reactjs.org/) y [Vue.js](https://v3.vuejs.org/). El primero ofrecía, originalmente, una vía de acceso cómoda a la programación de aplicaciones web para quienes ya programaban software en [Java](https://es.wikipedia.org/wiki/Plataforma_Java), los otros dos están basado en JavaScript (JS). El tercero, [Vue.js](https://v3.vuejs.org/), es el más respetuoso de los estándares web y el más adaptable (progresivamente) a los diversos niveles de complejidad que puede tener un proyecto.

- - - - - - - - - - - - - - 

#### Exploración práctica

Para reconocer los tres lenguajes mencionados más arriba, podemos comenzar creando un documento nuevo en un editor de código fuente, el que guardaremos con el nombre `index.html`, y así tal cual está escrito, sin mayúscula, tilde, acento ni espacio.

Allí peguemos la estructura típica de toda página HTML: 

```
<!DOCTYPE html>
<html lang="es">
    <head>…</head>
    <body>…</body>
</html>
```

Dentro de `<head>…</head>`, agreguemos un par de metadatos, algo de CSS y un título para la etiqueta de la pestaña del navegador que muestre nuestra página.

```
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
* { margin: 0; padding: 0; }
body { background: black; color: white; }
div { padding: 2rem; }
p { padding: 1rem 0; }
@media (min-width: 800px) { p { max-width: 60%; } }
</style>
<title>Hola mundo!</title>
```

Después del título para la pestaña, y aún dentro del `<head>…</head>`, vinculemos a la biblioteca de JavaScript que estamos usando:

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.1/p5.min.js" integrity="sha512-NxocnqsXP3zm0Xb42zqVMvjQIktKEpTIbCXXyhBPxqGZHqhcOXHs4pXI/GoZ8lE+2NJONRifuBpi9DxC58L0Lw==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

Ahora tenemos lo necesario para copiar algo dentro de `<body>…</body>`, y copiarlo entre etiquetas `<script>…</script>`:

```
function setup() {
   createCanvas(windowWidth - 40, windowHeight - 40).position(20, 20).style("z-index", -1);
   document.getElementById("nombre").textContent += "Perico de los palotes";
}
function draw() {
   background(100);
}
function windowResized() { 
   resizeCanvas(windowWidth - 40, windowHeight - 40);
} 
```

Lo último que agregaremos dentro de `<body>…</body>`, pero justo antes del `<script>…</script>`, será lo siguiente:

```
<div>
<h1>Hola. Me llamo <span id="nombre"></span></h1>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur quam ligula, sollicitudin vitae dolor non, ornare accumsan ante. Morbi at dapibus eros. Duis consectetur egestas ipsum ac luctus.</p>
</div>
```

Si el código en el `index.html` queda un poco desordenado, podemos ordenarlo con ayuda de https://webformatter.com/html

Después de ordenar el código y guardar el `index.html`, podemos abrirlo en un navegador web y ver el resultado.

Con esta base podemos volver a consultar las [referencias](https://p5js.org/es/reference/) del conjunto de funcionalidades de [p5.js](https://p5js.org/es/), con las que

> no estás limitado solo a dibujar. Puedes tomar toda la página del navegador como tu bosquejo, incluyendo los objetos HTML5 para texto, entrada, video, cámara web y sonido.

Pero en una consulta a tales referencias no encontraremos algo como `document.getElementById("nombre").textContent += "…"`

Eso sí lo podríamos encontrar por acá: 

- https://developer.mozilla.org/es/docs/Web/API/Document/getElementById
- https://developer.mozilla.org/es/docs/Web/API/Node/textContent

De a poco iremos asomándonos fuera de esta biblioteca de JavaScript, para aprender algo de JavaScript "a secas".

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_01) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_03)
