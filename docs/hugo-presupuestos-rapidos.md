# Hugo — Presupuestos rápidos para autónomos y pequeños negocios

## 1. Objetivo del documento

Este documento define el diseño inicial de Hugo, el próximo empleado digital de Aidely.

Hugo estará enfocado en ayudar a autónomos y pequeños negocios a preparar presupuestos rápidos, claros y revisables, sin tener que redactarlos desde cero al final del día.

Hugo no enviará presupuestos automáticamente. Su función inicial será preparar borradores para que el profesional revise, corrija y envíe cuando quiera.

---

## 2. Qué es Hugo

Hugo es un empleado digital sencillo especializado en presupuestos rápidos.

Su objetivo es convertir una solicitud de trabajo, una nota escrita o una nota de voz en un borrador de presupuesto ordenado.

Hugo ayuda a que el profesional no pierda oportunidades por tardar demasiado en responder.

---

## 3. Cliente ideal

Hugo está pensado para:

* fontaneros,
* electricistas,
* pintores,
* reformistas,
* técnicos de mantenimiento,
* instaladores,
* cerrajeros,
* jardineros,
* autónomos de servicios,
* pequeños negocios que preparan presupuestos manualmente.

---

## 4. Problema que resuelve

Muchos autónomos reciben solicitudes durante el día, pero no pueden preparar presupuestos en el momento porque están trabajando, conduciendo, atendiendo clientes o resolviendo urgencias.

El resultado habitual es:

* presupuestos que se preparan tarde,
* clientes que contratan a otro antes,
* trabajos que se olvidan,
* mensajes mezclados en WhatsApp,
* notas sueltas,
* falta de seguimiento,
* noches dedicadas a tareas administrativas.

Hugo busca reducir ese caos.

---

## 5. Propuesta de valor

La promesa sencilla de Hugo es:

```text
Me cuentas el trabajo y Hugo te deja un presupuesto listo para revisar.
```

Otra forma de explicarlo:

```text
Hugo no decide por ti.
Hugo te prepara el borrador para que tú solo tengas que revisar y enviar.
```

---

## 6. Versión inicial recomendada

La versión ideal de Hugo será con audio porque resulta más espectacular y natural para oficios.

Pero la primera versión debe contemplar dos entradas posibles:

```text
Opción A — Formulario escrito
Más fácil, más estable y más controlado.

Opción B — Audio o nota de voz
Más potente comercialmente, más natural para autónomos, pero requiere transcripción.
```

La estrategia recomendada:

```text
Primero diseñar Hugo pensando en audio.
Si la parte técnica se complica, crear una demo inicial con formulario y luego añadir audio.
```

---

## 7. Flujo conceptual de Hugo

```text
Audio o formulario
↓
Extracción de datos
↓
Organización del trabajo solicitado
↓
Aplicación de plantilla
↓
Borrador de presupuesto
↓
Aviso interno
↓
Revisión humana
↓
Envío manual por el profesional
```

---

## 8. Datos mínimos que necesita Hugo

Hugo debe trabajar con datos simples.

Datos permitidos:

* nombre del cliente,
* teléfono,
* email si existe,
* tipo de trabajo,
* dirección aproximada si el profesional la necesita,
* descripción del problema,
* materiales estimados,
* horas estimadas,
* desplazamiento,
* urgencia,
* notas internas,
* precio orientativo,
* condiciones básicas,
* fecha de solicitud.

Datos que se deben evitar al inicio:

* DNI,
* datos bancarios,
* facturas fiscales reales,
* contratos legales,
* datos sensibles,
* documentos oficiales,
* pagos automáticos,
* datos de menores,
* datos médicos.

---

## 9. Campos recomendados para la tabla de Hugo

Nombre de tabla sugerido:

```text
Hugo — Presupuestos
```

Campos:

```text
Presupuesto ID
Fecha entrada
Nombre cliente
Teléfono
Email
Tipo de trabajo
Descripción
Materiales
Horas estimadas
Desplazamiento
Urgencia
Precio orientativo
Estado presupuesto
Borrador preparado
Borrador enviado
Canal de entrada
Notas internas
Fecha revisión
Empleado digital
```

Estados recomendados:

```text
nuevo
borrador_preparado
revisado
enviado_por_humano
pendiente_datos
descartado
```

---

## 10. Qué debe hacer Hugo

