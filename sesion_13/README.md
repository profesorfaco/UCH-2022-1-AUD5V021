# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 16 de junio → sesion_13 → Trabajo final: Evaluación de Rendimiento, Accesibilidad y SEO

- - - - - - -

#### Teoría

**I. Dos pruebas rápidas y extremas para revisar la accesibilidad en cualquier página web:**

1. Si se está visitando la página con Chrome, se puede buscar en el menú la opción Editar > Voz > Empezar a hablar.

2. Si se está visitando la página con Firefox, se puede buscar en el menú la opción Ver > Estilo de página > sin estilo.

Lo que se dicte o se vea sin estilo, aun **podría ser utilizado por usuarios específicos para alcanzar objetivos específicos con un mínimo de eficacia, eficiencia y satisfacción, en un contexto de uso específico**.

Lo destacado en el párrafo anterior es una definición de usabilidad: 

> Usabilidad es el grado en que un sistema, producto o servicio puede ser utilizado por usuarios específicos para alcanzar objetivos específicos con eficacia, eficiencia y satisfacción en un contexto de uso específico ([ISO 9241-11:2018](https://www.iso.org/obp/ui/#iso:std:iso:9241:-11:ed-2:v1:en))

Accesibilidad implica acceso al uso. Usabilidad implica eficacia, eficiencia y satisfacción en el uso.

**II. Si se cuenta con más tiempo, podemos complementar las pruebas rápidas y extremas recién mencionadas. Podríamos usar [WAVE: Web Accessibility Evaluation Tool](https://wave.webaim.org/)**.

Un problema común en la evaluación es la falta de contraste figura/fondo. Este se puede resolver revisando y ajustando los código de colores figura/fondo en https://webaim.org/resources/contrastchecker/

**III. Para hacer una auditoría desde la perspectiva de la máquina**, que considere rendimiento, accesibilidad, buenas práctica de programación, SEO (Search Engine Optimization; posicionamiento en buscadores) y PWA (Progressive Web App), **podemos usar [LightHouse](https://developers.google.com/web/tools/lighthouse?hl=es)**.

Lighthouse genera reportes en dos versiones: [resumida](https://github.com/profesorfaco/infografia/tree/main/clase-5/reportes) o extendida, en distintos formatos (hasta en [JSON](https://www.json.org/json-es.html)).

Es probable que el reporte de LightHouse dé indicaciones respecto del CCS, porque estamos aprovechando unas pocas líneas entre las muchísimas que ofrece Bootstrap. Consideren que Bootstrap ofrece [un estilo CSS muy grande](https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.css), de 11.266 líneas, que el navegador revisa completo antes de mostrar la página; y siempre conviene limitar las lecturas del navegador a lo estrictamente necesario. 

Para reducir el CSS a lo que realmente es aplicado, puede aprovecharse https://purifycss.online/ o algún otro truco explicado en https://css-tricks.com/how-do-you-remove-unused-css-from-a-site/

También es probable que el reporte de LightHouse dé indicaciones respecto del SEO, porque las máquinas necesitan datos o, mejor dicho, metadatos. Con ellos pueden catalogar cada página web. Para cuidar los metadatos, es recomendable:

1. Hacer una revisión con https://www.heymeta.com/

2. Hacer una edición con https://megatags.co/ 

Al cuidar los [metadatos, cuidamos el posicionamiento en buscadores (SEO)](https://developers.google.com/search/docs/advanced/crawling/special-tags?hl=es)

- - - - - - -

#### Exploración práctica

Ponga a prueba lo avanzado con las técnicas recién compartidas.

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_12) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_15)
