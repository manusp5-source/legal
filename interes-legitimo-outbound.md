# Valoración de interés legítimo — prospección a clínicas

**Art. 6.1.f RGPD · considerando 47 · art. 21 LSSI-CE**

| | |
|---|---|
| **Responsable** | PENDIENTE_NOMBRE_COMPLETO (Agendia) |
| **Tratamiento evaluado** | A4 del [RAT](registro-actividades-tratamiento.md) — pipeline `gtm-clinicas` |
| **Fecha** | 15 de agosto de 2026 |
| **Conclusión** | **Favorable**, con las cinco salvaguardas de la sección 4 |

## Por qué hay que escribir esto

El interés legítimo no es una casilla que se marca: es una base jurídica que hay
que **poder demostrar** que se ponderó antes de tratar (art. 5.2, responsabilidad
proactiva). Si la AEPD pregunta y la respuesta es «entendí que valía», la base
jurídica no existe y el tratamiento es ilícito desde el primer día.

Sin este documento firmado y fechado, todo el pipeline outbound está sin cobertura.

---

## 1. Test de finalidad — ¿el interés es legítimo?

**Sí.** La prospección comercial figura expresamente en el considerando 47 del
RGPD como ejemplo de interés legítimo. El destinatario es una **empresa**
—clínica privada— y el mensaje se dirige a su actividad profesional, no a su
esfera personal.

Interés concreto: dar a conocer un servicio de automatización de recepción a
clínicas privadas de la provincia de Granada.

## 2. Test de necesidad — ¿hace falta tratar estos datos?

**Sí, y solo estos.** Para presentar un servicio a una clínica hay que poder
dirigirse a ella. Los datos tratados son exclusivamente:

| Dato | Por qué es necesario |
|---|---|
| Nombre del centro, dirección | Identificar a quién se escribe y construir la ruta a pie |
| Teléfono, correo público, web | Es el canal. Sin él no hay contacto posible |
| Horario, presencia de reserva online y de WhatsApp | Son las cuatro señales auditadas: **son el contenido del mensaje**, no un extra |
| Nombre del titular, cuando está publicado | Escribir a una persona con nombre en vez de a `info@` reduce el envío ciego |

**Lo que no se trata, pudiendo:** ningún dato de paciente, ningún dato de
empleados, ningún dato de fuentes no públicas, ninguna base de datos comprada.
No se hace scraping de perfiles personales.

Alternativas menos invasivas descartadas y por qué:

- **Publicidad pagada.** No permite la personalización que es el núcleo de la
  propuesta —un informe con los datos de *esa* clínica— y no llega a quien no
  busca.
- **Consentimiento previo.** Es circular: no se puede pedir consentimiento sin
  contactar antes.

## 3. Test de ponderación — ¿pesa más que los derechos del interesado?

| A favor del tratamiento | En contra |
|---|---|
| Datos exclusivamente **profesionales y publicados** por el propio interesado para ser contactado | El nombre del titular autónomo es dato personal aunque sea profesional |
| **Expectativa razonable**: una clínica que publica su correo en su web espera recibir propuestas comerciales | El volumen del censo (516 fichas) hace que no sea un contacto puntual |
| Contenido **útil y específico**: una auditoría de cuatro señales de su propio negocio, no un folleto | — |
| Cero datos sensibles, cero perfilado, cero cesión a terceros | — |
| Ámbito geográfico acotado a una provincia | — |
| Oposición efectiva y en un clic, con lista de exclusión permanente | — |

**Resultado:** el impacto sobre el interesado es bajo —recibir un mensaje
profesional que puede rechazar sin coste— y el interés del responsable es real y
concreto. **La ponderación es favorable.**

El punto que la haría bascular en contra es la insistencia: contactar más de dos
veces sin respuesta convierte una propuesta en una molestia y destruye la
expectativa razonable en la que se apoya toda la ponderación.

## 4. Salvaguardas — condición de validez, no buenas intenciones

Si alguna de estas cinco deja de cumplirse, esta valoración deja de ser válida y
hay que rehacerla.

1. **Información del art. 14 en el primer contacto**, siempre, en cualquier canal.
   Texto en [aviso-primer-contacto.md](aviso-primer-contacto.md).
2. **Máximo dos contactos** por clínica sin respuesta. El segundo cierra:
   *«no vuelvo a escribir salvo que me digas tú»*.
3. **Oposición en un solo paso**, gratuita y sin justificación. Se atiende en 24 h.
4. **Lista de exclusión permanente.** Quien se opone entra ahí y no vuelve a
   entrar al censo aunque se regenere. Base: art. 21.3 RGPD.
   *Implementada el 15/08/2026:* `gtm-clinicas/data/exclusion.csv`, consultada
   por los cuatro scripts que producen contacto, que **paran si el fichero no
   existe**. Gestión con `npm run excluir`.
5. **Sin datos comprados y sin scraping de personas.** Solo OpenStreetMap y la web
   pública de cada clínica.

## 5. LSSI-CE art. 21 — el correo comercial

El art. 21.1 prohíbe la comunicación comercial por correo electrónico sin
solicitud o autorización previa. Es una norma **distinta** del RGPD y con su
propio régimen sancionador: cumplir el art. 6.1.f no da cobertura aquí.

Consecuencias operativas, que son las que importan:

| Regla | Cómo se aplica |
|---|---|
| El art. 21.2 solo exime cuando hay **relación contractual previa** con productos similares | No la hay con una clínica en frío → **el correo comercial puro no está amparado** |
| La AEPD y los tribunales admiten el contacto B2B a **direcciones genéricas de empresa** (`info@`, `clinica@`) con fines profesionales | Priorizar esas direcciones. Es la vía más defendible |
| Toda comunicación comercial debe ser **identificable como tal** y llevar identificado al remitente | Asunto sin engaño, firma con nombre y NIF |
| Debe incluir procedimiento de oposición sencillo y gratuito | Una frase, no un formulario |

**Recomendación operativa, por orden de riesgo de menor a mayor:**

1. **Entrega en mano del PDF.** No es comunicación electrónica: la LSSI no aplica.
   Es el canal principal del pipeline y el más sólido jurídicamente.
2. **Llamada telefónica.** Fuera del ámbito del art. 21. Verificar la lista
   Robinson solo si se llamara a personas físicas particulares; no aplica a
   centros.
3. **Correo a dirección genérica de empresa** con contenido informativo y aviso
   del art. 14. Riesgo bajo.
4. **Correo a dirección nominal de persona física.** El más expuesto. Usar solo
   cuando sea la única dirección publicada, y con la información del art. 14 en
   el propio cuerpo.

> El diseño del pipeline ya favorece el canal correcto: la ruta a pie y la
> entrega en mano son el eje, y el correo es el apoyo. Mantenerlo así.

## 6. Revisión

Se revisa esta valoración si cambia el volumen, el ámbito geográfico, el canal
principal o las categorías de datos tratadas. En todo caso, una vez al año.

| Fecha | Resultado |
|---|---|
| 2026-08-15 | Favorable con las cinco salvaguardas |
