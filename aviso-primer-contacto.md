*This document is a Spanish-law legal template and is intentionally kept in Spanish.*

# Aviso del art. 14 — textos para el primer contacto

Cuando los datos **no los da el interesado** sino que se obtienen de una fuente
pública, el art. 14 del RGPD obliga a informarle: quién eres, qué tratas, de
dónde salió, con qué base y cómo oponerse. El plazo máximo es un mes, pero si el
primer uso es una comunicación —y aquí lo es— hay que informar **en esa misma
comunicación** (art. 14.3.b).

Sin esto, la valoración de interés legítimo no sostiene nada: el art. 6.1.f
exige transparencia como condición, no como añadido.

Un texto por canal. **Ninguno es opcional.**

---

## 1. Correo electrónico

Va al final del mensaje, después de la firma. No en letra minúscula ni escondido.

```
—
PENDIENTE_NOMBRE_COMPLETO · NIF PENDIENTE_NIF · Agendia
PENDIENTE_EMAIL_NEGOCIO · PENDIENTE_TELEFONO_NEGOCIO

Sobre tus datos: te escribo a la dirección que tu clínica publica en su web.
Trato el nombre del centro y sus datos de contacto públicos para presentarte
este servicio, por interés legítimo en la prospección profesional (art. 6.1.f
RGPD). No los he comprado, no los cedo a nadie y los borro a los doce meses si
no hay respuesta.

Si no quieres recibir nada más, responde «baja» a este correo. Lo hago el mismo
día y no vuelvo a escribirte. Más detalle en agendia.es/legal/privacidad y
reclamación ante la AEPD en aepd.es.
```

Comprobaciones antes de enviar, cada vez:

- [ ] El asunto no engaña sobre el carácter comercial (LSSI art. 20).
- [ ] Va identificado el remitente con nombre y NIF.
- [ ] Es el primer o el segundo contacto. **Nunca el tercero.**
- [ ] La dirección no está en la lista de exclusión.

## 2. PDF de auditoría entregado en mano

Bloque al pie de la última página, cuerpo pequeño pero legible.

```
Cómo se hizo este informe

Los datos proceden de fuentes públicas —OpenStreetMap y la web de la propia
clínica— consultadas el DD/MM/AAAA. No se ha accedido a ningún sistema vuestro
ni se ha tratado dato de paciente alguno.

Trato los datos de contacto de la clínica para presentaros este servicio, por
interés legítimo (art. 6.1.f RGPD). Se conservan doce meses desde el último
contacto. Podéis oponeros escribiendo a PENDIENTE_EMAIL_NEGOCIO y dejo de
usarlos ese mismo día; también podéis reclamar ante la AEPD (aepd.es).

PENDIENTE_NOMBRE_COMPLETO · NIF PENDIENTE_NIF · agendia.es/legal/privacidad
```

## 3. Guion de puerta y de teléfono

No se lee un párrafo legal en voz alta: se dice en una frase y se deja el PDF,
que lleva el texto completo. La frase, cuando pregunten de dónde han salido los
datos —y van a preguntar:

> «De la web de la clínica y del mapa, nada más. No he entrado en ningún sistema
> vuestro ni tengo dato de ningún paciente. Todo lo que he mirado lo ve
> cualquiera que os busque desde fuera, y lo tenéis explicado al final del
> informe.»

Si piden no volver a ser contactados: se anota en la lista de exclusión **en el
momento**, delante de ellos si se puede. Es la respuesta que más confianza genera
de todas las posibles.

## 4. Lista de exclusión

| Regla | Detalle |
|---|---|
| **Dónde** | `gtm-clinicas/data/exclusion.csv` — fuera del repositorio, como el resto de `data/` |
| **Qué se guarda** | Solo lo mínimo para reconocer el contacto: id de ficha, nombre, correo o teléfono, fecha, canal y motivo |
| **Cuánto** | Indefinidamente. Es la única forma de garantizar que no se vuelve a contactar (art. 21.3 RGPD) |
| **Cuándo se comprueba** | Antes de **cada** envío o ruta, no una vez al mes |
| **Quién puede sacar a alguien de la lista** | Nadie, salvo petición expresa del propio interesado |

**Implementado el 15/08/2026.**

```bash
npm run excluir -- --init                      # una sola vez
npm run excluir -- --nombre="Clínica X" --motivo="baja en el mostrador"
npm run excluir -- --email=info@clinica.es --canal=email
npm run excluir -- --telefono="958 20 30 40" --canal=telefono
npm run excluir -- --listar
```

Cuatro scripts la consultan antes de generar material de contacto —informes
(`3`), ruta (`4`), emails (`5`) y priorización (`6`)— y **paran si el fichero no
existe**. Reconoce el contacto por id, correo (también dentro de `emails_todos`),
teléfono en cualquier formato y nombre, con o sin municipio.

Se apunta **en el momento de la petición**, delante del interesado si se puede.
Entre la petición y el apunte cabe un envío.
