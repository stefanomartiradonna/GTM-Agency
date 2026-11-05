# GTM Collective Brain

Questo è il sistema operativo del collettivo. Leggilo per intero ad ogni sessione prima di fare qualsiasi altra cosa.

---

## Struttura del repo

```
gtm-collective-brain/
├── CLAUDE.md                  ← questo file — sistema operativo
├── _agency/                   ← dati del collettivo stesso
│   ├── context/               — ICP, positioning, profile, personas, competitor radar
│   ├── knowledge/             — learnings cross-client del collettivo
│   ├── content/               — narrative e pillars
│   ├── kpi/                   — dashboard e benchmark
│   ├── outbound/              — campagne outbound proprie
│   └── outputs/               — asset prodotti internamente
├── _methodology/              ← metodologia condivisa (non duplicare per cliente)
│   ├── skills/                — tutte le skill operative
│   ├── playbooks/             — playbook per situazioni ricorrenti
│   ├── workflows/             — flussi operativi
│   └── signals/               — libreria e routing segnali
└── clients/                   ← un sottodir per ogni cliente
    └── client-[nome]/
        ├── context/           — ICP, positioning, personas del cliente
        ├── knowledge/         — learnings specifici del cliente
        ├── kpi/               — metriche del cliente
        └── outputs/           — asset prodotti per il cliente
```

---

## Chi siamo

Siamo un collettivo di 4 specialisti (P.I. individuali) che offrono un servizio di **GTM Engineering + Outbound with Signals** per startup B2B.

Non siamo un'agenzia di outbound classica. Non partiamo dalle campagne. Partiamo dall'analisi.

**Il nostro differenziatore**: le agenzie tradizionali iniziano con le sequenze dalla settimana uno, senza capire davvero il prodotto, il mercato o il buyer. Risultato: reply rate basso, lead sbagliati, nessun apprendimento. Noi passiamo prima 2 settimane a capire — chi è il buyer reale, quali problemi sente urgenti, quali segnali indicano una finestra d'acquisto. Solo dopo costruiamo i messaggi.

**Il modello**: analisi → asset operativi → outbound with signals → contenuto → iterazione continua.

**Target clienti**: startup B2B SaaS, pre-seed → serie A. Soglia minima: 8K MRR oppure funding ≥ 200K. Settori con track record: travel, HR, healthcare, gaming, cosmetica.

---

## Il nostro metodo

### GTM Engineering + Outbound with Signals

Invece di contattare aziende in modo indiscriminato dentro un ICP generico, intercettiamo momenti specifici che indicano una finestra d'acquisto reale — funding round appena chiuso, assunzione di un RevOps Manager, adozione di un nuovo stack tecnologico. Chi si muove in quel momento converte a tassi 3-5x superiori.

Il processo opera su 4 livelli in parallelo:
1. **Analisi e strategia** — capire prima, agire dopo
2. **Asset operativi** — le analisi diventano homepage, deck, email, case study (non documenti statici)
3. **Outbound** — campagne basate su segnali, ottimizzate settimanalmente
4. **Contenuto e narrativa** — costruire autorevolezza su LinkedIn, gestito operativamente (non un piano editoriale)

### Principi di sistema

- **Signal decay**: un segnale perde valore nel tempo. Funding round a 10 giorni = alta priorità. A 180 giorni = irrilevante.
- **Signal combinations**: due segnali concorrenti valgono più della loro somma. Funding + hiring RevOps = priorità massima.
- **ICP prima di tutto**: senza ICP solido, segnali e sequenze sono costruiti su sabbia.
- **Analisi → asset**: ogni insight dell'analisi si traduce in materiale concreto. Niente documenti che non portano da nessuna parte.

---

## Come usare questo sistema

### Per il collettivo stesso (trovare nuovi clienti)
1. Leggi `_agency/context/icp-definition.md` — chi sono i nostri clienti ideali
2. Consulta `_methodology/signals/signal-library.md` — quali segnali stiamo monitorando
3. Usa `_methodology/skills/account-research/SKILL.md` — brief su un prospect prima di contattarlo
4. Usa `_methodology/skills/signal-to-sequence/SKILL.md` — segnale rilevato → campagna live
5. Ogni lunedì: `_methodology/skills/weekly-update/SKILL.md` — mantieni il contesto aggiornato
6. Dopo ogni campagna: `_methodology/skills/brain-update/SKILL.md` — aggiorna i learnings

### Per un nuovo cliente
1. Crea `clients/client-[nome]/` con sottocartelle: `context/`, `knowledge/`, `kpi/`, `outputs/`
2. Esegui `_methodology/skills/setup/SKILL.md` sul dominio del cliente — popola `clients/[nome]/context/` in 30 min
3. Affina con informazioni del kick-off (vedi `_methodology/workflows/client-onboarding.md`)
4. Fai la diagnosi plays con `_methodology/skills/gtm-plays-diagnostic/SKILL.md` — decidi quali motion attivare *prima* di costruire campagne
5. Opera con le skill in `_methodology/skills/` — outbound, segnali, content

### Quando lavori su un cliente specifico
- Leggi prima `_agency/context/` per il contesto del collettivo
- Poi leggi `clients/[nome]/context/` per i dati specifici del cliente
- Le skill globali (claude-brain) sono disponibili automaticamente — non servono path. Le skill operative del collettivo sono in `_methodology/skills/` e non vengono duplicate per cliente

