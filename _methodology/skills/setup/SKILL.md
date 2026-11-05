---
name: setup
description: Popola automaticamente context/ ricercando un dominio pubblicamente. Usare all'inizio di ogni nuovo engagement cliente o per aggiornare il profilo del collettivo. Trigger: "set up this repo for [domain]", "popola il contesto per", "setup per nuovo cliente [nome]".
license: MIT
metadata:
  author: GTM Collective (adattato da KarlRaf/gtm-starter-kit)
  version: 1.0.0
---

## Overview

Ricerca pubblica su un dominio e popola automaticamente i file `clients/[nome]/context/`. Tempo stimato: 30-60 minuti. Richiede conferma prima di sovrascrivere file esistenti.

---

## Instructions

### Step 1 — Ricevi il dominio

Chiedi se non fornito: "Per quale dominio devo fare il setup? (es. acme.com)"

### Step 2 — Ricerca pubblica

Ricerca le seguenti fonti nell'ordine:

1. **Sito web** (`dominio.com`): prodotto, clienti citati, pricing (se visibile), tech stack visibile, CTA principale
2. **LinkedIn aziendale**: dimensione team, hiring recente, post fondatori, settore dichiarato
3. **Crunchbase**: funding history, investor, founding date, team size, descrizione
4. **Job posting**: cercare su LinkedIn/Indeed per capire stack usato, ruoli in espansione, problemi che stanno risolvendo internamente
5. **Google News**: notizie recenti, PR, menzioni in media
6. **G2 / Capterra** (se SaaS): categorie, recensioni, competitor elencati
7. **Evidenze sui clienti**: pagina clienti, case study, testimonial, loghi in homepage, pagine soluzioni o settori, pagina integrazioni. Sono la base della bozza ICP.

Per ogni fonte usata, annota URL e data di accesso: finiscono nella sezione Fonti della bozza ICP.

### Step 3 — Popola context/

Crea o aggiorna questi file con i dati trovati:

**`clients/[nome]/context/profile.md`**:
- Chi sono, cosa fanno, prodotto principale
- Clienti citati (se presenti)
- Team size e fondatori
- Stage e funding (se disponibile)

**`clients/[nome]/context/icp-definition.md`** (prima bozza, outside-in):

Apri con un TLDR di 3 righe, una confidenza da 1 a 5 e un avviso fisso: *"Bozza da evidenze pubbliche. I clienti in vetrina sono quelli che l'azienda sceglie di mostrare, non per forza quelli che comprano meglio. Da validare in kick-off e con gtm-icp-definition."*

Poi:
1. **Tabella evidenze clienti**: una riga per cliente citato pubblicamente. Colonne: azienda, settore, dimensione, regione, ruolo della persona citata, problema descritto, risultato riportato, tool menzionati, fonte (URL).
2. **Normalizzazione**: metti dimensione, settore e regione in fasce coerenti (es. 1-10 / 11-50 / 51-200 / 201-1000 / 1000+ dipendenti), così si possono contare.
3. **Segmenti candidati (2-4)**: con il conteggio dietro ("5 case study su 12"). Un solo logo, anche grande, non è un segmento. Integra con quello che dicono i job posting (ruoli in espansione, problemi interni) per ipotizzare il ruolo decisore.
4. **Proof point**: clienti con risultato riportato e URL.
5. **Voice of customer pubblica**: frasi testuali da testimonial e recensioni, attribuite al ruolo, mai parafrasate. Segnala che sono testi già revisionati dal marketing: la VoC vera arriva da interviste e call.
6. **Data gaps**: cosa manca e cosa lo colmerebbe (lista clienti, churn, interviste, export CRM). Diventa l'agenda dati del kick-off.
7. **Fonti**: URL e data di accesso.

Regole: niente nomi di clienti inventati, niente citazioni composte unendo più frasi. Se il campione è piccolo, dillo una volta nella confidenza, non in ogni sezione.

**`clients/[nome]/context/competitor-radar.md`** (prima bozza):
- Competitor menzionati sul sito o su G2
- Come si posizionano rispetto a loro (se visibile)

**`clients/[nome]/context/positioning.md`** (prima bozza):
- Headline del sito → che problema risolvono?
- CTA principale → a chi si rivolgono?
- Linguaggio usato → tecnico? business? consumer?

### Step 4 — Chiedi le 5 domande di raffinamento

Dopo la ricerca automatica, chiedi queste domande (opzionali — l'utente può saltarle):

1. C'è qualcosa di importante sul prodotto che non trovo online?
2. Chi è il vostro cliente ideale — quello che porta più valore?
3. Qual è la principale obiezione che sentite nelle call?
4. Quali competitor considerate più pericolosi?
5. C'è un deal recente (vinto o perso) che ha insegnato qualcosa?

### Step 5 — Conferma e salva

Mostra un sommario di cosa hai popolato. Chiedi conferma prima di salvare se ci sono file esistenti da sovrascrivere.

---

## Examples

```
Prompt: "Read skills/setup/SKILL.md and set up this repo for acme.com"
Output: clients/[nome]/context/profile.md, clients/[nome]/context/icp-definition.md, clients/[nome]/context/competitor-radar.md, clients/[nome]/context/positioning.md popolati con dati da ricerca pubblica.
```

---

## Troubleshooting

**Sito non informativo**: usa LinkedIn aziendale come fonte principale. Job posting sono spesso più descrittivi del sito.
**Nessun funding trovato**: non è un problema. Nota "funding: non noto" e procedi.
**Competitor non trovati**: lascia `competitor-radar.md` con la struttura vuota — verrà compilato in kick-off.
