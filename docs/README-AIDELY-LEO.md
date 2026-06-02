# README - Aidely + Leo MVP

## 1. Estado general del proyecto

Aidely es un proyecto de empleados digitales para pequeñas pymes.

El primer empleado digital funcional es **Leo**, un agente de atención y ventas diseñado para recibir leads desde una landing web, clasificarlos con inteligencia artificial, guardarlos automáticamente en un CRM y activar acciones comerciales posteriores.

Actualmente Aidely cuenta con:

* Landing web funcional.
* Landing publicada en Vercel.
* Repositorio conectado a GitHub.
* Formulario de diagnóstico conectado a n8n mediante webhook.
* Airtable funcionando como CRM.
* Gemini funcionando como motor de clasificación.
* Telegram funcionando para avisos internos.
* Gmail funcionando para creación de borradores comerciales.
* WF1, WF2, WF3, WF4 y WF5 publicados en n8n.
* Prueba general completa validada.
* Sistema automático funcionando de extremo a extremo.
* Próximo bloque estratégico definido: demo interactiva dentro de la landing.

La versión actual se considera:

```text
MVP funcional de Aidely + Leo con pipeline comercial automático validado
```

---

## 2. Objetivo de Aidely

Aidely busca ayudar a pequeñas pymes que pierden oportunidades comerciales por:

* Responder tarde.
* No registrar bien los contactos.
* No priorizar leads importantes.
* No hacer seguimiento.
* No tener CRM.
* Depender demasiado de tareas manuales.
* No saber qué contactos requieren atención inmediata.
* No tener claridad diaria de lo que ocurre en su actividad comercial.

La propuesta de Aidely es instalar **empleados digitales** que trabajen en segundo plano para automatizar tareas repetitivas y mejorar la gestión comercial.

---

## 3. Quién es Leo

Leo es el primer empleado digital de Aidely.

Rol:

```text
Agente digital de atención y ventas
```

Funciones principales:

* Recibir leads desde la landing web.
* Leer los datos del formulario.
* Preparar el lead para análisis.
* Clasificar el lead con IA.
* Guardar el resultado en Airtable.
* Diferenciar entre CALIENTE, TIBIO, FRIO y REVISAR.
* Asignar ruta comercial.
* Calcular score.
* Definir si requiere aviso.
* Definir si requiere borrador.
* Definir si requiere seguimiento.
* Enviar aviso interno cuando hay una oportunidad caliente.
* Preparar borradores comerciales revisables.
* Activar seguimiento comercial.
* Generar reporte diario de actividad.

---

## 4. Estado actual validado

Aidely ya funciona en modo producción local controlada con landing pública.

Estado validado:

* WF1 está publicado / activo en n8n.
* WF2 está publicado / activo en n8n.
* WF3 está publicado / activo en n8n.
* WF4 está publicado / activo en n8n.
* WF5 está publicado / activo en n8n.
* La landing usa `/webhook/leo-leads`.
* Ya no es necesario pulsar “Listen for test event”.
* El formulario de diagnóstico envía leads reales desde la landing.
* Los datos llegan correctamente al Webhook de WF1.
* Airtable recibe nombre, email, teléfono, empresa, mensaje y origen.
* Origen queda registrado como `Landing Aidely`.
* Las rutas CALIENTE, TIBIO y FRIO han sido validadas desde la landing.
* Telegram recibe avisos correctamente.
* Gmail crea borradores correctamente.
* Airtable actualiza estados correctamente.
* Los filtros devuelven 0 después de procesar.
* No se producen duplicados.

Estado actual de workflows:

```text
WF1 — Publicado / activo
WF2 — Publicado / activo
WF3 — Publicado / activo
WF4 — Publicado / activo
WF5 — Publicado / activo
```

---

## 5. Landing pública en Vercel validada

La landing de Aidely está publicada en Vercel y funciona correctamente como demo pública.

Estado validado:

* El proyecto está subido a GitHub.
* Vercel está conectado al repositorio.
* La landing pública carga correctamente.
* El formulario público de diagnóstico funciona desde Vercel.
* El formulario envía datos a través de ngrok hacia n8n local.
* WF1 está activo / publicado.
* El lead entra correctamente en Airtable.
* Se han realizado pruebas públicas desde Vercel hasta Airtable.

