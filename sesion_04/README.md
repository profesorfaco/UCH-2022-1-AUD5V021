# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 7 de abril → sesion_04 → Bootstrap v5

- - - - - - - - 

#### Teoría

**Existen marcos de trabajo de código abierto que nos permitirán a avanzar más rápido desde relaciones predefinidas de HTML y CSS**. Por su popularidad, corresponde mencionar a:

- [Bootstrap](https://getbootstrap.com/): *The world’s most popular front-end open source toolkit, featuring Sass variables and mixins, responsive grid system, extensive prebuilt components, and powerful JavaScript plugins.*

- [Foundations](https://get.foundation/): *The most advanced responsive front-end framework in the world* 

- [Semantic UI](https://semantic-ui.com/): *A development framework that helps create beautiful, responsive layouts using human-friendly HTML*

Nos quedaremos con el primero de los mencionados, en su versión más reciente, la 5.1. 

[Bootstrap](https://getbootstrap.com/) nos permite implementar tanto prototipos rápidos como productos acabados, esto mediante el uso de Elementos de HTML5 relacionados con [reglas de CSS3 predefinidas](https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.css), además de Javascript simplificado por una biblioteca (que debe complementarse con [jQuery](https://jquery.com/) en versiones de Bootstrap anteriores a la 5).

Hay distintas maneras de comenzar a trabajar con Boostrap. Nosotros vamos a partir con una adaptación de la [Starter template](https://getbootstrap.com/docs/5.1/getting-started/introduction/#starter-template), con un documento HTML que debe verse así: 

```
<!doctype html>
<html lang="es">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-F3w7mX95PdgyTmZZMECAngseQB83DfGTowi0iMjiWaeVhAn4FJkqJByhZMI3AhiU" crossorigin="anonymous">
    <title>¡Usemos Bootstrap!</title>
  </head>
  <body>
    <h1>¡Usemos Bootstrap!</h1>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-/bQdsTh/da6pkI1MST/rWKFNjaCP5gBSY4sEBT38Q/9RBh9AH40zEOg7Hlq2THRZ" crossorigin="anonymous"></script>
  </body>
</html>
```

En el cuerpo de tal documento HTML (`<body></body>`) podemos comenzar a utilizar las clases con las que Bootstrap define el *layout*, siguiendo un principio general de: Tomar de 1 a 12 columnas (`class="col"`) en cada fila (`class="row"`) que esté dentro de un contenedor (`class="container"`). Así, por ejemplo, podemos reemplazar el `<h1>¡Usemos Bootstrap!</h1>` en el código de arriba por lo siguiente:

```
<div class="container">
  <div class="row">
    <div class="col-6"><h1>¡Usemos Bootstrap!</h1></div>
    <div class="col-6"><h2>Bueno, ya.</h2></div>
  </div>
</div>
```

A todo evento, tendríamos el `¡Usemos Boostrap!` junto al `Bueno, ya`. Esto es así porque tomamos 6 de 12 columnas (`class="col-6"`) en cada caso. Esto es tomar la mitad de espacio disponible en tal fila (`class="row"`) dentro del contenedor (`class="container"`).

Pero podemos indicar excepciones que respondan al tamaño de pantalla en que se despliegue la página, sea esta pantalla muy pequeña, pequeña (`-sm-`), mediana (`-md-`), grande (`-lg-`), extra grande (`-xl-`) o extra-extra grande (`-xxl-`). Por ejemplo, así puedo tomar 6 y 6 columnas desde la pantalla mediana:

```
<div class="col-md-6"><h1>¡Usemos Bootstrap!</h1></div>
<div class="col-md-6"><h2>Bueno, ya.</h2></div> 
```

Los tamaños de cada pantalla los pueden consultar en los [Breakpoints de Bootstrap](https://getbootstrap.com/docs/5.1/layout/breakpoints/#available-breakpoints)

- - - - - - 

### Exploración

En el sitio web oficial de Bootstrap encontrarán [documentación detallada](https://getbootstrap.com/docs/5.1/getting-started/introduction/) sobre cada clase, utilidad y componente que ofrece este marco de trabajo de código abierto. Además, pueden encontrar [ejemplos](https://getbootstrap.com/docs/5.1/examples/) donde conviene explorar: 

- Grid → https://getbootstrap.com/docs/5.1/examples/grid/

- Cheatsheet → https://getbootstrap.com/docs/5.1/examples/cheatsheet/

Pero hay una cosa que no conviene descuidar al usar Bootstrap: **Ofrece un estilo CSS muy grande, de 11.222 líneas**, que el navegador revisa antes de mostrar la página. Pero rara vez usaremos más de 1.222 líneas entre las ofrecidas (le pedimos al navegador leer 10.000 líneas de más en cada carga de página creada con Boostrap). Por ello, si queremos limitar la lectura a lo estrictamente necesario, y con ello mejorar el rendimiento de lo preparado con Bootstrap, conviene aplicar algunos trucos: https://css-tricks.com/how-do-you-remove-unused-css-from-a-site/ 

Entre los trucos del artículo se menciona https://purifycss.online/ en donde podemos poner a prueba el archivo preparado para la práctica, para ver cuánto CSS del que se vincula está siendo realmente utilizado.

- - - - - - - 

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_03) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/front-end/tree/main/sesion_05)
