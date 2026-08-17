# Legal — Agendia

Documentación de cumplimiento común a los tres subproyectos (`clinicas-web`,
`gtm-clinicas`, `UnicornIA-CRM`). Ninguno de estos documentos se publica en la
web: son los que hay que poder enseñar cuando alguien pregunta.

Última revisión: 15 de agosto de 2026.

## Qué hay aquí

| Documento | Qué es | Cuándo lo necesitas |
|---|---|---|
| [registro-actividades-tratamiento.md](registro-actividades-tratamiento.md) | RAT del art. 30 RGPD | Ya. Es obligatorio y la AEPD lo pide primero en cualquier inspección |
| [interes-legitimo-outbound.md](interes-legitimo-outbound.md) | Valoración de interés legítimo (LIA) del correo y la visita en frío | Antes del primer envío del pipeline `gtm-clinicas` |
| [aviso-primer-contacto.md](aviso-primer-contacto.md) | Texto del art. 14 para email, PDF y guion de puerta | En cada contacto en frío, sin excepción |
| [contrato-encargado-tratamiento.md](contrato-encargado-tratamiento.md) | Plantilla del contrato del art. 28 | Firmado **antes** de recibir el primer registro de un cliente |

## Lo que falta rellenar

Estos huecos bloquean la publicación de la web y la primera venta. Están
marcados como `PENDIENTE_` en el código y como «PENDIENTE» en estos documentos.

| Hueco | Dónde aparece | Cómo se resuelve |
|---|---|---|
| NIF | `clinicas-web/src/lib/sitio.ts`, RAT, contrato art. 28 | Es tu NIF. 30 segundos |
| Domicilio fiscal | Igual que el anterior | El que conste en el modelo 036/037 |
| Correo de negocio | `sitio.ts` — hoy hay un Gmail personal | `hola@agendia.es` al comprar el dominio |
| Teléfono de negocio | `sitio.ts` — Q-06 | Número propio, no el personal. Es el argumento de venta |
| Proveedor de alojamiento | RAT (A3), contrato anexo III | Depende de dónde se despliegue |
| Proveedor de modelo de lenguaje | RAT (A6), contrato anexo III | El que se contrate, con región europea |
| Seguro de responsabilidad civil profesional | Contrato, cláusula 11 | No es obligación legal. Sí es lo que pregunta una clínica seria |

## El orden

1. Rellenar NIF y domicilio → desbloquea aviso legal y privacidad → **publicar la web**
2. Firmar el RAT (fecharlo y guardarlo) → obligación en vigor desde el primer tratamiento
3. LIA + aviso del art. 14 → **antes** de que salga el primer correo de `gtm-clinicas`
4. Contrato art. 28 revisado por abogado → antes de la primera clínica

## Qué está ya implementado en código

| Salvaguarda | Dónde |
|---|---|
| Lista de exclusión permanente, consultada antes de cada contacto | `gtm-clinicas/scripts/10-excluir.mjs` + filtro en los scripts 3, 4, 5 y 6. Falla cerrado si el fichero no existe |
| Datos personales fuera del control de versiones | `gtm-clinicas/.gitignore` — verificado con `git ls-files` |
| Cabeceras de seguridad (art. 32) | `clinicas-web/public/_headers` y `vercel.json` |
| Cero terceros con almacenamiento en el navegador | `clinicas-web` sin embed de Cal.com (DEC-017) |

Lo que sigue siendo papel y no código: el RAT, la LIA, los textos del art. 14 —
que hay que **pegar** en cada correo y en el PDF— y el contrato del art. 28.

## Lo que esto no es

Plantillas de trabajo redactadas contra el RGPD, la LOPDGDD y la LSSI-CE
vigentes. **No sustituyen a revisión jurídica**, y el contrato del art. 28 es
justamente el documento donde eso importa: lo firma un tercero y regula
responsabilidad sobre datos de salud.
