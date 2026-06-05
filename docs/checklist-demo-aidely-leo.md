# Checklist demo — Aidely + Leo

## Objetivo del checklist

Este checklist sirve para preparar, validar y presentar Aidely como una demo funcional de empleados digitales sencillos para autónomos y pequeños negocios.

Aidely no debe presentarse como una plataforma corporativa compleja ni como un sistema autónomo que toma decisiones irreversibles.

Aidely debe presentarse como una ayuda digital práctica que:

* ordena solicitudes,
* avisa oportunidades,
* prepara borradores,
* recuerda seguimientos,
* genera reportes,
* demuestra empleados digitales sencillos,
* mantiene siempre revisión humana.

---

## 1. Enfoque estratégico actual

* [ ] Aidely se presenta como empleados digitales sencillos para autónomos y pequeños negocios.
* [ ] El mensaje evita lenguaje técnico innecesario.
* [ ] No se habla de n8n, webhooks, APIs o Gemini delante del cliente salvo que pregunte.
* [ ] Se explica que Aidely prepara, ordena y avisa.
* [ ] Se explica que el dueño revisa y decide.
* [ ] Se evita prometer automatización total.
* [ ] Se evita prometer producción empresarial 24/7 en fase inicial.
* [ ] Se evita trabajar con datos sensibles al inicio.
* [ ] Se deja claro que los pilotos se cobran, aunque sean accesibles.

---

## 2. Preparar modo demo local

* [ ] VS Code abierto en el proyecto `landing-aidely`.
* [ ] n8n local abierto.
* [ ] ngrok activo solo para demo o prueba controlada.
* [ ] WF1 publicado / activo.
* [ ] WF2 publicado / activo.
* [ ] WF3 publicado / activo.
* [ ] WF4 publicado / activo.
* [ ] WF5 publicado / activo.
* [ ] No pulsar “Listen for test event” si se está usando producción local.
* [ ] URL del HTML usando `/webhook/leo-leads`.
* [ ] Landing abierta en navegador.
* [ ] Telegram abierto para verificar avisos.
* [ ] Gmail abierto para verificar borradores.
* [ ] Airtable abierto para revisar registros.

---

## 3. Arrancar ngrok para demo local

```bash
ngrok http 5678
```

---

## 4. Revisar URL en HTML

En `index.html`, comprobar:

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

Recordatorio:

```text
/webhook/leo-leads = producción local controlada.
/webhook-test/leo-leads = solo pruebas internas con Listen for test event.
```

---

## 5. Probar landing publicada en Vercel

* [ ] Abrir landing pública.
* [ ] Revisar que carga correctamente.
* [ ] Revisar menú superior.
* [ ] Revisar sección de Leo.
* [ ] Revisar sección de empleados digitales.
* [ ] Revisar precios.
* [ ] Revisar Demo Vera.
* [ ] Revisar formulario de diagnóstico.
* [ ] Confirmar que no hay errores visuales importantes.
* [ ] Confirmar que el mensaje es claro para autónomos y pequeños negocios.

---

## 6. Probar lead desde la landing

* [ ] Ir al formulario.
* [ ] Rellenar nombre.
* [ ] Rellenar email.
* [ ] Rellenar teléfono.
* [ ] Rellenar empresa.
* [ ] Seleccionar sector.
* [ ] Seleccionar urgencia.
* [ ] Seleccionar presupuesto.
* [ ] Escribir mensaje.
* [ ] Enviar diagnóstico.
* [ ] Confirmar mensaje visual de envío correcto.
* [ ] Confirmar que no se rompe el formulario.
* [ ] Confirmar que no se toca la Demo Vera.

---

## 7. Validar WF1 — Recepción y clasificación

