# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 21 de abril → sesion_06 →  Bootstrap v5.1 y datos en JavaScript

- - - - - - - - 

#### Teoría

Esta clase abrirá un paréntesis para revisar un aspecto pendiente en JavaScript, aspecto que debe clarificarse antes de la siguiente sesión.

Para comenzar, partamos con un 18261884. 

Si nos entregan tal secuencia de números, sin contexto alguno, resultaría inútil. Pero es distinto de la siguiente manera: 

| País      |  Población       | Superficie     |
|:----------|:-----------------|:---------------|
| Chile     | 18261884         | 756102         |

Entendiendo cómo funciona una tabla, contamos con una clara orientación para la utilización de tal número como información sobre algo concreto: La población en Chile. 

Además del dato de la población de Chile, contamos con su superficie. Si dividimos el primer dato numérico por el segundo, obtenemos la densidad de la población en Chile. El resultado de aquella división es 24,15267252.

Los números 18261884 y 24,15267252 tienen una diferencia que corresponde apuntar:

- **18261884** es un número entero, un `int` (del inglés *integer*).

- **24,15267252** es un número de coma flotante, un `float` (del inglés *floating point number*; y no se olviden de esta diferencia, lo que para nosotros es coma, *for them* es punto, y el *coding* se hace en *english*).

A estos dos tipos de datos, podemos agregar: 

