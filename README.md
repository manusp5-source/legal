# Legal — Agendia

Compliance documentation shared across the three sub-projects (`clinicas-web`,
`gtm-clinicas`, `UnicornIA-CRM`). None of these documents get published on the
website: they're the ones you need to be able to show when someone asks.

Last reviewed: August 15, 2026.

Note: the four legal documents listed below are Spanish-law templates and are
intentionally kept in Spanish — translating them would undermine their legal
validity in Spain.

## What's here

| Document | What it is | When you need it |
|---|---|---|
| [registro-actividades-tratamiento.md](registro-actividades-tratamiento.md) | RAT (Records of Processing Activities) under GDPR art. 30 | Now. It's mandatory, and the AEPD (Spain's data protection authority) asks for it first in any inspection |
| [interes-legitimo-outbound.md](interes-legitimo-outbound.md) | Legitimate interest assessment (LIA) for cold email and in-person visits | Before the first send of the `gtm-clinicas` pipeline |
| [aviso-primer-contacto.md](aviso-primer-contacto.md) | Art. 14 notice text for email, PDF, and the door script | On every cold contact, no exceptions |
| [contrato-encargado-tratamiento.md](contrato-encargado-tratamiento.md) | Art. 28 data processing agreement (DPA) template | Signed **before** receiving a client's first record |

## What's still missing

These gaps block the website launch and the first sale. They're marked
`PENDIENTE_` in the code and "PENDIENTE" in these documents.

| Gap | Where it appears | How to resolve it |
|---|---|---|
| NIF (Spanish tax ID) | `clinicas-web/src/lib/sitio.ts`, RAT, art. 28 contract | It's your NIF. 30 seconds |
| Registered business address | Same as above | Whatever's on file in tax form 036/037 |
| Business email | `sitio.ts` — currently a personal Gmail | `hola@agendia.es` once the domain is purchased |
| Business phone | `sitio.ts` — Q-06 | A dedicated number, not the personal one. It's a selling point |
| Hosting provider | RAT (A3), contract annex III | Depends on where it gets deployed |
| Language model provider | RAT (A6), contract annex III | Whichever gets contracted, with a European region |
| Professional liability insurance | Contract, clause 11 | Not a legal requirement. It is what a serious clinic will ask about |

## The order

1. Fill in NIF and address → unlocks the legal notice and privacy pages → **publish the website**
2. Sign the RAT (date it and keep it on file) → obligation in effect from the first processing activity
3. LIA + art. 14 notice → **before** the first `gtm-clinicas` email goes out
4. Art. 28 contract reviewed by a lawyer → before the first clinic

## What's already implemented in code

| Safeguard | Where |
|---|---|
| Permanent do-not-contact list, checked before every outreach | `gtm-clinicas/scripts/10-excluir.mjs` + filter in scripts 3, 4, 5, and 6. Fails closed if the file doesn't exist |
| Personal data kept out of version control | `gtm-clinicas/.gitignore` — verified with `git ls-files` |
| Security headers (art. 32) | `clinicas-web/public/_headers` and `vercel.json` |
| Zero third parties with browser storage | `clinicas-web` has no Cal.com embed (DEC-017) |

What's still paper and not code: the RAT, the LIA, the art. 14 texts — which
have to be **pasted** into every email and PDF — and the art. 28 contract.

## What this is not

Working templates drafted against the current GDPR, LOPDGDD, and LSSI-CE.
**They do not replace legal review**, and the art. 28 contract is exactly the
document where that matters most: a third party signs it, and it governs
liability over health data.