Flujo validado:

```text
Vercel público
↓
Formulario Aidely
↓
ngrok
↓
n8n local
↓
WF1 activo
↓
Airtable
```

Nota importante:

Para que el formulario público funcione, deben estar activos:

```text
n8n local
ngrok
WF1 publicado / activo
```

Si n8n o ngrok están cerrados, la landing seguirá viéndose, pero el formulario no podrá enviar leads a Leo.

---

## 6. Estructura recomendada del proyecto

Carpeta principal:

```text
C:\Users\zaphi\Documents\proyectos-aidely\landing-aidely
```

Estructura recomendada:

```text
landing-aidely
│
├── index.html
├── index-antiguo.html
├── index.html copy.html
├── index-aidely-leo-v1.html
├── index-aidely-form-v1.html
├── index-aidely-leo-form-n8n-v1.html
├── index-aidely-production-local-v1.html
│
├── docs
│   ├── README-AIDELY-LEO.md
│   ├── checklist-demo-aidely-leo.md
│   └── Aidely_Leo_MVP_Documentacion_v1.md
│
├── evidencias-aidely-leo
│
└── Aidely_Leo_MVP_Documentacion_v1.pdf
```

---

## 7. Archivos importantes

### Archivo principal para Vercel

```text
index.html
```

Este es el archivo que Vercel usa para publicar la landing.

### Copia estable de producción local

```text
index-aidely-production-local-v1.html
```

Representa:

```text
Landing + Leo + formulario + webhook production local funcionando
```

### README técnico

```text
docs/README-AIDELY-LEO.md
```

Este archivo documenta el estado actual del proyecto Aidely + Leo.

### Checklist de demo

```text
docs/checklist-demo-aidely-leo.md
```

Documento auxiliar para preparar pruebas y demostraciones.

---

## 8. GitHub

Repositorio conectado:

```text
https://github.com/crishdzvalencia-beep/aidely-landing.git
```

Rama principal:

```text
main
```

Comprobar estado de Git:

```bash
git status
```

Comprobar cambios:

```bash
git diff
```

Comprobar repositorio remoto:

```bash
git remote -v
```

Para futuros cambios:

```bash
git add .
git commit -m "descripcion del cambio"
git push
```

---

## 9. Vercel

El proyecto está desplegado en Vercel desde el repositorio de GitHub.

Configuración usada:

```text
Framework Preset: Other
Root Directory: ./
Build Command: vacío
Output Directory: vacío
Install Command: vacío
```

La landing funciona como sitio estático HTML.

Importante:

Vercel sirve la parte visual de Aidely, pero el motor de automatización sigue dependiendo de:

```text
n8n local
ngrok
WF1 activo
```

---

## 10. n8n local

n8n es el motor de automatización de Aidely.

URL local habitual:

```text
http://localhost:5678
```

Workflows actuales:

```text
WF1 — Leo clasificador
WF2 — Leo avisos inteligentes
WF3 — Leo respuesta comercial
WF4 — Leo seguimiento comercial
WF5 — Leo reporte de actividad
```

Estado actual:

```text
WF1 — Publicado / activo
WF2 — Publicado / activo
WF3 — Publicado / activo
WF4 — Publicado / activo
WF5 — Publicado / activo
```

---

## 11. ngrok

ngrok expone n8n local mediante una URL pública temporal.

Comando para arrancar ngrok:

```bash
ngrok http 5678
```

Webhook production local usado actualmente:

```text
/webhook/leo-leads
```

Si la URL de ngrok cambia, hay que actualizar el HTML.

---

## 12. Webhook actual

Antes se usaba modo test:

```text
/webhook-test/leo-leads
```

Ahora se usa modo production local:

```text
/webhook/leo-leads
```

Esto significa:

```text
No hace falta pulsar “Listen for test event”.
WF1 debe estar activo / publicado.
```

La URL completa se define en el JavaScript del archivo `index.html`.

---

## 13. Dónde se cambia la URL del webhook

