# AIDELY + LEO

## Documentación del MVP funcional v1

---

## 1. Resumen ejecutivo

Aidely es una solución de empleados digitales para pequeñas pymes. Su objetivo es ayudar a negocios que pierden oportunidades por responder tarde, no registrar correctamente sus contactos o no hacer seguimiento comercial.

Leo es el primer empleado digital funcional de Aidely. Está especializado en atención y ventas. Recibe leads desde una landing web, los clasifica con inteligencia artificial, los guarda en un CRM, avisa cuando detecta oportunidades importantes, prepara respuestas comerciales y permite generar reportes de actividad.

El MVP actual ya funciona de extremo a extremo en entorno local:

```text
Landing Aidely
↓
Formulario diagnóstico
↓
ngrok
↓
Webhook production de n8n
↓
WF1 activo
↓
Leo clasifica el lead
↓
Airtable CRM
```

Actualmente se ha decidido mantener solo WF1 activo en producción local controlada. WF2, WF3, WF4 y WF5 quedan desactivados temporalmente para evitar avisos, borradores o seguimientos automáticos no deseados durante la fase de demo controlada.

---

## 2. Objetivo del proyecto

El objetivo del proyecto es crear una demo funcional de Aidely donde una pyme pueda rellenar un formulario de diagnóstico y activar automáticamente a Leo.

Leo debe demostrar que un empleado digital puede:

* Captar leads desde una página web.
* Clasificar contactos según intención comercial.
* Guardar información en un CRM.
* Diferenciar leads CALIENTES, TIBIOS y FRIOS.
* Preparar la ruta comercial adecuada para cada caso.
* Servir como primer empleado digital vendible dentro de Aidely.

---

## 3. Problema que resuelve

Muchas pequeñas pymes pierden oportunidades porque:

* Responden tarde a clientes interesados.
* No registran todos los contactos.
* No priorizan leads importantes.
* No hacen seguimiento.
* Dependen demasiado de tareas manuales.
* No tienen un CRM ordenado.
* No saben qué oportunidades son urgentes.
* No tienen visibilidad clara de qué contactos requieren acción inmediata.

Aidely propone resolver esto mediante empleados digitales sencillos, configurados para trabajar en segundo plano.

---

## 4. Solución creada

La solución actual se centra en Leo, un agente digital de atención y ventas.

Leo trabaja con la siguiente lógica:

1. Recibe un lead desde la landing.
2. Limpia y prepara los datos.
3. Envía el caso a Gemini para clasificación.
4. Clasifica el lead como CALIENTE, TIBIO, FRIO o REVISAR.
5. Calcula ruta comercial.
6. Calcula score.
7. Define si requiere aviso.
8. Define si requiere borrador.
9. Define si requiere seguimiento.
10. Guarda el registro en Airtable.

En esta fase, la acción automática activa es WF1. Los flujos posteriores ya existen y han sido validados, pero se mantienen desactivados por seguridad.

---

## 5. Arquitectura general

### 5.1 Landing web local

La landing está creada como una página HTML local.

Archivo principal de trabajo:

```text
index.html copy.html
```

Versiones estables recomendadas:

```text
index-aidely-leo-v1.html
index-aidely-form-v1.html
index-aidely-leo-form-n8n-v1.html
index-aidely-production-local-v1.html
```

La versión más importante actualmente es:

```text
index-aidely-production-local-v1.html
```

Representa:

```text
Landing + Leo + formulario + webhook production local funcionando
```

---

### 5.2 n8n local

n8n actúa como motor de automatización. Recibe los leads, ejecuta la lógica de Leo y conecta con Airtable, Telegram y Gmail.

Actualmente:

```text
WF1 — Activo / publicado
WF2 — Desactivado
WF3 — Desactivado
WF4 — Desactivado
WF5 — Desactivado
```

---

### 5.3 ngrok

ngrok expone n8n local mediante una URL pública temporal.

Comando:

```bash
ngrok http 5678
```

URL usada en la última prueba:

