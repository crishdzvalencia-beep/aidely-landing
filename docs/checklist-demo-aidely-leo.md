# Checklist demo - Aidely + Leo

## 1. Preparar entorno de trabajo

* [ ] Abrir VS Code en la carpeta correcta:

```bash
C:\Users\zaphi\Documents\proyectos-aidely\landing-aidely
```

* [ ] Comprobar estado de Git:

```bash
git status
```

* [ ] Confirmar que no hay cambios pendientes antes de empezar una prueba importante.
* [ ] Abrir n8n local.
* [ ] Abrir Airtable.
* [ ] Abrir Telegram.
* [ ] Abrir Gmail.
* [ ] Abrir la landing pública de Vercel o la landing local con Live Server.

---

## 2. Arrancar n8n local

* [ ] Abrir PowerShell.
* [ ] Ejecutar n8n si no está activo:

```bash
n8n
```

* [ ] Confirmar que n8n abre correctamente en:

```text
http://localhost:5678
```

---

## 3. Arrancar ngrok

* [ ] Abrir una segunda terminal.
* [ ] Ejecutar:

```bash
ngrok http 5678
```

* [ ] Copiar la nueva URL HTTPS de ngrok.
* [ ] Confirmar que la URL está activa.

Ejemplo:

```text
https://TU-URL.ngrok-free.dev
```

---

## 4. Revisar URL del webhook en HTML

* [ ] Abrir `index.html`.
* [ ] Buscar:

```javascript
const WEBHOOK_URL
```

* [ ] Confirmar que apunta a:

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

* [ ] Confirmar que usa `/webhook/leo-leads`.
* [ ] Confirmar que NO usa `/webhook-test/leo-leads`.

Si cambia la URL de ngrok:

* [ ] Actualizar `WEBHOOK_URL`.
* [ ] Guardar archivo.
* [ ] Probar en local.
* [ ] Hacer commit.
* [ ] Hacer push.

```bash
git add index.html
git commit -m "Actualizar URL webhook Aidely"
git push
```

---

## 5. Estado de workflows antes de la demo

Confirmar en n8n:

* [ ] WF1 — Publicado / Publish.
* [ ] WF2 — Publicado / Publish.
* [ ] WF3 — Publicado / Publish.
* [ ] WF4 — Publicado / Publish.
* [ ] WF5 — Publicado / Publish.

Estado esperado:

```text
WF1 activo
WF2 activo
WF3 activo
WF4 activo
WF5 activo
```

---

## 6. Frecuencias recomendadas

Revisar triggers:

* [ ] WF1 — Webhook inmediato.
* [ ] WF2 — Cada 5 minutos.
* [ ] WF3 — Cada 10 minutos.
* [ ] WF4 — Cada 15-30 minutos.
* [ ] WF5 — Diario, recomendado a las 20:00.

Notas:

* WF2 debe actuar antes que WF3.
* WF3 debe crear borrador después de que WF2 haya marcado `Aviso enviado = si`.
* WF4 debe actuar después de que WF3 haya marcado `Respuesta preparada = si`.
* WF5 debe resumir el día completo, por eso se recomienda horario de cierre.

---

## 7. Probar lead desde la landing

* [ ] Ir al formulario de diagnóstico.
* [ ] Rellenar nombre.
* [ ] Rellenar email.
* [ ] Rellenar teléfono.
* [ ] Rellenar empresa.
* [ ] Seleccionar sector.
* [ ] Seleccionar urgencia.
* [ ] Seleccionar presupuesto.
* [ ] Escribir mensaje.
* [ ] Enviar diagnóstico.

Ejemplo de lead CALIENTE para prueba:

```text
Nombre: Laura Prueba Final
Empresa: Clínica Horizonte
Email: laura.pruebafinal@aidelytest.com
Teléfono: 600555444
Sector: Clínica
Urgencia: Alta
Presupuesto: 500-800€

Mensaje:
Hola, tenemos una clínica y necesitamos automatizar cuanto antes las solicitudes de nuevos pacientes. Recibimos consultas por la web y por WhatsApp, pero tardamos en responder y estamos perdiendo oportunidades. Queremos avisos rápidos, clasificación de contactos y una respuesta preparada para contactar mejor.
```

---

## 8. Validar WF1 — Recepción y clasificación

Después de enviar el formulario:

* [ ] WF1 se ejecuta automáticamente.
* [ ] Webhook recibe datos.
* [ ] Preparar lead conserva nombre, email, empresa y teléfono.
* [ ] Origen = Landing Aidely.
* [ ] Gemini clasifica.
* [ ] Preparar resultado final Leo genera ruta.
* [ ] Airtable crea registro.

Campos esperados en Airtable:

* [ ] Nombre correcto.
* [ ] Empresa correcta.
* [ ] Email correcto.
* [ ] Teléfono correcto.
* [ ] Sector correcto.
* [ ] Mensaje correcto.
* [ ] Origen = Landing Aidely.
* [ ] Clasificación generada.
* [ ] Ruta Leo generada.
* [ ] Estado comercial generado.

---

## 9. Validar lead CALIENTE

Para lead caliente:

* [ ] Clasificación = CALIENTE.
* [ ] Ruta Leo = accion_urgente.
* [ ] Estado comercial = contactar_hoy.
* [ ] Requiere aviso = si.
* [ ] Requiere borrador = si.
* [ ] Aviso enviado = no al crearse.
* [ ] Respuesta preparada = no al crearse.
* [ ] Seguimiento pendiente = no al crearse.
* [ ] Seguimiento enviado = no al crearse.

Luego esperar automatización:

* [ ] WF2 envía Telegram.
* [ ] WF3 crea borrador Gmail.
* [ ] WF4 envía recordatorio de seguimiento.
* [ ] WF5 incluye el lead en reporte diario.

---

## 10. Validar WF2 — Aviso de lead caliente

Filtro esperado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "no")
```

Validaciones:

* [ ] WF2 detecta el lead caliente.
* [ ] Telegram recibe aviso interno.
* [ ] El mensaje incluye empresa, nombre, teléfono, email y acción recomendada.
* [ ] Airtable actualiza `Aviso enviado = si`.
* [ ] Airtable actualiza `Fecha aviso`.
* [ ] Ejecutar Search después de procesar devuelve 0 items.
* [ ] No se duplican avisos.

---

## 11. Validar WF3 — Borrador Gmail

Filtro esperado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "si", {Respuesta preparada} = "no")
```

Validaciones:

* [ ] WF3 detecta leads calientes ya avisados.
* [ ] Preparar email Leo genera email limpio.
* [ ] El email NO incluye notas internas.
* [ ] El email NO incluye “Motivo IA”.
* [ ] El email NO incluye “Resumen de tu caso”.
* [ ] El email NO incluye “Próximo paso recomendado”.
* [ ] Gmail crea borrador.
* [ ] Gmail NO envía email automáticamente.
* [ ] Airtable actualiza `Respuesta preparada = si`.
* [ ] Airtable actualiza `Estado respuesta = preparada`.
* [ ] Airtable actualiza `Seguimiento pendiente = si`.
* [ ] Airtable mantiene `Seguimiento enviado = no`.
* [ ] Ejecutar Search después de procesar devuelve 0 items.
* [ ] No se duplican borradores.

---

## 12. Validar WF4 — Seguimiento comercial

Filtro esperado:

```text
AND({Respuesta preparada} = "si", {Seguimiento pendiente} = "si", {Seguimiento enviado} = "no")
```

Validaciones:

* [ ] WF4 detecta leads con respuesta preparada y seguimiento pendiente.
* [ ] Preparar seguimiento Leo genera mensaje interno.
* [ ] Telegram recibe recordatorio de seguimiento.
* [ ] El mensaje muestra `contactar hoy`, no `contactarhoy`.
* [ ] Airtable actualiza `Seguimiento enviado = si`.
* [ ] Airtable actualiza `Fecha seguimiento`.
* [ ] Airtable actualiza `Fecha próximo seguimiento` si aplica.
* [ ] Ejecutar Search después de procesar devuelve 0 items.
* [ ] No se duplican seguimientos.

---

## 13. Validar WF5 — Reporte diario

Filtro esperado:

```text
IS_SAME({Fecha entrada}, TODAY(), 'day')
```

Validaciones:

* [ ] WF5 busca leads del día.
* [ ] Crear reporte Leo genera 1 solo item.
* [ ] Telegram recibe 1 solo reporte.
* [ ] El reporte incluye leads revisados hoy.
* [ ] El reporte incluye calientes, tibios, fríos y revisar.
* [ ] El reporte incluye avisos enviados.
* [ ] El reporte incluye borradores preparados.
* [ ] El reporte incluye seguimientos enviados.
* [ ] El reporte incluye seguimientos pendientes sin avisar.
* [ ] El reporte no se contradice.
* [ ] Si no hay score válido, muestra `Score medio: No disponible`.
* [ ] No aparece mensaje automático de n8n.

Ejemplo esperado:

```text
📊 Reporte de Leo — Aidely

📥 Leads revisados hoy: 2

🔥 Calientes: 2
🌤️ Tibios: 0
❄️ Fríos: 0
⚠️ Revisar: 0

📲 Avisos enviados: 2
✉️ Borradores preparados: 2
✅ Seguimientos enviados: 2
⏳ Seguimientos pendientes sin avisar: 0

⭐ Score medio: No disponible

🧠 Estado general:
Leo ha procesado oportunidades importantes y no quedan seguimientos pendientes sin avisar.
```

---

## 14. Validar lead TIBIO

Probar con un mensaje menos urgente.

Ejemplo:

```text
Hola, estoy valorando mejorar la organización de los clientes de mi negocio, pero no es urgente. Me gustaría recibir información y quizá probar algo más adelante.
```

Validaciones:

* [ ] Clasificación = TIBIO.
* [ ] Ruta Leo = seguimiento_suave.
* [ ] Estado comercial = hacer_seguimiento.
* [ ] No Telegram urgente por WF2.
* [ ] No Gmail automático inmediato si no corresponde.
* [ ] Seguimiento suave preparado si aplica.
* [ ] Airtable guarda el lead correctamente.

---