La URL del webhook se cambia al final del archivo HTML, en el bloque de JavaScript.

Buscar:

```javascript
const WEBHOOK_URL
```

Ejemplo:

```javascript
const WEBHOOK_URL = "https://TU-URL-DE-NGROK.ngrok-free.dev/webhook/leo-leads";
```

Si cambia la URL de ngrok:

1. Cambiar la URL en `WEBHOOK_URL`.
2. Guardar el archivo.
3. Probar en local.
4. Hacer commit.
5. Hacer push a GitHub.
6. Esperar a que Vercel redespliegue.

Comandos:

```bash
git add index.html
git commit -m "Actualizar URL de webhook de Aidely"
git push
```

---

## 14. Landing web

La landing actual incluye:

* Hero principal.
* Problemas de la pyme.
* Sección de Leo.
* Catálogo de empleados digitales.
* Métricas visuales de Leo.
* Rutas inteligentes: CALIENTE, TIBIO y FRIO.
* Explicación de cómo funciona Aidely.
* Precios orientativos.
* Casos de uso.
* Sección “Qué hace Leo cuando recibe tu solicitud”.
* Formulario de diagnóstico.
* CTA final.
* Footer.

Botones principales funcionando:

```text
Solicitar diagnóstico → formulario
Solicitar diagnóstico gratuito → formulario
Solicitar instalación de Leo → formulario
Ver cómo trabaja Leo → sección Leo
Empleados → catálogo de empleados
Cómo funciona → sección correspondiente
Precios → sección precios
Casos de uso → sección sectores
```

Mejoras visuales recientes:

* Sección de precios optimizada.
* Responsive mejorado.
* Menú Empleados corregido.
* Espaciado vertical compactado en secciones largas.
* Diseño más estable en pantalla al 100%.

---

## 15. Formulario de diagnóstico

El formulario recoge:

* Nombre.
* Empresa.
* Email.
* Teléfono.
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

* El formulario se ve correctamente.
* Captura datos correctamente.
* Muestra feedback visual.
* Envía datos a n8n mediante ngrok.
* WF1 recibe el lead.
* Airtable guarda los datos.

---

## 16. Script actual del formulario

El formulario usa JavaScript para enviar los datos al webhook.

La línea clave es:

```javascript
const WEBHOOK_URL = "https://TU-URL-DE-NGROK.ngrok-free.dev/webhook/leo-leads";
```

El envío se hace con:

```javascript
fetch(WEBHOOK_URL, {
  method: 'POST',
  body: new URLSearchParams(leadData)
});
```

Se usa `URLSearchParams` para evitar problemas de CORS y para que n8n reciba correctamente los datos dentro de `$json.body`.

---

## 17. WF1 — Leo clasificador

WF1 es el workflow principal de entrada.

Función:

```text
Recibir lead desde la landing
↓
Preparar datos
↓
Clasificar con Gemini
↓
Normalizar resultado
↓
Guardar en Airtable
```

