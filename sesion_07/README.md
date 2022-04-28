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

En este caso estamos yendo a buscar un JSON en línea. Pero no lo hacemos con p5.js. Ya estamos usando una biblioteca (charts.js), mejor evitar una segunda (p5.js). En este caso usamos un [Fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch), que es parte del lenguaje de programación.

Para comprender el uso de fetch conviene revisar un par de videos de Daniel Shiffman:

- https://youtu.be/tc8DU14qX6I
- https://youtu.be/uxf0--uiX0I


- - - - - - - - - - - - - - - 

#### Exploración práctica

Haremos fetch() de un [JSON](https://raw.githubusercontent.com/profesorfaco/front-end/main/sesion_07/titanic.json) con algunos datos sobre los pasajeros del Titanic. Originalmente los datos estaban disponibles en un [CSV] que presentado por GitHub se ve tal como una [hoja de cálculo](https://github.com/datasciencedojo/datasets/blob/master/titanic.csv), pero también podemos verlo en su [presentación original](https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv)

Los datos son:

- PassengerId: identificador único del pasajero.

- Survived: si el pasajero sobrevivió al naufragio, codificada como 0 (no) y 1 (si). 

- Pclass: clase a la que pertenecía el pasajero: 1, 2 o 3.

- Name: nombre del pasajero.

- Sex: sexo del pasajero.

- Age: edad del pasajero.

- SibSp: número de hermanos, hermanas, hermanastros o hermanastras en el barco.

- Parch: número de padres e hijos en el barco.

- Ticket: identificador del billete.

- Fare: precio pagado por el billete.

- Cabin: identificador del camarote asignado al pasajero.

- Embarked: puerto en el que embarcó el pasajero, puede ser S, C o Q (Southampton, Cherburgo o Queenstown, respectivamente)


Partiremos con el siguiente código, que corresponde copiar y pegar en un documento recién creado en su editor de código fuente. Documento que tienen que guardar como `index.html`: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <!-- CSS de Bootstrap-->
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <style>
            :root {
                --bs-body-color: #eef;
                --bs-body-bg: #10121c;
            }
        </style>
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body>
        <header>
            <div class="container">
                <div class="row pt-5">
                    <div class="col-sm-10 col-md-8 col-lg-6 mx-auto">
                        <h1 class="display-4 text-center py-2">Titanic</h1>
                        <p class="lead">Dos años fueron necesarios para construir el Titanic, también conocido como el barco insumergible. Y sin embargo, después de navegar durante cuatro días y medio, y, tras chocar con un iceberg, se hundió en apenas dos horas y 40 minutos.</p>
                        <p>El 10 de abril de 1912 el Titanic zarpó desde Southampton en su viaje inaugural, que tenía por destino final a Nueva York. El barco insumergible cruzó el canal de la Mancha hasta su primera escala, Cherburgo, en Normandía. Posteriormente viajó hasta el puerto de Queenstown (hoy Cork, Irlanda) para recoger a los últimos pasajeros antes de adentrarse en el océano Atlántico.</p>
                        <p>De los <a href="https://github.com/datasciencedojo/datasets/blob/master/titanic.csv" target="_blank" class="link-light">registros de 891 pasajeros</a>, podemos obtener algunos datos:</p>
                    </div>
                </div>
            </div>
        </header>

        <main class="container">
            <div class="accordion mx-md-5 my-5 rounded-0" id="accordionExample">
                <!--Edades de pasajeros-->
                <div class="accordion-item rounded-0">
                    <h2 class="accordion-header bg-dark" id="headingOne"><button class="accordion-button rounded-0" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">Edades</button></h2>
                    <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne" data-bs-parent="#accordionExample">
                        <div class="accordion-body text-black-50">
                            <p>La edad promedio de quienes viajaban en el titanic era de <span id="edad_promedio"></span></p>
                        </div>
                    </div>
                </div>
                <!--Pasajeras y pasajeros-->
                <div class="accordion-item rounded-0">
                    <h2 class="accordion-header" id="headingTwo">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">Pasajeras y pasajeros</button>
                    </h2>
                    <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo" data-bs-parent="#accordionExample">
                        <div class="accordion-body text-black-50">
                            <p>De un total de 891 personas, <span id="total_mujeres"></span> de ellas eran mujeres y <span id="total_hombres"></span> eran hombres.</p>
                        </div>
                    </div>
                </div>
                <!--Clases-->
                <div class="accordion-item rounded-0">
                    <h2 class="accordion-header" id="headingThree">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">Las tres clases</button>
                    </h2>
                    <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="headingThree" data-bs-parent="#accordionExample">
                        <div class="accordion-body text-black-50">
                            <p>Eran tres clases, en primera clase viajaban ?? personas, en segunda viajaban ?? y en tercera ??.</p>
                        </div>
                    </div>
                </div>
                <!--Otros-->
                <div class="accordion-item rounded-0">
                    <h2 class="accordion-header" id="headingFour">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseFour" aria-expanded="false" aria-controls="collapseFour">Otro dato</button>
                    </h2>
                    <div id="collapseFour" class="accordion-collapse collapse" aria-labelledby="headingFour" data-bs-parent="#accordionExample">
                        <div class="accordion-body text-black-50">
                            <p>Define otro dato.</p>
                        </div>
                    </div>
                </div>
                <!--Otro más-->
                <div class="accordion-item rounded-0">
                    <h2 class="accordion-header" id="headingFive">
                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseFive" aria-expanded="false" aria-controls="collapseFive">Otro dato más</button>
                    </h2>
                    <div id="collapseFive" class="accordion-collapse collapse" aria-labelledby="headingFive" data-bs-parent="#accordionExample">
                        <div class="accordion-body text-black-50">
                            <p>Define otro dato más.</p>
                        </div>
                    </div>
                </div>
                <!--Fin-->
            </div>
            <div class="row">
                <div class="col-sm-10 col-md-8 col-lg-6 mx-auto">
                    <p>Los registros de 891 representan una parte de los más de 2.400 personas que viajaban en el Titanic aquel fatídico 14 de abril de 1912, cuando la nave choca con el iceberg faltando minutos para la medianoche.</p>
                </div>
            </div>
        </main>

        <aside>
            <div class="container">
                <div class="row py-5">
                    <div class="col-sm-10 col-md-8 col-lg-6 mx-auto small text-center">            
                        <p>Fuentes: <a href="https://historia.nationalgeographic.com.es/a/historia-titanic-tragedia-barco-insumergible_16344">La historia del Titanic, la tragedia del barco insumergible</a>, <a href="https://rpubs.com/paraneda/titanic">RPubs - Titanic</a>, otra y otra más.</p>
                    </div>
                </div>
            </div>
        </aside>

        <footer>
            <div class="container">
                <div class="row">
                    <div class="col"><p class="text-muted mt-5 text-center small">Bootstrap v5.1 y Charts.js</p></div>
                </div>
            </div>
        </footer>

        <!-- Biblioteca de Bootstrap -->
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
        <!-- Biblioteca Chart.js -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js" integrity="sha512-QSkVNOCYLtj73J4hbmVoOV6KVZuMluZlioC+trLpewV8qMjsWqlIQvkn1KGX2StWvPMdWGBqim1xlC8krl1EKQ==" crossorigin="anonymous" referrerpolicy="no-referrer"
        ></script>
        <script>
            async function todo() {
                //el fetch
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/front-end/main/sesion_07/titanic.json");
                const data = await consulta.json();
                //algunas variables para calcular
                var edades = [];
                var mujeres = 0;
                var hombres = 0;
                //consultando en cada elemento del arreglo
                data.forEach((d) => {
                    edades.push(d.Age);
                    if (d.Sex == "female") {
                        mujeres = mujeres + 1;
                    } else {
                        hombres = hombres + 1;
                    }
                });
                //veamos las edades en la consola
                console.log(edades);
                //saquemos los null de las edades
                var edadesreales = edades.filter((e) => {
                    return e != null;
                });
                //veamos las edadesreales en la consola
                console.log(edadesreales);
                //ahora saquemos un promedio de las edadesreales
                var promedio = edadesreales.reduce((a, b) => a + b, 0) / edadesreales.length;
                //y completemos un par de frase
                document.querySelector("#edad_promedio").innerHTML = Math.round(promedio) + " años.";
                document.querySelector("#total_mujeres").innerHTML = mujeres;
                document.querySelector("#total_hombres").innerHTML = hombres;
                /*
                    Los demás datos deben ser propustos por ustedes.
                    Cuando tengan datos suficientes, había que visualizarlos.
                    Habrá que colocar una visualización dentro de cada división de clase .accordion-body
                */
            }
            todo().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

Una vez hayan guardado el documento como `index.html`, corresponde leer y comprender lo que está preparado, echarle un vistazo en el navegador y volver al editor de código fuente para seguir trabajando.


- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_06) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_08)
