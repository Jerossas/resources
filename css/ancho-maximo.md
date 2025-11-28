# Definir un Ancho Máximo

Según Gemini, a esta técnica se le conoce como "**Contenedor Centralizado**" o "**Límite de Ancho de Contenido**".

## Ejemplo

**HTML**

```html

<body>
    <div class="page-container"> <header></header>
        <main></main>
        <footer></footer>
    </div>
</body>

```

**CSS**

```css

.page-container {
    /* 1. Define el ancho máximo deseado */
    max-width: 1440px; 
    
    /* 2. Centra el contenedor horizontalmente */
    /* El "auto" en margin: 0 auto; distribuye el espacio sobrante por igual en ambos lados. */
    margin: 0 auto; 
    
    /* 3. Activa y define el Grid Layout dentro de este contenedor */
    display: grid;
    grid-template-columns: 1fr; /* O la estructura que necesites */
    /* ... otras reglas de Grid ... */
}

```

La idea es que si el display del dispositivo que esta mostrando la información es muy grande, CSS  limite el ancho del contenido para mejorar la atención y comodidad del usuario al ver la información.  