## 15. Validar lead FRIO

Probar con un mensaje poco concreto o sin intención clara.

Ejemplo:

```text
Hola, solo estaba mirando la página. No tengo negocio todavía, pero quería saber de qué va esto.
```

Validaciones:

* [ ] Clasificación = FRIO.
* [ ] Ruta Leo = nutricion.
* [ ] Estado respuesta = no_prioritaria.
* [ ] No Telegram urgente.
* [ ] No Gmail.
* [ ] No seguimiento inmediato.
* [ ] Airtable guarda el lead correctamente.

---

## 16. Validar que no hay duplicados

Después de una prueba completa:

* [ ] Search de WF2 devuelve 0.
* [ ] Search de WF3 devuelve 0.
* [ ] Search de WF4 devuelve 0.
* [ ] No se repite Telegram de lead caliente.
* [ ] No se crea segundo borrador Gmail.
* [ ] No se repite recordatorio de seguimiento.

---

## 17. Validar Gmail

* [ ] Gmail conectado correctamente.
* [ ] No hay error de token.
* [ ] Se crean borradores.
* [ ] No se envían emails automáticamente.
* [ ] El texto del borrador es cliente-facing.
* [ ] El texto no contiene notas internas.
* [ ] El asunto es correcto.
* [ ] El destinatario es correcto.
* [ ] El cuerpo del email es claro y profesional.

Si hay error de token:

* [ ] Abrir credencial Gmail.
* [ ] Reconectar cuenta.
* [ ] Guardar.
* [ ] Reintentar nodo Gmail.

---

## 18. Validar Telegram

* [ ] Telegram recibe aviso de WF2.
* [ ] Telegram recibe seguimiento de WF4.
* [ ] Telegram recibe reporte de WF5.
* [ ] No aparece atribución automática de n8n.
* [ ] No se pierde formato por guiones bajos.
* [ ] Los mensajes son internos, claros y accionables.

Si aparece texto automático de n8n:

* [ ] Revisar opción `Append n8n Attribution`.
* [ ] Desactivarla.

---

## 19. Validar Airtable

Revisar que los campos cambian en orden:

### Al entrar por WF1

* [ ] Aviso enviado = no.
* [ ] Respuesta preparada = no.
* [ ] Seguimiento pendiente = no.
* [ ] Seguimiento enviado = no.

### Después de WF2

* [ ] Aviso enviado = si.
* [ ] Fecha aviso rellena.

### Después de WF3

* [ ] Respuesta preparada = si.
* [ ] Estado respuesta = preparada.
* [ ] Seguimiento pendiente = si.
* [ ] Fecha respuesta preparada rellena.
* [ ] Asunto email relleno.

### Después de WF4

* [ ] Seguimiento enviado = si.
* [ ] Fecha seguimiento rellena.
* [ ] Fecha próximo seguimiento rellena si aplica.

---

## 20. Validar prueba general completa

Flujo esperado:

```text
Landing pública
↓
WF1 recibe y clasifica
↓
Airtable guarda el lead
↓
WF2 avisa por Telegram
↓
WF3 crea borrador Gmail
↓
WF4 avisa seguimiento pendiente
↓
WF5 genera reporte diario
```

Checklist final:

* [ ] Landing envía lead.
* [ ] Airtable recibe lead.
* [ ] WF1 clasifica.
* [ ] WF2 avisa.
* [ ] WF3 crea borrador.
* [ ] WF4 recuerda seguimiento.
* [ ] WF5 reporta.
* [ ] No hay duplicados.
* [ ] No hay errores de credenciales.
* [ ] No se toca manualmente ningún nodo durante la prueba automática.

---

## 21. Próxima demo estratégica — Vera

Pendiente de construir:

```text
Demo Vera — control de stock y pedidos
```

Objetivo:

* [ ] Crear sección demo en la landing.
* [ ] Usar datos ficticios de una tienda.
* [ ] Mostrar tabla de stock.
* [ ] Añadir botón “Probar a Vera”.
* [ ] Simular revisión de stock.
* [ ] Detectar productos bajo mínimo.
* [ ] Mostrar pedido sugerido.
* [ ] Mostrar reporte generado.
* [ ] Mostrar borrador de pedido.
* [ ] Añadir CTA “Quiero una demo adaptada a mi negocio”.

Reglas:

* [ ] No tocar webhook real.
* [ ] No tocar formulario real.
* [ ] No tocar WF1-WF5.
* [ ] No tocar Airtable real.
* [ ] No tocar Gmail real.
* [ ] No tocar Telegram real.
* [ ] La demo debe funcionar solo en la landing con datos ficticios.

---

## 22. Cierre de demo

Antes de cerrar una jornada:

* [ ] Revisar `git status`.
* [ ] Guardar cambios en VS Code.
* [ ] Hacer commit si hubo cambios documentales o de código.
* [ ] Hacer push.
* [ ] Confirmar Vercel si se tocó `index.html`.
* [ ] Confirmar que README y checklist están actualizados.

Comandos:

```bash
git status
git add docs/checklist-demo-aidely-leo.md
git commit -m "Actualiza checklist demo Aidely Leo"
git push
```
