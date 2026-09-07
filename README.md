# Índice ERU — San Isidro Club

Dashboard que lee `SIC_Carga.xlsx` directamente desde este repositorio
cada vez que se abre. No hace falta reconstruir nada: cuando reemplaces
el Excel por una versión nueva (mismo nombre de archivo, misma hoja
"GPS", mismas columnas), el sitio va a reflejar los datos actualizados
en la próxima carga de la página.

## Subir los archivos (primera vez)

1. Entrá a tu repo: https://github.com/AlePastorPF/Indice-Esfuerzo-RU
2. Botón **Add file → Upload files**.
3. Arrastrá `index.html` y `SIC_Carga.xlsx` (los dos, sueltos en la
   raíz del repo — no en una subcarpeta).
4. Commit.

## Activar GitHub Pages

1. En el repo: **Settings → Pages**.
2. En "Build and deployment" → Source: **Deploy from a branch**.
3. Branch: **main** (o la que uses), carpeta **/ (root)**.
4. Guardar. GitHub te va a dar una URL del estilo:
   `https://alepastorpf.github.io/Indice-Esfuerzo-RU/`
   (puede tardar 1–2 minutos en estar disponible la primera vez).

## Actualizar los datos más adelante

1. Entrá al repo → click en `SIC_Carga.xlsx` → ícono de lápiz
   (o simplemente "Add file → Upload files" de nuevo, arrastrando el
   Excel nuevo con el mismo nombre para que lo sobrescriba).
2. Commit.
3. Recargá la página del dashboard (puede tardar uno o dos minutos en
   propagarse el cambio en GitHub Pages). El sitio va a recalcular
   todo — Índice ERU, tarjetas, tabla, gráfico y filtros — con los
   datos nuevos, sin que yo tenga que tocar nada.

## Importante — el repo es público

Como el repositorio es público, el archivo `SIC_Carga.xlsx` (y por lo
tanto los datos de los jugadores) va a ser descargable por cualquiera
que tenga el link, aunque no sea evidente a simple vista. Si en algún
momento preferís que los datos no sean accesibles públicamente,
avisame y armamos la variante con GitHub Actions (recalcula todo del
lado del servidor y solo publica el resultado ya procesado) o
recomendamos pasar el repo a privado con un plan de GitHub que
soporte Pages privado.

## Qué cambia respecto a la versión anterior

- El archivo ya no lleva los datos "horneados" adentro — los lee del
  Excel en el momento de abrir la página, usando la librería SheetJS
  (incluida en el propio `index.html`, no depende de internet salvo
  para bajar el Excel del repo).
- Toda la lógica (ponderaciones por puesto, normalización por
  temporada, detección de rivales, filtros cruzados, etc.) es la
  misma que ya validamos juntos — solo cambió dónde se ejecuta: antes
  se calculaba una vez al generar el archivo, ahora se calcula en el
  navegador cada vez que se abre la página.
- Si la hoja `GPS` cambia de nombre, o alguna de las columnas usadas
  (Jugador, Periodo, Actividad, Puesto, Dist Exp, RHIE Total Bouts,
  # BiG, Contactos, Duracion (min), Etiqueta de Actividad, Temporada)
  cambia de posición, el dashboard va a mostrar un mensaje de error
  claro en lugar de romperse en silencio.
