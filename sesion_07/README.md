# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 28 de abril → sesion_07 → Bootstrap v5.1 y p5.js

- - - - - - - - 

#### Teoría

Recordemos que [p5.js](https://p5js.org/es/) es una biblioteca de JavaScript

> para la programación creativa, que busca hacer que programar sea accesible e inclusivo para artistas, diseñadores, educadores, principiantes y cualquier otra persona! p5.js es gratuito y de código abierto porque creemos que el software y las herramientas para aprenderlo deben ser accesibles para todos.

Recordemos que p5.js nos permite manipular el DOM más allá del Canvas, mediante:

- [`createElement()`](https://p5js.org/es/reference/#/p5/createElement)
- [`removeElements()`](https://p5js.org/es/reference/#/p5/removeElements)
- [`select()`](https://p5js.org/es/reference/#/p5/select)
- [`selectAll()`](https://p5js.org/es/reference/#/p5/selectAll)
- [etc.](https://p5js.org/es/reference/)

También nos permite [pre-cargar](https://p5js.org/reference/#/p5/preload) datos que se intercambian en formatos ligeros tales como [XML](https://p5js.org/es/reference/#/p5/loadXML), [CSV](https://p5js.org/es/reference/#/p5/loadTable) y [JSON](https://p5js.org/es/reference/#/p5/loadJSON). 

Entre los que comparten datos en JSON, tenemos:

- Movimientos telúricos: https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php
- Tiempo atmosférico: https://openweathermap.org/current#current_JSON
- Datos públicos: https://github.com/juanbrujo/listado-apis-publicas-en-chile
- Y un larguísimo etcéctera de [APIs](https://es.wikipedia.org/wiki/Interfaz_de_programaci%C3%B3n_de_aplicaciones) y cuanto dato se disponga en tal formato.

**Como vimos la sesión recién pasada, con JSON y p5.js, podríamos crear elementos ([`createElement()`](https://p5js.org/es/reference/#/p5/createElement)) basándonos en los datos en un JSON precargado, y presentarlos al modo que nos permita el CSS compilado de Bootstrap**.

No conviene quedarnos con la idea de que siempre necesitaremos de p5.js para ir por algún dato. También podemos tomar un JSON con el [uso de Fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch). La API Fetch es parte del lenguaje de programación original, por lo que podemos usarla sin vincular una biblioteca.

Lo recién dicho implica un desvío de lo que estamos viendo, por lo que conviene revisarlo aparte e ideal sería hacerlo con un par de videos publicados por Daniel Shiffman:

- https://youtu.be/tc8DU14qX6I
- https://youtu.be/uxf0--uiX0I

Seguiremos trabajando en esta sesión con p5.js, pero no tendrán que depender por siempre de esta biblioteca para poder tomar los datos que sean intercambiados mediante JSON u otro formato ligero de intercambio.

- - - - - - - 

#### Exploración práctica

Corresponde tener a mano:

- una descripción del [método `forEach()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/forEach);

- una descripción del [método `includes()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/includes).

- una descripción del [método `push()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/push); y

- las [referencias de p5.js](https://p5js.org/es/reference/).

Partiremos con el siguiente código, que corresponde copiar y pegar en un documento recién creado en su editor de código fuente. Documento que tienen que guardar como `index.html`: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <script
            src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.1/p5.min.js"
            integrity="sha512-NxocnqsXP3zm0Xb42zqVMvjQIktKEpTIbCXXyhBPxqGZHqhcOXHs4pXI/GoZ8lE+2NJONRifuBpi9DxC58L0Lw=="
            crossorigin="anonymous"
            referrerpolicy="no-referrer"
        ></script>
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body class="bg-light bg-gradient">
        <div class="sticky-top text-end p-3">
            <select class="form-select form-select-sm ms-auto shadow-sm" onchange="location = this.value;" style="width: 160px;">
                <option value="index.html" selected>Chile</option>
                <option value="pais-x.html">País X</option>
                <option value="pais-y.html">País Y</option>
                <option value="pais-z.html">País Z</option>
            </select>
        </div>
        <div class="container">
            <div class="row">
                <div class="col-sm-10 col-md-9 col-lg-8 col-xl-7 col-xxl-6 mx-auto mt-5">
                    <h1 class="text-center fs-3 mb-5">Lorem ipsum dolor sit amet</h1>

                    <p>Consectetur adipiscing elit. Nunc consequat felis at orci scelerisque, at blandit ex tempor. Vivamus sodales commodo quam vel commodo. Sed placerat dictum mauris in ultrices. Fusce feugiat risus ac nibh pretium dignissim.</p>

                    <table class="table table-sm table-striped table-hover mt-5">
                        <thead>
                            <tr>
                                <th scope="col">Magnitud</th>
                                <th scope="col">Lugar</th>
                                <th scope="col">Detalles</th>
                            </tr>
                        </thead>
                        <tbody></tbody>
                    </table>
                </div>
            </div>
        </div>
        <script>
            var data;
            var pais = [];
            function preload() {
                data = loadJSON("https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_week.geojson");
            }
            function setup() {
                noCanvas;
                data.features.forEach((t) => {
                    if (t.properties.place.includes("Chile")) {
                        pais.push(t);
                    }
                });
                console.log(pais);
                var donde = select("tbody");
                pais.forEach((p) => {
                    createElement("tr", "<td>" + p.properties.mag + " M<sub>W</sub></td><td>" + p.properties.place + "</td>" + "<td><a href='" + p.properties.url + "' target='_blank'>vínculo</a></td>").parent(donde);
                });
            }
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_06) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_08)
