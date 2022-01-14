# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 28 de abril → sesion_07 → Bootstrap v5 y p5.js

- - - - - - - - 

#### Teoría

**[Chart.js](https://www.chartjs.org/) es una biblioteca de JavaScript que nos permite implementar gráficos (dentro de un elemento [`<canvas>…</canvas>`](https://www.w3schools.com/html/html5_canvas.asp)) de manera sencilla**.

Con [Chart.js](https://www.chartjs.org/) podemos implementar gráficos de [línea](https://www.chartjs.org/docs/latest/charts/line.html), [barra](https://www.chartjs.org/docs/latest/charts/bar.html), [radar](https://www.chartjs.org/docs/latest/charts/radar.html), [torta](https://www.chartjs.org/docs/latest/charts/doughnut.html), [área polar](https://www.chartjs.org/docs/latest/charts/polar.html), [burbujas](https://www.chartjs.org/docs/latest/charts/bubble.html) y [dispersión](https://www.chartjs.org/docs/latest/charts/scatter.html), que son los tipos de gráficos disponibles en esta biblioteca de JavaScript, que ofrece:

> *simple yet flexible JavaScript charting for designers & developers*. 
 
Hay muchas alternativas de *JavaScript charting*. Por nombrar algunas: [Apache ECharts](https://echarts.apache.org/en/index.html), [d3.js](https://d3js.org/) (que [tuvo su cuarto de hora](https://medium.com/@PepsRyuu/why-i-no-longer-use-d3-js-b8288f306c9a)), [dygraph](https://dygraphs.com/). 

Usaremos [Chart.js](https://www.chartjs.org/) porque permite resolver gráficos simples ([línea](https://www.chartjs.org/docs/latest/charts/line.html), [barra](https://www.chartjs.org/docs/latest/charts/bar.html), [torta](https://www.chartjs.org/docs/latest/charts/doughnut.html), etc.) con una estructura clara:

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

#### Exploración

Antes de partir la exploración necesaria para hacer la configuración de [Chart.js](https://www.chartjs.org/docs/latest/charts/?h=type), corresponde tener a mano:

- el [método `forEach()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/forEach);

- el [método `push()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/push); 

- el [método `toLocaleString()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Number/toLocaleString); y

- la [documentación de Charts.js](https://www.chartjs.org/docs/latest/).

Aquello que pueden tener a mano se aplica en lo que sigue:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.5.1/chart.min.js" integrity="sha512-Wt1bJGtlnMtGP0dqNFH1xlkLBNpEodaiQ8ZN5JLA5wpc1sUlk/O5uuOMNgvzddzkpvZ9GLyYNa8w2s7rqiTk5Q==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <title>Esto es un ejemplo</title>
    </head>
    <body>
        <canvas id="misBarritas"></canvas>
        <script>
            var poblacion = [
                { region: "Arica y Parinacota", hombres: 112581, mujeres: 113487 },
                { region: "Tarapacá", hombres: 167793, mujeres: 113487 },
                { region: "Antofagasta", hombres: 315014, mujeres: 292520 },
                { region: "Atacama", hombres: 144420, mujeres: 141748 }
            ];

            var lasRegiones = [], losHombres = [], lasMujeres = [];

            poblacion.forEach(d => {
                lasRegiones.push(d.region);
                losHombres.push(d.hombres);
                lasMujeres.push(d.mujeres);
            });

            new Chart(document.getElementById("misBarritas").getContext("2d"), {
                type: "bar",
                data: {
                    labels: lasRegiones,
                    datasets: [
                        {
                            data: losHombres,
                            backgroundColor: "#f1a340" /* revisar https://colorbrewer2.org */,
                            label: "Hombres",
                        },
                        {
                            data: lasMujeres,
                            backgroundColor: "#645294" /* revisar https://colorbrewer2.org */,
                            label: "Mujeres",
                        },
                    ],
                },
                options: {
                    scales: {
                        y: {
                            ticks: {
                                callback: function (numero) {
                                    return numero.toLocaleString("es-CL");
                                },
                            },
                        },
                    },
                    plugins: {
                        title: {
                            display: true,
                            text: "POBLACIÓN: POR SEXO Y REGIONES",
                        },
                    },
                },
            });
        </script>
    </body>
</html>
```

Copien y peguen el código fuente en su editor y agreguen más datos en la variable `poblacion` para poder completar el gráfico: 

![Captura de Pantalla 2021-10-07 a la(s) 10 48 47](https://user-images.githubusercontent.com/7999767/136397506-26d4ba51-89c5-46fc-abdd-0ea4641ce09a.png)

Notarán que al agregar un nuevo elemento al arreglo contenido en la variable `poblacion`, siguiendo la estructura `{region: "…", hombres: …, mujeres: …},` se agregarán las barras correspondondientes e incluso se alterarán los valores en el eje Y.


- - - - - - - 

#### Práctica

https://profesorfaco.github.io/interaccion/sesion_07/

- - - - - - - 

[← CLASE ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_06) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/front-end/tree/main/sesion_08)
