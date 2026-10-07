# GrabAll Lite

Extensión de Chrome (Manifest V3) para detectar y descargar de forma masiva las
imágenes cargadas en una página, incluidas las generadas tras iniciar la captura
y las presentes en iframes anidados de otros orígenes.

## Cargar en Chrome

1. Abre `chrome://extensions`.
2. Activa **Modo de desarrollador**.
3. Pulsa **Load unpacked** y selecciona esta carpeta.

## Características

- Captura activa/inactiva por pestaña.
- Detección de imágenes en el documento principal y en iframes, incluso
  cross-origin.
- Filtro por tamaño mínimo y detección opcional de `background-image`.
- Descarga individual, seleccionada o de toda la lista.
- Exportación ZIP de imágenes seleccionadas o de toda la lista.
- Historial local de descargas.
- Config por sitio (carpeta y patrón de nombre).
- Selección por intervalo (dos anclas + botón Intervalo).
- Atajo `Alt+G` para alternar captura.

## Estructura

```
manifest.json
icons/
src/
  background/service-worker.js   # SW minificado; fflate va en un chunk separado
  content/detector.js            # content script bundled (IIFE)
  popup/                         # UI del popup
  options/                       # página de configuración
  lib/vendor/ (queda en fflate chunk)
```

## Privacidad

No hay backend: los datos se guardan con `chrome.storage` y las imágenes se
procesan localmente. Solo usa permisos `downloads` y `storage`.
