# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 28 de abril → sesion_07 → Bootstrap v5.1 y Charts.js

- - - - - - - - 

#### Teoría

**[Chart.js](https://www.chartjs.org/) es una biblioteca de JavaScript que nos permite implementar gráficos (dentro de un elemento [`<canvas>…</canvas>`](https://www.w3schools.com/html/html5_canvas.asp)) de manera sencilla**.

Con [Chart.js](https://www.chartjs.org/) podemos implementar gráficos de [línea](https://www.chartjs.org/docs/latest/charts/line.html), [barra](https://www.chartjs.org/docs/latest/charts/bar.html), [radar](https://www.chartjs.org/docs/latest/charts/radar.html), [torta](https://www.chartjs.org/docs/latest/charts/doughnut.html), [área polar](https://www.chartjs.org/docs/latest/charts/polar.html), [burbujas](https://www.chartjs.org/docs/latest/charts/bubble.html) y [dispersión](https://www.chartjs.org/docs/latest/charts/scatter.html), que son los tipos de gráficos disponibles en esta biblioteca de JavaScript, que se ofrece como *simple yet flexible JavaScript charting for designers & developers*. 
 
Conviene mencionar otras alternativas de *JavaScript charting*. Por nombrar algunas: [Apache ECharts](https://echarts.apache.org/en/index.html), [d3.js](https://d3js.org/) (que [tuvo su cuarto de hora](https://medium.com/@PepsRyuu/why-i-no-longer-use-d3-js-b8288f306c9a)), [dygraph](https://dygraphs.com/). 

Pero usaremos [Chart.js](https://www.chartjs.org/) porque en el contexto intructorio basta con resolver gráficos simples aprovechando una estructura clara:

```
var contexto = document.getElementById('nombre').getContext('2d');
var configuracion = {type: '…', data: {…}, options: {…}}
var chart = new Chart(contexto, configuracion);
```

La estructura también puede escribirse así:

```
new Chart(document.getElementById('nombre').getContext('2d'), {type: '…', data: {…}, options: {…}});
```

Esto es lo mismo que decir:

- Vamos a crear un `new Chart(…, {…});`

- Tal será su contexto `(document.getElementById('nombre').getContext('2d')`

- Y tal será su configuración: `{type: '…', data: {…}, options: {…}}`

En la configuración se decide el tipo de gráfico y los datos para el gráfico, además de opciones de presentación.

Revisemos lo dicho con un código que pueden copiar y pegar en un documento HTML de nombre `ejemplo-1.html`:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <!-- Vamos a buscar el CSS de Bootstrap-->
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <!-- Vamos a buscar la biblioteca Chart.js-->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js" integrity="sha512-QSkVNOCYLtj73J4hbmVoOV6KVZuMluZlioC+trLpewV8qMjsWqlIQvkn1KGX2StWvPMdWGBqim1xlC8krl1EKQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col-md-11 col-lg-10 col-xl-9 col-xxl-8 mx-auto my-1">
                    <canvas id="misBarritas" class="my-4"></canvas>
                    <p class="text-center small">Fuente: <a href="http://www.censo2017.cl/descargas/home/sintesis-de-resultados-censo2017.pdf" target="_blank">Síntesis de resultados CENSO 2017</a>.</p>
                </div>
            </div>
        </div>
        <script>
            function visualizacion() {
                const regiones = ["Arica y Parinacota", "Tarapacá", "Antofagasta", "Atacama", "Coquimbo", "Valparaíso", "Metropolitana", "O'Higgins", "Maule", "Ñuble", "Biobío", "La Araucanía", "Los Ríos", "Los Lagos", "Aysén", "Magallanes",];
                const habitantes = [226068, 330558, 607534, 286168, 757586, 1815902, 7112808, 914555, 1044950, 480609, 1556805, 957224, 384837, 828708, 103158, 166533];
                new Chart(document.getElementById("misBarritas").getContext("2d"), {
                    type: "bar",
                    data: {
                        labels: regiones,
                        datasets: [{ data: habitantes, label: "Población total", backgroundColor: "#aaa" }],
                    },
                    options: {
                        indexAxis: "y",
                    },
                });
            }
            visualizacion();
        </script>
    </body>
</html>
```

Así como tenemos los datos bien ordenados en dos arreglos, para "llegar y visualizar", también podríamos trabajar un poco con los datos antes de ordenarlos para visualizar. Así se hace en el siguiente código que conviene copiar y pegar en `ejemplo-2.html`:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <!-- Vamos a buscar el CSS de Bootstrap-->
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <!-- Vamos a buscar la biblioteca Chart.js-->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js" integrity="sha512-QSkVNOCYLtj73J4hbmVoOV6KVZuMluZlioC+trLpewV8qMjsWqlIQvkn1KGX2StWvPMdWGBqim1xlC8krl1EKQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col-md-11 col-lg-10 col-xl-9 col-xxl-8 mx-auto my-1">
                    <canvas id="masBarritas" class="my-4"></canvas>
                </div>
            </div>
        </div>
        <script>
            async function visualizacion() {
                var consulta = await fetch("https://digimon-api.vercel.app/api/digimon");
                var data = await consulta.json();
                //crear algunas variables
                var cuantosTraining = 0;
                var cuantosRookie = 0;
                var cuantosChampion = 0;
                var cuantosFresh = 0;
                var cuantosMega = 0;
                var cuantosArmor = 0;
                var cuantosUltimate = 0;
                //cambiar el 0
                data.forEach((d) => {
                    if (d.level == "In Training" || d.level == "Training") {
                        cuantosTraining = cuantosTraining + 1;
                    } else if (d.level == "Rookie") {
                        cuantosRookie = cuantosRookie + 1;
                    } else if (d.level == "Champion") {
                        cuantosChampion = cuantosChampion + 1;
                    } else if (d.level == "Fresh") {
                        cuantosFresh = cuantosFresh + 1;
                    } else if (d.level == "Mega") {
                        cuantosMega = cuantosMega + 1;
                    } else if (d.level == "Armor") {
                        cuantosArmor = cuantosArmor + 1;
                    } else {
                        cuantosUltimate = cuantosUltimate + 1;
                    }
                });
                //armar el gráfico
                new Chart(document.getElementById("masBarritas").getContext("2d"), {
                    type: "bar",
                    data: {
                        labels: ["Fresh", "In training", "Rookie", "Champion", "Armor", "Mega", "Ultimate"],
                        datasets: [
                            {
                                data: [cuantosFresh, cuantosTraining, cuantosRookie, cuantosChampion, cuantosArmor, cuantosMega, cuantosUltimate],
                                backgroundColor: ["#ccebc5", "#a8ddb5", "#7bccc4", "#4eb3d3", "#2b8cbe", "#0868ac", "#084081"],
                            },
                        ],
                    },
                    options: {
                        indexAxis: "y",
                        plugins: {
                            legend: { display: false },
                        },
                    },
                });
            }
            visualizacion().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

En este caso estamos yendo a buscar un JSON en línea. Pero no lo hacemos con p5.js. Mejor sería usar un [Fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch). La API Fetch es parte del lenguaje de programación.

Para comprender el uso de fetch conviene revisar un par de videos publicados por Daniel Shiffman:

- https://youtu.be/tc8DU14qX6I
- https://youtu.be/RfMkdvN-23o
- https://youtu.be/uxf0--uiX0I


- - - - - - - - - - - - - - - 

#### Exploración práctica

Partiremos con el siguiente código, que corresponde copiar y pegar en un documento recién creado en su editor de código fuente. Documento que tienen que guardar como `index.html`: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <!-- CSS de Bootstrap-->
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />

        <title>Hello, world!</title>
    </head>
    <body>
        <header class="p-5 mb-4 rounded-3">
            <div class="container">
                <h1 class="display-5 fw-bold">Digimon</h1>
                <div class="row align-items-center g-5">
                    <div class="col-md-7">
                        <p class="lead">Los Digimon son criaturas digitales que digievolucionan para mejorar su nivel de poder y habilidades con respecto a su anterior forma.</p>
                        <p>Los Digimon se dividen según diferentes tipos o atributos, actuando o cumpliendo un determinado rol (como un programa informático) que pueden ser principalmente de tipo: datos, vacuna o virus.</p>
                    </div>
                    <div class="col-md-5 d-none d-md-block">
                        <small class="text-muted">PONGA AQUÍ UN GRÁFICO CON CHART.JS, USE LOS DATOS DE DIGIMON. Y "PÓNGALE MÁS DISEÑO" A LA PÁGINA.</small>
                    </div>
                </div>
            </div>
        </header>

        <main class="container">
            <div class="accordion mb-5" id="accordionExample">
                <!--Fresh-->
                <div class="accordion-item">
                    <h2 class="accordion-header" id="headingOne"><button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">Fresh</button></h2>
                    <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne" data-bs-parent="#accordionExample">
                        <div class="accordion-body row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="LesFresh"></div>
                    </div>
                </div>
                <!--In Training-->
                <div class="accordion-item">
                    <h2 class="accordion-header" id="headingTwo">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">In Training</button>
                    </h2>
                    <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo" data-bs-parent="#accordionExample">
                        <div class="accordion-body row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="LesInTraining"></div>
                    </div>
                </div>
                <!--Rookies-->
                <div class="accordion-item">
                    <h2 class="accordion-header" id="headingThree">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">Rookies</button>
                    </h2>
                    <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="headingThree" data-bs-parent="#accordionExample">
                        <div class="accordion-body row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="LesRookie"></div>
                    </div>
                </div>
                <!--Champion-->
                <div class="accordion-item">
                    <h2 class="accordion-header" id="headingFour">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseFour" aria-expanded="false" aria-controls="collapseFour">Champion</button>
                    </h2>
                    <div id="collapseFour" class="accordion-collapse collapse" aria-labelledby="headingFour" data-bs-parent="#accordionExample">
                        <div class="accordion-body row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="LesChampion"></div>
                    </div>
                </div>
                <!--Armor-->
                <div class="accordion-item">
                    <h2 class="accordion-header" id="headingFive">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseFive" aria-expanded="false" aria-controls="collapseFive">Armor</button>
                    </h2>
                    <div id="collapseFive" class="accordion-collapse collapse" aria-labelledby="headingFive" data-bs-parent="#accordionExample">
                        <div class="accordion-body row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="LesArmor"></div>
                    </div>
                </div>
                <!--Mega-->
                <div class="accordion-item">
                    <h2 class="accordion-header" id="headingSix">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseSix" aria-expanded="false" aria-controls="collapseSix">Mega</button>
                    </h2>
                    <div id="collapseSix" class="accordion-collapse collapse" aria-labelledby="headingSix" data-bs-parent="#accordionExample">
                        <div class="accordion-body row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="LesMega"></div>
                    </div>
                </div>
                <!--Ultimate-->
                <div class="accordion-item">
                    <h2 class="accordion-header" id="headingSeven">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseSeven" aria-expanded="false" aria-controls="collapseSeven">Ultimate</button>
                    </h2>
                    <div id="collapseSeven" class="accordion-collapse collapse" aria-labelledby="headingSeven" data-bs-parent="#accordionExample">
                        <div class="accordion-body row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="LesUltimate"></div>
                    </div>
                </div>
                <!--Fin-->
            </div>
        </main>

        <!-- Biblioteca de Bootstrap -->
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
        <!-- Biblioteca Chart.js -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js" integrity="sha512-QSkVNOCYLtj73J4hbmVoOV6KVZuMluZlioC+trLpewV8qMjsWqlIQvkn1KGX2StWvPMdWGBqim1xlC8krl1EKQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <script>
            async function todo() {
                const consulta = await fetch("https://digimon-api.vercel.app/api/digimon");
                const data = await consulta.json();
                data.forEach((d) => {
                    if (d.level == "In Training" || d.level == "Training") {
                        document.querySelector("#LesInTraining").innerHTML += '<div class="col"><img src="' + d.img + '" class="w-100"><p>' + d.name + "</p></div>";
                    } else if (d.level == "Rookie") {
                        document.querySelector("#LesRookie").innerHTML += '<div class="col"><img src="' + d.img + '" class="w-100"><p>' + d.name + "</p></div>";
                    } else if (d.level == "Champion") {
                        document.querySelector("#LesChampion").innerHTML += '<div class="col"><img src="' + d.img + '" class="w-100"><p>' + d.name + "</p></div>";
                    } else if (d.level == "Fresh") {
                        document.querySelector("#LesFresh").innerHTML += '<div class="col"><img src="' + d.img + '" class="w-100"><p>' + d.name + "</p></div>";
                    } else if (d.level == "Mega") {
                        document.querySelector("#LesMega").innerHTML += '<div class="col"><img src="' + d.img + '" class="w-100"><p>' + d.name + "</p></div>";
                    } else if (d.level == "Armor") {
                        document.querySelector("#LesArmor").innerHTML += '<div class="col"><img src="' + d.img + '" class="w-100"><p>' + d.name + "</p></div>";
                    } else {
                        document.querySelector("#LesUltimate").innerHTML += '<div class="col"><img src="' + d.img + '" class="w-100"><p>' + d.name + "</p></div>";
                    }
                });
            }
            todo().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

Usamos `fetch()` para tomar datos sobre los Digimon desde un JSON. Con tales datos rellenamos cada cuerpo en el [Accordion](https://getbootstrap.com/docs/5.1/components/accordion/). 

Con la misma estructura de condiciones, se podrían obtener números de las distintas evoluciones (ej: cuántos hay en cada una). Y con tales números podemos armar un gráfico.

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_06) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_08)