Estructura:

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
Activo / publicado
Validado en producción local
Validado desde Vercel
Validado en prueba general WF1-WF5
```

---

## 18. Nodo “Preparar lead”

El nodo “Preparar lead” debe leer datos tanto si vienen directos como si vienen dentro de `$json.body`.

Línea clave:

```javascript
const input = $json.body || $json || {};
```

Esto corrige el problema donde el Webhook recibía bien los datos, pero el Code no pasaba nombre, email, teléfono o empresa.

Campos que debe conservar:

* nombre
* email
* telefono
* empresa
* sector
* mensaje
* urgencia
* presupuesto
* origen
* empleado_interesado

Origen esperado:

```text
Landing Aidely
```

---

## 19. Nodo “Preparar resultado final Leo”

Este nodo toma la respuesta de Gemini, recupera los datos originales y prepara el registro final para Airtable.

Debe conservar:

* nombre
* empresa
* email
* teléfono
* origen
* clasificación
* prioridad
* ruta Leo
* score Leo
* estado comercial
* seguimiento pendiente
* respuesta preparada
* estado respuesta

El origen debe llegar como:

```text
Landing Aidely
```

---

## 20. Airtable como CRM

Airtable guarda el resultado de cada lead.

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

## 21. Reglas de clasificación

### CALIENTE

Ruta:

```text
accion_urgente
```

Resultado esperado:

```text
Estado comercial = contactar_hoy
Requiere aviso = si
Requiere borrador = si
Aviso enviado = no
Respuesta preparada = no
Seguimiento pendiente = no
Seguimiento enviado = no
Cadencia seguimiento = 24h
Origen = Landing Aidely
```

Acciones automáticas:

* Aviso por Telegram mediante WF2.
* Borrador Gmail mediante WF3.
* Seguimiento mediante WF4.
* Inclusión en reporte mediante WF5.

---

### TIBIO

Ruta:

```text
seguimiento_suave
```

Resultado esperado:

```text
Estado comercial = hacer_seguimiento
Requiere aviso = no
Requiere borrador = opcional
Seguimiento pendiente = si
Cadencia seguimiento = 3dias
Origen = Landing Aidely
```

---

### FRIO

Ruta:

```text
nutricion
```

Resultado esperado:

```text
Estado comercial = nutrir_lead
Requiere aviso = no
Requiere borrador = no
Seguimiento pendiente = no
Estado respuesta = no_prioritaria
Origen = Landing Aidely
```

---

### REVISAR

Ruta:

```text
revision_manual
```

Resultado esperado:

```text
Guardar en Airtable
Marcar para revisión manual
Evitar acciones automáticas
```

---

## 22. Rutas validadas desde la landing

Se validaron desde la landing usando `/webhook/leo-leads` y WF1 activo.

Estado:

```text
CALIENTE → accion_urgente / contactar_hoy → OK
TIBIO → seguimiento_suave → OK
FRIO → nutricion / no_prioritaria → OK
```

---

## 23. WF2 — Leo avisos inteligentes

Función:

```text
Buscar leads CALIENTES pendientes de aviso
↓
Preparar aviso Leo
↓
Enviar aviso por Telegram
↓
Actualizar Airtable
```

Estructura:

```text
Schedule
↓
Search records
↓
Preparar aviso Leo
↓
Send a text message
↓
Update record
```

Estado:

```text
Activo / publicado
Validado individualmente
Validado en prueba general
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

## 24. WF3 — Leo respuesta comercial

Función:

```text
Buscar leads calientes ya avisados
↓
Preparar email comercial
↓
Crear borrador Gmail
↓
Actualizar Airtable
```

Estructura:

```text
Schedule
↓
Search records
↓
Preparar email Leo
↓
Crear borrador Gmail
↓
Marcar respuesta preparada
```

Estado:

```text
Activo / publicado
Validado individualmente
Validado en prueba general
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

Punto importante:

El email fue corregido para que sea un email externo limpio para el cliente.

Ya no incluye:

```text
Resumen de tu caso
El lead tiene...
Motivo IA
Próximo paso recomendado
Contactar inmediatamente...
```

El email ahora queda orientado al cliente y las notas internas se mantienen separadas en Airtable.

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

## 25. WF4 — Leo seguimiento comercial

Función:

```text
Buscar leads con respuesta preparada y seguimiento pendiente
↓
Preparar recordatorio Leo
↓
Enviar recordatorio por Telegram
↓
Actualizar Airtable
```

Estructura:

```text
Schedule Trigger
↓
Search records
↓
Preparar seguimiento Leo
↓
Send a text message
↓
Update record
```

Estado:

```text
Activo / publicado
Validado individualmente
Validado en prueba general
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

Mejora aplicada:

Se corrigió el formato de `Estado comercial` para que en Telegram no aparezca `contactarhoy`, sino `contactar hoy`.

Validación:

* Envía Telegram correctamente.
* Actualiza Airtable correctamente.
* Search devuelve 0 después de procesar.
* No duplica seguimientos.

Frecuencia recomendada:

```text
Cada 15-30 minutos
```

---

## 26. WF5 — Leo reporte de actividad

Función:

```text
Buscar leads del día
↓
Crear reporte diario
↓
Enviar reporte por Telegram
```

Estructura:

```text
Disparador diario
↓
Search records
↓
Crear reporte Leo
↓
Send a text message
```

