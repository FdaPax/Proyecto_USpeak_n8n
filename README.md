# Proyectos n8n

Automatizaciones desarrolladas en n8n, como parte del curso de automatización de procesos. Incluye análisis de negocio, diagramas AS-IS / TO-BE y cálculo de ROI.

---

## Herramientas utilizadas

- **n8n** — plataforma de automatización de workflows
- **Google Sheets / Forms** — captura y almacenamiento de datos
- **Google Drive** — respaldo de archivos
- **Gmail** — envío automatizado de correos
- **Zoom** — links de clases integrados en los flujos

---

## Contexto — Academia USpeak

USpeak es una academia de inglés ficticia creada para este proyecto. Se diseñó con procesos administrativos manuales como punto de partida: transcripción de formularios en papel, envío individual de correos, revisión celda por celda de pagos y gestión dispersa de comprobantes.

Se identificaron **4 stakeholders principales** con distintos niveles de poder e interés en la solución:

| Stakeholder | Problema principal | Expectativa |
|---|---|---|
| Recepcionista | Transcripción manual y emails uno a uno | Eliminar tareas repetitivas |
| Coordinadora Académica | Asignación manual de grupos y horarios | Notificaciones automáticas de nuevos inscritos |
| Administrativa de Finanzas | Desorden en comprobantes y cobros manuales | Comprobantes guardados solos y recordatorios automáticos |
| Estudiante | Espera larga y experiencia arcaica | Respuesta inmediata al inscribirse |

---

## Retorno de Inversión (ROI)

| Beneficio | Cálculo | Ahorro mensual |
|---|---|---|
| Transcripción (Recepcionista) | 45 prospectos × 0.25 hrs × $5.00/hr | $56.25 |
| Revisión de pagos (Finanzas) | 10 hrs × $5.63/hr | $56.30 |
| Asignación de grupos (Coordinadora) | 8 hrs × $7.50/hr | $60.00 |
| Recuperación de ventas | 1 alumno retenido por respuesta inmediata | $100.00 |
| **Total anual** | | **$3.270.60** |

**Inversión año 1:** $651.26 (desarrollo + licencia cloud + capacitación)

**ROI: 402%**

---

## Workflows

### 1. Flujo de Inscripción de Estudiantes
Automatiza el proceso completo desde que un prospecto llena el formulario hasta que recibe su correo de bienvenida con horario y link de Zoom.

**Archivo:** `USpeak_Flujo_Inscripcion_Estudiantes_SANITIZED.json`

**Flujo:**
1. `Google Sheets Trigger` — detecta nueva fila al llegar un formulario
2. `Switch` — enruta según el nivel elegido (Básico / Intermedio / Avanzado)
3. `Set` — asigna el horario y link de Zoom correspondiente
4. `Gmail` — envía correo de bienvenida personalizado con los datos del curso

---

### 2. Recordatorio de Pago
Envía automáticamente recordatorios de cobro a todos los alumnos con pago pendiente, el día 28 de cada mes.

**Archivo:** `USpeak_Recordatorio_de_Pago_SANITIZED.json`

**Flujo:**
1. `Schedule Trigger` — se activa el día 28 de cada mes a las 9:00 AM
2. `Google Sheets` — lee la lista completa de alumnos
3. `IF` — filtra los que tienen estado de pago distinto a "Pagado"
4. `Gmail` — envía recordatorio de cobro a cada alumno moroso

---

### 3. Respaldo de Comprobantes de Pago
Procesa automáticamente los comprobantes que los alumnos envían por correo, los respalda en Drive y actualiza el estado de pago en la planilla.

**Archivo:** `USpeak_Respaldo_de_Pagos_SANITIZED.json`

**Flujo:**
1. `Gmail Trigger` — detecta correos entrantes con adjuntos
2. `Google Drive` — sube la imagen del comprobante a la carpeta oficial
3. `Google Sheets` — actualiza el estado a "Pagado" y registra el link del comprobante
4. `Gmail` — envía acuse de recibo al alumno

---

## Nota sobre credenciales

Todos los archivos JSON han sido sanitizados antes de publicar. Los IDs de credenciales, hojas de cálculo, carpetas de Drive e instancia de n8n han sido reemplazados por placeholders del tipo `YOUR_CREDENTIAL_ID`. Para usar estos workflows debes reemplazar cada placeholder con tus propios valores en n8n.

---

## Autora

Fernanda Paz
