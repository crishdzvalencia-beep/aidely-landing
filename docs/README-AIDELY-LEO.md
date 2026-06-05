# README — Aidely

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

```text
Empleados digitales sencillos para autónomos y pequeños negocios.
```

Aidely no vende tecnología por vender tecnología. Aidely vende ayuda práctica instalada, configurada y mantenida para resolver problemas concretos del día a día.

---

## 1. Principio principal de Aidely

Aidely trabaja bajo una regla clara:

```text
Aidely prepara, ordena y avisa.
El dueño revisa y decide.
```

Esto significa que los empleados digitales de Aidely no deben tomar decisiones irreversibles ni actuar sin control humano en la fase inicial.

Aidely puede preparar:

* borradores,
* avisos internos,
* reportes,
* presupuestos preliminares,
* recordatorios,
* listas de revisión,
* seguimientos,
* registros ordenados.

Aidely no debe prometer:

* automatización total sin supervisión,
* decisiones autónomas finales,
* envío automático de presupuestos sin revisión,
* compras automáticas,
* facturación fiscal real sin validación,
* tratamiento de datos sensibles sin contrato y análisis legal,
* funcionamiento crítico 24/7 en fase inicial.

---

## 2. Estado global actualizado

Aidely cuenta actualmente con:

### Leo — atención y ventas

Estado:

```text
Funcional y validado.
```

Leo es el primer empleado digital funcional de Aidely.

Está especializado en atención comercial, captación, clasificación de interesados y seguimiento.

Leo ya puede:

* recibir solicitudes desde una landing,
* leer datos de un formulario,
* preparar el lead,
* clasificarlo con IA,
* guardarlo en Airtable,
* avisar oportunidades importantes por Telegram,
* crear borradores comerciales revisables en Gmail,
* recordar seguimientos pendientes,
* generar reportes diarios de actividad.

Workflows validados:

```text
WF1 — Recepción y clasificación de leads
WF2 — Avisos Telegram de leads calientes
WF3 — Borradores Gmail
WF4 — Seguimientos
WF5 — Reporte diario comercial
```

---

### Hugo — presupuestos rápidos

Estado:

```text
Funcional y validado.
```

Hugo es el segundo empleado digital funcional de Aidely.

Está enfocado en ayudar a autónomos, oficios y pequeños negocios a preparar presupuestos rápidos, claros y revisables.

Hugo convierte una solicitud de trabajo en un borrador de presupuesto, guarda el registro en Airtable, crea un borrador Gmail, avisa por Telegram, recuerda presupuestos pendientes y genera reportes de actividad.

Hugo está pensado para:

* fontaneros,
* electricistas,
* pintores,
* reformistas,
* técnicos,
* autónomos de mantenimiento,
* pequeños servicios locales.

Workflows validados:

```text
WF1 — Preparación de presupuestos
WF2 — Recordatorios de presupuestos pendientes
WF3 — Reporte de actividad
```

Regla principal de Hugo:

```text
Hugo prepara.
El profesional revisa y decide.
```

---

### Vera — reposición sencilla

Estado:

```text
Demo visual validada.
```

Vera es una demo visual interactiva publicada en la landing.

Su objetivo es demostrar cómo un empleado digital podría revisar datos sencillos de stock, detectar productos que conviene reponer y preparar una lista de revisión.

Vera no está conectada todavía a n8n, Airtable, Gmail ni Telegram.

Vera debe presentarse como:

```text
Demo de lista simple de reposición para revisar.
```

No debe presentarse como control exacto de inventario ni como producto conectado a datos reales.

---

## 3. Arquitectura general de Aidely

El MVP actual de Aidely trabaja con esta arquitectura:

```text
Landing Aidely
↓
Formulario / Demo visual
↓
n8n local
↓
Gemini
↓
Airtable
↓
Telegram
↓
Gmail
```

En fase demo y validación se permite usar:

* n8n local,
* Vercel,
* Airtable,
* Google Sheets,
* Gmail,
* Telegram,
* Gemini,
* datos ficticios,
* pruebas controladas.

No se recomienda usar ngrok para clientes reales.

ngrok puede usarse en laboratorio o demo controlada, pero no debe ser infraestructura estable de cliente.

Para pilotos reales se recomienda valorar:

