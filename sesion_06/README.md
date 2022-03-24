# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 21 de abril → sesion_06 →  Bootstrap v5.1 y datos en JavaScript

- - - - - - - - 

#### Teoría

Esta clase abrirá un paréntesis, para revisar un aspecto pendiente en JavaScript, que debe clarificarse antes de la siguiente clase.

Para comenzar, partamos con el número 18261884. 

Si nos entregan tal número, sin contexto alguno, resultaría inútil. Pero es distinto de la siguiente manera: 

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

Para cerrar: Las variables `f` y `g` contienen un objeto. Las variables `h` es un arreglo con tres objetos. Luego, las variables `f`, `g` y `h`, con sus particularidades, aprovechan la Notación de Objetos de JavaScript, lo que en inglés es **J**ava**S**cript **O**bject **N**otation ([JSON](https://www.json.org/json-es.html)).

En lo recién dicho aparecen las iniciales con las que se denomina a un formato ligero de intercambio de datos: 

> JSON (JavaScript Object Notation - Notación de Objetos de JavaScript) es un formato ligero de intercambio de datos. Leerlo y escribirlo es simple para humanos, mientras que para las máquinas es simple interpretarlo y generarlo.

Dos ejemplos de JSON:

- https://hp-api.herokuapp.com/api/characters/staff
- https://digimon-api.vercel.app/api/digimon

¿Qué ofrece cada ejemplo? Eso lo pueden responder después de leer cada JSON. Para hacerlo conviene contar con una extensión que permita visualizar JSON de manera más ordenada en su navegador web. Para Chrome: [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/mhimpmpmffogbmmkmajibklelopddmjf?hl=es) o [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=es). Para Firefox: [JSON Lite](https://addons.mozilla.org/es/firefox/addon/json-lite/) o [Basic JSON Formatter](https://addons.mozilla.org/es/firefox/addon/basic-json-formatter/).

Y para obtener los datos de un JSON en línea, también podemos contar con la ayuda de p5.js, como se puede revisar en los siguientes ejemplos del editor:

- https://editor.p5js.org/profesorfaco/sketches/7FrCDZKc1
- https://editor.p5js.org/profesorfaco/sketches/dbC5hqQya

La consulta de los datos contenidos en un JSON dependerá de su estructura, así como dependía la consulta por los nombres de los personajes en las variables `f`, `g` y `h`.

No conviene quedarnos con la idea de que siempre necesitaremos de p5.js para obtener los datos de un JSON en línea. También podemos tomar un JSON con el [uso de Fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch). La API Fetch es parte del lenguaje de programación original, por lo que podemos usarla sin vincular una biblioteca.

Para comprender el uso de fetch conviene revisar un par de videos publicados por Daniel Shiffman:

- https://youtu.be/tc8DU14qX6I
- https://youtu.be/uxf0--uiX0I


- - - - - - - - - - -

#### Exploración práctica

Corresponde tener a mano:

- una descripción del método [forEach()](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach); y

- la propiedad [innerHTML](https://developer.mozilla.org/es/docs/Web/API/Element/innerHTML).

Partiremos con el siguiente código, que corresponde copiar y pegar en un documento recién creado en su editor de código fuente. Documento que tienen que guardar como index.html:

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
                <div class="col"><h1 class="text-center py-5 display-3">DIGIMON</h1></div>
            </div>
        </header>
        <main class="container">
            <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 g-3 text-center" id="aqui"></div>
        </main>
        <footer class="container">
            <div class="row">
                <div class="col"><p class="text-muted py-2 text-center small">Bootstrap v5.1 y datos en JavaScript</p></div>
            </div>
        </footer>
        <script>
            async function visualizacion() {
                const consulta = await fetch("https://digimon-api.vercel.app/api/digimon");
                const data = await consulta.json();
                data.forEach((d) => {
                    if (d.level == "In Training") {
                        document.getElementById("aqui").innerHTML += '<div><div class="card shadow-sm"><img class="card-img-top" src="' + d.img + '"><div class="card-body"><p class="card-text">' + d.name + "</p></div></div>";
                    }
                });
            }
            visualizacion();
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_05) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_07)