* [ ] Webhook recibe datos.
* [ ] Preparar lead conserva nombre.
* [ ] Preparar lead conserva email.
* [ ] Preparar lead conserva teléfono.
* [ ] Preparar lead conserva empresa.
* [ ] Origen = Landing Aidely.
* [ ] Gemini clasifica correctamente.
* [ ] Preparar resultado final Leo genera ruta.
* [ ] Airtable crea registro.
* [ ] Lead ID se genera correctamente.
* [ ] Fecha entrada se guarda correctamente.
* [ ] Clasificación se guarda correctamente.
* [ ] Ruta Leo se guarda correctamente.
* [ ] Estado comercial se guarda correctamente.
* [ ] Requiere aviso se guarda correctamente.
* [ ] Requiere borrador se guarda correctamente.

---

## 8. Validar lead CALIENTE

* [ ] Clasificación = CALIENTE.
* [ ] Ruta Leo = accion_urgente.
* [ ] Estado comercial = contactar_hoy.
* [ ] Requiere aviso = si.
* [ ] Requiere borrador = si.
* [ ] Aviso enviado inicial = no.
* [ ] Respuesta preparada inicial = no.
* [ ] WF2 encuentra el lead.
* [ ] WF2 envía Telegram.
* [ ] WF2 marca Aviso enviado = si.
* [ ] WF3 encuentra el lead.
* [ ] WF3 crea Gmail draft.
* [ ] WF3 marca Respuesta preparada = si.
* [ ] WF3 marca Estado respuesta = preparada.
* [ ] WF3 activa Seguimiento pendiente = si.
* [ ] WF4 envía recordatorio si corresponde.
* [ ] WF5 incluye el lead en el reporte diario.

---

## 9. Validar lead TIBIO

* [ ] Clasificación = TIBIO.
* [ ] Ruta Leo = seguimiento_suave.
* [ ] No envía Telegram urgente.
* [ ] No crea Gmail automático de respuesta urgente.
* [ ] Queda registrado en Airtable.
* [ ] Queda preparado para seguimiento suave.
* [ ] Estado comercial no se confunde con contactar_hoy.
* [ ] No activa flujo de aviso caliente.

---

## 10. Validar lead FRIO

* [ ] Clasificación = FRIO.
* [ ] Ruta Leo = nutricion.
* [ ] Estado respuesta = no_prioritaria.
* [ ] No envía Telegram urgente.
* [ ] No crea Gmail automático.
* [ ] No activa seguimiento inmediato.
* [ ] Queda guardado en Airtable.
* [ ] Puede revisarse manualmente si se desea.

---

## 11. Validar WF2 — Avisos Telegram

Filtro esperado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "no")
```

Checklist:

* [ ] Search records encuentra leads correctos.
* [ ] No encuentra leads ya avisados.
* [ ] Preparar aviso Leo genera mensaje claro.
* [ ] Telegram recibe aviso.
* [ ] Mensaje incluye nombre.
* [ ] Mensaje incluye empresa.
* [ ] Mensaje incluye teléfono.
* [ ] Mensaje incluye email.
* [ ] Mensaje incluye clasificación.
* [ ] Mensaje incluye próxima acción.
* [ ] Update record marca Aviso enviado = si.
* [ ] No duplica avisos.

---

## 12. Validar WF3 — Borradores Gmail

Filtro esperado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "si", {Respuesta preparada} = "no")
```

Checklist:

* [ ] Search records encuentra leads correctos.
* [ ] Preparar email Leo genera asunto claro.
* [ ] Preparar email Leo genera cuerpo comercial limpio.
* [ ] El cuerpo no copia texto interno como “motivo IA” de forma cruda.
* [ ] El cuerpo habla al cliente de forma natural.
* [ ] Gmail crea borrador.
* [ ] Gmail no envía correo automáticamente.
* [ ] Update record marca Respuesta preparada = si.
* [ ] Update record marca Estado respuesta = preparada.
* [ ] Update record activa Seguimiento pendiente = si.
* [ ] No duplica borradores.

---

## 13. Validar WF4 — Seguimientos

Filtro esperado:

```text
AND({Seguimiento pendiente} = "si", {Seguimiento enviado} = "no")
```

Checklist:

