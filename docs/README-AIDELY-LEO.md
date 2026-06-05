# README — Aidely + Leo

## Aidely — empleados digitales para autónomos y pequeños negocios

Aidely es un proyecto de empleados digitales sencillos para autónomos, microempresas y pequeños negocios.

El objetivo no es crear una plataforma corporativa compleja ni competir con grandes sistemas empresariales. Aidely está pensado para ayudar a negocios reales y cercanos que necesitan más orden, más rapidez y menos tareas repetitivas, pero que no tienen tiempo, equipo administrativo ni conocimientos técnicos para montar automatizaciones por su cuenta.

Aidely quiere ayudar a negocios como:

* peluquerías,
* centros de estética,
* fontaneros,
* electricistas,
* pintores,
* reformistas,
* técnicos de mantenimiento,
* taxistas,
* entrenadores personales,
* academias pequeñas,
* freelancers,
* talleres pequeños,
* comercios de barrio,
* cafeterías,
* pequeños restaurantes,
* autónomos de servicios.

La propuesta principal es:

> Empleados digitales sencillos para autónomos y pequeños negocios.

Aidely no vende tecnología por vender tecnología. Aidely vende ayuda práctica instalada, configurada y mantenida para resolver problemas concretos del día a día.

---

## 1. Estado actual del proyecto

Aidely ya cuenta con un primer empleado digital funcional:

## Leo — atención y ventas

Leo es el primer empleado digital validado de Aidely.

Está especializado en atención comercial, captación, clasificación de interesados y seguimiento.

Leo ya puede:

* recibir solicitudes desde una landing,
* leer los datos del formulario,
* preparar el lead,
* clasificarlo con IA,
* guardar el resultado en Airtable,
* avisar oportunidades importantes por Telegram,
* crear borradores comerciales revisables en Gmail,
* recordar seguimientos pendientes,
* generar reportes diarios de actividad.

Leo ya está validado de extremo a extremo mediante los workflows WF1-WF5 en n8n.

---

## 2. Flujo general validado

El flujo actual funciona así:

```text
Landing pública
↓
Formulario de diagnóstico
↓
Webhook n8n
↓
WF1 recibe y clasifica leads
↓
Airtable guarda el lead
↓
WF2 avisa leads calientes por Telegram
↓
WF3 crea borradores Gmail revisables
↓
WF4 recuerda seguimientos pendientes
↓
WF5 genera reporte diario comercial
```

---

## 3. Workflows actuales

### WF1 — Leo recibe y clasifica leads

Objetivo:

```text
Recibir leads desde la landing, prepararlos, clasificarlos con IA y guardarlos en Airtable.
```

Funciones principales:

* Recibe datos desde formulario web.
* Lee nombre, email, teléfono, empresa, sector, urgencia, presupuesto y mensaje.
* Prepara el lead.
* Envía el caso a Gemini.
* Clasifica como CALIENTE, TIBIO, FRIO o REVISAR.
* Define ruta comercial.
* Guarda el registro en Airtable.

Rutas principales:

```text
CALIENTE → accion_urgente
TIBIO → seguimiento_suave
FRIO → nutricion / no_prioritaria
```

---

### WF2 — Leo avisa oportunidades calientes

Objetivo:

```text
Detectar leads calientes pendientes de aviso y enviar alerta interna por Telegram.
```

