# AIDELY + LEO

## Documentación del MVP funcional v2

---

## 1. Resumen ejecutivo

Aidely es una solución de empleados digitales para pequeñas pymes. Su objetivo es ayudar a negocios que pierden oportunidades por responder tarde, no registrar correctamente sus contactos o no hacer seguimiento comercial.

Leo es el primer empleado digital funcional de Aidely. Está especializado en atención y ventas. Recibe leads desde una landing web, los clasifica con inteligencia artificial, los guarda en un CRM, avisa cuando detecta oportunidades importantes, prepara borradores comerciales, activa seguimientos y genera reportes de actividad.

El MVP actual ya funciona de extremo a extremo en entorno local controlado:

```text
Landing Aidely
↓
Formulario diagnóstico
↓
ngrok
↓
Webhook production de n8n
↓
WF1 recibe y clasifica
↓
Airtable CRM
↓
WF2 avisa por Telegram
↓
WF3 crea borrador Gmail
↓
WF4 recuerda seguimiento
↓
WF5 genera reporte diario
```

Actualmente WF1, WF2, WF3, WF4 y WF5 están publicados y validados. La prueba general automática ha terminado correctamente y el sistema funciona sin duplicados.

---

## 2. Objetivo del proyecto

El objetivo del proyecto es crear una demo funcional de Aidely donde una pyme pueda rellenar un formulario de diagnóstico y activar automáticamente a Leo.

Leo debe demostrar que un empleado digital puede:

* Captar leads desde una página web.
* Clasificar contactos según intención comercial.
* Guardar información en un CRM.
* Diferenciar leads CALIENTES, TIBIOS, FRIOS y REVISAR.
* Preparar la ruta comercial adecuada para cada caso.
* Avisar oportunidades importantes.
* Crear borradores comerciales revisables.
* Recordar seguimientos.
* Enviar reportes de actividad.
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
* No tienen tiempo ni conocimiento técnico para montar automatizaciones.

Aidely propone resolver esto mediante empleados digitales sencillos, configurados para trabajar en segundo plano y ayudar al negocio a actuar antes, ordenar mejor y no perder oportunidades.

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
11. Si es CALIENTE, WF2 envía aviso por Telegram.
12. Si requiere respuesta, WF3 crea borrador comercial en Gmail.
13. Si queda pendiente seguimiento, WF4 envía recordatorio interno.
14. WF5 genera reporte diario de actividad.

La solución actual ya no es solo una landing visual. Es un pipeline comercial funcional.

---

## 5. Arquitectura general

### 5.1 Landing web

La landing está creada como una página HTML con Tailwind.

Archivo principal actual:

```text
index.html
```

Versiones estables y archivos históricos:

```text
index-aidely-leo-v1.html
index-aidely-form-v1.html
index-aidely-leo-form-n8n-v1.html
index-aidely-production-local-v1.html
```

La landing está publicada en Vercel y conectada al repositorio de GitHub.

---

### 5.2 n8n local

n8n actúa como motor de automatización. Recibe los leads, ejecuta la lógica de Leo y conecta con Airtable, Telegram y Gmail.

Actualmente:

```text
WF1 — Publicado / activo
WF2 — Publicado / activo
WF3 — Publicado / activo
WF4 — Publicado / activo
WF5 — Publicado / activo
```

---

### 5.3 ngrok

ngrok expone n8n local mediante una URL pública temporal.

Comando:

```bash
ngrok http 5678
```

Webhook production usado por la landing:

```text
/webhook/leo-leads
```

Ejemplo de URL completa:

```text
https://TU-URL.ngrok-free.dev/webhook/leo-leads
```

Si la URL de ngrok cambia, hay que actualizar `WEBHOOK_URL` en `index.html`.

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
* Fechas de aviso, respuesta y seguimiento.

---

### 5.5 Gemini

Gemini analiza el mensaje del lead y devuelve una clasificación estructurada.

La respuesta de Gemini se normaliza en el nodo:

```text
Preparar resultado final Leo
```

---

### 5.6 Telegram

Telegram se usa para:

* Avisar leads calientes mediante WF2.
* Enviar recordatorios de seguimiento mediante WF4.
* Enviar reportes diarios mediante WF5.

---

### 5.7 Gmail

Gmail se usa para crear borradores comerciales preparados por Leo mediante WF3.

Importante:

```text
WF3 crea borradores, no envía emails automáticamente.
```

Esto permite revisar el mensaje antes de enviarlo al cliente.

---

## 6. Landing web de Aidely

La landing actual incluye:

* Hero principal.
* Problemas de la pyme.
* Sección de Leo.
* Catálogo de empleados digitales.
* Rutas inteligentes: CALIENTE, TIBIO y FRIO.
* Explicación de cómo funciona Aidely.
* Precios orientativos.
* Casos de uso.
* Sección “Qué hace Leo cuando recibe tu solicitud”.
* Formulario de diagnóstico.
* CTA final.
* Footer.

Botones principales funcionando:

* “Solicitar diagnóstico” → formulario.
* “Solicitar diagnóstico gratuito” → formulario.
* “Solicitar instalación de Leo” → formulario.
* “Ver cómo trabaja Leo” → sección Leo.
* “Empleados” → catálogo de empleados.
* “Cómo funciona” → sección correspondiente.
* “Precios” → sección precios.
* “Casos de uso” → sección sectores.

Mejoras recientes:

* Menú Empleados corregido.
* Sección de precios optimizada.
* Espaciado vertical compactado.
* Responsive más estable.
* Sección de empleados recuperada correctamente.

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
* Empleado interesado.
* Origen.

Empleado interesado:

```text
Leo
```

Origen:

```text
Landing Aidely
```

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

Se ha validado que Aidely funciona en producción local con todos los workflows publicados.

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
WF1 — Publicado / activo
WF2 — Publicado / activo
WF3 — Publicado / activo
WF4 — Publicado / activo
WF5 — Publicado / activo
```

Conclusión:

```text
Aidely funciona como demo operativa de extremo a extremo.
```

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
Publicado, activo y validado
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

Filtro validado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "no")
```

Resultado esperado:

```text
Aviso enviado = si
Fecha aviso = fecha actual
```

Estado:

```text
Publicado, activo y validado
```

Validación:

* Envía Telegram correctamente.
* Actualiza Airtable correctamente.
* Search devuelve 0 después de procesar.
* No duplica avisos.

Frecuencia recomendada:

```text
Cada 5 minutos
```

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

Filtro validado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "si", {Respuesta preparada} = "no")
```

Resultado esperado:

```text
Respuesta preparada = si
Estado respuesta = preparada
Seguimiento pendiente = si
Seguimiento enviado = no
Fecha respuesta preparada = fecha actual
```

Estado:

```text
Publicado, activo y validado
```

Mejora importante:

El email fue corregido para que sea un email externo limpio para el cliente.

Ya no incluye:

```text
Resumen de tu caso
El lead tiene...
Motivo IA
Próximo paso recomendado
Contactar inmediatamente...
```

Validación:

* Gmail crea borradores.
* No envía emails automáticamente.
* Los borradores son revisables.
* Search devuelve 0 después de procesar.
* No duplica borradores.

Frecuencia recomendada:

```text
Cada 10 minutos
```

---

### 9.4 WF4 — Leo seguimiento comercial

Función:

Busca leads con respuesta preparada y seguimiento pendiente, y envía recordatorio interno por Telegram.

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

Filtro validado:

```text
AND({Respuesta preparada} = "si", {Seguimiento pendiente} = "si", {Seguimiento enviado} = "no")
```

Resultado esperado:

```text
Seguimiento enviado = si
Fecha seguimiento = fecha actual
Fecha próximo seguimiento = fecha actual o fecha calculada
```

Estado:

```text
Publicado, activo y validado
```

Mejora aplicada:

Se corrigió el formato de `Estado comercial` para que en Telegram no aparezca:

```text
contactarhoy
```

Y aparezca como:

```text
contactar hoy
```

Frecuencia recomendada:

```text
Cada 15-30 minutos
```

---

### 9.5 WF5 — Leo reporte de actividad

Función:

Crea un reporte diario de actividad de Leo y lo envía por Telegram.

Flujo:

```text
Schedule Trigger
↓
Airtable Search Records
↓
Crear reporte Leo
↓
Telegram
```

Filtro validado:

```text
IS_SAME({Fecha entrada}, TODAY(), 'day')
```

Estado:

```text
Publicado, activo y validado
```

El reporte incluye:

* Leads revisados hoy.
* Calientes.
* Tibios.
* Fríos.
* Revisar.
* Avisos enviados.
* Borradores preparados.
* Seguimientos enviados.
* Seguimientos pendientes sin avisar.
* Leads calientes destacados.
* Estado general.

Mejora aplicada:

El reporte fue corregido para diferenciar:

```text
Seguimientos enviados
Seguimientos pendientes sin avisar
```

También se ajustó el Score medio para mostrar:

```text
No disponible
```

cuando los scores no aportan información útil.

Horario recomendado:

```text
Todos los días a las 20:00
```

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
* Motivo IA.
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
* Fecha próximo seguimiento.
* Asunto email.

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
* Aviso enviado: `no` al crearse.
* Respuesta preparada: `no` al crearse.
* Seguimiento pendiente: `no` al crearse.
* Seguimiento enviado: `no` al crearse.
* Cadencia seguimiento: `24h`.
* Origen: `Landing Aidely`.

Acciones automáticas:

* WF2 envía aviso por Telegram.
* WF3 crea borrador Gmail.
* WF4 envía recordatorio de seguimiento.
* WF5 lo incluye en el reporte diario.

Estado:

```text
Validado desde la landing
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
Validado desde la landing
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
Validado desde la landing
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
* Landing pública en Vercel funcionando.
* GitHub conectado.
* Sección Leo integrada.
* Catálogo de empleados corregido.
* Formulario visible.
* Botones conectados.
* Envío del formulario a n8n mediante ngrok.
* Webhook production recibe datos.
* WF1 activo / publicado.
* WF2 activo / publicado.
* WF3 activo / publicado.
* WF4 activo / publicado.
* WF5 activo / publicado.
* No hace falta pulsar “Listen for test event”.
* Preparar lead lee correctamente `$json.body`.
* Datos personales llegan bien.
* Origen = Landing Aidely.
* Airtable guarda correctamente.
* CALIENTE validado.
* TIBIO validado.
* FRIO validado.
* WF2 avisa por Telegram.
* WF3 crea borradores Gmail limpios.
* WF4 recuerda seguimiento.
* WF5 genera reporte diario.
* Los filtros devuelven 0 después de procesar.
* No hay duplicados.

