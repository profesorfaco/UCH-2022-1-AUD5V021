# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 24 de marzo → sesion_02 → HTML5, CSS3 y p5.js

- - - - - - - - 

#### Teoría

Escribir código fuente es describir y/o programar. Hay lenguajes de descripción y lenguajes de programación. En web, se utilizan los siguientes:

- **HTML (HyperText Markup Language)**. Lenguaje estándar que describe la estructura de las páginas web (qué es lo que contiene la página). HTML5 es la versión más reciente de este lenguaje. El bloque constructivo más básico del HTML es el elemento. Cada elemento de HTML se escribe, generalmente, entre etiquetas: `<etiqueta>contenido</etiqueta>` → Puedes complementar esta brevísima introducción a HTML con una revisión de https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/HTML_basics

- **CSS (Cascading Style Sheets)**. Lenguaje estándar que describe la presentación de las páginas web (cómo se muestra lo que contiene la página). CSS3 es la versión más reciente de este lenguaje. Su unidad más básica es la regla. Cada regla se inicia con un selector, seguido de paréntesis de llave `{…}`. Tal paréntesis contiene un bloque de declaraciones. En tal bloque, cada declaración se separa de otra mediante punto y coma `;`. Una declaración se compone del par `propiedad: valor`. Con todo lo dicho, una regla se escribirá, generalmente, de la siguiente manera: `selector{ propiedad: valor; }` → Puedes complementar esta brevísima introducción a CSS con una revisión de https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/CSS_basics (no es necesario realizar el ejercicio que allí se propone).

- **JS (JavaScript)**. Lenguaje de programación que controla el comportamiento de las páginas web (qué hace la página). Con JS se pueden escribir secuencias de instrucciones con las que una computadora realizará una tarea determinada en el navegador. Su estructura puede variar dependiendo de la lógica de cada instrucción, la [versión](https://www.w3schools.com/js/js_versions.asp) en uso, la biblioteca (*library*) de JavaScript en la que nos apoyemos, o el *framework* de programación en el que se basa el trabajo; podemos imaginar que una biblioteca como una selección de ingredientes listos para poder preparar determinado tipo de comida, mientras que el *framework* te permite preparar un banquete si es que ya tienes suficiente experiencia en la cocina → Puedes complementar esta breve introducción a JS con una revisión de https://jsparagatos.com/

[Python](https://www.python.org/), [PHP](https://www.php.net/) y [Ruby](https://www.ruby-lang.org/es/) son otros lenguajes de programación populares para el diseño de interacción en web. 

Y solo para evitar pensar en ellos como lenguajes, conviene mencionar tres *framework* populares para el desarrollo Web: [Angular](https://angular.io/), [React](https://es.reactjs.org/) y [Vue.js](https://v3.vuejs.org/). El primero ofrecía, originalmente, una vía de acceso cómoda a la programación de aplicaciones web para quienes ya programaban software en [Java](https://es.wikipedia.org/wiki/Plataforma_Java), los otros dos están basado en JavaScript (JS).

- - - - - - - - - - - - - - 

#### Exploración práctica

Para reconocer los tres primeros lenguajes mencionados más arriba, podemos aprovechar los documentos contenidos en esta carpeta, comenzando con la página [index.html](https://github.com/profesorfaco/interaccion/blob/main/sesion_01/index.html):

Allí podemos ver la estructura típica de toda página HTML: 

```
<!DOCTYPE html>
<html lang="es">
    <head>…</head>
    <body>…</body>
</html>
```

Dentro de la cabeza (`<head></head>`), podemos ver un vínculo a un [style.css](https://github.com/profesorfaco/interaccion/blob/main/sesion_01/style.css):

```
<link href="style.css" rel="stylesheet" />
```

En las líneas finales del `index.html`, dentro de unas etiquetas de script (`<script></script>`), podemos ver una variable de JavaScript; esta variable se llama `palabras` y contiene un arreglo (*array*) con 8 cadenas de caracteres entre comillas. 

```
var palabras = ["siguiente", "repüyen", "seguente", "suivant", "next", "Nächster", "次の", "다음의"];
```

Cada cadena de caracteres, contenida entre comillas, tiene una posición dentro del arreglo. Las posiciones se identifican con un número, partiendo a la izquierda con el 0. Considerando lo recién dicho, `palabras[0]` refiere a `siguiente` y `palabras[7]` refiere a `다음의` 

Esta variable es utilizada para realizar una tarea simplificada con [p5.js](https://p5js.org/es/get-started/), una bibliteca de JS. Para comprender tal simplificación, conviene hacer un paréntesis para:

- aprovechar [el **p5.js** Web Editor](https://editor.p5js.org/profesorfaco/sketches/wBvBZ1V6n); y

- revisar [la página de referencias de **p5.js**](https://p5js.org/es/reference/).

Una vez cerremos el paréntesis podremos volver a la página [index.html](https://github.com/profesorfaco/interaccion/blob/main/sesion_01/index.html) para resolver el ejercicio de la clase de hoy.

- - - - - - - 

[← CLASE ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_01) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/front-end/tree/main/sesion_03)
