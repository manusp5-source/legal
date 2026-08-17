# Registro de Actividades de Tratamiento (RAT)

**Art. 30 del Reglamento (UE) 2016/679 (RGPD)**

| | |
|---|---|
| **Responsable** | PENDIENTE_NOMBRE_COMPLETO — nombre comercial «Agendia» |
| **NIF** | PENDIENTE_NIF |
| **Domicilio** | PENDIENTE_DOMICILIO_FISCAL |
| **Contacto** | PENDIENTE_EMAIL_NEGOCIO · PENDIENTE_TELEFONO_NEGOCIO |
| **Delegado de protección de datos** | No designado. No concurre ninguno de los supuestos del art. 37.1 RGPD ni del art. 34 LOPDGDD |
| **Primera versión** | 15 de agosto de 2026 |
| **Última revisión** | 15 de agosto de 2026 |

## Por qué existe este documento

La exención del art. 30.5 (menos de 250 empleados) **no aplica aquí**, y conviene
tenerlo claro antes de tentarse a saltárselo. Decae por dos motivos
independientes, y basta uno:

1. El tratamiento **no es ocasional** — la prospección comercial y la operación
   de los sistemas del cliente son continuas.
2. Se prevé tratar **categorías especiales del art. 9** (datos de salud) como
   encargado.

---

# Parte I — Tratamientos como RESPONSABLE

## A1 · Reserva de llamada de descubrimiento

| Campo | Contenido |
|---|---|
| **Finalidad** | Concertar y atender la llamada de 15 minutos solicitada por el interesado |
| **Base jurídica** | Art. 6.1.b RGPD — medidas precontractuales a petición del interesado |
| **Interesados** | Personas de contacto de clínicas privadas que reservan por sí mismas |
| **Categorías de datos** | Identificativos (nombre), de contacto (email, teléfono), profesionales (clínica, cargo) |
| **Destinatarios** | Cal.com, Inc. (encargado) |
| **Transferencias internacionales** | Sí — EE. UU. Amparada en Marco de Privacidad de Datos UE-EE. UU. o CCT, según lo que figure en el DPA del proveedor. **PENDIENTE: descargar y archivar el DPA firmado de Cal.com** |
| **Plazo de supresión** | 12 meses desde el último contacto sin contrato. Con contrato, vigencia + plazos de prescripción fiscal (4 años) y mercantil (6 años) |
| **Medidas de seguridad** | Acceso al calendario con MFA. Sin copia local del dato |

## A2 · Comunicaciones entrantes (WhatsApp, correo, teléfono)

| Campo | Contenido |
|---|---|
| **Finalidad** | Atender consultas y conversaciones comerciales |
| **Base jurídica** | Art. 6.1.b y 6.1.f RGPD — precontractual e interés legítimo en responder a quien nos escribe |
| **Interesados** | Quien contacta por iniciativa propia |
| **Categorías de datos** | Contacto y contenido del mensaje |
| **Destinatarios** | WhatsApp Ireland Ltd. (grupo Meta) y proveedor de correo, como encargados |
| **Transferencias internacionales** | Sí en el caso de Meta. Mecanismo: CCT del proveedor |
| **Plazo de supresión** | 12 meses desde el último mensaje |
| **Medidas de seguridad** | Dispositivo con cifrado y bloqueo. **PENDIENTE: pasar el canal a un número de negocio, hoy es el personal** |

> Esta última pendiente no es cosmética. El argumento de venta de Agendia es
> literalmente «saca el WhatsApp de la clínica del móvil personal». Tener el
> canal comercial en el móvil personal reproduce el problema que se vende
> resolver, y una clínica que lo note lo va a usar en la negociación.

## A3 · Registros del servidor web

| Campo | Contenido |
|---|---|
| **Finalidad** | Entrega del sitio, seguridad y detección de abusos |
| **Base jurídica** | Art. 6.1.f RGPD — interés legítimo en la seguridad del servicio |
| **Interesados** | Visitantes del sitio |
| **Categorías de datos** | Dirección IP, agente de usuario, recurso solicitado, marca temporal |
| **Destinatarios** | PENDIENTE_PROVEEDOR_ALOJAMIENTO, como encargado |
| **Transferencias internacionales** | Depende del proveedor. Archivar su DPA |
| **Plazo de supresión** | El del proveedor, inferior a 30 días. No se descargan ni se cruzan |
| **Medidas de seguridad** | HTTPS obligatorio, HSTS, CSP restrictiva, sin base de datos propia |

## A4 · Prospección comercial a clínicas (pipeline `gtm-clinicas`)

| Campo | Contenido |
|---|---|
| **Finalidad** | Presentar los servicios a clínicas privadas de la provincia de Granada por correo, teléfono o entrega en mano |
| **Base jurídica** | Art. 6.1.f RGPD — interés legítimo en la prospección entre profesionales (considerando 47). Ponderación documentada en [interes-legitimo-outbound.md](interes-legitimo-outbound.md) |
| **Interesados** | Titulares y personas de contacto de clínicas privadas |
| **Categorías de datos** | Nombre del centro, dirección, teléfono, web, correo público, horario, valoración pública y, cuando figura publicado, nombre del titular |
| **Origen (art. 14.2.f)** | Fuentes de acceso público: OpenStreetMap y la web pública de cada clínica. **No se compran bases de datos** |
| **Destinatarios** | Ninguno. No se ceden ni se venden |
| **Transferencias internacionales** | No |
| **Plazo de supresión** | 12 meses desde el último contacto sin respuesta. Ante oposición, supresión inmediata y alta en lista de exclusión, que se conserva indefinidamente con el fin exclusivo de no volver a contactar (art. 21.3 RGPD) |
| **Medidas de seguridad** | Ficheros CSV en equipo con cifrado de disco. Fuera del repositorio público vía `.gitignore` |