---

## 13. Prueba general validada

Se realizó una prueba general automática de todo el sistema.

Flujo probado:

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

Resultado:

```text
Validado correctamente
```

Comprobaciones superadas:

* WF1 recibe y guarda leads.
* WF2 detecta lead caliente y avisa.
* WF3 crea borrador Gmail limpio.
* WF4 envía recordatorio de seguimiento.
* WF5 genera un único reporte diario.
* Airtable actualiza estados.
* Los filtros devuelven 0 después de procesar.
* No hay duplicados.

Conclusión:

```text
Aidely ya tiene un pipeline comercial funcional:
landing → clasificación → aviso → borrador → seguimiento → reporte.
```

---

## 14. Cómo probar la demo actual

Para probar la demo actual en producción local controlada:

1. Abrir n8n local.
2. Abrir la landing con Live Server o Vercel.
3. Ejecutar ngrok:

```bash
ngrok http 5678
```

4. Copiar la URL HTTPS de ngrok.
5. Revisar en el HTML que `WEBHOOK_URL` tenga la URL correcta:

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

6. Confirmar que WF1-WF5 están publicados.
7. No pulsar “Listen for test event”.
8. Rellenar el formulario de la landing.
9. Enviar diagnóstico.
10. Revisar que WF1 recibe el lead automáticamente.
11. Revisar Airtable.
12. Esperar a que WF2, WF3 y WF4 actúen según sus intervalos.
13. Revisar Telegram.
14. Revisar Gmail/Borradores.
15. Revisar WF5 o esperar su horario.

---

## 15. Limitaciones actuales

El MVP actual funciona en entorno local y con ngrok.

Limitaciones:

* La URL de ngrok puede cambiar si se reinicia.
* n8n sigue funcionando en local.
* No existe backend estable permanente.
* No existe login de usuarios.
* No hay panel privado real.
* Las métricas de la landing son estáticas.
* No hay todavía gestión legal/RGPD completa.
* No hay sistema de multiempresa.
* No hay dashboard dinámico conectado a Airtable.
* No hay seguridad avanzada del webhook.
* El sistema actual trabaja para Aidely, no todavía dentro del entorno real de cada cliente.
* Para clientes reales será necesario definir instalación asistida, cuenta técnica o conexión segura mediante permisos.