* n8n Cloud,
* Make,
* n8n en VPS,
* dominio propio,
* HTTPS estable,
* separación de datos por cliente,
* credenciales propias del cliente,
* límites claros de alcance.

---

## 4. Leo — empleado digital de atención y ventas

Leo es el primer empleado digital validado de Aidely.

Su función principal es ayudar a negocios que reciben contactos, mensajes o solicitudes comerciales y no siempre responden a tiempo.

Leo permite:

* ordenar solicitudes,
* clasificar leads,
* detectar oportunidades urgentes,
* preparar borradores comerciales,
* avisar por Telegram,
* guardar información en Airtable,
* recordar seguimientos,
* generar reportes.

---

## 5. Flujo general de Leo

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

## 6. Workflows de Leo

### WF1 — Leo recibe y clasifica leads

Objetivo:

```text
Recibir leads desde la landing, prepararlos, clasificarlos con IA y guardarlos en Airtable.
```

Funciones principales:

* recibe datos desde formulario web,
* lee nombre, email, teléfono, empresa, sector, urgencia, presupuesto y mensaje,
* prepara el lead,
* envía el caso a Gemini,
* clasifica como CALIENTE, TIBIO, FRIO o REVISAR,
* define ruta comercial,
* guarda el registro en Airtable.

Rutas principales:

