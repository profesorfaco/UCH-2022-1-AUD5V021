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

- - - - - - - - - - - - - - - 

#### Exploración práctica

Corresponde tener a mano:

- una descripción del [método `toLocaleString()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Number/toLocaleString); y

- la [documentación de Charts.js](https://www.chartjs.org/docs/latest/).

Partiremos con el siguiente código, que corresponde copiar y pegar en un documento recién creado en su editor de código fuente. Documento que tienen que guardar como `index.html`: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js" integrity="sha512-QSkVNOCYLtj73J4hbmVoOV6KVZuMluZlioC+trLpewV8qMjsWqlIQvkn1KGX2StWvPMdWGBqim1xlC8krl1EKQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col-sm-10 col-md-9 col-lg-8 col-xl-7 col-xxl-6 mx-auto mt-5">
                    <h1 class="text-center fs-3 mb-4">Pandemia</h1>
                </div>
                <div class="col-md-11 col-lg-10 col-xl-9 col-xxl-8 mx-auto my-1">
                    <canvas id="misBarritas" class="my-4"></canvas>
                </div>
                <div class="col-sm-10 col-md-9 col-lg-8 col-xl-7 col-xxl-6 mx-auto mb-3">
                    <p>Estos son datos oficiales, <a href="https://github.com/MinCiencia/Datos-COVID19/tree/master/output/producto5" target="_blank">obtenidos del repositorio de GitHub de Datos-COVID19</a> del Ministerio de Ciencia, Tecnología, Conocimiento, e Innovación del Gobierno de Chile.</p>
                </div>
            </div>
        </div>
        <script>
            async function visualizacion() {
                const consulta = await fetch("https://raw.githubusercontent.com/MinCiencia/Datos-COVID19/master/output/producto5/TotalesNacionales.csv");
                const data = await consulta.text();
                const filas = data.split("\n");
                const fechas = filas[0].split(",").slice(1);
                const activos = filas[5].split(",").slice(1);
                new Chart(document.getElementById("misBarritas").getContext("2d"), {
                    type: "bar",
                    data: {
                        labels: fechas,
                        datasets: [{ data: activos,  backgroundColor: "#d00" }]
                    },
                    options: {
                        scales: {
                            y: {
                                ticks: {
                                    callback: function (numero) {
                                        return numero.toLocaleString("es-CL");
                                    }
                                }
                            }
                        },
                        plugins: {
                            legend: { display: false },
                            title: { display: true, text: "CASOS ACTIVOS DE COVID-19 EN CHILE" },
                        }
                    }
                })
            }
            visualizacion();
        </script>
    </body>
</html>
```

Usamos `fetch()` para obtener los datos más recientes en [TotalesNacionales.csv](https://github.com/MinCiencia/Datos-COVID19/blob/master/output/producto5/TotalesNacionales.csv). En caso no hayas revisado los videos de Daniel Shiffman recomendados en la clase anterior, estos fueron:

- https://youtu.be/tc8DU14qX6I
- https://youtu.be/uxf0--uiX0I

A tales videos podrían sumar el que enseña como ir por un CSV (**C**omma **S**eparated **V**alues) publicado por la NASA:

- https://youtu.be/RfMkdvN-23o

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_06) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_08)
