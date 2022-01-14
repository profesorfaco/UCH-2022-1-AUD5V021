# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 17 de marzo → sesion_01 → HTML5 y p5.js

- - - - - - - - 

#### Teoría

Para comenzar a profundizar en Javascript, un lenguaje de programación, nos aprovecharemos de [p5.js](https://p5js.org/es/):

> ¡**p5.js** es una biblioteca de JavaScript para la programación creativa, que busca hacer que programar sea accesible e inclusivo para artistas, diseñadores, educadores, principiantes y cualquier otra persona! **p5.js** es gratuito y de código abierto porque creemos que el software y las herramientas para aprenderlo deben ser accesibles para todos.

Esta biblioteca fue creada por [Lauren McCarthy](http://lauren-mccarthy.com/) y es desarrollada por una comunidad de colaboradores, con apoyo de [Processing Foundation](https://processingfoundation.org/). Entre los colaboradores hay 2 chilenos, que se han encargado de la traducción de referencias, tutoriales y [un libro](https://processingfoundation.press/product/introduccion-a-p5-js/) al castellano; ellos son: [Guillermo Montecinos](https://twitter.com/guillermolooped) y [Aarón Montoya-Moraga](https://twitter.com/montoyamoraga).

[p5.js](https://p5js.org/es/) es una reinterpretación de [Processing](https://processing.org/) para la web. 

En Processing, que se basa en Java, cada *sketch* debe tener dos partes:

- `void setup()`; y 
- `void draw()`. 
 
Hay un `setup` que se ejecuta una única vez, en la partida. Y hay un `draw` que por defecto se ejecuta una y otra vez. 

Ahora, cambiemos el `void` de [Java](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n)) por el `function` de [JavaScript](https://es.wikipedia.org/wiki/JavaScript), y tenemos:

- `function setup()`; y 
- `function draw()`. 

Cuando ingresamos al [editor web de p5.js](https://editor.p5js.org/) podemos encontrar la misma estructura, que incluye la creación de un [elemento `canvas`](https://developer.mozilla.org/es/docs/Web/HTML/Element/canvas) con ancho y alto determanidos (creación que se ejecuta una única vez), y la definición de un color de fondo que se dibuja (o pinta) una y otra vez:

```
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}
```

El tamaño del [`createCanvas`](https://p5js.org/es/reference/#/p5/createCanvas) se indica en pixeles (son 400 x 400 pixeles en el caso recién presentado). El color del [`background`](https://p5js.org/es/reference/#/p5/background) utiliza, por defecto, el modelo RGB; cuando se indica solo un número, se asume que se está definiendo algo entre negro (0,0,0) y blanco (255,255,255), porque es un mismo número repitiéndose tres veces.

En el mismo [editor web de p5.js](https://editor.p5js.org/) podemos hacer cambios para asegurarnos de comprender las diferencias. Podríamos crear un canvas más ancho que alto, donde la velocidad del re-dibujar no sea de 30 cuadros por segundo sino 2. Y podríamos pintar cada vez el fondo de un color distinto, dejando los valores de rojo, verde y azul al azar entre 0 y 255:

```
function setup() {
  createCanvas(400, 100);
  frameRate(2);
}

function draw() {
  background(random(0,255),random(0,255),random(0,255));
}
```

Ya utilizamos `createCanvas()`, `frameRate()`, `background()`, `random()`. Tal como Processing, [p5.js](https://p5js.org/es/) ofrece

> un conjunto completo de funcionalidades para dibujar. Sin embargo, no estás limitado solo a dibujar. Puedes tomar toda la página del navegador como tu bosquejo, incluyendo los objetos HTML5 para texto, entrada, video, cámara web y sonido.

Para enteder cómo es que puede tomar toda la página del navegador, conviene agregar una nota sobre el [Modelo de Objeto de Documento (DOM)](https://developer.mozilla.org/es/docs/Glossary/DOM): **A través del DOM, los programas escritos en JavaScript pueden acceder y modificar la interpretación del contenido, estructura y estilo de la página web**. Para no entrar en tecnisismos, quedemonos con que JavaScript no cambia lo escrito, lo que modifica es la comprensión de lectura del navegador. 

Con el DOM podemos manipular una página así como cuando manipulamos una imagen con Photoshop. Si capturaste una imagen con 3 elementos y agregas un cuarto *photoshopénadolo*, en ningún caso modificas la escena capturada, pero todos podrán ver una imagen con 4 elementos. 

Estirando la analogía: Podríamos encontrar inconcruencias en los despliegue de (1) código fuente de la página y (2) elementos de la página. Esto es así porque en el código fuente de la página está lo capturado originalmente, mientras que en la vista de elementos de la misma página está lo *photoshopeado*, y esto último coincide con la comprensión de lectura del navegador, que tenemos a la vista.

- - - - - - - - - - - - -

#### Exploración

Es muy necesario saber como **ver código fuente**, [inspeccionar elementos](https://support.hostinger.es/es/articles/2333029-como-inspeccionar-los-elementos-del-sitio-web) y [abrir consola](https://transferwise.com/es/help/articles/2954851/como-abrir-la-consola-de-tu-navegador) en Chrome o Firefox.

También es necesario contar con un editor de código fuente; vamos a crear un documento nuevo, pegar el código que sigue y guardarlo con el nombre `ejemplo.html`:

```
<!doctype html>
<html lang="es">
    <head>
        <title>Esto es un ejemplo</title>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.min.js"></script>
        <script>
            function setup() {
                createCanvas(windowWidth - 40, windowHeight - 40).position(20, 20).style('z-index',-1);
            }
            function draw() {
                background(0);
            }
            function windowResized() { 
                resizeCanvas(windowWidth - 40, windowHeight - 40);
            } 
        </script>
    </head>
    <body></body>
</html>
```

Podemos abrir este `ejemplo.html` en Chrome o Firefox. En la ventana del navegador podemos ver una página web con un recuadro negro. Si vamos a inspeccionar los elementos notaremos que ese recuadro negro es un elemento `<canvas></canvas>` dentro del elemento `<main></main>` que está, a su vez, dentro del elemento `<body></body>`. Pero en el código fuente hay un `<body></body>` vacío. Esta diferencia se debe al DOM.

Para familiarizanos con el trabajo con el DOM, desarrollaremos un ejercicio para el que conviene:

- revisar el [método `querySelector`](https://developer.mozilla.org/es/docs/Web/API/Element/querySelector);

- revisar el [constructor `Date()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Date);

- revisar la [propiedad `Element.classList`](https://developer.mozilla.org/es/docs/Web/API/Element/classList); y

- tener a mano la [página de referencias de **p5.js**](https://p5js.org/es/reference/)

- - - - - - - 

[SIGUIENTE CLASE →](https://github.com/profesorfaco/front-end/tree/main/sesion_02)