Estado:

```text
Activo / publicado
Validado individualmente
Validado en prueba general
```

Filtro validado:

```text
IS_SAME({Fecha entrada}, TODAY(), 'day')
```

Resultado esperado:

* Total de leads del día.
* Calientes.
* Tibios.
* Fríos.
* Revisar.
* Avisos enviados.
* Borradores preparados.
* Seguimientos enviados.
* Seguimientos pendientes sin avisar.
* Leads calientes destacados.
* Estado general del sistema.

Mejora aplicada:

El reporte fue corregido para diferenciar:

```text
Seguimientos enviados
Seguimientos pendientes sin avisar
```

Antes podía parecer que había seguimientos pendientes aunque ya hubieran sido enviados. Ahora el reporte es coherente.

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

## 27. Prueba general WF1-WF5

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

## 28. Cómo probar en local

1. Abrir n8n local.
2. Abrir la landing con Live Server.
3. Ejecutar ngrok:

```bash
ngrok http 5678
```

4. Confirmar que la URL HTTPS de ngrok coincide con `WEBHOOK_URL`.
5. Confirmar que WF1 está activo.
6. No pulsar “Listen for test event”.
7. Rellenar formulario en la landing local.
8. Enviar diagnóstico.
9. Revisar que WF1 se ejecuta automáticamente.
10. Revisar Airtable.
11. Esperar a que WF2, WF3 y WF4 actúen según sus intervalos.
12. Ejecutar o esperar WF5 según horario.

---

## 29. Cómo probar desde Vercel

Antes de compartir la landing:

1. Abrir n8n local.
2. Ejecutar:

```bash
ngrok http 5678
```

3. Confirmar que WF1-WF5 están activos si se quiere probar el flujo completo.
4. Confirmar que la URL configurada en el HTML publicado sigue funcionando.
5. Abrir la URL pública de Vercel.
6. Rellenar formulario.
7. Enviar diagnóstico.
8. Revisar Airtable.
9. Revisar Telegram.
10. Revisar Gmail/Borradores.
11. Revisar reporte si corresponde.

Importante:

La landing de Vercel funciona visualmente siempre, pero el formulario solo funcionará si están activos:

```text
n8n local
ngrok
WF1 activo
```

Para que el flujo completo funcione, deben estar activos:

```text
WF1
WF2
WF3
WF4
WF5
```

---

## 30. Cómo compartir la demo con otra persona

Antes de compartir el enlace:

* Encender n8n.
* Encender ngrok.
* Confirmar que WF1-WF5 están activos si se quiere mostrar el flujo completo.
* Confirmar que el webhook de la landing apunta a la URL correcta.
* Abrir Airtable.
* Abrir Telegram.
* Abrir Gmail.
* Enviar el enlace de Vercel.

Mensaje sugerido:

```text
Te comparto una demo pública de Aidely, el proyecto que estoy construyendo.

Es una landing con Leo, un empleado digital de atención y ventas para pequeñas pymes. Puedes probar el formulario con datos ficticios de una clínica, gimnasio o negocio pequeño.

Cuando envíes el formulario, Leo recibe el lead, lo clasifica, lo guarda en el CRM, avisa si es una oportunidad caliente, prepara un borrador comercial y lo incluye en el reporte diario.
```

---

## 31. Prueba simbólica validada

Se realizó una prueba desde la landing pública de Vercel usando el nombre:

```text
Gloria
```

La prueba fue importante a nivel personal y técnico.

Resultado:

```text
Formulario Vercel → ngrok → n8n local → WF1 → Airtable
```

Estado:

```text
Validado correctamente
```

---

## 32. Problemas conocidos

### Formulario llega al Webhook, pero se pierden datos en Code

Revisar que el nodo “Preparar lead” empiece con:

```javascript
const input = $json.body || $json || {};
```

### Airtable no muestra campos nuevos

Hacer refresh del nodo Airtable en n8n.

### Telegram añade texto automático de n8n

Desactivar:

```text
Append n8n Attribution
```

### Telegram muestra mal textos con guion bajo

Ejemplo:

```text
contactar_hoy → contactarhoy
```

Solución:

