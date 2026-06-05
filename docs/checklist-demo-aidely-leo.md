# Checklist demo — Aidely

## Objetivo del checklist

Este checklist sirve para preparar, validar y presentar Aidely como una solución de empleados digitales sencillos para autónomos, microempresas y pequeños negocios.

Aidely debe presentarse como una ayuda práctica que:

* ordena solicitudes,
* prepara borradores,
* avisa oportunidades,
* recuerda tareas pendientes,
* genera reportes,
* mantiene revisión humana,
* evita automatizaciones irreversibles.

Regla principal:

```text
Aidely prepara, ordena y avisa.
El dueño revisa y decide.
```

---

## 1. Estado global del proyecto

* [ ] Leo está validado con WF1-WF5.
* [ ] Hugo está validado con WF1-WF3.
* [ ] Vera está validada como demo visual.
* [ ] La landing está publicada en Vercel.
* [ ] GitHub está actualizado.
* [ ] La documentación está actualizada.
* [ ] No se usan datos reales sensibles.
* [ ] No se promete automatización total.
* [ ] No se promete producción estable con ngrok.
* [ ] Los flujos críticos mantienen revisión humana.

---

## 2. Enfoque estratégico actual

Aidely se presenta como:

```text
Empleados digitales sencillos para autónomos y pequeños negocios.
```

Checklist de mensaje:

* [ ] El mensaje evita lenguaje técnico innecesario.
* [ ] No se habla de n8n, webhooks, APIs o Gemini delante del cliente salvo que pregunte.
* [ ] Se explica que Aidely prepara, ordena y avisa.
* [ ] Se explica que el dueño revisa y decide.
* [ ] Se evita prometer automatización total.
* [ ] Se evita prometer producción empresarial 24/7 en fase inicial.
* [ ] Se evita trabajar con datos sensibles al inicio.
* [ ] Se deja claro que los pilotos se cobran, aunque sean accesibles.

---

## 3. Preparar entorno local

* [ ] VS Code abierto en el proyecto `landing-aidely`.
* [ ] n8n local abierto.
* [ ] Airtable abierto.
* [ ] Telegram abierto.
* [ ] Gmail abierto.
* [ ] Landing abierta en navegador.
* [ ] Git en carpeta correcta:

```bash
cd C:\Users\zaphi\Documents\proyectos-aidely\landing-aidely
```

* [ ] Revisar estado Git:

```bash
git status
```

Estado esperado antes de empezar:

```text
nothing to commit, working tree clean
```

---

## 4. Landing pública

Archivo principal:

```text
index.html
```

Checklist visual:

* [ ] La landing carga correctamente.
* [ ] El menú superior funciona.
* [ ] El enlace “Demos” baja a Hugo.
* [ ] Hero principal comunica autónomos y pequeños negocios.
* [ ] Leo aparece como empleado de atención y ventas.
* [ ] Hugo aparece como presupuestos rápidos.
* [ ] Vera aparece como reposición sencilla.
* [ ] Precios visibles.
* [ ] Formulario de diagnóstico visible.
* [ ] No hay errores visuales importantes.
* [ ] No hay textos que prometan automatización total.
* [ ] No hay textos que prometan stock exacto.
* [ ] No hay textos que prometan envío automático sin revisión.

---

## 5. Demo visual Hugo

La demo visual de Hugo está en la landing y no conecta con sistemas reales.

Funcionamiento:

```text
Usuario escribe solicitud
↓
Pulsa “Probar a Hugo”
↓
Aparece borrador simulado
↓
Aparece aviso interno simulado
```

Checklist:

* [ ] La sección Demo Hugo aparece antes que Vera.
* [ ] El textarea de Hugo aparece correctamente.
* [ ] El botón “Probar a Hugo” funciona.
* [ ] Aparece estado “Borrador preparado”.
* [ ] Aparece borrador de presupuesto simulado.
* [ ] Aparece aviso interno simulado.
* [ ] El texto indica que no se envía información a sistemas externos.
* [ ] No usa webhook.
* [ ] No usa n8n.
* [ ] No usa Gemini.
* [ ] No gasta tokens.
* [ ] No usa Gmail real.
* [ ] No usa Telegram real.
* [ ] No toca Airtable.
* [ ] No toca datos reales.

---

## 6. Demo visual Vera

La demo visual de Vera está en la landing y no conecta con sistemas reales.

Funcionamiento:

```text
Usuario pulsa “Probar a Vera”
↓
La landing revisa stock ficticio
↓
Muestra reporte simulado
↓
Muestra lista de reposición simulada
```

Checklist:

