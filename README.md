# Proyecto VD | Svelte Scroller Template

## Descripción del Proyecto
Nuestro proyecto consiste en una página web interactiva que cuenta la evolución de Apple, desde el inicio hasta la actualidad, a través de una línea de tiempo y secciones con información detallada de eventos significativos. Utilizamos Svelte para la construcción de componentes dinámicos y Svelte Scroller para manejar la navegación fluida entre secciones.

## Estructura del Proyecto

### Componentes Importados
- **Scroller**: Componente de Svelte Scroller que permite crear una experiencia de desplazamiento fluido.
- **Quiz**: Componente del cuestionario incluido en la sección de encabezado.

### Variables Principales
- **count, index, offset, progress**: Variables vinculadas al scroller.
- **top, threshold, bottom**: Parámetros de configuración del scroller.
- **years**: Array con los años importantes en la historia de Apple.
- **iframes**: URLs de los gráficos hechos con DataWrapper que se muestran en cada sección.
- **icons**: Iconos asociados a ciertos años.
- **uniqueYears**: Array con los años únicos extraídos de years.
- **showTimeline**: Booleano para mostrar u ocultar la línea de tiempo.

### Funciones Principales
- **handleScroll**: Maneja la visibilidad de la línea de tiempo en función del desplazamiento de la página.
- **onMount**: Agrega un evento de escucha para manejar el desplazamiento cuando el componente se monta.

## Estructura del HTML
- **Encabezado (header)**: Contiene el logo, el título, subtítulos, y secciones históricas con texto desde 1976 (creación) hasta 1985. Incluye un componente Quiz al final del encabezado.
- **Línea de Tiempo (timeline)**: Muestra los años de forma fija a la izquierda de la página durante las secciones.
- **Pie de Página (footer)**: Contiene información actual de Apple y una imagen con la evolución de los logos, además de información personal de contacto.

## Estilos
- Utilizamos la fuente Roboto para los textos, similar a la fuente de Apple.
- Encuadramos la información descriptiva de los años en marcos blancos.
- Resaltamos con colores en los gráficos para indicar la posición actual.