Convertir textos visibles para Telegram:

```javascript
.replace(/_/g, " ")
```

### Gmail da error de token

Si Gmail muestra error de autorización o refresh token:

1. Abrir credencial Gmail en n8n.
2. Reconectar cuenta.
3. Guardar credencial.
4. Volver a ejecutar nodo de borrador.

### La landing pública abre, pero el formulario no envía

Revisar:

* n8n local abierto.
* ngrok activo.
* WF1 activo.
* URL correcta en `WEBHOOK_URL`.
* Uso de `/webhook/leo-leads`.
* No usar `/webhook-test/leo-leads`.

### Cambia la URL de ngrok

Actualizar `WEBHOOK_URL`, guardar, hacer commit y push.

---

## 33. Limitaciones actuales

La demo actual es funcional, pero no es producción final.

Limitaciones:

* n8n sigue funcionando en local.
* ngrok actúa como túnel temporal.
* No hay backend estable permanente.
* No hay login.
* No hay panel privado real.
* No hay multiempresa.
* No hay gestión completa de usuarios.
* No hay RGPD completo implementado.
* No hay seguridad avanzada del webhook.
* Las métricas de la landing son estáticas.
* El formulario público depende de que el ordenador esté encendido con n8n y ngrok.
* El sistema actual trabaja para Aidely, no todavía dentro del entorno real de cada cliente.
* Para clientes reales será necesario definir instalación asistida, cuenta técnica o conexión segura mediante permisos.

---

## 34. Nueva prioridad estratégica: demo interactiva en la landing

La próxima mejora principal será crear una demo interactiva dentro de la propia landing.

Objetivo:

```text
Demostrar cómo trabaja un empleado digital sin pedir claves,
sin conectar cuentas reales y sin usar datos del cliente.
```

Demo propuesta:

```text
Vera — control de stock y pedidos
```

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

## 35. Instalación para clientes reales

Para clientes poco técnicos, Aidely debe ofrecer una instalación asistida.

Opciones:

### 1. Demo sin tocar datos reales

Primero se muestra una demo con datos ficticios.

### 2. Plantilla creada por Aidely

Aidely puede entregar una plantilla sencilla de stock, leads, clientes o tareas.

### 3. Carga inicial asistida

Aidely puede ayudar a cargar los primeros productos, clientes o datos.

### 4. Cuenta técnica

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

### 5. Sesión guiada

El cliente comparte pantalla y autoriza permisos desde su propia cuenta.

Aidely guía el proceso, pero no recibe contraseñas.

Frase comercial clave:

```text
No necesitas saber usar Sheets, n8n ni automatizaciones.
Aidely te instala el empleado digital y tú solo revisas el resultado.
```

---

## 36. Futuras mejoras

Próximas mejoras posibles:

* Crear demo interactiva Vera dentro de la landing.
* Crear sección “Ver demo en directo”.
* Crear panel privado de Leo.
* Conectar métricas reales desde Airtable.
* Preparar producción real sin ngrok.
* Publicar n8n en servidor estable.
* Añadir seguridad al webhook.
* Añadir aviso legal y política de privacidad.
* Preparar sistema multiempresa.
* Crear documentación comercial.
* Crear vídeo demo.
* Preparar presentación para socios o clientes.
* Crear empleados digitales adicionales:

  * Vera — stock y operaciones.
  * Bruno — documentos y presupuestos.
  * Nora — datos y CRM.
  * Alma — recuperación y seguimiento.

---

## 37. Nota final

Aidely ya no es solo una idea.

Actualmente existe:

```text
Landing pública en Vercel
↓
Formulario real
↓
ngrok
↓
n8n local
↓
WF1 clasifica
↓
Airtable guarda
↓
WF2 avisa
↓
WF3 crea borrador
↓
WF4 recuerda seguimiento
↓
WF5 reporta actividad
```

Este README documenta la versión actual del MVP de Aidely + Leo.

La prioridad ahora es mantener el sistema ordenado, seguro y controlado, y construir la demo interactiva de Vera para demostrar a clientes cómo trabaja un empleado digital sin necesidad de pedir contraseñas ni conectar datos reales.