* [ ] La sección Demo Vera sigue funcionando.
* [ ] El botón “Probar a Vera” funciona.
* [ ] Aparece reporte generado.
* [ ] Aparece lista de reposición preparada.
* [ ] No se habla de stock exacto como promesa real.
* [ ] Se presenta como reposición sencilla.
* [ ] No usa webhook.
* [ ] No usa n8n.
* [ ] No usa Gemini.
* [ ] No gasta tokens.
* [ ] No usa Gmail real.
* [ ] No usa Telegram real.
* [ ] No toca Airtable.
* [ ] No toca datos reales.

---

## 7. Formulario de diagnóstico Aidely

Checklist:

* [ ] El formulario aparece correctamente.
* [ ] Se puede rellenar nombre.
* [ ] Se puede rellenar email.
* [ ] Se puede rellenar teléfono.
* [ ] Se puede rellenar empresa.
* [ ] Se puede seleccionar sector.
* [ ] Se puede seleccionar urgencia.
* [ ] Se puede seleccionar presupuesto.
* [ ] Se puede escribir mensaje.
* [ ] El botón de envío funciona.
* [ ] El formulario no se rompe tras añadir Hugo.
* [ ] El formulario no se rompe tras mantener Vera.
* [ ] La demo Hugo no interfiere con el formulario.
* [ ] La demo Vera no interfiere con el formulario.

---

# LEO — Validación funcional

## 8. Estado de Leo

Leo es el empleado digital de atención y ventas.

Estado:

```text
Funcional y validado.
```

Workflows:

```text
WF1 — Recepción y clasificación de leads
WF2 — Avisos Telegram de leads calientes
WF3 — Borradores Gmail
WF4 — Seguimientos
WF5 — Reporte diario comercial
```

---

## 9. Preparar modo demo local Leo

* [ ] n8n local abierto.
* [ ] ngrok activo solo si se va a probar el formulario real contra n8n local.
* [ ] WF1 publicado / activo.
* [ ] WF2 publicado / activo.
* [ ] WF3 publicado / activo.
* [ ] WF4 publicado / activo.
* [ ] WF5 publicado / activo.
* [ ] No pulsar “Listen for test event” si se usa producción local.
* [ ] URL del HTML usando `/webhook/leo-leads`.
* [ ] Telegram abierto para verificar avisos.
* [ ] Gmail abierto para verificar borradores.
* [ ] Airtable abierto para revisar registros.

---

## 10. URL webhook Leo

En `index.html`, revisar:

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

Recordatorio:

```text
/webhook/leo-leads = producción local controlada.
/webhook-test/leo-leads = solo pruebas internas con Listen for test event.
```

No usar ngrok para clientes reales.

---

## 11. Probar lead desde landing

* [ ] Ir al formulario.
* [ ] Rellenar datos.
* [ ] Enviar diagnóstico.
* [ ] Confirmar mensaje visual de envío correcto.
* [ ] Confirmar que n8n recibe el lead.
* [ ] Confirmar que no se rompe Demo Hugo.
* [ ] Confirmar que no se rompe Demo Vera.

---

## 12. Leo WF1 — Recepción y clasificación

Checklist:

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

## 13. Validar lead CALIENTE

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

## 14. Validar lead TIBIO

* [ ] Clasificación = TIBIO.
* [ ] Ruta Leo = seguimiento_suave.
* [ ] No envía Telegram urgente.
* [ ] No crea Gmail automático de respuesta urgente.
* [ ] Queda registrado en Airtable.
* [ ] Queda preparado para seguimiento suave.
* [ ] Estado comercial no se confunde con contactar_hoy.
* [ ] No activa flujo de aviso caliente.

---

## 15. Validar lead FRIO

* [ ] Clasificación = FRIO.
* [ ] Ruta Leo = nutricion.
* [ ] Estado respuesta = no_prioritaria.
* [ ] No envía Telegram urgente.
* [ ] No crea Gmail automático.
* [ ] No activa seguimiento inmediato.
* [ ] Queda guardado en Airtable.
* [ ] Puede revisarse manualmente si se desea.

---

## 16. Leo WF2 — Avisos Telegram

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

## 17. Leo WF3 — Borradores Gmail

