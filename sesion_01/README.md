# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 17 de marzo → sesion_01 → p5.js

- - - - - - - - 

#### Teoría

Para lanzarnos a la piscina sin haber averiguado su profundidad, aprovecharemos "el flotador" que nos ofrece [p5.js](https://p5js.org/es/):

> ¡**p5.js** es una biblioteca de JavaScript para la programación creativa, que busca hacer que programar sea accesible e inclusivo para artistas, diseñadores, educadores, principiantes y cualquier otra persona! **p5.js** es gratuito y de código abierto porque creemos que el software y las herramientas para aprenderlo deben ser accesibles para todos.

Esta biblioteca fue creada por [Lauren McCarthy](http://lauren-mccarthy.com/) y es desarrollada por una comunidad de colaboradores, con apoyo de [Processing Foundation](https://processingfoundation.org/). Entre los colaboradores hay 2 chilenos, que se han encargado de la traducción de referencias, tutoriales y [un libro](https://processingfoundation.press/product/introduccion-a-p5-js/) al castellano; ellos son: [Guillermo Montecinos](https://twitter.com/guillermolooped) y [Aarón Montoya-Moraga](https://twitter.com/montoyamoraga).

[p5.js](https://p5js.org/es/) es una reinterpretación de [Processing](https://processing.org/) para la web. 

En Processing, que se basa en [Java](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n)), cada *sketch* debe tener dos partes:

- `void setup()`; y 
- `void draw()`. 
 
Hay un `setup` que se ejecuta una única vez, en la partida. Y hay un `draw` que, por defecto, se ejecuta una y otra vez. 

Ahora, cambiemos el `void` de Java por el `function` de [JavaScript](https://es.wikipedia.org/wiki/JavaScript), y tenemos:

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

Ya utilizamos `createCanvas()`, `frameRate()`, `background()`, `random()`, que son parte de

> un conjunto completo de funcionalidades para dibujar. Sin embargo, no estás limitado solo a dibujar. Puedes tomar toda la página del navegador como tu bosquejo, incluyendo los objetos HTML5 para texto, entrada, video, cámara web y sonido.

Para enteder cómo es que esta biblioteca de JavaScript nos permite dibujar en el canvas o tomar toda la página del navegador, conviene agregar una nota sobre el [Modelo de Objeto de Documento (DOM)](https://developer.mozilla.org/es/docs/Glossary/DOM): **A través del DOM, los programas escritos en JavaScript pueden acceder y modificar la interpretación del contenido, estructura y estilo de la página web**. 

Para no entrar en tecnisismos, quedemonos con que JavaScript no cambia lo escrito, lo que modifica es la comprensión de lectura del navegador. Como el resultado está a la vista, quizá convenga esta analogía para establecer la diferencia entre código fuente y DOM: Si capturaste una imagen con 3 elementos y agregas un cuarto "photoshopénadolo", en ningún caso modificas la escena capturada, pero todos podrán ver una imagen con 4 elementos. 

Estirando la analogía: Podríamos encontrar inconcruencias en los despliegue de (1) código fuente de la página y (2) elementos de la página. Esto es así porque en el código fuente de la página está lo capturado originalmente, mientras que en la vista de elementos de la misma página está lo "photoshopeado", y esto último coincide con la comprensión de lectura del navegador.

**Ahora volvamos al *Preview* del [editor web de p5.js](https://editor.p5js.org/): Lo que allí tenemos es lo "photoshopeado"**.

En este mismo editor podrán notar que a la izquierda, justo debajo de *play*, encuentran con este símbolo: `>`. Al presionarlo, se muestra una caja con tres archivos: `index.html`, `sketch.js` y `style.css`. Estos son los necesarios para poder hacer cualquier sitio o aplicación que atienda a [los estándares web](https://www.w3.org/standards/webdesign/). El `index.html` describe la captura original a mostrar, el `style.css` describe cómo mostrarla, y en el `sketch.js` se programa el "photoshopeo" (eso que se muestre, bajo ciertas condiciones, que puede ser distinto de lo que se describe originalmente en el ìndex.html`).

No corresponde pensar en tales `.html`, `.css` y `.js` como extensiones de archivos que deben abrirse en programas determinados, así como el `.psd` se abre y edita con Photoshop y el `.ai` con Illustrator. HTML, CSS y JavaScript son lenguajes que se pueden escribir en cualquier editor de código fuente, incluso con un block de notas: ¡Guardamos lo escrito como `.txt`, luego cambiamos la extensión por la que corresponda y listo!

- - - - - - - - - - - - -

#### Exploración práctica

Continuaremos la exploración del *conjunto completo de funcionalidades para dibujar* en el [editor web de p5.js](https://editor.p5js.org/). 

Después pasaremos al editor de código fuente, copiando y pegando los tres archivos que genera el [editor web de p5.js](https://editor.p5js.org/), para trabajarlo de manera local.

Además del editor de código fuente, es muy necesario disponer de un navegador Firefox o Chrome; y saber como **ver código fuente**, [inspeccionar elementos](https://support.hostinger.es/es/articles/2333029-como-inspeccionar-los-elementos-del-sitio-web) y [abrir consola](https://transferwise.com/es/help/articles/2954851/como-abrir-la-consola-de-tu-navegador) en el que dispongan.

- - - - - - - 

###### [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_02)
