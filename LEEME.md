# Modulus

Presentación web en español, sin instalación ni dependencias externas. Todo el diseño y la lógica están en index.html. Incluye marcadores de foto ilustrados, no personas reales. Los nombres y mensajes son ejemplos editables.

## Mascota y paleta morada

La portada incluye un espacio para la mascota junto al título (debajo en móvil). Guarda tu imagen como assets/mascota.png y cambia en CONFIG:

```js
mascot: { src: 'assets/mascota.png', alt: 'Mascota de Modulus' },
```

PNG o WebP transparente permite conservar la silueta. Se muestra completa sin recortarla. Si la ruta falla, vuelve el marcador de posición. La paleta usa fondo berenjena, aurora violeta y acentos lavanda; puedes cambiar las variables de :root.

## Personalizar

1. Abre index.html en un editor y busca `const CONFIG`.
2. Sustituye cada `name` y `message`.
3. Coloca las fotos en assets/ y cambia `photo:''` por `photo:'assets/presidente.jpg'`, etc. Usa imágenes verticales (idealmente 1200 × 1600). `object-fit:cover` recorta para llenar; puedes ajustar `object-position` en `.photo img`.
4. Fondo GIF: `background: { type:'image', src:'assets/fondo.gif' }`.
5. Fondo de video, recomendado por calidad/tamaño: `background: { type:'video', src:'assets/fondo.mp4' }`. Sin audio; MP4 H.264 o WebM. Usa un bucle 1080p comprimido. Para imagen fija, type:'image'. El fondo degradado animado funciona sin archivos.
6. Prueba nombres largos en móvil. Los cargos están en vertical con letras derechas; las fotos alternan izquierda/derecha y los cargos quedan hacia el centro.

## Usar y publicar en tu servidor

Sube index.html y la carpeta assets/ juntos a la misma carpeta pública del servidor (por ejemplo /modulus/). Abre https://tu-dominio/modulus/. No requiere Node, base de datos ni ejecutables. Nombres de archivo distinguen mayúsculas/minúsculas en muchos servidores. No incluyas fotos que no quieras hacer públicas.

Flechas, Page Up/Down y espacio cambian de sección. Los botones inferiores también. ⛶ activa pantalla completa; F11 es la alternativa. El botón de pausa detiene el fondo generado/video; para un GIF con extensión .gif, lo oculta porque el navegador no permite pausarlo directamente. Se respeta la preferencia de movimiento reducido.

## Swarm Rebuild integrado

El motor REAL del swarm.js adjuntado está incluido directamente dentro de index.html. No necesitas instalar una extensión ni agregar otra etiqueta script. assets/swarm-web.js es una copia de referencia; el HTML no la carga para evitar ejecutarlo dos veces. Si modificas esa copia, también debes actualizar el bloque del motor dentro del HTML.

Al abrir la página espera a las imágenes (máximo 6 segundos) y fuentes, e inicia la reconstrucción automáticamente. Si tu sistema prefiere movimiento reducido, pulsa Swarm: off para iniciarlo manualmente. Swarm: on/off activa o desactiva el motor real y Esc sale del efecto. Los controles de navegación y pantalla completa siguen disponibles durante el efecto. El sonido puede requerir un clic por las políticas del navegador.

Sube index.html y assets/ juntos a tu servidor. El motor está embebido; fotos, mascota y fondos siguen usando sus rutas configuradas. No hay dependencias de CDN ni APIs de la extensión.

La captura opcional de la extensión no se usa: fotos y SVG se reconstruyen desde el DOM. Videos, canvas e iframes pueden diferir o aparecer como marcadores según el recurso; fondos CSS animados no garantizan una reproducción idéntica en la capa de reconstrucción.

Origen: https://github.com/DhvanilPatel/swarm-cursors — créditos originales conservados: DhvanilPatel y Joel Califa. El repositorio indica que no tiene licencia y pide consultar a los autores antes de reutilizar públicamente su código.

Validación de esta entrega: sintaxis JavaScript y estructura del paquete comprobadas. No se ha validado visualmente el motor en un navegador ni en tu servidor. Si tu servidor restringe scripts inline mediante Content-Security-Policy, debe permitir estos bloques mediante hashes/nonces o externalizarlos.

## Corrección de visibilidad del swarm

Se corrigió el orden de las capas fijas: el fondo y el velo con z-index negativo ahora se reconstruyen detrás del contenido, mientras la cabecera y los controles permanecen delante. La corrección está en index.html y assets/swarm-web.js.

Este paquete no contiene fotos ni una imagen de mascota; conserva los marcadores originales. Añade tus archivos y configura sus rutas en CONFIG.

La corrección se verificó con comprobaciones de sintaxis y de asignación de capas. No fue posible hacer una prueba visual porque este entorno no dispone de un navegador instalado.

## Controles durante swarm

Las flechas de sección, pantalla completa y la cabecera siguen siendo los controles reales y se muestran por encima de la reconstrucción. También funcionan las teclas de navegación. Se eliminó visualmente la barra del motor; el botón pequeño «Swarm: on/off» activa o desactiva el efecto y Esc lo desactiva. El botón informa su estado mediante aria-pressed. La página estática ya no se recorre automáticamente al activar el efecto.

Validación de controles: navegación arriba/abajo, teclado con swarm activo, llamada de pantalla completa, alternancia de estado y sincronización al salir comprobadas con un DOM simulado. No se hizo validación visual en navegador.
