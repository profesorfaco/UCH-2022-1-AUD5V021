# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 28 de abril → sesion_07 → Bootstrap v5.1 y p5.js

- - - - - - - - 

#### Teoría

Volvamos con [p5.js](https://p5js.org/es/), la biblioteca de JavaScript

> para la programación creativa, que busca hacer que programar sea accesible e inclusivo para artistas, diseñadores, educadores, principiantes y cualquier otra persona! p5.js es gratuito y de código abierto porque creemos que el software y las herramientas para aprenderlo deben ser accesibles para todos.

Recordemos que p5.js nos permite manipular el DOM más allá del Canvas, mediante:

- [`createElement()`](https://p5js.org/es/reference/#/p5/createElement)
- [`removeElements()`](https://p5js.org/es/reference/#/p5/removeElements)
- [`select()`](https://p5js.org/es/reference/#/p5/select)
- [`selectAll()`](https://p5js.org/es/reference/#/p5/selectAll)
- [etc.](https://p5js.org/es/reference/)

También nos permite [pre-cargar](https://p5js.org/reference/#/p5/preload) datos que se intercambian en formatos ligeros tales como [XML](https://p5js.org/es/reference/#/p5/loadXML), [CSV](https://p5js.org/es/reference/#/p5/loadTable) y [JSON](https://p5js.org/es/reference/#/p5/loadJSON). Entre los que comparten datos en JSON, tenemos:

- Movimientos telúricos: https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php
- Tiempo atmosférico: https://openweathermap.org/current#current_JSON
- Datos públicos: https://github.com/juanbrujo/listado-apis-publicas-en-chile
- Y un larguísimo etcéctera de [APIs](https://es.wikipedia.org/wiki/Interfaz_de_programaci%C3%B3n_de_aplicaciones) y cuanto dato se disponga en tal formato.

**Con JSON y p5.js, podríamos crear elementos ([`createElement()`](https://p5js.org/es/reference/#/p5/createElement)) basándonos en los datos en un JSON precargado, y con ellos estructurar una página completa con un aspecto basado en lo que ofrece Bootstrap**.

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
        <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.min.js" integrity="sha512-N4kV7GkNv7QR7RX9YF/olywyIgIwNvfEe2nZtfyj73HdjCUkAfOBDbcuJ/cTaN04JKRnw1YG1wnUyNKMsNgg3g==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col-sm-10 col-md-9 col-lg-8 col-xl-7 col-xxl-6 mx-auto my-5">
                    <h1 class="text-center fs-3 mb-4">Lorem ipsum dolor sit amet</h1>

                    <p>Consectetur adipiscing elit. Nunc consequat felis at orci scelerisque, at blandit ex tempor. Vivamus sodales commodo quam vel commodo. Sed placerat dictum mauris in ultrices. Fusce feugiat risus ac nibh pretium dignissim. Praesent vel nulla pellentesque, congue velit a, pulvinar quam. Phasellus consectetur nibh id lectus aliquam, at tincidunt turpis pellentesque. Nulla a urna vitae enim consequat pellentesque.</p>

                    <table class="table table-sm table-striped table-hover">
                        <thead>
                            <tr>
                                <th scope="col">Magnitud</th>
                                <th scope="col">Lugar</th>
                            </tr>
                        </thead>
                        <tbody></tbody>
                    </table>
                </div>
            </div>
        </div>
        <script>
            var data;
            var chileno = [];
            function preload() {
                data = loadJSON("https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_week.geojson");
            }
            function setup() {
                noCanvas;
                data.features.forEach((t) => {
                    if (t.properties.place.includes("Chile")) {
                        chileno.push(t);
                    }
                });
                console.log(chileno);
                var donde = select("tbody");
                chileno.forEach((c) => {
                    createElement("tr", "<td>" + c.properties.mag + " M<sub>W</sub></td><td>" + c.properties.place + "</td>").parent(donde);
                });
            }
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_06) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_08)