* [ ] Search records encuentra seguimientos pendientes.
* [ ] Preparar seguimiento Leo genera mensaje claro.
* [ ] Telegram recibe recordatorio.
* [ ] Mensaje no muestra estados deformados.
* [ ] Mensaje incluye acción sugerida.
* [ ] Update record marca Seguimiento enviado = si.
* [ ] No duplica seguimientos.
* [ ] El seguimiento sigue siendo interno, no se envía al cliente.

---

## 14. Validar WF5 — Reporte diario

Filtro esperado:

```text
IS_SAME({Fecha entrada}, TODAY(), 'day')
```

Checklist:

* [ ] Ejecutar reporte.
* [ ] Search records encuentra leads del día.
* [ ] Crear reporte Leo cuenta total de leads.
* [ ] Cuenta calientes.
* [ ] Cuenta tibios.
* [ ] Cuenta fríos.
* [ ] Cuenta revisar.
* [ ] Cuenta avisos enviados.
* [ ] Cuenta borradores preparados.
* [ ] Cuenta seguimientos enviados.
* [ ] Diferencia seguimientos pendientes sin enviar.
* [ ] Telegram recibe reporte.
* [ ] Reporte se entiende fácil.
* [ ] No aparece mensaje automático innecesario de n8n si se puede evitar.

---

## 15. Validar Demo Vera

* [ ] Enlace Demo aparece en el menú.
* [ ] Al pulsar Demo baja a la sección Vera.
* [ ] La sección se ve bien en escritorio.
* [ ] La tabla de stock ficticio se ve clara.
* [ ] El botón “Probar a Vera” funciona.
* [ ] Aparece reporte generado.
* [ ] Aparece borrador simulado.
* [ ] No conecta con datos reales.
* [ ] No toca Airtable.
* [ ] No toca n8n.
* [ ] No toca Gmail real.
* [ ] No toca Telegram.
* [ ] No interfiere con el formulario.
* [ ] Se explica como lista simple de reposición, no inventario exacto.

---

## 16. Validar mensaje comercial

Durante la demo, comprobar que se comunica:

* [ ] Aidely ayuda a pequeños negocios.
* [ ] Aidely no es una plataforma corporativa compleja.
* [ ] Leo ya funciona como empleado de atención y ventas.
* [ ] Vera es una demo visual con datos ficticios.
* [ ] Hugo será el próximo empleado enfocado en presupuestos rápidos.
* [ ] Aidely trabaja con datos mínimos.
* [ ] Aidely prepara borradores y avisos.
* [ ] El dueño mantiene el control.
* [ ] No se prometen acciones automáticas peligrosas.
* [ ] Los pilotos se cobran de forma accesible.

---

## 17. Qué decir sobre ChatGPT Agents

* [ ] Explicar que ChatGPT puede crear agentes y ayudar mucho.
* [ ] No decir que Aidely es mejor que ChatGPT.
* [ ] Decir que Aidely convierte esas posibilidades en procesos concretos para pequeños negocios.
* [ ] Decir que el cliente no necesita aprender prompts, APIs, n8n, Make ni conectores.
* [ ] Usar la frase:

```text
ChatGPT te da la herramienta.
Aidely te deja el proceso funcionando.
```

---

## 18. Qué no prometer

No decir:

* [ ] “La IA lo hace todo.”
* [ ] “Esto funciona para cualquier empresa automáticamente.”
* [ ] “Conectamos cualquier sistema sin problema.”
* [ ] “No hace falta revisar nada.”
* [ ] “Enviamos presupuestos automáticamente.”
* [ ] “Gestionamos facturas reales desde el primer día.”
* [ ] “Controlamos stock exacto.”
* [ ] “Cumplimos todo legalmente sin revisar el caso.”

Mejor decir:

```text
Aidely prepara, ordena y avisa.
Tú revisas y decides.
```

---

## 19. Primeros pilotos

Antes de ofrecer piloto:

