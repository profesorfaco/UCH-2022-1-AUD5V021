# Introducción al Desarrollo Front End con HTML, CSS y JavaScript

### Jueves 14 de abril → sesion_05 → Bootstrap v5 y JavaScript 

- - - - - - - - 

#### Teoría

Además de ofrecer un estilo de CSS compilado (basado en [Sass](https://sass-lang.com/)), Bootstrap tiene una biblioteca de JavaScript que permite el funcionamiento de varios de sus componentes, que requieren también [Popper](https://popper.js.org/):

- [Accordion](https://getbootstrap.com/docs/5.1/components/accordion/)
- [Carousel](https://getbootstrap.com/docs/5.1/components/carousel/)
- [Collapse](https://getbootstrap.com/docs/5.1/components/collapse/)
- [Dropdowns](https://getbootstrap.com/docs/5.1/components/dropdowns/)
- [Modal](https://getbootstrap.com/docs/5.1/components/modal/)
- [Offcanvas](https://getbootstrap.com/docs/5.1/components/offcanvas/)
- [Popovers](https://getbootstrap.com/docs/5.1/components/popovers/)
- [Toltips](https://getbootstrap.com/docs/5.1/components/tooltips/)

Si se opta por ir por los scripts de Bootstrap.js y Popper.js separados, Popper debe venir primero (si usted está usando tooltips o popovers), y luego vendría el de Boostrap:

```
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.10.2/dist/umd/popper.min.js" integrity="sha384-7+zCNj/IqJ95wo16oMtfsKbZ9ccEh31eOz1HGyDuCQ6wgnyJNSYdrPa03rtR1zdB" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js" integrity="sha384-QJHtvGhmr9XOIpI6YVutG+2QOK9T+ZnN4kzFN1RtK3zEFEIsxhlmWl5/YESvpZ13" crossorigin="anonymous"></script>
```

También está la opción de ir por ambos de una vez, con la opción *Bundle*:

```
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
```

Habiendo una tercera opción, donde se van a buscar por módulos precisos, que supera un poco el alcance de una introducción.

- - - - - - - - - -

#### Exploración práctica

Pendiente

- - - - - - - 

###### [← SESIÓN ANTERIOR](https://github.com/profesorfaco/front-end/tree/main/sesion_04) — [SIGUIENTE SESIÓN →](https://github.com/profesorfaco/front-end/tree/main/sesion_06)
