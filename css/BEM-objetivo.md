# BEM: Block - Element - Modifier

Bueno, la idea con BEM es dividir la interfaz en bloques independientes para que sea más fácil desarrollar, mover cosas y reutilizar código sin copiar y pegar.
La idea es no craer estructuras que no sean muy parecidas para evitar craer bloques repetidos.

## Ejemplo

Sin BEM podríamos hacer algo tipo:

**HTML**

```html

<!-- Home -->
<section class="home-articles">
  <article class="home-article-card">
    <h2 class="home-article-title">Título 1</h2>
    <p class="home-article-excerpt">Resumen…</p>
  </article>
</section>

<!-- Sidebar -->
<aside class="sidebar">
  <article class="sidebar-article-card">
    <h3 class="sidebar-article-title">Título 2</h3>
    <p class="sidebar-article-excerpt">Resumen…</p>
  </article>
</aside>

```

**CSS**

```css

.home-article-card {
  background: white;
  padding: 1rem;
  border-radius: 0.5rem;
}

.home-article-title {
  font-size: 1.2rem;
}

.home-article-excerpt {
  font-size: 0.9rem;
}

/* Y ahora en la sidebar copias casi lo mismo… */

.sidebar-article-card {
  background: white;
  padding: 1rem;
  border-radius: 0.5rem;
}

.sidebar-article-title {
  font-size: 1.2rem;
}

.sidebar-article-excerpt {
  font-size: 0.9rem;
}

```

Como vemos, la estructura del artículo del home y del artículo del sidebar es muy parecida y lo que podemos hacer es crear algo un poco más genérico que se pueda utilizar en ambos casos.

**HTML**

```html
<!-- Home -->
<section class="home">
  <div class="home__list">
    <article class="post-card">
      <h2 class="post-card__title">Título 1</h2>
      <p class="post-card__excerpt">Resumen…</p>
    </article>
  </div>
</section>

<!-- Sidebar -->
<aside class="sidebar">
  <div class="sidebar__list">
    <article class="post-card">
      <h3 class="post-card__title">Título 2</h3>
      <p class="post-card__excerpt">Resumen…</p>
    </article>
  </div>
</aside>

```

**CSS**

```css

.post-card {
  background: white;
  padding: 1rem;
  border-radius: 0.5rem;
}

.post-card__title {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

.post-card__excerpt {
  font-size: 0.9rem;
  line-height: 1.5;
}

.home__list .post-card {
  margin-bottom: 1.5rem;
}

.sidebar__list .post-card {
  margin-bottom: 0.75rem;
}

```










