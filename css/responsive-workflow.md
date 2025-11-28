# Flujo de trabajo recomendado cuando se tiene el diseño responsive en mente.

## 1. Reset y estilos globales

Antes de definir cualquier layout, es bueno establecer la base del proyecto:

* **Reset o Normalize**: Aplicar un "reset" de CSS (como Eric Meyer's Reset o Normalize.css) para que todos los navegadores partan del mismo punto y eliminen los márgenes y padding por defecto que causan problemas.
* **Definición Tipográfica Base**: Establecer la fuente base (font-family) y el tamaño de fuente global (idealmente en rem) en el selector html o body.
* **Box Sizing**: Crucial para Grid y Flexbox. Establece ```css box-sizing: border-box;``` globalmente. Esto asegura que el padding y los bordes se incluyan dentro del ancho y alto del elemento, no fuera, facilitando enormemente el cálculo de tamaños.

  ```css
  *, *::before, *::after {
    box-sizing: border-box; /* ¡La regla de oro del Layout! */
  }
  ```

## 2. Estructura y Layout Móvil (Mobile First)

Este es el paso fundamental de la metodología Móvil Primero. Diseñas y codificas el layout para la pantalla más pequeña primero.

* **HTML Estructural**: Define la estructura semántica básica (<header>, <main>, <footer>, etc.).
* **Grid para Móvil**: Aplica ```css display: grid;``` al contenedor principal (el ```body``` o el ```.page-container```) y define una estructura de una sola columna (```grid-template-columns: 1fr;```).
* **Dimensiones del Contenedor**: En esta etapa, el ancho es 100% por defecto. No defines el ```max-width``` todavía, ya que en móviles queremos que el contenido ocupe todo el ancho disponible.

## 3. Ancho Máximo y Centrado (El contenedor)

Aquí introduces la restricción que mencionaste, pero solo para limitar el crecimiento en pantallas grandes.

* Definición de ```max-width```: Aplica el ```max-width``` y el ```margin: 0 auto;``` al contenedor principal (ej. ```.page-container```). Esto afecta solo a los dispositivos grandes que superen ese límite, dejando a los móviles sin cambios.
  
  ```css
  .page-container {
      max-width: 1440px; 
      margin: 0 auto; 
      /* Agrega un poco de padding horizontal para evitar que el contenido toque los bordes en móviles */
      padding: 0 1rem; 
  }
  ```

## 4. Defición de Puntos de Ruptura (Media Queries)

Una vez que el layout móvil está funcional y el contenedor principal está definido, usas Media Queries para reintroducir las columnas y la complejidad del diseño de escritorio.

* **Estrategia de Puntos de Ruptura**: Elige tus puntos de corte (ej: ```768px``` para Tablet, ```1024px``` para Desktop).
* **Redefinición del Grid**: Dentro de cada ```min-width``` Media Query, redefines la plantilla de la rejilla (```grid-template-columns```, ```grid-template-areas```) para crear el layout de múltiples columnas que planeaste en tu wireframe.

  ```css
    @media (min-width: 768px) {
      .page-container {
            /* Redefinimos el grid para crear 2 columnas (Sidebar + Main) */
            grid-template-columns: 250px 1fr;
        }
    }
  ```

## Ejemplo

**HTML Base**

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grid Layout Responsivo</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="page-container">
        <header class="header">HEADER | Logo y Navegación</header>
        <main class="main">CONTENIDO PRINCIPAL | Artículos y Publicaciones</main>
        <aside class="sidebar">BARRA LATERAL | Publicidad y Links</aside>
        <footer class="footer">FOOTER | Derechos de Autor</footer>
    </div>
</body>
</html>
```

**CSS - Estilos Base (Mobile First)**

```css
/* PASO 1: Reset y Box Sizing */
*, *::before, *::after {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: sans-serif;
    min-height: 100vh; /* Para que el footer se quede abajo */
}

/* PASO 2 & 3: Layout Móvil y Ancho Máximo */
.page-container {
    display: grid;
    
    /* Mobile First: Todo en una sola columna vertical. */
    grid-template-columns: 1fr; 
    
    /* Definimos el orden vertical para móvil */
    grid-template-areas:
        "header"
        "main"
        "sidebar"
        "footer";
        
    /* Limita el ancho para pantallas gigantes y lo centra */
    max-width: 1200px;
    margin: 0 auto; 
    
    /* Padding para que el contenido no pegue a los bordes de la pantalla en móvil */
    padding: 0 1rem;
    gap: 1.5rem; /* Espacio entre filas y columnas */
}

/* Asignamos los elementos a las áreas definidas */
.header { grid-area: header; background: #333; color: white; padding: 1rem; }
.main { grid-area: main; background: #f0f0f0; padding: 1rem; }
.sidebar { grid-area: sidebar; background: #ccc; padding: 1rem; }
.footer { grid-area: footer; background: #333; color: white; padding: 1rem; }

/* En móvil, la barra lateral aparece debajo del contenido principal. */

/* PASO 4: Media Query para redefinir la estructura */
@media (min-width: 768px) {
    
    .page-container {
        /* Redefinimos el Grid para tener 3 filas */
        /* La 2da fila (contenido) es la que tendrá las columnas Sidebar y Main */
        grid-template-rows: auto 1fr auto; 
        
        /* Definimos 2 columnas: una para Sidebar (300px fijo) y una para Main (el resto) */
        grid-template-columns: 300px 1fr; 
        
        /* Redefinimos el flujo y la posición de los elementos */
        grid-template-areas:
            "header header"    /* Header ocupa las 2 columnas */
            "sidebar main"     /* Sidebar a la izquierda, Main a la derecha */
            "footer footer";   /* Footer ocupa las 2 columnas */
    }
}
```














  
