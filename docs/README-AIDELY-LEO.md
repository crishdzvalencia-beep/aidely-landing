# README - Aidely + Leo MVP

## Estado actual

Aidely tiene una landing local funcional con Leo integrado y un formulario de diagnóstico conectado a n8n mediante ngrok.

Actualmente el proyecto está en **modo producción local controlada**.

---

## Producción local validada

Aidely ya funciona en modo producción local.

Estado validado:

* WF1 está publicado / activo en n8n.
* La landing usa `/webhook/leo-leads`.
* Ya no es necesario pulsar “Listen for test event”.
* El formulario de diagnóstico envía leads reales desde la landing.
* Los datos llegan correctamente al Webhook de WF1.
* El nodo “Preparar lead” lee correctamente datos desde `$json.body`.
* Airtable recibe nombre, email, teléfono, empresa, mensaje y origen.
* Origen queda registrado como `Landing Aidely`.
* Las rutas CALIENTE, TIBIO y FRIO han sido validadas desde la landing.

URL actual en el HTML:

```javascript
const WEBHOOK_URL = "https://vexingly-paltry-sesame.ngrok-free.dev/webhook/leo-leads";
```

Workflows activos actualmente:

```text
WF1 — Activo
WF2 — Desactivado
WF3 — Desactivado
WF4 — Desactivado
WF5 — Desactivado
```

Motivo:

De momento dejamos solo WF1 activo para mantener una demo controlada. WF2, WF3, WF4 y WF5 se ejecutarán manualmente hasta validar el comportamiento automático completo.

---

## Archivo de trabajo actual

```text
index.html copy.html
```

## Copias estables recomendadas

```text
index-aidely-leo-v1.html
index-aidely-form-v1.html
index-aidely-leo-form-n8n-v1.html
index-aidely-production-local-v1.html
```

## Comando para arrancar ngrok

```bash
ngrok http 5678
```

## URL de webhook en producción local

```text
https://TU-URL.ngrok-free.dev/webhook/leo-leads
```

## URL usada en la última prueba

```text
https://vexingly-paltry-sesame.ngrok-free.dev/webhook/leo-leads
```

## Dónde se cambia la URL

En el script final del HTML:

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

## Cómo probar

1. Abrir n8n local.
2. Abrir la landing con Live Server.
3. Ejecutar ngrok:

```bash
ngrok http 5678
```

4. Copiar la URL HTTPS de ngrok.
5. Pegarla en `WEBHOOK_URL` si ha cambiado.
6. Abrir WF1.
7. Activar WF1 / Published.
8. No pulsar “Listen for test event”.
9. Rellenar formulario en la landing.
10. Revisar que el lead entra en WF1 automáticamente.
11. Revisar Airtable.
12. Ejecutar manualmente WF2, WF3, WF4 o WF5 si se quiere probar la cadena completa.

## Workflows

* WF1 - Leo clasificador: recibe y clasifica leads.
* WF2 - Leo avisos inteligentes: envía Telegram para leads calientes.
* WF3 - Leo respuesta comercial: crea borradores Gmail.
* WF4 - Leo seguimiento comercial: gestiona seguimientos.
* WF5 - Leo reporte de actividad: envía reporte diario por Telegram.

## Reglas de clasificación

CALIENTE:

```text
accion_urgente
```

TIBIO:

```text
seguimiento_suave
```

FRIO:

```text
nutricion
```

REVISAR:

```text
revision_manual
```

## Estado de rutas validado desde la landing

CALIENTE:

```text
Ruta Leo = accion_urgente
```

TIBIO:

```text
Ruta Leo = seguimiento_suave
```

FRIO:

```text
Ruta Leo = nutricion
Estado respuesta = no_prioritaria
```

## Problemas conocidos

* Si el formulario llega al webhook pero se pierden datos en Code, revisar si los datos vienen dentro de `$json.body`.
* El nodo Preparar lead debe empezar con:

```javascript
const input = $json.body || $json || {};
```

* Si Airtable no muestra campos nuevos, hacer refresh del nodo Airtable en n8n.
* Si Telegram añade texto de n8n, desactivar Append n8n Attribution.
* Si falla el envío desde la web, revisar:

  * n8n abierto.
  * ngrok activo.
  * WF1 activo.
  * URL correcta en `WEBHOOK_URL`.
  * Uso de `/webhook/leo-leads` y no `/webhook-test/leo-leads`.

## Siguiente paso técnico

Mantener WF1 activo y dejar WF2, WF3, WF4 y WF5 desactivados por seguridad hasta decidir cuándo activar la automatización completa.

Cuando se quiera pasar a automatización completa:

1. Revisar filtros de WF2.
2. Activar WF2.
3. Probar lead CALIENTE.
4. Revisar filtros de WF3.
5. Activar WF3.
6. Revisar filtros de WF4.
7. Activar WF4.
8. Activar WF5 si se quiere reporte diario automático.

## Nota importante

La demo actual es producción local, no producción pública.

Funciona con:

```text
Landing local + Live Server + n8n local + ngrok + WF1 activo
```

Para una publicación real futura en Vercel o Netlify habrá que revisar:

* URL estable del backend.
* Seguridad del webhook.
* RGPD / privacidad.
* Multiempresa.
* Persistencia del entorno n8n.
