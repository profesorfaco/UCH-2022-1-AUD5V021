# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 14 de abril → sesion_05 → Bootstrap v5.1 y JavaScript 

- - - - - - - - 

#### Teoría

Además de ofrecer un estilo de CSS compilado (basado en [Sass](https://sass-lang.com/)), Bootstrap tiene una biblioteca de JavaScript que permite el funcionamiento de varios de sus componentes. Funcionamiento que requieren también de [Popper](https://popper.js.org/):

- [Accordion](https://getbootstrap.com/docs/5.1/components/accordion/)
- [Carousel](https://getbootstrap.com/docs/5.1/components/carousel/)
- [Collapse](https://getbootstrap.com/docs/5.1/components/collapse/)
- [Dropdowns](https://getbootstrap.com/docs/5.1/components/dropdowns/)
- [Modal](https://getbootstrap.com/docs/5.1/components/modal/)
- [Offcanvas](https://getbootstrap.com/docs/5.1/components/offcanvas/)
- [Popovers](https://getbootstrap.com/docs/5.1/components/popovers/)
- [Tooltips](https://getbootstrap.com/docs/5.1/components/tooltips/)

Si se opta por ir por los scripts de Bootstrap.js y Popper.js separados, Popper debe estar primero:

```
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.10.2/dist/umd/popper.min.js" integrity="sha384-7+zCNj/IqJ95wo16oMtfsKbZ9ccEh31eOz1HGyDuCQ6wgnyJNSYdrPa03rtR1zdB" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js" integrity="sha384-QJHtvGhmr9XOIpI6YVutG+2QOK9T+ZnN4kzFN1RtK3zEFEIsxhlmWl5/YESvpZ13" crossorigin="anonymous"></script>
```

También está la opción de ir por ambos de una vez, con la opción *Bundle*:

```
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
```

Corresponde mencionar que hay una tercera opción, donde se van a buscar sólo determinados módulos, pero ello supera el alcance de una introducción.

Si nos quedamos con la segunda opción mencionada, nuestra adaptación de la [Starter template](https://getbootstrap.com/docs/5.1/getting-started/introduction/#starter-template) tendría que verse como sigue:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <title>¡Usemos Bootstrap!</title>
    </head>
    <body>
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
    </body>
</html>
```

Además del `.CSS` de Bootstrap que está vinculado en la cabeza del documento, ahora necesitamos el `.JS` de Bootstrap que, en este caso, está en el cuerpo.

Luego, justo en el espacio entre las etiquetas de apertura de `<body>` y `<scrip>` podemos comenzar a probar distintos componentes. Uno de ellos puede ser el carrusel:

```
<div class="container">
    <div id="probandoCarrusel" class="carousel slide" data-bs-ride="carousel">
        <div class="carousel-inner">
            <div class="carousel-item active">
                <img src="https://picsum.photos/600/300?random=1" class="d-block w-100" alt="…" />
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/600/300?random=2" class="d-block w-100" alt="..." />
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/600/300?random=3" class="d-block w-100" alt="..." />
            </div>
        </div>
        <button class="carousel-control-prev" type="button" data-bs-target="#probandoCarrusel" data-bs-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#probandoCarrusel" data-bs-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
        </button>
    </div>
</div>
```

Entre el cierre de la división de identidad `probandoCarrusel` y el cierre de la división de clase `container` podemos incluir algo más:

```
<div class="row">
    <div class="col-md-4 mx-auto text-center">
        <button type="button" class="btn btn-sm btn-primary my-3" data-bs-toggle="modal" data-bs-target="#probandoModal">
            Más información
        </button>
    </div>
</div>
<div class="modal fade" id="probandoModal" tabindex="-1" aria-labelledby="probandoModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="probandoModalLabel">Más información</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque aliquam vitae odio a ullamcorper. Vestibulum justo lorem, gravida et tempor in, vulputate id libero. Etiam feugiat pulvinar aliquam. Pellentesque imperdiet
                    cursus lacus, sit amet lacinia metus posuere at. Maecenas pretium libero leo, non fermentum ipsum mattis ac. Vivamus vel arcu et ligula interdum ultrices. Curabitur ut placerat tellus, quis euismod quam. Quisque tempor,
                    diam id bibendum fringilla, urna sapien imperdiet nulla, at ultrices sapien leo nec metus. Aliquam id arcu tortor.
                </p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-sm btn-secondary" data-bs-dismiss="modal">Cerrar</button>
            </div>
        </div>
    </div>
</div>
```

Recuerden que al copiar y pegar estas distintas partes se podría desordenar un poco su código fuente. Para volver a ordenarlo pueden usar https://webformatter.com/html 

- - - - - - - - - -

#### Exploración práctica

Nuevamente aprovecharemos un ejemplo del sitio web oficial de Bootstrap: https://getbootstrap.com/docs/5.1/examples/album/

Corresponde repetir la operación de copiar el código fuente completo, para pegarlo en un documento recién creado en un editor de código fuente, para luego guardarlo como `index.html` y hacer los ajustes necesario para que se vea tal como está ofrecido en línea. 

Sobre tal base, haremos algunos cambios que nos permitirán tener un [*carousel*](https://getbootstrap.com/docs/5.1/components/carousel/) en la parte superior, desplegar un [*modal*](https://getbootstrap.com/docs/5.1/components/modal/) cuando se presione un botón en cada [*card*](https://getbootstrap.com/docs/5.1/components/card/). 

Donde haya que sumar imágenes, aprovecharemos el servicios de https://picsum.photos/

**Paso a paso, el proceso sería así**:

1. Copiar el código fuente de https://getbootstrap.com/docs/5.1/examples/album/ y pegarlo en un documento nuevo, el que debe guardarse como `index.html`
2. Revisar los vínculos rotos, borrar metadatos innecesarios y eliminar 3 tarjetas (originalmente son 9, usaremos 6). Conviene ordenar lo editado con https://webformatter.com/html
3. Incluir un Carousel, reemplazando la sección con el título "Album example". Se puede incluir el código compartido más arriba, en la sección de Teoría (pero edite el tamaño de las imágenes random, para que no se pixelen; y use el formato WebP, para que no pesen tanto)
4. Eliminar el par de botones en cada tarjeta (View|Edit) para dejar sólo uno (View o Edit)
5. Cambiar el botón que dejamos por "más información" con el que probamos el modal (más arriba, en sección de Teoría). Incluya también la parte del modal casi al cierre del `<body>…</body>`.
6. "Poner más diseño": Decidamos un sentido para la página y anunciémoslo en la sección de la navegación, cambiando el ícono en SVG y la palabra Album; integremos p5.js como fondo, con un emoji que siga al mouse; cambiemos todas las imágenes y textos por una selección personal.
7. Subir a una nuevo repositorio de GitHub y activar GitHub Pages.


- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_04) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_06)