- **true** o **false** como las dos opciones posibles de un [tipo de dato lógico](https://es.wikipedia.org/wiki/Tipo_de_dato_l%C3%B3gico) (bool: *boolean*)

- **"A"** como un carácter (char: *character*)

Notemos que en el tipo de dato numérico y booleano no se usan comillas, pero en el caso del caracter sí. 

Mencionamos `int`, `float`, `bool` y `char` porque son palabras que en lenguajes de programación más clásicos se reservan para **declarar que tal variable almacenará tal tipo de dato**. 

**En JavaScript podemos crear toda variables con una única palabra reservada,`var`**. También podemos usar `let` y `const`. Para entender la diferencia, nos conviene consultar el artículo [Var, let y const. ¿Donde, cuando y por qué?](https://medium.com/@tatymolys/var-let-y-const-donde-cuando-y-por-qu%C3%A9-d4a0ee66883b).

Usando únicamente `var`, en JavaScript podemos asignar como contenido de la variable todas las siguientes alternativas:

```
var a = 18261884;
var b = 24.15267252;
var c = true;
var d = "Lisa the Vegetarian";
var e = ["Marge Simpson", "Homer Simpson", "Bart Simpson", "Lisa Simpson", "Maggie Simpson"];
var f = {
    mom: "Luann Van Houten",
    dad: "Kirk Van Houten",
    child: "Milhouse Van Houten"
};
var g = {
    mom: "Marge Simpson",
    dad: "Homer Simpson",
    children: ["Bart Simpson", "Lisa Simpson", "Maggie Simpson"]
};
var h = [
    {
        mom: "Marge",
        dad: "Homer",
        children: ["Bart", "Lisa", "Maggie"]
    },
    {
        mom: "Manjula",
        dad: "Apu",
        children: ["Poonam", "Sashi", "Pria", "Uma", "Anoop", "Sandeep", "Nabendu", "Gheet"]
    }
];

```

**Lo que cambia viene después del signo igual `=`, que en este caso está asignando contenido a cada variable.** 

Las variables `a`, `b` y `c` no requieren comillas. La variable `d`, que contiene una cadena de caracteres (*string*) sí usa comillas. 

La variable `e`, que contiene un arreglo, usa paréntesis cuadrado y cada elemento, por tratarse de un *string*, usa comillas (si fuesen números o booleanos no las usarían). 

La variable `f`, que contiene un objeto, usa paréntesis de llave que en su interior contiene pares de `nombre:valor`. 

Las variables `g` y `h` son mezclas de las anteriores.

Si necesitamos el valor de las variables `a`, `b`, `c` o `d`, basta con pedirlo directamente. Pero el caso es distinto si necesitamos un valor específico dentro de las variables  `e`, `f`, `g` o `h`.

Vamos con la variable `e`. Digamos que necesitamos a `Marge Simpson`. Para solicitarla tenemos que escribir `e[0]`, porque se encuentra en la primera posición del arreglo asignado como valor a la variable `e`. Si escribimos `e[1]` el resultado sería `Homer Simpson`. Corresponde **recordar que la primera posición es cero, no uno**.

Pasemos a la variable `f`. Si necesitamos escribir la frase `Fue Kirk Van Houten quien intentó dibujar la dignidad`, tendríamos que escribir `'Fue ' + f.dad + ' quien intentó dibujar la dignidad'`.

Vamos por la variable `g`. Si necesitamos escribir la frase `El chupete de Maggie Simpson`, tendríamos que escribir `'El chupete de ' + g.children[2]`.

Llegando a la variable `h`, conviene aprovechar algo preparado en el Editor de p5.js: https://editor.p5js.org/profesorfaco/sketches/8-3OZsD8O

¿Qué utilidad tienen variables como la `f`, `g` y `h`?

Un ejemplo de utilidad: Ellas pueden usarse en la construcción de una página como la hecha [la sesión recién pasada](https://github.com/profesorfaco/front-end/tree/main/sesion_05#exploraci%C3%B3n-pr%C3%A1ctica).

```
var i = [
{ id: 4, texto: "Este texto irá debajo de la imagen que en picsum tiene id 4." },
{ id: 5, texto: "Este texto irá debajo de la imagen que en picsum tiene id 5." },
{ id: 6, texto: "Este texto irá debajo de la imagen que en picsum tiene id 6." }
];
```

Copia la variable `i` y pégala en el `index.html` creado la sesión anterior, **dentro del script de p5.js que hace que el emoji siga al mouse**; pégala entre `<script>` y `setup(){…}`, esto es pegarla como variable global (lo primero dentro del script, fuera de un contexto específico) 

Y dentro del `setup(){…}`, pega lo que sigue:

```
var donde = select(".row-cols-1");
i.forEach((datos) =>{
    createElement('div','<div class="card shadow-sm"><img src="https://picsum.photos/id/'+datos.id+'/600/400.webp" class="card-img-top"><div class="card-body"><p class="card-text">'+datos.texto+'</p><div class="d-flex justify-content-between align-items-center"><button type="button" class="btn btn-sm btn-primary" data-bs-toggle="modal" data-bs-target="#probandoModalUno">El primero</button><small class="text-muted">9 mins</small></div></div></div>').class('col').parent(donde);
});
```

Guarda y revisa el resultado en tu navegador: Ahora deberías tener 9 tarjetas, no 6. Si agregas un objeto al arreglo contenido por la variable `i`, sumarás otra tarjeta. Si cambias los valores de `id` y `texto` dentro de cada objeto, se cambiarán los contenidos de las tarjetas. 

**Para recordar y dar el último paso**: Las variables `f` y `g` contienen un objeto. Las variables `h` e `i` son arreglos que contienen objetos. Luego, las variables `f`, `g`, `h` e `i`, con sus particularidades, aprovechan la Notación de Objetos de JavaScript, lo que en inglés es **J**ava**S**cript **O**bject **N**otation.

En lo recién dicho aparecen las iniciales con las que se nombra a un formato ligero de intercambio de datos: 

> [JSON](https://www.json.org/json-es.html) (JavaScript Object Notation - Notación de Objetos de JavaScript) es un formato ligero de intercambio de datos. Leerlo y escribirlo es simple para humanos, mientras que para las máquinas es simple interpretarlo y generarlo.

Tres ejemplos de [JSON](https://www.json.org/json-es.html):

- https://hp-api.herokuapp.com/api/characters/staff
- https://digimon-api.vercel.app/api/digimon
- https://aves.ninjas.cl/api/birds

¿Qué ofrece cada ejemplo? Eso lo pueden responder después de leer cada JSON. Para leerlos conviene contar con una extensión que permita visualizar JSON de manera más ordenada en su navegador web. Para Chrome: [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/mhimpmpmffogbmmkmajibklelopddmjf?hl=es) o [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=es). Para Firefox: [JSON Lite](https://addons.mozilla.org/es/firefox/addon/json-lite/) o [Basic JSON Formatter](https://addons.mozilla.org/es/firefox/addon/basic-json-formatter/).

Y para obtener los datos de un JSON en línea, también podemos contar con la ayuda de p5.js, como se puede revisar en los siguientes ejemplos del editor:

- https://editor.p5js.org/profesorfaco/sketches/7FrCDZKc1
- https://editor.p5js.org/profesorfaco/sketches/dbC5hqQya
- https://editor.p5js.org/profesorfaco/sketches/T-PeCUgjt

- - - - - - - - - - -

#### Exploración práctica

Corresponde tener a mano referencias para el uso de [`forEach()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach), [`if…else`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/if...else), [`includes()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/includes).

Partiremos con el siguiente código, que corresponde copiar y pegar en un documento recién creado en su editor de código fuente. Documento que tienen que guardar como `index.html`:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body>
        <header class="container">
            <div class="row">
                <div class="col">
                    <h1 class="text-center display-4 mt-5">PATOS EN CHILE</h1>
                    <h2 class="text-center fs-6 mb-5">Introducción al Desarrollo Front End con HTML, CSS y JavaScript</h2>
                </div>
            </div>
        </header>
        <main class="container">
            <div class="row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3 text-center" id="aqui"></div>
        </main>
        <footer class="container">
            <div class="row">
                <div class="col"><p class="text-muted mt-5 text-center small">Bootstrap v5.1 y datos en JavaScript</p></div>
            </div>
        </footer>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.min.js" integrity="sha512-N4kV7GkNv7QR7RX9YF/olywyIgIwNvfEe2nZtfyj73HdjCUkAfOBDbcuJ/cTaN04JKRnw1YG1wnUyNKMsNgg3g==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <script>
            var data, aves;

            function preload() {
                data = loadJSON("https://aves.ninjas.cl/api/birds");
            }

            function setup() {
                noCanvas();
                console.log(data);
                aves = Object.values(data);
                console.log(aves);
                aves.forEach((a) => {
                    if ((a.name.spanish.includes("Pato"))||(a.name.english.includes("duck"))) {
                        createElement("div", '<div class="card shadow-sm"><img class="card-img-top" src="' + a.images.thumb + '"><div class="card-body"><p class="card-text">' + a.name.spanish + "</p></div>").class("col").parent("aqui");
                    }
                });
            }
        </script>
    </body>
</html>
```

Revisando el [JSON de aves de Chile](https://aves.ninjas.cl/api/birds), podemos encontrar un vínculo a más detalles para cada ave, dentro de `_links.self`. Aprovechémonos de esto para crear una segunda página a la que corresponde llamar `single.html`. En tal página corresponde pegar lo siguiente:  

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />
        <title>Introducción al Desarrollo Front End con HTML, CSS y JavaScript</title>
    </head>
    <body>
        <header class="container">
            <div class="row">
                <div class="col">
                    <h1 class="text-center display-4 mt-5"></h1>
                    <h2 class="text-center fs-6 mb-5"><a href="index.html">&larr; Volver</a></h2>
                </div>
            </div>
        </header>
        <main class="container">
            <div class="row">
                <div class="col-11 col-sm-10 col-md-9 col-lg-8 col-xl-7 col-xxl-6 mx-auto" id="aqui">
                </div>
            </div>
        </main>
        <footer class="container">
            <div class="row">
                <div class="col"><p class="text-muted mt-5 text-center small">Bootstrap v5.1 y datos en JavaScript</p></div>
            </div>
        </footer>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.min.js" integrity="sha512-N4kV7GkNv7QR7RX9YF/olywyIgIwNvfEe2nZtfyj73HdjCUkAfOBDbcuJ/cTaN04JKRnw1YG1wnUyNKMsNgg3g==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <script>
            var url = new URLSearchParams(window.location.search).get('detalle');

            var data;

            function preload() {
                data = loadJSON(url);
            }

            function setup() {
                noCanvas();
                console.log(data);
                var titulo = select("h1")
                createElement('span', data.name.spanish).parent(titulo);
                createP(data.didyouknow).class("lead").parent("aqui");
                createP(data.habitat).parent("aqui");
            }
        </script>
    </body>
</html>
```

Para que funcione la consulta en esta página, necesitamos hacer un cambio en el script del `index.html`, agregar un "detalle".

Una vez funcione la relación entre los *scripts* en `index.html` y `single.html`, podemos hacer más cosas con Bootstrap.

Una vez nos conforme el resultado, podemos duplicar el `index.html`, cambiar su nombre por `page.html` y también cambiar los datos consultados: de criaturas voladoras a criaturas digitales: https://digimon-api.vercel.app/api/digimon

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_05) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_07)