* [ ] Tener claro el alcance.
* [ ] Tener claro qué datos se usarán.
* [ ] Evitar datos sensibles.
* [ ] Evitar ngrok.
* [ ] Usar n8n Cloud, Make o infraestructura estable.
* [ ] Separar datos del cliente.
* [ ] Explicar que las acciones serán revisables.
* [ ] Cobrar siempre algo por el piloto.
* [ ] Definir duración del piloto.
* [ ] Definir qué se considera éxito.
* [ ] Definir qué no está incluido.

---

## 20. Pricing inicial orientativo

* [ ] Diagnóstico inicial gratuito o simbólico.
* [ ] Piloto de 30 días desde 49€.
* [ ] Instalación básica 99€ - 149€.
* [ ] Mensualidad por empleado sencillo 49€ - 79€/mes.
* [ ] Pack de 2 empleados 99€ - 129€/mes.
* [ ] No regalar instalaciones completas.
* [ ] No aceptar clientes que pidan todo por muy poco.
* [ ] Mantener precios accesibles.

---

## 21. Checklist Git

Antes de cerrar cualquier bloque:

```bash
git status
```

Revisar cambios:

```bash
git diff --stat
```

Añadir archivos:

```bash
git add .
```

Commit:

```bash
git commit -m "Mensaje claro del cambio"
```

Push:

```bash
git push
```

Estado final esperado:

```text
nothing to commit, working tree clean
```

---

## 22. Ruta actual de trabajo

### Bloque 1 — Estrategia

* [x] Crear `docs/estrategia-aidely-negocios-pequenos.md`.
* [x] Revisar contenido.
* [x] Corregir ubicación si se creó carpeta duplicada.
* [x] Commit.
* [x] Push.

---

### Bloque 2 — Documentación

* [x] Actualizar `README-AIDELY-LEO.md`.
* [ ] Actualizar `checklist-demo-aidely-leo.md`.
* [ ] Actualizar `Aidely_Leo_MVP_Documentacion_v1.md`.
* [ ] Regenerar PDF si corresponde.
* [ ] Actualizar NotebookLM con el nuevo enfoque.

---

### Bloque 3 — Landing

* [ ] Revisar hero principal.
* [ ] Revisar subtítulo.
* [ ] Revisar sección de empleados.
* [ ] Revisar Demo Vera.
* [ ] Revisar precios.
* [ ] Revisar formulario.
* [ ] Revisar guion comercial.
* [ ] Ajustar texto para autónomos y pequeños negocios.

---

### Bloque 4 — Diseño de Hugo

* [ ] Crear `docs/hugo-presupuestos-rapidos.md`.
* [ ] Definir objetivo.
* [ ] Definir cliente ideal.
* [ ] Definir problema.
* [ ] Definir datos mínimos.
* [ ] Definir flujo.
* [ ] Definir herramientas.
* [ ] Definir riesgos.
* [ ] Definir mitigaciones.
* [ ] Definir versión demo.
* [ ] Definir versión piloto.
* [ ] Definir mensajes.
* [ ] Definir formato de presupuesto.
* [ ] Definir validación.

---

### Bloque 5 — Demo Hugo

* [ ] Decidir formulario o audio.
* [ ] Diseñar plantilla de presupuesto.
* [ ] Crear datos ficticios.
* [ ] Crear flujo de prueba.
* [ ] Generar borrador revisable.
* [ ] Validar que no envía nada automáticamente.

---

### Bloque 6 — Infraestructura para piloto

* [ ] Decidir n8n Cloud, Make o VPS.
* [ ] Evitar ngrok para cliente real.
* [ ] Separar datos por cliente.
* [ ] Definir consentimiento básico.
* [ ] Crear documento de alcance.
* [ ] Crear checklist de instalación.

---

### Bloque 7 — Validación comercial

* [ ] Hablar con 3 oficios.
* [ ] Hablar con 3 peluquerías/estética.
* [ ] Preguntar por presupuestos, citas, clientes perdidos y tareas repetitivas.
* [ ] No vender en la primera conversación.
* [ ] Registrar respuestas.
* [ ] Elegir primer piloto pagado.