Hugo puede:

* recibir una solicitud,
* transcribir o leer el mensaje,
* extraer datos clave,
* ordenar la información,
* detectar datos faltantes,
* preparar un borrador,
* usar una plantilla base,
* avisar al profesional,
* guardar el registro,
* dejar seguimiento pendiente.

---

## 11. Qué no debe hacer Hugo

Hugo no debe:

* enviar presupuestos automáticamente,
* inventar precios finales,
* prometer disponibilidad,
* confirmar trabajos,
* cerrar ventas,
* aplicar descuentos no autorizados,
* emitir facturas,
* cobrar,
* borrar registros,
* sustituir la revisión humana.

Regla principal:

```text
Hugo prepara.
El profesional revisa y decide.
```

---

## 12. Plantilla base de presupuesto

Estructura inicial del presupuesto:

```text
Hola [Nombre],

Gracias por contactar.

Según la información recibida, te dejo una propuesta inicial para el trabajo solicitado:

Trabajo:
[Tipo de trabajo]

Descripción:
[Descripción del problema o servicio]

Materiales estimados:
[Materiales]

Tiempo estimado:
[Horas estimadas]

Precio orientativo:
[Precio orientativo]

Condiciones:
Este presupuesto es orientativo y queda pendiente de revisión final por el profesional.
El precio puede variar si aparecen trabajos adicionales, materiales no previstos o cambios en la solicitud.

Un saludo,
[Nombre del profesional / negocio]
```

---

## 13. Mensaje interno al profesional

Ejemplo de aviso interno:

```text
🧾 Hugo ha preparado un borrador de presupuesto

👤 Cliente: [Nombre]
📞 Teléfono: [Teléfono]
🛠️ Trabajo: [Tipo de trabajo]
⚠️ Urgencia: [Urgencia]

📌 Estado:
Borrador preparado para revisar.

✅ Acción recomendada:
Revisar el presupuesto antes de enviarlo al cliente.
```

---

## 14. Versión demo

La versión demo de Hugo debe usar datos ficticios.

Objetivo de la demo:

* demostrar cómo Hugo convierte una solicitud en un presupuesto,
* enseñar que no envía nada automáticamente,
* mostrar el borrador,
* mostrar el aviso interno,
* explicar que el profesional mantiene el control.

Datos ficticios de ejemplo:

```text
Cliente: Marta López
Teléfono: 600123456
Trabajo: Cambio de grifo de cocina
Descripción: El grifo actual pierde agua y la clienta quiere instalar uno nuevo.
Materiales: Grifo estándar, latiguillos si hacen falta.
Horas estimadas: 1,5 horas
Desplazamiento: zona Valencia
Precio orientativo: 85€ - 120€
Urgencia: media
```

---

## 15. Versión piloto

La versión piloto de Hugo debe ser sencilla y controlada.

Debe incluir:

* una fuente de entrada,
* una tabla simple,
* una plantilla de presupuesto,
* un aviso interno,
* un borrador revisable,
* seguimiento manual.

No debe incluir:

* facturación real,
* cobro,
* envío automático,
* integración con software externo complejo,
* datos sensibles,
* WhatsApp no oficial,
* promesas de funcionamiento 24/7 sin infraestructura estable.

---

## 16. Herramientas posibles

Para demo:

* formulario,
* Google Sheets o Airtable,
* n8n local,
* Telegram,
* Gmail,
* datos ficticios.

Para piloto real:

* n8n Cloud, Make o VPS sencillo,
* Google Sheets o Airtable separado por cliente,
* Gmail del cliente o cuenta técnica,
* Telegram para avisos,
* posible transcripción de audio,
* plantilla de Google Docs o email.

Para futuro:

* WhatsApp Business API oficial,
* Google Drive,
* generación de PDF,
* panel simple,
* base de datos más robusta si hiciera falta.

---

## 17. Riesgos principales

### Riesgo 1 — Hugo inventa precios

Mitigación:

* usar precios orientativos,
* trabajar con tabla de tarifas si existe,
* dejar siempre revisión humana,
* incluir texto de “pendiente de revisión final”.

### Riesgo 2 — El presupuesto se envía sin revisar

Mitigación:

* no automatizar envío,
* crear solo borrador,
* avisar al profesional,
* exigir aprobación manual.

### Riesgo 3 — Datos incompletos

Mitigación:

* marcar estado `pendiente_datos`,
* preparar mensaje de solicitud de información,
* no generar presupuesto final si falta información clave.

### Riesgo 4 — El cliente cree que Aidely sustituye al profesional

Mitigación:

* explicar que Hugo solo prepara borradores,
* el profesional mantiene el control,
* el trato humano sigue siendo del negocio.

### Riesgo 5 — Infraestructura inestable

Mitigación:

* no usar ngrok para clientes reales,
* usar n8n Cloud, Make o VPS para piloto,
* separar datos por cliente,
* documentar límites.

---

## 18. Métricas de éxito

Para validar Hugo, medir:

* número de solicitudes recibidas,
* número de borradores preparados,
* tiempo medio de preparación,
* presupuestos revisados,
* presupuestos enviados por el profesional,
* trabajos ganados,
* errores detectados,
* datos faltantes,
* ahorro de tiempo estimado.

---

## 19. Preguntas de validación para clientes

Preguntas para fontaneros, electricistas, pintores o reformistas:

1. ¿Cuánto tardas normalmente en enviar un presupuesto?
2. ¿Cuántos presupuestos se te quedan pendientes cada semana?
3. ¿Has perdido trabajos por contestar tarde?
4. ¿Dónde apuntas ahora las solicitudes?
5. ¿Usas WhatsApp, libreta, email o memoria?
6. ¿Te serviría mandar una nota de voz y recibir un borrador ordenado?
7. ¿Qué datos necesitas siempre antes de presupuestar?
8. ¿Tienes precios fijos o cada trabajo cambia?
9. ¿Te gustaría recibir un aviso cuando el presupuesto esté preparado?
10. ¿Pagarías una cuota accesible si esto te ahorra tiempo o te ayuda a responder antes?

---

## 20. Primera demo recomendada

Primera demo de Hugo:

```text
Formulario o audio ficticio
↓
extracción de datos
↓
tabla Hugo
↓
generación de borrador
↓
aviso interno
```

Resultado visible:

* registro creado,
* borrador generado,
* aviso interno,
* estado `borrador_preparado`.

---

## 21. Decisiones pendientes

Antes de construir Hugo hay que decidir:

* si la demo empieza con formulario o audio,
* qué herramienta usaremos para transcribir audio,
* si el primer borrador será email o documento,
* si se usará Google Sheets o Airtable,
* si el aviso será por Telegram,
* si el presupuesto tendrá PDF o solo texto al inicio,
* si el piloto será con n8n Cloud, Make o VPS.

---

## 22. Recomendación actual

La recomendación inicial es:

```text
Crear primero una demo controlada de Hugo.
Empezar con datos ficticios.
No enviar nada automáticamente.
Generar borrador revisable.
Validar visualmente.
Después valorar piloto pagado.
```

Hugo debe construirse con el mismo principio que Leo:

```text
El empleado digital prepara.
El humano decide.
```

---

## 23. Ruta de pasos

### Bloque 4 — Diseño de Hugo

* [ ] Crear `docs/hugo-presupuestos-rapidos.md`.
* [ ] Revisar documento.
* [ ] Hacer commit.
* [ ] Hacer push.

### Bloque 5 — Demo Hugo

* [ ] Decidir entrada inicial: formulario o audio.
* [ ] Crear datos ficticios.
* [ ] Diseñar plantilla de presupuesto.
* [ ] Definir tabla Hugo.
* [ ] Crear primer flujo.
* [ ] Generar borrador revisable.
* [ ] Enviar aviso interno.
* [ ] Validar que no se envía nada automáticamente.
* [ ] Documentar resultados.

### Bloque 6 — Piloto real

* [ ] Elegir primer tipo de cliente.
* [ ] Validar con 3 oficios.
* [ ] Definir precio del piloto.
* [ ] Elegir infraestructura estable.
* [ ] Evitar ngrok.
* [ ] Separar datos por cliente.
* [ ] Definir alcance.
* [ ] Lanzar piloto pagado.
## 24. Validación inicial de demo Hugo

Estado: validado en entorno local de n8n.

Workflow:

```text
Disparador manual
↓
Solicitud demo Hugo
↓
Analizar solicitud Hugo
↓
Preparar presupuesto Hugo
├── Crear borrador Gmail Hugo
├── Telegram Hugo Aidely
└── Create a record Airtable