# Página de propuestas de Modulus

Abre `propuestas.html`. Es independiente del index existente, que no se modificó. Incluye el motor swarm dentro del HTML y no usa dependencias externas.

## Foto de la Junta Directiva

Coloca nueve recortes PNG transparentes en `assets/`, con estos nombres:

- junta-01.png
- junta-02.png
- junta-03.png
- junta-04.png
- junta-05.png
- junta-06.png
- junta-07.png
- junta-08.png
- junta-09.png

Los números siguen el orden de izquierda a derecha. El centro queda delante y las imágenes se superponen. Para un resultado uniforme, recorta el espacio transparente sobrante y usa encuadres y alturas similares. WebP transparente también funciona cambiando las rutas en `const PAGE` al final de propuestas.html. Allí puedes escribir el nombre real de cada integrante en `alt` y ajustar `position`. Las listas `heights` y `layers` controlan las alturas y el orden de superposición.

Hasta que se agreguen las fotos se muestran siluetas gráficas numeradas, no fotografías de personas reales. En móvil se conserva la fila grupal y se puede deslizar horizontalmente.

## Códigos QR

Coloca dos códigos QR reales en `assets/qr-01.png` y `assets/qr-02.png`. Cambia `label` y `alt` en `PAGE.qr` por el destino de cada QR. Las dos imágenes se mantienen lado a lado también en móvil. Los espacios actuales son marcadores, no códigos escaneables. Se conserva margen blanco alrededor de cada imagen; no recortes la zona de silencio del código original.

## Publicar

Sube propuestas.html y assets/ juntos. La nueva página estará en la misma carpeta que index.html, con la ruta /propuestas.html. El ZIP conserva index.html y el motor de swarm anterior sin cambios.

Comprobaciones: sintaxis JavaScript, seis propuestas, nueve posiciones de fotos, dos posiciones QR, eventos de carga de imagen y conservación exacta del index. No se hizo una prueba visual en navegador en este entorno.

## Swarm integrado

El efecto se inicia después de cargar imágenes y fuentes, excepto con movimiento reducido. El botón pequeño «Swarm: on/off» lo activa y desactiva; Esc también permite salir. La cabecera permanece visible y todos los enlaces y el botón están por encima de la reconstrucción. La barra inferior del motor está oculta. El archivo assets/swarm-web.js es de referencia y no se ejecuta de nuevo.

Se conservaron las fotos y los QR configurables, así como el index anterior sin cambios. La sintaxis y los eventos de activación/desactivación se verificaron mediante simulación; no se pudo hacer validación visual en navegador.

Las flechas fijas de la esquina inferior izquierda permiten avanzar y retroceder entre las cinco secciones. Permanecen por encima del swarm y respetan la preferencia de movimiento reducido.

El botón ⛶ junto a las flechas activa y desactiva pantalla completa. Su estado también se actualiza al salir con Esc. Si el navegador no admite la función, se indica la alternativa F11.