Filtro esperado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "si", {Respuesta preparada} = "no")
```

Checklist:

* [ ] Search records encuentra leads correctos.
* [ ] Preparar email Leo genera asunto claro.
* [ ] Preparar email Leo genera cuerpo comercial limpio.
* [ ] Gmail crea borrador.
* [ ] Gmail no envía correo automáticamente.
* [ ] Update record marca Respuesta preparada = si.
* [ ] Update record marca Estado respuesta = preparada.
* [ ] Update record activa Seguimiento pendiente = si.
* [ ] No duplica borradores.

---

## 18. Leo WF4 — Seguimientos

Filtro esperado:

```text
AND({Seguimiento pendiente} = "si", {Seguimiento enviado} = "no")
```

Checklist:

* [ ] Search records encuentra seguimientos pendientes.
* [ ] Preparar seguimiento Leo genera mensaje claro.
* [ ] Telegram recibe recordatorio.
* [ ] Mensaje incluye acción sugerida.
* [ ] Update record marca Seguimiento enviado = si.
* [ ] No duplica seguimientos.
* [ ] El seguimiento sigue siendo interno, no se envía al cliente.

---

## 19. Leo WF5 — Reporte diario

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

---

# HUGO — Validación funcional

## 20. Estado de Hugo

Hugo es el empleado digital de presupuestos rápidos.

Estado:

```text
Funcional y validado.
```

Workflows:

```text
WF1 — Hugo presupuestos rápidos
WF2 — Hugo recordatorio de presupuestos pendientes
WF3 — Hugo reporte de actividad
```

Regla:

```text
Hugo prepara.
El profesional revisa y decide.
```

---

## 21. Hugo WF1 — Presupuestos rápidos

Estructura validada:

```text
Disparador manual
↓
Solicitud demo Hugo
↓
Analizar solicitud Hugo
↓
Preparar presupuesto Hugo
├── Create a record Airtable
├── Crear borrador Gmail Hugo
└── Telegram Hugo Aidely
```

Checklist:

* [ ] Disparador manual funciona.
* [ ] Solicitud demo Hugo genera datos de prueba.
* [ ] Gemini analiza la solicitud.
* [ ] Preparar presupuesto Hugo genera JSON limpio.
* [ ] Airtable guarda en tabla `Hugo Presupuestos`.
* [ ] Gmail crea borrador revisable.
* [ ] Telegram Hugo avisa internamente.
* [ ] No se envía nada automáticamente al cliente.
* [ ] No usa webhook.
* [ ] No usa ngrok.
* [ ] El workflow queda en modo manual para demo interna.

---

## 22. Hugo WF1 — Campos clave generados

El nodo `Preparar presupuesto Hugo` debe generar:

* [ ] presupuesto_id
* [ ] fecha_entrada
* [ ] origen
* [ ] canal_entrada
* [ ] empleado_digital
* [ ] nombre_cliente
* [ ] teléfono
* [ ] email
* [ ] negocio_profesional
* [ ] tipo_profesional
* [ ] zona
* [ ] solicitud_original
* [ ] tipo_trabajo
* [ ] descripcion_trabajo
* [ ] urgencia
* [ ] materiales_estimados
* [ ] horas_estimadas
* [ ] rango_precio_orientativo
* [ ] datos_faltantes
* [ ] nivel_confianza
* [ ] resumen_interno
* [ ] accion_recomendada
* [ ] estado_presupuesto = borrador_preparado
* [ ] borrador_preparado = si
* [ ] borrador_enviado = no
* [ ] recordatorio_enviado = no
* [ ] reporte_incluido = no
* [ ] estado_revision = pendiente_revision
* [ ] asunto_email
* [ ] cuerpo_email
* [ ] mensaje_telegram

---

## 23. Hugo Airtable — Tabla Presupuestos

Tabla:

```text
Hugo Presupuestos
```

Campos esperados:

* [ ] Presupuesto ID
* [ ] Fecha entrada
* [ ] Empleado digital
* [ ] Origen
* [ ] Canal entrada
* [ ] Nombre cliente
* [ ] Teléfono
* [ ] Email
* [ ] Zona
* [ ] Negocio profesional
* [ ] Tipo profesional
* [ ] Solicitud original
* [ ] Tipo trabajo
* [ ] Descripción trabajo
* [ ] Urgencia
* [ ] Materiales estimados
* [ ] Horas estimadas
* [ ] Precio
* [ ] Datos faltantes
* [ ] Estado presupuesto
* [ ] Borrador preparado
* [ ] Borrador enviado
* [ ] Nivel confianza
* [ ] Resumen interno
* [ ] Acción recomendada
* [ ] Asunto email
* [ ] Cuerpo email
* [ ] Mensaje Telegram
* [ ] Recordatorio enviado
* [ ] Fecha recordatorio
* [ ] Reporte incluido
* [ ] Estado revisión

---

## 24. Hugo WF2 — Recordatorio de presupuestos pendientes

Estructura validada:

```text
Schedule Trigger
↓
Buscar presupuestos pendientes Hugo
↓
Preparar recordatorio Hugo
↓
Avisar recordatorio Hugo
↓
Marcar recordatorio Hugo
```

Filtro esperado:

```text
AND({Estado presupuesto} = "borrador_preparado", {Borrador enviado} = "no", {Recordatorio enviado} = "no", {Estado revisión} = "pendiente_revision")
```

Checklist:

* [ ] Search records encuentra presupuestos pendientes.
* [ ] No encuentra presupuestos ya recordados.
* [ ] Preparar recordatorio Hugo genera mensaje claro.
* [ ] Telegram Hugo recibe aviso.
* [ ] Mensaje incluye cliente.
* [ ] Mensaje incluye teléfono.
* [ ] Mensaje incluye email.
* [ ] Mensaje incluye trabajo.
* [ ] Mensaje incluye precio pendiente de revisión.
* [ ] Mensaje incluye acción recomendada.
* [ ] Airtable marca Recordatorio enviado = si.
* [ ] Airtable guarda Fecha recordatorio.
* [ ] No duplica recordatorios.

---

## 25. Hugo WF3 — Reporte de actividad

Estructura validada:

```text
Disparador reporte Hugo
↓
Buscar presupuestos del día Hugo
↓
Crear reporte Hugo
↓
Enviar reporte Hugo
```

Filtro esperado:

```text
IS_SAME({Fecha entrada}, TODAY(), 'day')
```

Checklist:

* [ ] Search records encuentra presupuestos del día.
* [ ] Crear reporte Hugo cuenta presupuestos revisados.
* [ ] Cuenta borradores preparados.
* [ ] Cuenta marcados como enviados.
* [ ] Cuenta pendientes de revisión.
* [ ] Cuenta recordatorios enviados.
* [ ] Cuenta pendientes de datos.
* [ ] Cuenta revisados.
* [ ] Cuenta descartados.
* [ ] Detecta registros sin estado de revisión.
* [ ] Lista presupuestos preparados.
* [ ] Lista pendientes de revisión.
* [ ] Telegram Hugo envía reporte.
* [ ] El reporte se entiende.
* [ ] No usa Gemini.
* [ ] No gasta tokens de IA.

---

## 26. Seguridad y límites de Hugo

Hugo no debe:

* [ ] Enviar presupuestos automáticamente.
* [ ] Confirmar precios finales.
* [ ] Confirmar disponibilidad.
* [ ] Cerrar ventas.
* [ ] Emitir facturas.
* [ ] Cobrar.
* [ ] Borrar registros.
* [ ] Trabajar con datos sensibles.
* [ ] Usar ngrok para clientes reales.

Hugo sí puede:

* [ ] Preparar borradores.
* [ ] Guardar registros.
* [ ] Avisar internamente.
* [ ] Recordar pendientes.
* [ ] Generar reportes.
* [ ] Ayudar a responder más rápido.

---

## 27. Validación en Vercel

Después de cada cambio en landing:

* [ ] Hacer commit.
* [ ] Hacer push.
* [ ] Esperar despliegue Vercel.
* [ ] Abrir landing pública.
* [ ] Validar hero.
* [ ] Validar Demo Hugo.
* [ ] Validar Demo Vera.
* [ ] Validar formulario.
* [ ] Validar diseño móvil si es posible.
* [ ] Confirmar que no hay errores visibles.

---

## 28. Checklist Git

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

## 29. Documentación relacionada

Archivos principales:

```text
docs/README-AIDELY-LEO.md
docs/checklist-demo-aidely-leo.md
docs/hugo-presupuestos-rapidos.md
docs/estrategia-aidely-negocios-pequenos.md
docs/Aidely_Leo_MVP_Documentacion_v1.md
```

Checklist:

* [ ] README actualizado.
* [ ] Checklist actualizado.
* [ ] Documento Hugo actualizado.
* [ ] Documento estrategia actualizado.
* [ ] PDF actualizado si corresponde.
* [ ] NotebookLM actualizado si corresponde.

---

## 30. Cierre de jornada

Antes de cerrar:

* [ ] Git limpio.
* [ ] Vercel validado.
* [ ] n8n workflows guardados.
* [ ] No dejar ejecuciones innecesarias activas.
* [ ] No gastar Gemini sin necesidad.
* [ ] Si hay webhooks locales, revisar ngrok.
* [ ] Apuntar próximo paso.

Estado ideal:

```text
Leo funcional.
Hugo funcional.
Vera visual.
Landing validada.
Documentación actualizada.
GitHub y Vercel al día.
```