> **Verificado el 15/08/2026:** `gtm-clinicas/.gitignore` excluye `data/*.csv`,
> `data/*.json`, `data/*.log` y `output/`, y `git ls-files` solo devuelve la
> plantilla `registro-llamadas.example.csv`. Ningún fichero con datos personales
> está versionado. Mantenerlo así: un `censo.csv` con nombres y correos en un
> repositorio es una brecha notificable, y el historial de git es prácticamente
> imborrable.

## A5 · Clientes, facturación y contabilidad

| Campo | Contenido |
|---|---|
| **Finalidad** | Ejecución del contrato, facturación y cumplimiento fiscal |
| **Base jurídica** | Art. 6.1.b (contrato) y 6.1.c (obligación legal: LGT, Código de Comercio, RD 1007/2023 Verifactu) |
| **Interesados** | Clientes y sus personas de contacto |
| **Categorías de datos** | Identificativos, fiscales, bancarios y de contacto |
| **Destinatarios** | Asesoría fiscal, entidad bancaria y AEAT |
| **Transferencias internacionales** | No |
| **Plazo de supresión** | 6 años (Código de Comercio art. 30), 4 años a efectos fiscales |
| **Medidas de seguridad** | Sistema de facturación conforme a Verifactu. Copias cifradas |

---

# Parte II — Tratamiento como ENCARGADO (art. 30.2)

## E1 · Operación de sistemas de comunicación y agenda para clínicas

Este es el tratamiento delicado y el que hay que poder explicar sin titubear.

| Campo | Contenido |
|---|---|
| **Responsable** | Cada clínica cliente. Uno por contrato |
| **Encargado** | PENDIENTE_NOMBRE_COMPLETO (Agendia) |
| **Categorías de tratamiento** | Recepción y respuesta automática de mensajes, recordatorio de citas, relleno de huecos de agenda, seguimiento de presupuestos, captación de reseñas, triaje de correo |
| **Categorías de datos** | Identificativos y de contacto del paciente, y datos de cita. **Puede incluir dato de salud (art. 9) por el contenido libre de un mensaje entrante**, aunque no se solicite |
| **Lo que queda fuera** | Historia clínica, diagnóstico, tratamiento, imagen médica. No se accede ni se importa |
| **Transferencias internacionales** | No. Alojamiento en la UE e inferencia de modelos en región europea |
| **Plazo de supresión** | El que fije el responsable por contrato. A la terminación: devolución o supresión certificada, a su elección |
| **Subencargados** | Ver anexo III del contrato. Alta sujeta a información previa y derecho de oposición del responsable |
| **Medidas de seguridad** | Ver anexo II del contrato |

### La deuda que hay que decir en voz alta

**Ningún modelo del CRM lleva `organizationId`** (`DEC-D06` en el registro de
decisiones de `UnicornIA-CRM`). Dos clínicas en la misma instalación verían los
datos de la otra: eso no es un fallo de configuración, es una brecha de
confidencialidad del art. 32 con datos del art. 9.

**Mitigación en vigor:** una instalación por clínica, aislada.
**Consecuencia:** no se puede vender un modo multiinquilino hasta cerrarlo, ni
insinuarlo en una llamada comercial.

---

## Medidas de seguridad comunes (art. 32)

| Medida | Estado |
|---|---|
| Cifrado en tránsito (TLS 1.2+) en todos los servicios | Aplicado — Caddy con TLS automático |
| Cifrado en reposo del disco de los equipos de trabajo | PENDIENTE verificar BitLocker activo |
| Autenticación multifactor en Cal.com, correo, registrador y proveedor de alojamiento | PENDIENTE verificar uno por uno |
| Aislamiento por cliente: una pila Docker por clínica | Aplicado |
| Separación de bases: `unicornia_crm`, `n8n` y `langfuse` en instancias lógicas distintas | Aplicado |
| Copia diaria cifrada **fuera** del servidor | PENDIENTE — el `README` de despliegue lo advierte y aún no hay cron |
| Registro de auditoría de accesos en el CRM | Aplicado |
| Trazabilidad de las llamadas a modelo (Langfuse autoalojado) | Parcial — los workflows de IA todavía no envían trazas |
| Prueba de restauración de copia | PENDIENTE — una copia sin restauración probada no es una copia |

## Procedimiento ante brecha de seguridad

1. **Contener** — aislar el servicio afectado.
2. **Evaluar** en 24 h: qué datos, cuántos interesados, qué riesgo.
3. **Notificar al responsable** (la clínica) **sin dilación indebida**. El plazo
   de 72 h del art. 33 es suyo, no tuyo: si tardas, le haces incumplir.
4. **Documentar** en este registro aunque no sea notificable. El art. 33.5 obliga
   a documentar **todas**, también las descartadas.
5. **Corregir** y registrar la medida adoptada.

## Historial de revisiones

| Fecha | Cambio |
|---|---|
| 2026-08-15 | Versión inicial |
