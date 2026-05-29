# Checklist demo - Aidely + Leo

## Preparar modo producción local

- [ ] n8n local abierto.
- [ ] ngrok activo con `ngrok http 5678`.
- [ ] WF1 publicado / activo.
- [ ] No pulsar “Listen for test event”.
- [ ] URL del HTML usando `/webhook/leo-leads`.



## Arrancar ngrok

```bash
ngrok http 5678
```

## Revisar URL en HTML

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

## Probar lead desde la landing

- [ ] Ir al formulario.
- [ ] Rellenar nombre.
- [ ] Rellenar email.
- [ ] Rellenar teléfono.
- [ ] Rellenar empresa.
- [ ] Seleccionar sector.
- [ ] Seleccionar urgencia.
- [ ] Seleccionar presupuesto.
- [ ] Escribir mensaje.
- [ ] Enviar diagnóstico.

## Validar WF1

- [ ] Webhook recibe datos.
- [ ] Preparar lead conserva nombre, email, empresa y teléfono.
- [ ] Origen = Landing Aidely.
- [ ] Gemini clasifica.
- [ ] Preparar resultado final Leo genera ruta.
- [ ] Airtable crea registro.

## Validar lead CALIENTE

- [ ] Clasificación = CALIENTE.
- [ ] Ruta Leo = accion_urgente.
- [ ] Requiere aviso = si.
- [ ] Requiere borrador = si.
- [ ] WF2 envía Telegram.
- [ ] WF3 crea Gmail draft.
- [ ] WF4 gestiona seguimiento.

## Validar lead TIBIO

- [ ] Clasificación = TIBIO.
- [ ] Ruta Leo = seguimiento_suave.
- [ ] No Telegram urgente.
- [ ] No Gmail automático.
- [ ] Seguimiento suave preparado.

## Validar lead FRIO

- [ ] Clasificación = FRIO.
- [ ] Ruta Leo = nutricion.
- [ ] Estado respuesta = no_prioritaria.
- [ ] No Telegram.
- [ ] No Gmail.
- [ ] No seguimiento inmediato.

## Validar WF5

- [ ] Ejecutar reporte.
- [ ] Telegram recibe reporte.
- [ ] No aparece mensaje automático de n8n.