### Skills disponibili

Le skill si dividono in due gruppi. Le skill globali vengono da **claude-brain** (`~/.claude/skills/`) e sono disponibili automaticamente — non servono path. Le skill operative sono specifiche di questo repo.

**Prerequisito**: claude-brain deve essere configurato sulla tua macchina. Setup: clona `https://github.com/martiraste-lgtm/claude-brain` → `~/.claude`

#### Skill globali (claude-brain — disponibili automaticamente)

| Skill | Quando usarla |
|-------|---------------|
| `b2b-positioning-diagnostic` | Positioning Dunford 5-step, post-PMF — fase 1 di ogni nuovo engagement |
| `positioning-framework-estner` | Positioning Estner Primary + Secondary anchor, pre-PMF o early post-seed |
| `gtm-icp-definition` | Costruire ICP strutturato per cliente |
| `saas-homepage-analyzer` | Analisi/creazione homepage cliente |
| `pricing-teardown` | Audit conversione di una pricing page (10 dimensioni: UX buyer + AI-agent readiness) |
| `sales-deck-creator` | Deck commerciale cliente (primo meeting / pitch / asset outbound) |
| `sales-demo-estner` | Preparare demo call con prospect già interessato — 10-step Estner + discovery SPICED + demo loop |
| `competitor-map-tittarelli` | Dossier standard su un competitor (13 dimensioni, minaccia, refresh). Dossier in `context/competitors/`, il landscape è `competitor-radar.md`. Poi `deep-research-gtm` solo sui primary |
| `winn-loss` | Dopo 5+ deal chiusi con call registrate: perché vinciamo, perdiamo o andiamo in churn. Sei dimensioni + quattro forze di Moesta. Alimenta ICP, positioning e messaging |
| `okr-hybrid` | Definire KPI con il cliente (uso interno) |
| `business-case-builder` | Stima/valutazione di un'opportunità in business case (metodo Tharin) — feature, iniziativa GTM o deliverable cliente |
| `account-research` | Brief approfondito su un prospect prima dell'outreach |
| `icp-scoring` | Qualificare e assegnare tier A/B/C a una lista di account |
| `signal-to-sequence` | Segnale rilevato → campagna outbound completa |
| `case-study-creator` | Dopo il primo risultato misurabile |
| `mkt1-marketing-strategy-setup` | Inizio engagement — orchestra tutte le skill MKT1 |
| `mkt1-company-overview` | Fondamenta: stage, modello, audience, competitive landscape |
| `mkt1-marketing-advantages` | Identifica i vantaggi marketing unici del business |
| `mkt1-perceptions` | Definisce le 3-4 narrative strategiche del mercato |
| `mkt1-channel-strategy` | Determina il channel mix giusto per stage e GTM motion |
| `mkt1-revenue-levers` | Prioritizza dove il marketing può avere impatto adesso |
| `mkt1-big-bets` | Progetta 1-3 campagne coordinate ad alto impatto |
| `mkt1-gaccs` | Brief operativo per ogni campagna o iniziativa |

#### Skill operative collettivo (`_methodology/skills/` — specifiche di questo repo)

| Skill | Quando usarla |
|-------|---------------|
| `setup` | Inizio di ogni nuovo engagement cliente — popola context/ |
| `gtm-plays-diagnostic` | Dopo strategia/positioning, prima della prima campagna — diagnosi di quali plays/motion attivare |
| `deep-research-gtm` | Ricerca GTM rigorosa (fonti + piano + citazioni) — teardown competitor o playbook interno, inline o scaffold esterno |
| `weekly-update` | Ogni lunedì — mantiene context/ e kpi/ aggiornati |
| `brain-update` | Dopo ogni campagna (2-4 settimane) — aggiorna knowledge/ |
| `preventivo` | Generare preventivo per il servizio GTM Engineering del collettivo |

---

## Regole apprese (aggiornato trimestralmente)

*Questa sezione viene aggiornata ogni trimestre con i pattern promossi da `_agency/knowledge/`. Inizia vuota e si popola con l'uso.*

---

## Stato corrente

**Data ultimo aggiornamento**: 2026-04-20
**Fase**: Sistema in setup — nessuna campagna attiva ancora
**ICP prioritario**: Startup B2B SaaS (pre-seed/seed/serie A) con trigger round o stallo pipeline, settori travel/HR/healthcare/gaming/cosmetica, min. 8K MRR o 200K+ funding
**Campagne attive**: nessuna
**Segnali più performanti**: da popolare — vedi `_agency/knowledge/signals/confirmed.md`
**Pricing beta**: 2.500-3.000 €/mese | target: 5.000 €/mese
**Next actions**: avviare primo outbound su noi stessi, raccogliere dati campagna 1, fare brain-update dopo 2-4 settimane

---

## File da leggere per contesto completo

- `_agency/context/profile.md` — dettaglio su chi siamo
- `_agency/context/icp-definition.md` — ICP con tier e criteri
- `_agency/context/positioning.md` — come ci posizioniamo
- `_methodology/signals/signal-library.md` — tutti i segnali con scoring
- `_agency/knowledge/INDEX.md` — mappa di tutto il knowledge accumulato
