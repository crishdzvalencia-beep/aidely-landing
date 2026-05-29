# README - Aidely + Leo MVP

## 1. Estado general del proyecto

Aidely es un proyecto de empleados digitales para pequeñas pymes.

El primer empleado digital funcional es **Leo**, un agente de atención y ventas diseñado para recibir leads desde una landing web, clasificarlos con inteligencia artificial y guardarlos automáticamente en un CRM.

Actualmente Aidely cuenta con:

* Landing web funcional.
* Sección visual de Leo integrada.
* Formulario de diagnóstico.
* Conexión real con n8n mediante webhook.
* WF1 activo en modo producción local.
* Airtable funcionando como CRM.
* GitHub configurado.
* Vercel publicado y validado.
* Prueba pública realizada desde Vercel hasta Airtable.
* Workflows WF2, WF3, WF4 y WF5 construidos y validados previamente, pero desactivados actualmente por seguridad.

La versión actual se considera:

```text
MVP funcional en producción local controlada + landing pública en Vercel
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
* Dejar el lead listo para que otros workflows actúen.

---

## 4. Estado actual validado

### Producción local validada

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

Estado actual de workflows:

```text
WF1 — Activo
WF2 — Desactivado
WF3 — Desactivado
WF4 — Desactivado
WF5 — Desactivado
```

Motivo:

De momento dejamos solo WF1 activo para mantener una demo controlada. WF2, WF3, WF4 y WF5 se ejecutarán manualmente hasta validar cuándo conviene activar el comportamiento automático completo.

---

## 5. Landing pública en Vercel validada

La landing de Aidely ya está publicada en Vercel y funciona correctamente como demo pública.

Estado validado:

* El proyecto está subido a GitHub.
* Vercel está conectado al repositorio.
* La landing pública carga correctamente.
* El formulario público de diagnóstico funciona desde Vercel.
* El formulario envía datos a través de ngrok hacia n8n local.
* WF1 está activo / publicado.
* El lead entra correctamente en Airtable.
* Se realizó una prueba simbólica con el nombre Gloria.
* El lead de prueba entró correctamente en Airtable.

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

### Archivo de trabajo local anterior

```text
index.html copy.html
```

Fue el archivo principal durante el desarrollo local.

### Copia estable de producción local

```text
index-aidely-production-local-v1.html
```

Representa:

```text
Landing + Leo + formulario + webhook production local funcionando
```

### Documentación principal

```text
docs/Aidely_Leo_MVP_Documentacion_v1.md
```

### README técnico

```text
docs/README-AIDELY-LEO.md
```

### Checklist de demo

```text
docs/checklist-demo-aidely-leo.md
```

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

Comandos usados para subir la versión actual:

```bash
git add .
git commit -m "MVP Aidely Leo en produccion local"
git push -u origin main
```

Para futuros cambios:

```bash
git add .
git commit -m "descripcion del cambio"
git push
```

Comprobar estado de Git:

```bash
git status
```

Comprobar repositorio remoto:

```bash
git remote -v
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

Actualmente el workflow activo es:

```text
WF1 — Leo clasificador
```

Los demás workflows están desactivados por decisión de seguridad:

```text
WF2 — Desactivado
WF3 — Desactivado
WF4 — Desactivado
WF5 — Desactivado
```

---

## 11. ngrok

ngrok expone n8n local mediante una URL pública temporal.

Comando para arrancar ngrok:

```bash
ngrok http 5678
```

URL usada en la última prueba:

```text
https://vexingly-paltry-sesame.ngrok-free.dev
```

Webhook production local usado actualmente:

```text
https://vexingly-paltry-sesame.ngrok-free.dev/webhook/leo-leads
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

URL actual completa:

```javascript
const WEBHOOK_URL = "https://vexingly-paltry-sesame.ngrok-free.dev/webhook/leo-leads";
```

---

## 13. Dónde se cambia la URL del webhook

La URL del webhook se cambia al final del archivo HTML, en el bloque de JavaScript.

Buscar:

```javascript
const WEBHOOK_URL
```

Ejemplo:

```javascript
const WEBHOOK_URL = "https://vexingly-paltry-sesame.ngrok-free.dev/webhook/leo-leads";
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
git add .
git commit -m "Actualizar URL de webhook de Aidely"
git push
```

---

## 14. Landing web

La landing actual incluye:

* Hero principal.
* Problemas de la pyme.
* Sección de Leo.
* Métricas visuales de Leo.
* Rutas inteligentes: CALIENTE, TIBIO y FRIO.
* Explicación de cómo funciona Aidely.
* Precios orientativos.
* Casos de uso.
* Formulario de diagnóstico.
* CTA final.
* Footer.

Botones principales funcionando:

```text
Solicitar diagnóstico → formulario
Solicitar diagnóstico gratuito → formulario
Solicitar instalación de Leo → formulario
Ver cómo trabaja Leo → sección Leo
Empleados → sección Leo
Cómo funciona → sección correspondiente
Precios → sección precios
Casos de uso → sección sectores
```

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
const WEBHOOK_URL = "https://vexingly-paltry-sesame.ngrok-free.dev/webhook/leo-leads";
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

WF1 es el workflow principal actualmente activo.

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
Cadencia seguimiento = 24h
Origen = Landing Aidely
```

