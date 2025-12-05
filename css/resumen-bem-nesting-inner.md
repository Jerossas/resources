# Resumen de BEM: Nesting y `something__inner`

## 1. Nesting (anidación) en BEM

En BEM hay que distinguir dos cosas:

1. **Anidación en el HTML (DOM)**  
   Puedes tener elementos dentro de otros elementos:

   ```html
   <nav class="menu">
     <ul class="menu__list">
       <li class="menu__item">
         <a class="menu__link">
           <span class="menu__icon"></span>
         </a>
       </li>
     </ul>
   </nav>
   ```

   Aquí sí hay padres, hijos, nietos, etc.

2. **Nombres BEM (pertenencia al bloque)**  
   Todos los elementos pertenecen directamente al bloque y se nombran así:

   - `menu__list`
   - `menu__item`
   - `menu__link`
   - `menu__icon`

   y **no** así:

   - `menu__item__link`
   - `menu__link__icon`

👉 En resumen:

- En el **HTML**: los elementos pueden estar metidos unos dentro de otros sin problema.  
- En los **nombres BEM**: todos los elementos “se apellidan” con el bloque:  
  `block__element`, nunca `block__element__otro`.


## 2. Elementos que contienen otros elementos

Los elementos que contienen otros elementos:

- **No son bloques padres nuevos**.
- Son **partes internas del bloque** que sirven para:
  - agrupar contenido,
  - organizar la estructura,
  - aplicar layout interno (flex, grid, etc.).

Ejemplo:

```html
<article class="card">
  <header class="card__header">
    <h2 class="card__title">Título</h2>
  </header>

  <div class="card__body">
    <p class="card__text">Contenido…</p>
  </div>
</article>
```

Aquí:

- `card` → bloque  
- `card__header`, `card__body` → elementos contenedores  
- `card__title`, `card__text` → otros elementos del **mismo** bloque

A nivel BEM, todos son hijos del bloque `card`, aunque en el HTML estén unos dentro de otros.


## 3. ¿Qué es `something__inner`?

`something__inner` **no es algo especial del método BEM**, es solo un nombre de elemento muy común.

Se usa cuando quieres marcar la “cajita interna” de un bloque, donde organizas su contenido.

Ejemplo típico:

```html
<header class="header">
  <div class="header__inner">
    <a href="/" class="header__logo">Mi sitio</a>
    <nav class="header__nav">...</nav>
  </div>
</header>
```

- `header` → bloque (la franja completa)  
- `header__inner` → elemento que:
  - centra el contenido,
  - define `max-width`,
  - aplica `display: flex`, `padding`, etc.  
- `header__logo`, `header__nav` → otros elementos del bloque

Podrías usar otros nombres equivalentes:

- `header__content`
- `header__wrapper`
- `header__container`

La idea es la misma: un elemento que envuelve el contenido interno del bloque para organizarlo mejor.