Filtro usado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "no")
```

Flujo:

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

Resultado:

* Envía aviso interno por Telegram.
* Marca `Aviso enviado = si`.
* Evita duplicados.

---

### WF3 — Leo prepara borradores comerciales

Objetivo:

```text
Crear borradores Gmail revisables para leads calientes ya avisados.
```

Filtro usado:

```text
AND({Clasificación} = "CALIENTE", {Estado comercial} = "contactar_hoy", {Aviso enviado} = "si", {Respuesta preparada} = "no")
```

Flujo:

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

Resultado:

* Crea borrador Gmail.
* No envía el correo automáticamente.
* Marca `Respuesta preparada = si`.
* Marca `Estado respuesta = preparada`.
* Activa seguimiento pendiente.

Regla principal:

```text
Leo prepara.
El responsable humano revisa y decide.
```

---

### WF4 — Leo recuerda seguimientos pendientes

Objetivo:

```text
Avisar internamente cuando hay seguimientos pendientes sin enviar.
```

Filtro usado:

```text
AND({Seguimiento pendiente} = "si", {Seguimiento enviado} = "no")
```

Flujo:

```text
Schedule
↓
Search records
↓
Preparar seguimiento Leo
↓
Send a text message
↓
Update record
```

Resultado:

* Envía recordatorio interno por Telegram.
* Marca `Seguimiento enviado = si`.
* Evita duplicados.

---

### WF5 — Leo genera reporte diario

Objetivo:

```text
Generar reporte diario de actividad comercial.
```

Filtro usado:

```text
IS_SAME({Fecha entrada}, TODAY(), 'day')
```

Flujo:

```text
Schedule diario
↓
Search records
↓
Crear reporte Leo
↓
Send a text message
```

Reporte incluye:

* leads revisados,
* leads calientes,
* leads tibios,
* leads fríos,
* avisos enviados,
* borradores preparados,
* seguimientos enviados,
* seguimientos pendientes,
* estado general.

---

## 4. Demo Vera

Aidely también cuenta con una demo interactiva llamada Vera.

## Vera — demo de reposición simple

Vera existe como demo interactiva publicada en la landing.

Usa datos ficticios para mostrar cómo un empleado digital puede revisar una tabla de productos, detectar artículos bajo mínimo y preparar una lista de reposición.

Vera no debe presentarse como control exacto de inventario ni como producto conectado a datos reales todavía.

Vera debe entenderse como:

> Demo de lista simple de reposición para revisar.

La demo Vera demuestra:

* cómo se vería otro tipo de empleado digital,
* cómo se pueden revisar datos simples,
* cómo se puede generar un reporte,
* cómo se puede preparar un borrador de pedido,
* cómo se puede enseñar valor sin pedir contraseñas ni conectar datos reales.

Regla de Vera:

```text
Vera no decide por el dueño.
Vera prepara una lista para revisar.
```

---

## 5. Próximo empleado recomendado

## Hugo — presupuestos rápidos

El siguiente empleado recomendado es Hugo.

Hugo estará enfocado en presupuestos rápidos para oficios y pequeños servicios.

Cliente ideal:

* fontaneros,
* electricistas,
* pintores,
* reformistas,
* técnicos,
* autónomos de mantenimiento,
* pequeños servicios locales.

Problema que resuelve:

```text
El profesional pierde trabajos porque tarda en preparar presupuestos o los deja para la noche.
```

Idea inicial de flujo:

```text
Audio o formulario
↓
Extracción de datos del trabajo
↓
Cliente, trabajo, materiales, horas, notas
↓
Plantilla de presupuesto
↓
Borrador revisable
↓
Aviso interno
```

Hugo no debe enviar presupuestos automáticamente.

Hugo debe preparar un borrador para que el autónomo lo revise antes de enviarlo.

Prioridad:

```text
Alta. Próximo empleado recomendado.
```

---

## 6. Principios de Aidely

Aidely debe trabajar bajo estos principios:

* Datos mínimos.
* Procesos sencillos.
* Acciones revisables.
* Borradores antes que envíos automáticos.
* Avisos internos antes que decisiones autónomas.
* Precio accesible.
* Instalación guiada.
* Mantenimiento claro.
* Nada de promesas corporativas exageradas.
* Nada de automatizaciones irreversibles en fase inicial.

La regla principal es:

> Aidely prepara, ordena y avisa.
> El dueño revisa y decide.

---

## 7. Lo que Aidely sí hace

Aidely puede:

* crear borradores de email,
* preparar mensajes revisables,
* enviar avisos internos,
* clasificar solicitudes,
* guardar contactos en tablas simples,
* leer formularios,
* organizar datos básicos,
* crear reportes sencillos,
* generar presupuestos preliminares,
* recordar citas,
* detectar clientes dormidos,
* preparar listas simples de tareas o reposición.

---

## 8. Lo que Aidely no debe hacer al inicio

Aidely no debe prometer:

* automatización total sin supervisión,
* gestión completa del negocio,
* decisiones autónomas irreversibles,
* envío automático de presupuestos sin revisión,
* compras automáticas a proveedores,
* borrado automático de datos,
* facturación fiscal real sin contrato y validación,
* tratamiento de datos médicos,
* tratamiento de nóminas,
* gestión de datos sensibles,
* integración con cualquier sistema sin analizarlo,
* garantía 24/7 en fase inicial.

Aidely no debe decir:

```text
La IA lo hace todo.
```

Debe decir:

```text
El empleado digital prepara el trabajo y tú mantienes el control.
```

---

## 9. Datos permitidos en la fase inicial

Aidely puede trabajar con datos simples como:

* nombre,
* teléfono,
* email,
* tipo de solicitud,
* fecha,
* hora,
* servicio interesado,
* mensaje del cliente,
* estado del seguimiento,
* nota interna sencilla,
* producto básico,
* cantidad aproximada,
* proveedor básico,
* presupuesto preliminar,
* datos de contacto comercial.

Estos datos deben usarse solo para la finalidad acordada con el cliente.

---

## 10. Datos fuera de alcance inicial

Aidely no debe trabajar al inicio con:

* DNI,
* datos bancarios,
* datos médicos,
* historiales clínicos,
* nóminas,
* contratos laborales,
* expedientes legales,
* facturas fiscales reales complejas,
* datos de menores,
* información especialmente sensible,
* automatizaciones de pago,
* devoluciones automáticas,
* pedidos automáticos irreversibles.

Si un caso requiere estos datos, debe tratarse como una fase futura con más seguridad, documentación, contrato y revisión legal.

---

## 11. Infraestructura por fases

### Fase 1 — Demo y validación

Permitido:

* n8n local,
* ngrok,
* Vercel,
* Airtable,
* Google Sheets,
* Gmail,
* Telegram,
* datos ficticios,
* pruebas internas,
* demostraciones controladas.

No permitido:

* clientes reales dependiendo de ngrok,
* prometer servicio estable,
* usar datos sensibles,
* dejar procesos críticos funcionando desde el ordenador personal.

---

### Fase 2 — Primeros pilotos reales

Para pilotos reales, Aidely debe usar una infraestructura más estable.

Recomendado:

* n8n Cloud o Make,
* cuentas separadas por cliente,
* Google Sheets o Airtable separado por cliente,
* Gmail del cliente o cuenta técnica,
* Telegram para avisos internos,
* borradores revisables,
* documentación básica del flujo,
* límites claros de alcance,
* consentimiento y política de privacidad cuando corresponda.

No usar:

* ngrok como infraestructura de cliente,
* automatizaciones irreversibles,
* bases mezcladas entre varios clientes,
* WhatsApp no oficial,
* datos sensibles.

---

### Fase 3 — Madurez futura

Cuando Aidely tenga clientes, ingresos y necesidad real de escalar, se valorará:

* n8n en VPS,
* dominio propio,
* HTTPS estable,
* logs,
* backups,
* monitorización,
* Supabase o Postgres,
* separación avanzada por cliente,
* contratos de tratamiento de datos,
* política RGPD completa,
* WhatsApp Business API oficial,
* procesos de soporte.

Esta fase es una madurez interna del producto. No debe comunicarse al cliente inicial con lenguaje complejo.

---

## 12. Diferenciación frente a ChatGPT Agents

ChatGPT Agents, GPTs y herramientas de IA pueden hacer muchas tareas.

Pero muchos autónomos y pequeños negocios no quieren:

* aprender a crear agentes,
* configurar conectores,
* tocar permisos,
* diseñar prompts,
* revisar logs,
* mantener automatizaciones,
* decidir qué herramienta usar,
* solucionar errores,
* investigar tutoriales,
* aprender n8n o Make.

Aidely no compite diciendo que tiene una IA mejor.

Aidely se diferencia porque diseña, instala, configura y mantiene empleados digitales concretos para pequeños negocios que no quieren aprender herramientas, prompts, conectores, APIs ni automatizaciones.

Frase clave:

> ChatGPT te da la herramienta.
> Aidely te deja el proceso funcionando.

Otra frase importante:

> Puedes hacerlo tú mismo si tienes tiempo, ganas y conocimientos.
> Aidely existe para quien quiere que alguien se lo deje funcionando de forma clara, sencilla y revisable.

---

## 13. Herramientas actuales

### VS Code

Editor principal del proyecto.

Uso:

* editar landing,
* editar documentación,
* revisar archivos,
* controlar versiones con Git,
* mantener README, checklist y documentos estratégicos.

---

### GitHub

Repositorio del proyecto.

Uso:

* control de versiones,
* historial de cambios,
* sincronización con Vercel,
* respaldo del código y documentación.

---

### Vercel

Hosting de la landing pública.

Uso:

* publicar la página,
* desplegar cambios desde GitHub,
* validar visualmente la landing.

---

### n8n

Motor de automatización actual.

Uso:

* recibir leads,
* ejecutar workflows,
* conectar Airtable, Gemini, Telegram y Gmail,
* crear lógica de Leo.

Estado actual:

```text
n8n local válido para demo y validación.
No usar ngrok para clientes reales.
```

---

### ngrok

Túnel temporal usado para exponer n8n local.

Uso actual:

* pruebas,
* validación,
* demo controlada.

Limitación:

```text
No apto para producción ni clientes reales.
```

---

### Airtable

CRM actual de Leo.

Uso:

* guardar leads,
* almacenar clasificación,
* estado comercial,
* avisos,
* respuestas,
* seguimientos,
* reportes.

Limitación:

```text
Válido para MVP y piloto controlado.
Para escalado multiempresa se valorará otra arquitectura.
```

---

### Gemini

IA usada para clasificación.

Uso:

* clasificar leads,
* analizar intención,
* decidir ruta comercial,
* generar motivo IA y próxima acción.

---

### Telegram

Canal interno de avisos.

Uso:

* avisos de leads calientes,
* recordatorios de seguimiento,
* reportes diarios.

---

### Gmail

Canal de borradores revisables.

Uso:

* crear borradores comerciales,
* evitar envíos automáticos,
* mantener control humano.

---

## 14. Campos principales en Airtable

Campos usados por Leo:

* Lead ID
* Nombre
* Email
* Teléfono
* Empresa
* Sector
* Mensaje
* Urgencia
* Presupuesto
* Origen
* Fecha entrada
* Clasificación
* Score Leo
* Motivo IA
* Próxima acción
* Ruta Leo
* Estado comercial
* Requiere aviso
* Aviso enviado
* Requiere borrador
* Respuesta preparada
* Estado respuesta
* Seguimiento pendiente
* Seguimiento enviado
* Cadencia seguimiento
* Procesado por
* Herramienta IA

---

## 15. Estados principales

### Clasificación

```text
CALIENTE
TIBIO
FRIO
REVISAR
```

### Ruta Leo

```text
accion_urgente
seguimiento_suave
nutricion
revisar_manual
```

### Estado comercial

```text
contactar_hoy
seguimiento_suave
no_prioritaria
revisar
```

### Aviso enviado

```text
si
no
```

### Respuesta preparada

```text
si
no
```

### Seguimiento pendiente

```text
si
no
```

### Seguimiento enviado

```text
si
no
```

---

## 16. Validaciones realizadas

### Validación WF1

Comprobado:

* formulario envía datos,
* webhook recibe,
* n8n procesa,
* Gemini clasifica,
* Airtable guarda,
* rutas comerciales funcionan.

---

### Validación CALIENTE

Comprobado:

* Clasificación = CALIENTE.
* Ruta Leo = accion_urgente.
* Requiere aviso = si.
* Requiere borrador = si.
* WF2 envía Telegram.
* WF3 crea Gmail draft.
* WF4 gestiona seguimiento.
* WF5 reporta actividad.

---

### Validación TIBIO

Comprobado:

* Clasificación = TIBIO.
* Ruta Leo = seguimiento_suave.
* No Telegram urgente.
* No Gmail automático.
* Seguimiento suave preparado.

---

### Validación FRIO

Comprobado:

* Clasificación = FRIO.
* Ruta Leo = nutricion.
* Estado respuesta = no_prioritaria.
* No Telegram.
* No Gmail.
* No seguimiento inmediato.

---

### Validación WF5

Comprobado:

* reporte diario se genera,
* Telegram recibe reporte,
* métricas se calculan,
* seguimientos enviados y pendientes se diferencian correctamente.

---

### Validación Demo Vera

Comprobado en Vercel:

* enlace Demo visible,
* sección Vera visible,
* botón “Probar a Vera” funciona,
* reporte simulado aparece,
* borrador simulado aparece,
* formulario de diagnóstico sigue intacto.

---

## 17. Landing

Archivo principal:

```text
index.html
```

La landing incluye:

* hero principal,
* secciones de problema,
* empleados digitales,
* Leo,
* precios,
* casos de uso,
* Demo Vera,
* formulario de diagnóstico,
* scripts del formulario,
* script de Demo Vera.

Reglas:

* No tocar `WEBHOOK_URL` sin revisar.
* No tocar el formulario real sin prueba.
* No mezclar Demo Vera con webhook real.
* No conectar Vera a datos reales todavía.
* Mantener toda demo simulada aislada del formulario.

---

## 18. Checklist de demo

Archivo relacionado:

```text
docs/checklist-demo-aidely-leo.md
```

Uso:

* preparar entorno,
* arrancar n8n,
* arrancar ngrok,
* validar WF1-WF5,
* probar lead caliente,
* probar lead tibio,
* probar lead frío,
* validar reporte,
* validar Demo Vera,
* confirmar Git limpio.

---

## 19. Guion comercial

Archivo relacionado:

```text
docs/guion-demo-aidely.md
```

Uso:

* presentar Aidely en 5-7 minutos,
* explicar problema,
* mostrar Leo,
* mostrar Vera,
* explicar seguridad,
* diferenciar demo de producto validado,
* cerrar con diagnóstico.

---

## 20. Documento estratégico actualizado

Archivo relacionado:

```text
docs/estrategia-aidely-negocios-pequenos.md
```

Uso:

* definir el nuevo enfoque,
* reposicionar Aidely hacia autónomos y pequeños negocios,
* ordenar lo permitido y fuera de alcance,
* definir próximos empleados,
* preparar camino hacia Hugo.

---

## 21. Pricing inicial recomendado

Aidely debe cobrar siempre.

No se recomienda regalar instalaciones completas, porque el trabajo tiene valor y el cliente debe comprometerse.

Modelo inicial recomendado:

```text
Diagnóstico inicial: gratuito o precio simbólico.
Piloto de 30 días: desde 49€.
Instalación básica: 99€ - 149€.
Mensualidad por empleado digital sencillo: 49€ - 79€/mes.
Pack de 2 empleados: 99€ - 129€/mes.
```

Regla:

```text
Precio accesible, pero nunca gratis.
```

El piloto puede tener una promesa simple:

```text
Probamos durante 30 días.
Si no te ayuda, lo apagamos.
Si te ayuda, lo mantenemos con una mensualidad clara.
```

---

## 22. Mensaje comercial recomendado

Aidely debe hablar claro.

No decir:

```text
Automatizaciones inteligentes con IA y workflows conectados.
```

Decir:

```text
Te ayudamos a ordenar clientes, citas, presupuestos y tareas con empleados digitales sencillos que trabajan para ti.
```

No decir:

```text
Integramos n8n, webhooks, CRMs y APIs.
```

Decir:

```text
Tú nos dices qué tarea te quita tiempo. Nosotros te dejamos un sistema funcionando para que lo revises desde tu correo o tu móvil.
```

Frase principal propuesta:

```text
Empleados digitales sencillos para autónomos y pequeños negocios.
```

Subfrase:

```text
Ordena solicitudes, prepara presupuestos, recuerda citas y no pierdas clientes por falta de tiempo.
```

---

## 23. Comandos útiles

### Revisar estado Git

```bash
git status
```

### Ver cambios resumidos

```bash
git diff --stat
```

### Ver cambios en index.html

```bash
git diff -- index.html
```

### Añadir archivo concreto

```bash
git add docs/README-AIDELY-LEO.md
```

### Commit

```bash
git commit -m "Actualiza README con estrategia Aidely para pequenos negocios"
```

### Push

```bash
git push
```

### Estado final esperado

```text
nothing to commit, working tree clean
```

---

## 24. Comandos habituales de entorno

### Entrar al proyecto

```bash
cd C:\Users\zaphi\Documents\proyectos-aidely\landing-aidely
```

### Arrancar ngrok para pruebas

```bash
ngrok http 5678
```

### URL del webhook en HTML

```javascript
const WEBHOOK_URL = "https://TU-URL.ngrok-free.dev/webhook/leo-leads";
```

Recordatorio:

```text
Usar /webhook/leo-leads para producción local controlada.
No usar /webhook-test/leo-leads salvo pruebas internas.
```

---

## 25. Próximos pasos

### Bloque 1 — Estrategia

Estado:

```text
Completado.
```

Documento:

```text
docs/estrategia-aidely-negocios-pequenos.md
```

---

### Bloque 2 — Documentación

Pendiente actualizar:

* README-AIDELY-LEO.md.
* checklist-demo-aidely-leo.md.
* Aidely_Leo_MVP_Documentacion_v1.md.
* PDF de documentación si corresponde.
* NotebookLM con el nuevo enfoque.

---

### Bloque 3 — Landing

Revisar si debe actualizarse:

* hero principal,
* subtítulo,
* sección de empleados,
* Demo Vera,
* precios,
* formulario,
* guion comercial.

Objetivo:

```text
Aclarar que Aidely sirve para autónomos, microempresas y pequeños negocios.
```

---

### Bloque 4 — Hugo

Crear documento:

```text
docs/hugo-presupuestos-rapidos.md
```

Incluir:

* objetivo,
* cliente ideal,
* problema,
* datos mínimos,
* flujo,
* herramientas,
* riesgos,
* mitigaciones,
* versión demo,
* versión piloto,
* mensajes,
* formato de presupuesto,
* validación.

---

### Bloque 5 — Demo Hugo

Crear primero una demo controlada.

Pendiente:

* definir si empieza con formulario o audio,
* diseñar plantilla de presupuesto,
* crear datos ficticios,
* crear flujo de prueba,
* generar borrador revisable,
* validar que no envía nada automáticamente.

---

### Bloque 6 — Infraestructura para piloto

Antes de cliente real:

* decidir n8n Cloud, Make o VPS,
* evitar ngrok para cliente real,
* separar datos por cliente,
* definir consentimiento básico,
* crear documento de alcance,
* crear checklist de instalación.

---

### Bloque 7 — Validación comercial

Pendiente:

* hablar con 3 oficios,
* hablar con 3 peluquerías/estética,
* preguntar por presupuestos, citas, clientes perdidos y tareas repetitivas,
* no vender en la primera conversación,
* registrar respuestas,
* elegir primer piloto pagado.

---

## 26. Decisión final

Aidely debe continuar.

Pero debe continuar con un enfoque más claro:

```text
No grandes sistemas.
No promesas corporativas.
No datos sensibles al inicio.
No automatizaciones irreversibles.

Sí a empleados digitales sencillos.
Sí a autónomos y pequeños negocios.
Sí a borradores revisables.
Sí a pilotos pagados.
Sí a procesos concretos.
Sí a precio accesible.
```

El siguiente movimiento recomendado es:

```text
1. Actualizar documentación.
2. Actualizar landing si corresponde.
3. Diseñar Hugo.
4. Crear demo Hugo.
5. Validar con negocios reales.
```
