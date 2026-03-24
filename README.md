Tres workflows de n8n que automatizan procesos clave de USpeak:

- Flujo de inscripción: se activa con nuevas filas en Google Sheets,
  enruta por nivel (Básico/Intermedio/Avanzado) y envía email de bienvenida
- Recordatorio de pago: se ejecuta el día 28 de cada mes, filtra
  alumnos morosos y envía correo de cobro automático
- Respaldo de comprobantes: detecta emails con adjuntos, sube
  el comprobante a Drive y actualiza el estado de pago en Sheets

Incluye PDF de análisis de negocio (stakeholders, pain points, ROI).
Todos los IDs de credenciales y hojas de cálculo han sido sanitizados.