---

## 16. Nueva prioridad estratégica: demo interactiva Vera

La próxima mejora principal será crear una demo interactiva dentro de la propia landing.

Nombre propuesto:

```text
Vera — control de stock y pedidos
```

Objetivo:

Demostrar cómo trabaja un empleado digital sin pedir claves, sin conectar cuentas reales y sin usar datos del cliente.

Problema que resuelve:

Muchos clientes no saben usar Sheets, no quieren crear cuentas, no quieren conectar WhatsApp, Telegram o Gmail, y necesitan ver algo funcionando antes de confiar.

La demo permitirá mostrar:

* Una tienda ficticia.
* Una tabla de stock simulada.
* Productos con stock bajo.
* Botón “Probar a Vera”.
* Análisis automático simulado.
* Reporte de stock generado.
* Pedido sugerido.
* Borrador de pedido preparado.
* CTA para solicitar una demo adaptada.

La demo será local dentro de la landing y no tocará:

* Webhook real.
* Formulario real.
* JavaScript del diagnóstico.
* n8n.
* Airtable real.
* Gmail real.
* Telegram real.

Objetivo comercial:

Responder a la objeción:

```text
¿Cómo me demuestras que funciona?
```

Respuesta futura:

```text
Te lo enseño aquí mismo con una demo interactiva. No necesito tus datos ni tus contraseñas para que veas cómo trabaja un empleado digital.
```

---

## 17. Instalación para clientes reales

Para clientes poco técnicos, Aidely debe ofrecer una instalación asistida.

Opciones:

### 17.1 Demo sin tocar datos reales

Primero se muestra una demo con datos ficticios.

### 17.2 Plantilla creada por Aidely

Aidely puede entregar una plantilla sencilla de stock, leads, clientes o tareas.

### 17.3 Carga inicial asistida

Aidely puede ayudar a cargar los primeros productos, clientes o datos.

### 17.4 Cuenta técnica

Se puede crear una cuenta tipo:

```text
automatizaciones@empresa.com
```

Esta cuenta se usa solo para el empleado digital.

Ventajas:

* No toca el correo personal del dueño.
* Se puede revocar.
* Se puede limitar.
* Todo queda separado.

### 17.5 Sesión guiada

El cliente comparte pantalla y autoriza permisos desde su propia cuenta.

Aidely guía el proceso, pero no recibe contraseñas.

Frase comercial clave:

```text
No necesitas saber usar Sheets, n8n ni automatizaciones.
Aidely te instala el empleado digital y tú solo revisas el resultado.
```

---

## 18. Próximos pasos

Próximos pasos recomendados:

1. Mantener WF1-WF5 publicados y controlados.
2. Revisar periódicamente que los filtros siguen evitando duplicados.
3. Mantener WF2 cada 5 minutos.
4. Mantener WF3 cada 10 minutos.
5. Mantener WF4 cada 15-30 minutos.
6. Mantener WF5 como reporte diario preferiblemente a las 20:00.
7. Crear demo interactiva Vera dentro de la landing.
8. Crear sección “Ver demo en directo”.
9. Preparar capturas de evidencia.
10. Preparar demo guiada para clientes.
11. Revisar RGPD, privacidad y seguridad.
12. Diseñar futura pantalla de panel de Leo.
13. Pensar en multiempresa.
14. Preparar propuesta comercial para pymes.
15. Preparar producción real sin ngrok.
16. Publicar n8n en servidor estable.

---

## 19. Conclusión

Aidely ya cuenta con un MVP funcional de Leo, su primer empleado digital.

Leo no es solo una idea visual. Ya existe un flujo real donde una landing captura datos, los envía a n8n mediante webhook production local, clasifica leads con IA, guarda la información en Airtable, avisa por Telegram, crea borradores Gmail, recuerda seguimientos y genera reportes diarios.

El sistema WF1-WF5 ya ha sido validado individualmente y en conjunto.

Este MVP demuestra que Aidely puede convertirse en una solución real para pequeñas pymes que necesitan responder más rápido, ordenar sus contactos y no perder oportunidades comerciales.

La prioridad ahora es construir una demo interactiva dentro de la landing, empezando por Vera, para demostrar a clientes cómo trabaja un empleado digital sin pedir contraseñas ni conectar datos reales.