```text
https://vexingly-paltry-sesame.ngrok-free.dev
```

Webhook production usado por la landing:

```text
https://vexingly-paltry-sesame.ngrok-free.dev/webhook/leo-leads
```

---

### 5.4 Airtable

Airtable funciona como CRM de leads.

Guarda:

* Datos del contacto.
* Clasificación.
* Ruta Leo.
* Score Leo.
* Estado comercial.
* Avisos.
* Respuestas.
* Seguimientos.
* Origen del lead.

---

### 5.5 Gemini

Gemini analiza el mensaje del lead y devuelve una clasificación estructurada.

La respuesta de Gemini se normaliza en el nodo:

```text
Preparar resultado final Leo
```

---

### 5.6 Telegram

Telegram se usa en los workflows posteriores para:

* Avisar leads calientes.
* Enviar recordatorios de seguimiento.
* Enviar reportes de actividad.

Actualmente los workflows que usan Telegram están desactivados para mantener la demo controlada.

---

### 5.7 Gmail

Gmail se usa para crear borradores comerciales preparados por Leo.

Actualmente WF3 está desactivado para evitar creación automática de borradores durante la fase de control.

---

## 6. Landing web de Aidely

La landing actual ya incluye:

* Hero principal.
* Problemas de la pyme.
* Sección de Leo.
* Rutas inteligentes: CALIENTE, TIBIO y FRIO.
* Explicación de cómo funciona Aidely.
* Precios orientativos.
* Casos de uso.
* Formulario de diagnóstico.
* CTA final.

Botones principales funcionando:

* “Solicitar diagnóstico” → formulario.
* “Solicitar diagnóstico gratuito” → formulario.
* “Solicitar instalación de Leo” → formulario.
* “Ver cómo trabaja Leo” → sección Leo.
* “Empleados” → sección Leo.
* “Cómo funciona” → sección correspondiente.
* “Precios” → sección precios.
* “Casos de uso” → sección sectores.

---

## 7. Formulario de diagnóstico

El formulario de diagnóstico recoge:

* Nombre.
* Email.
* Teléfono.
* Empresa.
* Sector.
* Urgencia.
* Presupuesto aproximado.
* Mensaje.
* Empleado interesado: Leo.
* Origen: Landing Aidely.

Estado validado:

* El formulario se ve correctamente en la landing.
* Captura los datos en navegador.
* Muestra confirmación visual.
* Envía los datos al webhook production de n8n mediante ngrok.
* El webhook recibe correctamente los datos.
* El nodo “Preparar lead” lee correctamente datos dentro de `$json.body`.
* Los datos llegan correctamente a Airtable.
* El origen queda registrado como `Landing Aidely`.

---

## 8. Producción local validada

Se ha validado que Aidely funciona en producción local con WF1 activo.

Antes la landing enviaba datos a:

```text
/webhook-test/leo-leads
```

Ahora envía datos a:

```text
/webhook/leo-leads
```

Esto permite que el formulario funcione sin pulsar:

```text
Listen for test event
```

Estado actual:

```text
WF1 — Activo / publicado
WF2 — Desactivado
WF3 — Desactivado
WF4 — Desactivado
WF5 — Desactivado
```

Decisión tomada:

Mantener solo WF1 activo para controlar la demo y evitar acciones automáticas no deseadas mientras se sigue preparando Aidely.

---

## 9. Workflows de n8n

### 9.1 WF1 — Leo clasificador

Función:

Recibe leads, prepara datos, los clasifica con Gemini y los guarda en Airtable.

Flujo:

```text
Webhook production
↓
Preparar lead
↓
Gemini
↓
Preparar resultado final Leo
↓
Airtable Create Record
```

Estado:

```text
Activo y validado en producción local
```

Notas importantes:

El nodo “Preparar lead” debe empezar con:

```javascript
const input = $json.body || $json || {};
```

Esto permite leer datos tanto si vienen directos como si vienen dentro de `$json.body`.

---

