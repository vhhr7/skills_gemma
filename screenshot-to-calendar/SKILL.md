---
name: screenshot-to-calendar
description: Creates a Google Calendar event from a screenshot or text. Extracts event title, date, time, location and adds it to a specific Google Calendar.
metadata:
  require-secret: true
  require-secret-description: "Ingresa el ID de tu calendario 'familia'. En Google Calendar: ⚙️ Configuración → selecciona el calendario 'familia' → copia el campo 'ID del calendario'."
---

# Screenshot to Calendar Event

## Purpose
Extract event information from a screenshot, image, or text and create a Google Calendar event in the user's "familia" calendar.

## Instructions

When the user shares a screenshot, photo, or text with event information, extract the following details and call the `run_js` tool.

### Extraction rules:
- **title**: Name or subject of the event (e.g., "Cita médica", "Cumpleaños de Ana", "Reunión de trabajo")
- **start_date**: Start date in `YYYY-MM-DD` format. If no year is given, assume the next upcoming occurrence from today.
- **start_time**: Start time in `HH:MM` 24-hour format. If not found, use `09:00`.
- **end_date**: End date in `YYYY-MM-DD` format. If not specified, use the same as start_date.
- **end_time**: End time in `HH:MM` 24-hour format. If not specified, add 1 hour to start_time.
- **location**: Physical address or place name. Use empty string `""` if not found.
- **description**: Any additional details, notes, or special instructions about the event. Use empty string `""` if not found.

### Call the `run_js` tool with these exact parameters:
- script name: `index.html`
- data: A JSON string with the following fields:
  - `title`: String. The event title.
  - `start_date`: String. Format `YYYY-MM-DD`.
  - `start_time`: String. Format `HH:MM` (24h).
  - `end_date`: String. Format `YYYY-MM-DD`.
  - `end_time`: String. Format `HH:MM` (24h).
  - `location`: String. Location or empty string.
  - `description`: String. Additional details or empty string.

### Example data:
```json
{
  "title": "Cita con el dentista",
  "start_date": "2024-07-15",
  "start_time": "10:30",
  "end_date": "2024-07-15",
  "end_time": "11:30",
  "location": "Clínica Dental, Av. Principal 456",
  "description": "Traer radiografías previas. Dr. Martínez."
}
```
