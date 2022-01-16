# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 16 de junio → sesion_13 → Evaluación de accesibilidad, rendimiento y SEO

- - - - - - -

#### Teoría

**Dos pruebas rápidas y extremas para revisar la accesibilidad en cualquier página web:**

1. Si se está visitando la página **con Chrome**, se puede buscar en el menú la opción Editar > Voz > Empezar a hablar.

2. Si se está visitando la página **con Firefox**, se puede buscar en el menú la opción Ver > Estilo de página > sin estilo.

Lo que se dicte o se vea sin estilo, aun **podría ser utilizado por usuarios específicos para alcanzar objetivos específicos con un mínimo de eficacia, eficiencia y satisfacción, en un contexto de uso específico**.

Para recordar: Accesibilidad implica acceso al uso. Usabilidad implica eficacia, eficiencia y satisfacción en el uso.

**Si se cuenta con más tiempo, conviene complementar las pruebas rápidas y extremas recién mencionadas con [WAVE: Web Accessibility Evaluation Tool](https://wave.webaim.org/)**.

Un problema común en la evaluación es la falta de contraste figura/fondo. Este se puede resolver revisando y ajustando los código de colores figura/fondo en https://webaim.org/resources/contrastchecker/

**Para hacer una auditoría que considere rendimiento, además de accesibilidad, buenas práctica de programación, SEO (Search Engine Optimization; posicionamiento en buscadores) y PWA (Progressive Web App), podemos usar [LightHouse](https://developers.google.com/web/tools/lighthouse?hl=es)**.

Lighthouse genera reportes en dos versiones: [resumida](https://github.com/profesorfaco/infografia/tree/main/clase-5/reportes) o extendida, en distintos formatos (hasta en [JSON](https://www.json.org/json-es.html)).

**Es probable que el reporte de LightHouse nos recuerde que**:

1. **estamos usando un CSS muy grande** – el [CSS compilado de Bootstrap](https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.css) ofrece mucho y podríamos estar usando muy poco. Como fue mencionado la [sesión 4](https://github.com/profesorfaco/front-end/tree/main/sesion_04), esto puede arreglarse con https://purifycss.online/

2. **algunas imágenes podrían pesar menos** – por las capacidades de almacenaje y transferencia actuales, podemos malacostumbrarnos a omitir el equilibrio entre peso y resolución… *¡Déjala así no más, total existe [WeTransfer](https://wetransfer.com/)!* Pero nadie esperará la aparición de una imagen en un sitio o aplicación web tal como se espera la descarga de lo compartido vía WeTransfer; para reencontrar el equilibrio, conviene: 
   
    - optimizar imágenes en [Photoshop](https://helpx.adobe.com/es/photoshop-elements/using/optimizing-images.html);
    - optimizarlas un poco más con [TinyPNG](https://tinypng.com/); e 
    - investigar sobre [WebP](https://developers.google.com/speed/webp)

3. **se podría mejorar el posicionamiento en buscadores** (SEO; Search Engine Optimization) – las máquinas necesitan datos o, mejor dicho, metadatos. Con ellos pueden catalogar cada página web. Para [cuidar los metadatos](https://developers.google.com/search/docs/advanced/crawling/special-tags?hl=es), es recomendable:

    - hacer una revisión con https://www.heymeta.com/
    - hacer una edición con https://megatags.co/

- - - - - - -

#### Exploración práctica

En esta clase continuaremos con el desarrollo de su sitio web o prototipo avanzado de aplicación web.

El cuarto paso consiste en poner a prueba lo avanzado, con las técnicas recién compartidas.

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_12) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_15)