### 9.2 WF2 — Leo avisos inteligentes

Función:

Busca leads CALIENTES que aún no han sido avisados y envía un aviso por Telegram.

Flujo:

```text
Schedule Trigger
↓
Airtable Search Records
↓
Preparar aviso Leo
↓
Telegram
↓
Airtable Update Record
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar avisos automáticos durante la fase de producción local controlada.

---

### 9.3 WF3 — Leo respuesta comercial

Función:

Busca leads calientes avisados y prepara un borrador de respuesta comercial en Gmail.

Flujo:

```text
Schedule Trigger
↓
Airtable Search Records
↓
Preparar email Leo
↓
Gmail Create Draft
↓
Airtable Update Record
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar creación automática de borradores durante la demo controlada.

---

### 9.4 WF4 — Leo seguimiento comercial

Función:

Busca leads con seguimiento pendiente y envía recordatorio por Telegram.

Flujo:

```text
Schedule Trigger
↓
Airtable Search Records
↓
Preparar seguimiento Leo
↓
Telegram
↓
Airtable Update Record
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar seguimientos automáticos hasta revisar filtros finales.

---

### 9.5 WF5 — Leo reporte de actividad

Función:

Crea un reporte diario de actividad de Leo y lo envía por Telegram.

Flujo:

```text
Schedule Trigger 09:00
↓
Airtable Search Records
↓
Crear reporte Leo
↓
Telegram
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar reportes automáticos durante esta fase. Puede ejecutarse manualmente cuando se quiera revisar actividad.

---

## 10. Airtable como CRM

Airtable guarda la información de cada lead.

Campos principales:

* Lead ID.
* Fecha entrada.
* Nombre.
* Email.
* Teléfono.
* Empresa.
* Sector.
* Empleado interesado.
* Mensaje.
* Urgencia.
* Presupuesto.
* Origen.
* Clasificación.
* Prioridad.
* Motivo.
* Próxima acción.
* Mensaje sugerido.
* Estado comercial.
* Ruta Leo.
* Score Leo.
* Requiere aviso.
* Requiere borrador.
* Aviso enviado.
* Respuesta preparada.
* Estado respuesta.
* Seguimiento pendiente.
* Seguimiento enviado.
* Cadencia seguimiento.
* Nota seguimiento.
* Fecha aviso.
* Fecha respuesta preparada.
* Fecha seguimiento.

---

## 11. Lógica de clasificación

Leo clasifica leads en cuatro categorías:

---

### 11.1 CALIENTE

Lead con alta intención comercial.

Ruta:

```text
accion_urgente
```

Resultado esperado:

* Estado comercial: `contactar_hoy`.
* Requiere aviso: `si`.
* Requiere borrador: `si`.
* Cadencia seguimiento: `24h`.
* Origen: `Landing Aidely`.

Estado:

```text
Validado desde la landing en producción local
```

---

### 11.2 TIBIO

Lead con interés, pero sin urgencia clara.

Ruta:

```text
seguimiento_suave
```

Resultado esperado:

* Estado comercial: `hacer_seguimiento`.
* Requiere aviso: `no`.
* Requiere borrador: `opcional`.
* Seguimiento pendiente: `si`.
* Cadencia seguimiento: `3dias`.
* Origen: `Landing Aidely`.

Estado:

```text
Validado desde la landing en producción local
```

---

### 11.3 FRIO

Lead sin intención clara o sin presupuesto.

Ruta:

```text
nutricion
```

Resultado esperado:

* Estado comercial: `nutrir_lead`.
* Requiere aviso: `no`.
* Requiere borrador: `no`.
* Seguimiento pendiente: `no`.
* Estado respuesta: `no_prioritaria`.
* Origen: `Landing Aidely`.

Estado:

```text
Validado desde la landing en producción local
```

---

### 11.4 REVISAR

Lead ambiguo o con datos insuficientes.

Ruta:

```text
revision_manual
```

Resultado esperado:

* Guardar en Airtable.
* Marcar para revisión manual.
* Evitar acciones automáticas.

---

## 12. Estado actual validado

Actualmente está validado:

* Landing local funcionando.
* Sección Leo integrada.
* Formulario visible.
* Botones conectados.
* Captura de datos en consola.
* Envío del formulario a n8n mediante ngrok.
* Webhook production recibe datos.
* WF1 activo / publicado.
* No hace falta pulsar “Listen for test event”.
* Preparar lead lee correctamente `$json.body`.
* Datos personales llegan bien.
* Origen = Landing Aidely.
* Airtable guarda correctamente.
* CALIENTE validado.
* TIBIO validado.
* FRIO validado.
* WF2 validado anteriormente, pero desactivado.
* WF3 validado anteriormente, pero desactivado.
* WF4 validado anteriormente, pero desactivado.
* WF5 validado anteriormente, pero desactivado.

---

## 13. Cómo probar la demo actual

Para probar la demo actual en producción local controlada:

1. Abrir n8n local.
2. Abrir la landing con Live Server.
3. Ejecutar ngrok:

```bash
ngrok http 5678
```

4. Copiar la URL HTTPS de ngrok.
5. Revisar en el HTML que `WEBHOOK_URL` tenga la URL correcta:

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

6. Abrir WF1 en n8n.
7. Confirmar que WF1 está activo / publicado.
8. No pulsar “Listen for test event”.
9. Rellenar el formulario de la landing.
10. Enviar diagnóstico.
11. Revisar que WF1 recibe el lead automáticamente.
12. Revisar Airtable.
13. Ejecutar manualmente WF2, WF3, WF4 o WF5 si se quiere probar la cadena completa.

---

## 14. Limitaciones actuales

El MVP actual funciona en entorno local y con ngrok.

Limitaciones:

* La URL de ngrok puede cambiar si se reinicia.
* Todavía no está publicado en Vercel o Netlify.
* No existe login de usuarios.
* No hay panel privado real.
* Las métricas de la landing son estáticas.
* Solo WF1 está activo de forma automática.
* WF2, WF3, WF4 y WF5 están desactivados temporalmente.
* No hay todavía gestión legal/RGPD completa.
* No hay sistema de multiempresa.
* No hay dashboard dinámico conectado a Airtable.
* No hay backend estable público.
* No hay seguridad avanzada del webhook.

---

## 15. Próximos pasos

Próximos pasos recomendados:

1. Mantener WF1 activo como producción local controlada.
2. Revisar filtros de WF2 antes de activarlo.
3. Activar WF2 cuando se quiera probar avisos automáticos.
4. Revisar filtros de WF3 antes de activarlo.
5. Activar WF3 cuando se quiera probar borradores automáticos.
6. Revisar filtros de WF4 antes de activarlo.
7. Activar WF4 cuando se quiera probar seguimientos automáticos.
8. Activar WF5 cuando se quiera reporte diario automático.
9. Preparar capturas de evidencia.
10. Preparar demo guiada.
11. Preparar publicación futura en Vercel o Netlify.
12. Revisar RGPD, privacidad y seguridad.
13. Diseñar futura pantalla de panel de Leo.
14. Pensar en multiempresa.
15. Preparar propuesta comercial para pymes.

---

## 16. Conclusión

Aidely ya cuenta con un MVP funcional de Leo, su primer empleado digital.

Leo no es solo una idea visual. Ya existe un flujo real donde una landing captura datos, los envía a n8n mediante webhook production local, clasifica leads con IA y guarda la información en Airtable.

En esta fase se mantiene activo solo WF1 para controlar la demo y evitar automatizaciones no deseadas. Los workflows WF2, WF3, WF4 y WF5 ya han sido validados anteriormente, pero se mantienen desactivados hasta decidir cuándo activar la automatización completa.

Este MVP demuestra que Aidely puede convertirse en una solución real para pequeñas pymes que necesitan responder más rápido, ordenar sus contactos y no perder oportunidades comerciales.