```text
CALIENTE → accion_urgente
TIBIO → seguimiento_suave
FRIO → nutricion / no_prioritaria
REVISAR → revisar_manual
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

Resultado:

* envía aviso interno por Telegram,
* marca `Aviso enviado = si`,
* evita duplicados.

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

Resultado:

* crea borrador Gmail,
* no envía el correo automáticamente,
* marca `Respuesta preparada = si`,
* marca `Estado respuesta = preparada`,
* activa seguimiento pendiente.

Regla:

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

Resultado:

* envía recordatorio interno por Telegram,
* marca `Seguimiento enviado = si`,
* evita duplicados.

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

## 7. Hugo — presupuestos rápidos

Hugo es el segundo empleado digital funcional de Aidely.

Está enfocado en ayudar a autónomos, oficios y pequeños negocios a preparar presupuestos rápidos, claros y revisables.

Hugo convierte una solicitud de trabajo en un borrador de presupuesto.

Hugo puede:

* recibir una solicitud de trabajo,
* analizar el mensaje,
* extraer datos clave,
* detectar datos faltantes,
* preparar un borrador de presupuesto,
* guardar el registro en Airtable,
* crear un borrador Gmail,
* enviar aviso interno por Telegram,
* recordar presupuestos pendientes,
* generar reportes de actividad.

Hugo no debe:

* enviar presupuestos automáticamente,
* cerrar ventas,
* confirmar precios finales,
* confirmar disponibilidad,
* emitir facturas,
* cobrar,
* borrar registros,
* usar datos sensibles,
* sustituir la revisión humana.

---

## 8. Workflows de Hugo

Hugo queda dividido en tres workflows principales:

```text
WF1 — Hugo presupuestos rápidos
WF2 — Hugo recordatorio de presupuestos pendientes
WF3 — Hugo reporte de actividad
```

Esta estructura permite que Hugo no sea solo una demo aislada, sino un empleado digital con comportamiento más completo:

* prepara presupuestos,
* guarda registros,
* crea borradores,
* avisa internamente,
* recuerda pendientes,
* genera reportes.

---

## 9. WF1 — Hugo presupuestos rápidos

### Objetivo

Recibir una solicitud de trabajo, analizarla, preparar un borrador de presupuesto, guardarlo en Airtable, crear un borrador de Gmail y avisar por Telegram.

### Estructura validada

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

### Resultado validado

* Hugo recibe una solicitud de ejemplo.
* Gemini analiza la solicitud.
* El nodo `Preparar presupuesto Hugo` genera un JSON limpio.
* Airtable guarda el registro en la tabla `Hugo Presupuestos`.
* Gmail crea un borrador revisable.
* Telegram Hugo envía un aviso interno.
* No se envía nada automáticamente al cliente.
* No se usa webhook.
* No se usa ngrok.
* El workflow queda en modo manual para demo interna.

### Principio principal

```text
Hugo prepara.
El profesional revisa y decide.
```

---

## 10. WF2 — Hugo recordatorio de presupuestos pendientes

### Objetivo

Buscar presupuestos preparados que todavía están pendientes de revisión y enviar un recordatorio interno por Telegram.

### Estructura validada

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

### Filtro usado en Airtable

```text
AND({Estado presupuesto} = "borrador_preparado", {Borrador enviado} = "no", {Recordatorio enviado} = "no", {Estado revisión} = "pendiente_revision")
```

### Resultado validado

* WF2 encuentra presupuestos pendientes en Airtable.
* Prepara un aviso interno.
* Telegram Hugo envía el recordatorio.
* Airtable actualiza `Recordatorio enviado = si`.
* Airtable guarda `Fecha recordatorio`.
* Si se ejecuta otra vez, no duplica el aviso porque el registro ya queda marcado.

### Importante

WF2 no usa Gemini.

Esto permite recordar presupuestos pendientes sin gastar tokens de IA.

---

## 11. WF3 — Hugo reporte de actividad

### Objetivo

Generar un reporte de actividad de Hugo con los presupuestos preparados durante el día.

### Estructura validada

```text
Disparador reporte Hugo
↓
Buscar presupuestos del día Hugo
↓
Crear reporte Hugo
↓
Enviar reporte Hugo
```

### Filtro usado en Airtable

```text
IS_SAME({Fecha entrada}, TODAY(), 'day')
```

### Resultado validado

WF3 genera un reporte por Telegram con:

* presupuestos revisados hoy,
* borradores preparados,
* presupuestos marcados como enviados,
* pendientes de revisión,
* recordatorios enviados,
* pendientes de datos,
* revisados,
* descartados,
* registros sin estado de revisión,
* lista de presupuestos preparados,
* lista de pendientes de revisión,
* estado general.

### Validación real del reporte

El reporte detectó correctamente:

```text
Presupuestos revisados hoy: 5
Borradores preparados: 5
Pendientes de revisión: 1
Recordatorios enviados: 1
Sin estado de revisión: 4
```

La diferencia es correcta porque algunos registros antiguos fueron pruebas creadas antes de añadir el campo `Estado revisión`.

### Importante

WF3 no usa Gemini.

Esto permite generar reportes de actividad sin gastar tokens de IA.

---

## 12. Tabla Airtable — Hugo Presupuestos

La tabla `Hugo Presupuestos` contiene los registros generados por Hugo.

Campos principales:

```text
Presupuesto ID
Fecha entrada
Empleado digital
Origen
Canal entrada
Nombre cliente
Teléfono
Email
Zona
Negocio profesional
Tipo profesional
Solicitud original
Tipo trabajo
Descripción trabajo
Urgencia
Materiales estimados
Horas estimadas
Precio
Datos faltantes
Estado presupuesto
Borrador preparado
Borrador enviado
Nivel confianza
Resumen interno
Acción recomendada
Asunto email
Cuerpo email
Mensaje Telegram
Recordatorio enviado
Fecha recordatorio
Reporte incluido
Estado revisión
```

Valores principales:

### Estado presupuesto

```text
nuevo
borrador_preparado
revisado
enviado_por_humano
pendiente_datos
descartado
```

### Estado revisión

```text
pendiente_revision
revisado
enviado
pendiente_datos
descartado
```

### Recordatorio enviado

```text
si
no
```

### Reporte incluido

```text
si
no
```

### Borrador preparado

```text
si
no
```

### Borrador enviado

```text
si
no
```

---

## 13. Vera — demo de reposición sencilla

Vera existe como demo interactiva publicada en la landing.

Usa datos ficticios para mostrar cómo un empleado digital puede revisar una tabla de productos, detectar artículos bajo mínimo y preparar una lista de reposición.

Vera no debe presentarse como control exacto de inventario ni como producto conectado a datos reales todavía.

Vera debe entenderse como:

```text
Demo de lista simple de reposición para revisar.
```

La demo Vera demuestra:

* cómo se vería otro tipo de empleado digital,
* cómo se pueden revisar datos simples,
* cómo se puede generar un reporte,
* cómo se puede preparar una lista de reposición,
* cómo se puede enseñar valor sin pedir contraseñas ni conectar datos reales.

Regla de Vera:

```text
Vera no decide por el dueño.
Vera prepara una lista para revisar.
```

---

## 14. Landing actual

Archivo principal:

```text
index.html
```

La landing incluye:

* hero principal,
* secciones de problema,
* empleados digitales,
* Leo,
* Hugo,
* Vera,
* precios,
* casos de uso,
* Demo Hugo,
* Demo Vera,
* formulario de diagnóstico,
* scripts de demo,
* script del formulario.

Estado:

```text
Validada visualmente en Vercel.
```

---

## 15. Demo visual de Hugo en landing

Hugo está integrado como demo visual en la landing pública.

Funcionamiento:

```text
Usuario escribe una solicitud
↓
Pulsa “Probar a Hugo”
↓
La landing muestra un borrador simulado
↓
La landing muestra un aviso interno simulado
```

La demo visual de Hugo:

* no usa webhook,
* no usa n8n,
* no usa Gemini,
* no gasta tokens,
* no usa Gmail real,
* no usa Telegram real,
* no toca Airtable,
* no toca datos reales.

Su objetivo es enseñar al cliente cómo trabaja Hugo sin pedir contraseñas ni conectar sistemas.

---

## 16. Demo visual de Vera en landing

Funcionamiento:

```text
Usuario pulsa “Probar a Vera”
↓
La landing revisa datos ficticios
↓
Muestra reporte simulado
↓
Muestra lista de reposición simulada
```

La demo visual de Vera:

* no usa webhook,
* no usa n8n,
* no usa Gemini,
* no gasta tokens,
* no usa Gmail real,
* no usa Telegram real,
* no toca Airtable,
* no toca datos reales.

---

## 17. Herramientas actuales

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
* crear lógica de Leo y Hugo.

Estado actual:

```text
n8n local válido para demo y validación.
No usar ngrok para clientes reales.
```

---

### ngrok

Túnel temporal usado para exponer n8n local.

Uso permitido:

* pruebas,
* validación,
* demo controlada.

Limitación:

```text
No apto para producción ni clientes reales.
```

---

### Airtable

Base actual para Leo y Hugo.

Uso:

* guardar leads,
* guardar presupuestos,
* almacenar clasificación,
* estados,
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

IA usada para clasificación y análisis.

Uso en Leo:

* clasificar leads,
* analizar intención,
* decidir ruta comercial,
* generar motivo IA y próxima acción.

Uso en Hugo:

* analizar solicitudes de trabajo,
* extraer datos clave,
* detectar datos faltantes,
* preparar estructura para presupuesto revisable.

Nota:

```text
WF2 y WF3 de Hugo no usan Gemini.
```

---

### Telegram

Canal interno de avisos.

Uso:

* avisos de leads calientes,
* recordatorios de seguimiento,
* reportes diarios,
* avisos de presupuestos Hugo,
* recordatorios de presupuestos Hugo,
* reportes de actividad Hugo.

---

### Gmail

Canal de borradores revisables.

Uso:

* crear borradores comerciales de Leo,
* crear borradores de presupuesto de Hugo,
* evitar envíos automáticos,
* mantener control humano.

---

## 18. Datos permitidos en la fase inicial

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

## 19. Datos fuera de alcance inicial

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

## 20. Infraestructura por fases

### Fase 1 — Demo y validación

Permitido:

* n8n local,
* Vercel,
* Airtable,
* Google Sheets,
* Gmail,
* Telegram,
* Gemini,
* datos ficticios,
* pruebas internas,
* demostraciones controladas.

No permitido:

* clientes reales dependiendo de ngrok,
* prometer servicio estable,
* usar datos sensibles,
* dejar procesos críticos funcionando desde un ordenador personal.

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

## 21. Diferenciación frente a ChatGPT Agents

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

```text
ChatGPT te da la herramienta.
Aidely te deja el proceso funcionando.
```

Otra frase importante:

```text
Puedes hacerlo tú mismo si tienes tiempo, ganas y conocimientos.
Aidely existe para quien quiere que alguien se lo deje funcionando de forma clara, sencilla y revisable.
```

---

## 22. Pricing inicial recomendado

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

Nota:

Los precios actuales de landing pueden seguir como referencia comercial, pero deberán revisarse antes de una oferta real según alcance, herramientas, mantenimiento y tipo de cliente.

---

## 23. Mensaje comercial recomendado

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

Frase principal:

```text
Empleados digitales sencillos para autónomos y pequeños negocios.
```

Subfrase:

```text
Ordena solicitudes, prepara presupuestos, recuerda citas y no pierdas clientes por falta de tiempo.
```

---

## 24. Qué no prometer

No decir:

* “La IA lo hace todo.”
* “Esto funciona para cualquier empresa automáticamente.”
* “Conectamos cualquier sistema sin problema.”
* “No hace falta revisar nada.”
* “Enviamos presupuestos automáticamente.”
* “Gestionamos facturas reales desde el primer día.”
* “Controlamos stock exacto.”
* “Cumplimos todo legalmente sin revisar el caso.”

Mejor decir:

```text
Aidely prepara, ordena y avisa.
Tú revisas y decides.
```

---

## 25. Checklist de demo

Archivo relacionado:

```text
docs/checklist-demo-aidely-leo.md
```

Uso:

* preparar entorno,
* arrancar n8n,
* validar Leo WF1-WF5,
* validar Hugo WF1-WF3,
* probar Demo Hugo,
* probar Demo Vera,
* validar formulario,
* confirmar Git limpio.

---

## 26. Guion comercial

Archivo relacionado:

```text
docs/guion-demo-aidely.md
```

Uso:

* presentar Aidely en 5-7 minutos,
* explicar problema,
* mostrar Leo,
* mostrar Hugo,
* mostrar Vera,
* explicar seguridad,
* diferenciar demo visual de producto validado,
* cerrar con diagnóstico.

---

## 27. Documento estratégico actualizado

Archivo relacionado:

```text
docs/estrategia-aidely-negocios-pequenos.md
```

Uso:

* definir el enfoque hacia autónomos y pequeños negocios,
* ordenar lo permitido y fuera de alcance,
* definir empleados digitales,
* preparar camino hacia pilotos reales.

---

## 28. Documento de Hugo

Archivo relacionado:

```text
docs/hugo-presupuestos-rapidos.md
```

Uso:

* definir el diseño de Hugo,
* registrar arquitectura WF1-WF3,
* documentar tabla Airtable,
* documentar validación funcional,
* documentar demo visual en landing,
* definir límites y próximos pasos.

---

## 29. Comandos útiles

### Entrar al proyecto

```bash
cd C:\Users\zaphi\Documents\proyectos-aidely\landing-aidely
```

### Revisar estado Git

```bash
git status
```

### Ver cambios resumidos

```bash
git diff --stat
```

### Añadir archivos

```bash
git add .
```

### Commit

```bash
git commit -m "Mensaje claro del cambio"
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