Acciones automáticas posibles:

* Aviso por Telegram mediante WF2.
* Borrador Gmail mediante WF3.
* Seguimiento mediante WF4.

Actualmente estas acciones están desactivadas porque WF2-WF5 no están activos.

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
CALIENTE → accion_urgente → OK
TIBIO → seguimiento_suave → OK
FRIO → nutricion / no_prioritaria → OK
```

---

## 23. WF2 — Leo avisos inteligentes

Función:

```text
Buscar leads CALIENTES pendientes de aviso
↓
Enviar aviso por Telegram
↓
Actualizar Airtable
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar avisos automáticos durante la fase de producción local controlada.

Condiciones recomendadas antes de activarlo:

```text
Clasificación = CALIENTE
Aviso enviado = no
Requiere aviso = si
```

---

## 24. WF3 — Leo respuesta comercial

Función:

```text
Buscar leads calientes
↓
Preparar borrador comercial
↓
Crear borrador Gmail
↓
Actualizar Airtable
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar creación automática de borradores durante la demo controlada.

Condiciones recomendadas antes de activarlo:

```text
Clasificación = CALIENTE
Aviso enviado = si
Respuesta preparada = no
Requiere borrador = si
```

---

## 25. WF4 — Leo seguimiento comercial

Función:

```text
Buscar leads con seguimiento pendiente
↓
Enviar recordatorio por Telegram
↓
Actualizar Airtable
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar seguimientos automáticos hasta revisar filtros finales.

Condiciones recomendadas antes de activarlo:

```text
Seguimiento pendiente = si
Seguimiento enviado = no
```

Al ejecutarse correctamente debería actualizar:

```text
Seguimiento enviado = si
Seguimiento pendiente = no
Fecha seguimiento = fecha actual
```

---

## 26. WF5 — Leo reporte de actividad

Función:

```text
Crear reporte diario de actividad de Leo
↓
Enviar por Telegram
```

Estado:

```text
Validado anteriormente
Desactivado actualmente
```

Motivo:

Evitar reportes automáticos durante esta fase.

Puede ejecutarse manualmente cuando se quiera revisar actividad.

Configuración validada:

```text
Schedule Trigger 09:00
Airtable Search Records
Crear reporte Leo
Telegram
```

Se desactivó la atribución automática de n8n en Telegram.

---

## 27. Cómo probar en local

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

---

## 28. Cómo probar desde Vercel

Antes de compartir la landing:

1. Abrir n8n local.
2. Ejecutar:

```bash
ngrok http 5678
```

3. Confirmar que WF1 está activo.
4. Confirmar que la URL configurada en el HTML publicado sigue funcionando.
5. Abrir la URL pública de Vercel.
6. Rellenar formulario.
7. Enviar diagnóstico.
8. Revisar Airtable.

Importante:

La landing de Vercel funciona visualmente siempre, pero el formulario solo funcionará si están activos:

```text
n8n local
ngrok
WF1 activo
```

---

## 29. Cómo compartir la demo con otra persona

Antes de compartir el enlace:

* Encender n8n.
* Encender ngrok.
* Confirmar que WF1 está activo.
* Confirmar que el webhook de la landing apunta a la URL correcta.
* Abrir Airtable.
* Enviar el enlace de Vercel.

Mensaje sugerido:

```text
Te comparto una demo pública de Aidely, el proyecto que estoy construyendo.

Es una landing con Leo, un empleado digital de atención y ventas para pequeñas pymes. Puedes probar el formulario con datos ficticios de una clínica, gimnasio o negocio pequeño.

Cuando envíes el formulario, el lead entra en mi sistema y puedo ver cómo Leo lo procesa.
```

---

## 30. Prueba simbólica validada

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

## 31. Problemas conocidos

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

## 32. Siguiente paso técnico

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
* WF2-WF5 están desactivados.
* El formulario público depende de que el ordenador esté encendido con n8n y ngrok.

---

## 34. Futuras mejoras

Próximas mejoras posibles:

* Activar WF2 de forma segura.
* Activar WF3 de forma segura.
* Activar WF4 de forma segura.
* Activar WF5 como reporte automático.
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

---

## 35. Nota final

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
WF1 activo
↓
Leo clasifica
↓
Airtable guarda el lead
```

Este README documenta la versión actual del MVP de Aidely + Leo.

La prioridad ahora es mantener el sistema ordenado, seguro y controlado antes de activar automatizaciones adicionales.
