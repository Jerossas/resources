# BEM Naming Conventions

Ya sabemos que BEM significa Block-Element-Modifier.

## Bloque

Un bloque es un componente independiente que se puede reutilizar. El nombre del bloque debe describir lo qué es, más no cómo se ve. Algunos ejemplos son:

* header
* menu
* button
* search-form

### Reglas

* El bloque no debe definir su posición externa. Su posición externa la debe manejar su contenedor.

**Ejemplo**

```css

/* El bloque solo define su interior */
.card {
  background: white;
  padding: 1rem;
  border-radius: 0.5rem;
}

/* Aquí, el contenedor decide los márgenes/layout */
.blog__list .card {
  margin-bottom: 2rem;
}

.sidebar__item .card {
  margin-bottom: 0.5rem;
}

```

## Elemento

Ahora, un elemento es una parte interna del bloque. La característica principal es que los elementos no tienen un sentido por si solos, es decir que necesitan el contexto del bloque para que tengan un sentido.
El elemento responde a la pregunta ¿Qué es esto dentro del bloque? (item, title, input, button)

Se escibre de la siguiente forma: primero va el nombre del bloque, luego doble guión bajo y por último el nombre del elemento. Ejemplo: block-name__element-name

## Modificador

El modificador cambia la apariencia, estado o comportamiento, ya sea del bloque o del elemento. 

Para escribirlo se puede utilizar un solo guión bajo o un doble guión medio.

**Ejemplos**

* block-name__element-name_modifier_name
* block-name__element-name--modifier-name