## 30. Estado final actual del proyecto

Aidely cuenta actualmente con:

```text
Leo funcional con WF1-WF5.
Hugo funcional con WF1-WF3.
Vera como demo visual.
Landing actualizada y validada.
Documentación actualizada.
GitHub y Vercel al día.
```

---

## 31. Próximos pasos recomendados

### Documentación

* [ ] Actualizar checklist general con Hugo WF1-WF3.
* [ ] Revisar si hace falta regenerar PDF.
* [ ] Actualizar NotebookLM con documentos nuevos.

### Comercial

* [ ] Preparar guion de demo con Leo + Hugo + Vera.
* [ ] Crear argumentario para autónomos y pequeños negocios.
* [ ] Validar con oficios: fontaneros, electricistas, pintores, reformistas.
* [ ] Validar con negocios de barrio: peluquerías, estética, tiendas, academias.

### Producto

* [ ] Mantener Leo y Hugo en modo controlado.
* [ ] No ejecutar Gemini innecesariamente.
* [ ] Valorar entrada real de Hugo por formulario.
* [ ] Valorar audio transcrito como siguiente mejora.
* [ ] Definir primer piloto pagado.
* [ ] Elegir infraestructura para piloto: n8n Cloud, Make o VPS.

---

## 32. Decisión final actual

Aidely debe continuar con enfoque claro:

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

Aidely ya tiene dos empleados digitales funcionales y una demo visual complementaria:

```text
Leo — atención y ventas.
Hugo — presupuestos rápidos.
Vera — reposición sencilla.
```

La visión actual es construir empleados digitales útiles, humanos y accesibles para negocios reales.
