# screenshot-to-calendar

**AI Edge Gallery Skill** — Crea eventos en tu calendario de Google a partir de un screenshot o texto, usando Gemma 4.

## Cómo funciona

1. Compartes una imagen (screenshot de invitación, flyer, etc.) o describes un evento en texto
2. Gemma 4 extrae automáticamente: título, fecha, hora, lugar, y descripción
3. Aparece una tarjeta con el resumen del evento y dos botones:
   - **📅 Agregar a Google Calendar** → abre Google Calendar pre-rellenado en tu calendario "familia"
   - **🍎 Descargar .ics** → genera un archivo para importar en Apple Calendar (iCloud)

## Estructura

```
screenshot-to-calendar/
├── SKILL.md              ← Instrucciones para Gemma 4
├── scripts/
│   └── index.html        ← Lógica JS: construye URL de Google Calendar + ICS
└── assets/
    └── webview.html      ← UI: tarjeta del evento + botones
```

## Instalación en AI Edge Gallery

### Opción 1: Importar desde el celular (iOS/Android)

1. Copia esta carpeta a tu celular:
   - **iOS**: Usa la app Archivos para copiar la carpeta `screenshot-to-calendar/`
   - **Android**: `adb push screenshot-to-calendar/ /sdcard/Download/`

2. En AI Edge Gallery: Agent Skills → toca el chip **"Skills"** → botón **(+)** → **"Import local skill"**

3. Selecciona la carpeta `screenshot-to-calendar/`

### Opción 2: Cargar desde URL (GitHub Pages)

1. Sube este repositorio a GitHub y activa GitHub Pages
2. Crea un archivo `.nojekyll` en la raíz del repo (para que sirva el SKILL.md sin renderizar)
3. En AI Edge Gallery: **(+)** → **"Load skill from URL"** → pega la URL de GitHub Pages que apunta a la carpeta del skill

## Configurar el calendario "familia"

La primera vez que uses el skill, la app te pedirá el **Calendar ID** de tu calendario "familia":

1. Abre **Google Calendar** en el navegador: https://calendar.google.com
2. Ve a ⚙️ **Configuración** → en el panel izquierdo selecciona tu calendario **"familia"**
3. Baja hasta la sección **"Integrar calendario"**
4. Copia el valor del campo **"ID del calendario"** (ej: `abc123xyz@group.calendar.google.com` o `tunombre@gmail.com`)
5. Pégalo cuando la app lo solicite

Este ID se usará automáticamente para dirigir los eventos a tu calendario "familia".

## Modelos compatibles

Optimizado para **Gemma 4** (multimodal — soporta imágenes). También funciona con cualquier modelo de visión disponible en AI Edge Gallery.
