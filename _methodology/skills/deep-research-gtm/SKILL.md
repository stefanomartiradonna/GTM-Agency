---
name: deep-research-gtm
description: Metodologia di ricerca GTM rigorosa — gerarchia delle fonti, piano prima dell'esecuzione, citazioni in-text, freshness check, report a piramide. Due pattern coperti come playbook completi (teardown competitor, playbook di progetto interno); la metodologia è pattern-agnostica e si applica a qualsiasi ricerca decisionale. Esecuzione scelta volta per volta: inline coi nostri tool (WebSearch/WebFetch/Apify) o scaffold da incollare in ChatGPT Deep Research/Gemini. Trigger: "teardown competitor", "deep research su", "ricerca approfondita su", "compete brief su", "playbook per costruire X in-house", "analisi competitiva di [azienda]", "deep-research-gtm". NON usare per brief veloce mono-prospect (usa account-research), analisi editoriale per newsletter (usa company-teardown), audit homepage (usa saas-homepage-analyzer), battlecard feature (usa battlecard), market sizing/espansione (usa pm-market-research-market-sizing / beachhead-segment).
license: MIT
metadata:
  author: GTM Collective (adattato da Growth Unhinged "Deep Research for GTM")
  version: 1.0.0
---

## Overview

Esegue un workflow di Deep Research strutturato per progetti GTM. Invece di saltare alle ricerche web e riassumere la prima cosa che torna, questa skill:

1. Raccoglie il contesto che servirebbe a un ricercatore umano competente
2. Propone un research plan e aspetta l'OK prima di bruciare cicli
3. Prioritizza fonti di qualità e traccia cosa è stato usato dove
4. Consegna un report a piramide con citazioni, tabella fonti e disaccordi annotati

È il **muscolo dell'"analisi prima, agire dopo"** formalizzato. Rigorosa senza essere burocratica.

---

## Confine — quando NON usarla

Questa skill è la ricerca *rigorosa e multi-fonte*, quando la decisione vale 10-30 minuti. Non confonderla con le altre:

| Hai bisogno di… | Usa |
|---|---|
| Brief veloce su **un prospect** prima dell'outreach | `account-research` (globale) |
| Analisi **editoriale** long-form di un'azienda per la newsletter | `company-teardown` (globale) |
| Ricerca **shallow** per popolare il context cliente (30-60 min) | `skills/setup/` |
| **Dossier standard** su un competitor (13 dimensioni, livello di minaccia, refresh) | `competitor-map-tittarelli` (globale) |
| Cascata di **dati** per liste outbound | `workflows/enrichment.md` |
| Audit **homepage/landing** | `saas-homepage-analyzer` (globale) |
| **Battlecard / feature comparison** vs un competitor | `battlecard` / `pm-go-to-market-competitive-battlecard` (globali) |
| **Market sizing / espansione** (TAM-SAM-SOM, beachhead, Ansoff) | `pm-market-research-market-sizing`, `pm-go-to-market-beachhead-segment` (globali) |

**Nota importante**: i pattern audit/feature/market hanno già le loro skill (sopra). Questa skill copre come *playbook completi* solo **teardown competitor** e **playbook interno**. Ma la sua *metodologia* (gerarchia fonti, plan-first, piramide) si applica comunque anche a quei casi: puoi usarla come wrapper di rigore e poi consegnare l'output nel formato della skill globale giusta.

---

## I 4 principi core

Sono le quattro cose che separano un Deep Research utile da uno generico. Interiorizzali prima di ricercare.

1. **Le fonti fanno o rompono l'output.** I modelli trattano spesso le opinioni social come fatti, sovra-pesano un singolo blog, o citano dati vecchi. Contrasta questo: (a) specifica la priorità delle fonti nel piano, (b) per temi complessi compila una lista fonti a monte, (c) richiedi citazioni in-text + tabella fonti nell'output.

2. **Il contesto è lo sblocco.** Un report generico non serve. Prima di ricercare estrai: in quale azienda lavora il committente, cosa vuole *davvero* ottenere (non solo il task), quali vincoli valgono (budget, headcount, stack, timeline, no-go di legal/leadership).

3. **Piano prima dell'esecuzione.** Condividi un research plan prima. Copre tutto? Sono d'accordo sulla metodologia? Ci sono aree generiche perché manca contesto? Si sistema a monte, non dopo 20 minuti di ricerca.

4. **Il formato conta.** Default al Pyramid Principle — conclusioni e raccomandazioni in cima, evidenze dopo. Tabelle e bullet dove battono la prosa. Summary in cima al doc e in cima a ogni sezione.

---

## Workflow

### Step 0 — Scegli la modalità di esecuzione

Chiedi con **AskUserQuestion** (salvo l'utente l'abbia già detto):

- **Inline** — Claude esegue la ricerca dentro il sistema con WebSearch/WebFetch/Apify e consegna il report. Default per la maggior parte dei casi.
- **Scaffold esterno** — la skill genera un prompt XML da incollare in ChatGPT Deep Research/Gemini/Perplexity. Usalo quando vuoi più profondità/credito esterno o devi interagire con siti dinamici (ad library, dashboard loggati).

### Step 1 — Identifica il pattern

| Pattern | Segnale | Approccio |
|---|---|---|
| **Teardown competitor** | "Come si posiziona / vende / fa ads [competitor]?" | Priorità a fonti primarie (loro sito, docs, ad library); screenshot quando possibile |
| **Playbook interno** | "Come costruiamo X?" (attribution, lead scoring, comp, processi del collettivo) | Sintesi profonda + step-by-step tattico; appoggiati a blog di practitioner e docs dei tool |
| **Other** | Altro | Usa la struttura di prompt generica + il source-priority ladder |

Vedi `references/use-cases.md` per gli scaffold completi e le source-priority dei due pattern. Per audit pagina / feature compare / market expansion → rimanda alle skill globali (vedi box Confine), eventualmente applicando questa metodologia come wrapper.

**Parti dal dossier, se esiste.** Prima di un teardown competitor controlla se c'è già un dossier di `competitor-map-tittarelli` (`clients/[nome]/context/competitors/` o `_agency/context/competitors/`). Se c'è, il teardown parte da lì e approfondisce solo la domanda specifica, senza rifare l'inventario. Se non c'è e il competitor non è ancora classificato, proponi prima il dossier: il teardown profondo conviene sui competitor con minaccia "primary".

**Orchestrazione dentro il teardown competitor**: quando analizzi un competitor, la lettura GTM d'insieme la fai qui, ma per le viste che richiedono profondità **passi la palla alla skill specializzata e reincorpori il risultato come sezione del report** — homepage→`saas-homepage-analyzer`, pricing page→`pricing-teardown`, H1→`b2b-h1-writer`, feature compare→`battlecard`, positioning→`b2b-positioning-diagnostic`, market→`pm-market-research-market-sizing`. La tabella completa di hand-off è nel pattern 2 di `references/use-cases.md`. Distinzione: una richiesta *standalone* ("audita questa homepage") va direttamente alla skill globale; *dentro un teardown* quelle analisi diventano sotto-sezioni orchestrate da qui.

### Step 2 — Raccogli contesto dai file esistenti, poi colma i gap

**Non ripartire da zero.** Leggi prima ciò che è già popolato:
- Per un cliente: `clients/[nome]/context/` (profile, icp-definition, positioning, competitor-radar)
- Per il collettivo: `_agency/context/`

Estrai: azienda & situazione, **vero** obiettivo (non il task), vincoli, scope (geografia, orizzonte temporale, profondità, formato), lavoro pregresso esistente.

Solo per ciò che manca, chiedi 1-3 domande mirate con **AskUserQuestion**. Se il contesto è già ricco nella conversazione, salta le domande e conferma le assunzioni chiave in una riga.

### Step 3 — Proponi il research plan e aspetta l'OK

Prima di qualsiasi ricerca, scrivi un piano breve (≤200 parole):
- **Research questions**: le 3-6 domande specifiche a cui risponderai
- **Metodologia**: come valuterai (es. "confronto tier di pricing testa a testa")
- **Source priority**: Primary (sito, docs, dati gov) > practitioner > news > social. Dichiara cosa escludi.
- **Deliverable shape**: lunghezza, sezioni, tabelle/mockup/snippet
- **Assunzioni**: cosa stai assumendo che l'utente dovrebbe correggere

Chiedi: "Il piano ti torna? Da aggiungere, togliere o riformulare?" Aspetta l'OK prima di eseguire.

### Step 4 — Esecuzione

**Se modalità inline:**
Esegui WebSearch/WebFetch (e Apify per scraping di ad library, social, mappe, ecc.) contro le fonti prioritizzate. Mentre vai:
- Tieni una lista fonti running: URL, tipo (primary/practitioner/news/social), data, a cosa è servita
- Quando le fonti sono in disaccordo (specie sui dati), annotalo e indica la causa probabile (metodologia, definizioni, date diverse)
- Se trovi un dato di >12 mesi, verificalo con una ricerca fresca prima di usarlo
- Segnala i claim di marketing vaghi ("AI superiore") → trova esempi concreti o droppa il claim
- Budget: 8-15 fetch per un report standard; 20+ per teardown di ads/prodotto

**Se modalità scaffold esterno:**
Assembla il prompt XML dai blocchi in `references/use-cases.md` (`<goal>`, `<context>`, `<content>`, `<style>`, `<sources>`, `<instructions>`) per il pattern scelto. Includi solo le sezioni che servono. Consegna il prompt + il tool consigliato (vedi sotto), senza eseguire.

### Step 5 — Consegna il report (a piramide)

```
# [Titolo]

## TL;DR
- 3-5 bullet: conclusioni e raccomandazioni chiave, dette chiare

## [Sezione 1 — area/finding chiave]
**Summary:** 1-2 frasi.
[Dettagli, con citazioni in-text [1], [2]]

## [Sezione 2 — finding successivo]
...

## Raccomandazioni
Ordinate per impact × effort. Con note di implementazione.

## Fonti
| # | Fonte | Tipo | Data | Usata per |
|---|---|---|---|---|
| 1 | ... | Primary | 2025-08 | Confronto pricing |

## Disaccordi / caveat
- Dove le fonti confliggono, e cosa ho scelto di credere (e perché)
- Gap noti — cose che l'utente dovrebbe verificare di persona
```

Per i teardown di ads: includi esempi concreti con URL. Per i compete brief: includi copy suggerito.

### Step 6 — Follow-up + Bridge ai file del sistema

Dopo la consegna, suggerisci 1-3 next step naturali. E **non lasciare il report isolato**:
- **Teardown competitor** → aggiorna `clients/[nome]/context/competitor-radar.md` con la sintesi datata, e arricchisci la battlecard di `playbooks/competitor-switch.md` (Scenario 2).
- **Playbook interno** → versiona il risultato in `_methodology/` (se è un processo del collettivo) o in `knowledge/` del cliente.

---

## Tool-choice hint (per la modalità esterna)

- **ChatGPT Deep Research** — default. Massima profondità e rigore. Playbook interni, product compare, market expansion.
- **ChatGPT Agent Mode** — quando serve interazione reale con un sito (ad library, dashboard loggati, toggle su pagina). Teardown ads, documentazione di flussi, audit pagine con contenuto dinamico.
- **Gemini Deep Research** — fallback quando i crediti ChatGPT sono finiti. Mostra il piano a monte, limiti generosi.
- **Perplexity** — ricerca mirata su un sito specifico o forum; pulse check.
- **Claude / Grok** — report da 1-2k parole; buon entry point su un tema nuovo.

---

## Failure modes da evitare

- **Partire senza contesto.** Se non conosci azienda, obiettivo e vincoli, fermati e chiedi.
- **Saltare il piano.** Gli utenti hanno opinioni forti su metodologia e scope. Fai emergere il piano a basso costo.
- **Trattare i blog come fonti primarie.** Per i claim su prodotto/feature vai ai docs. Per i dati vai al dataset primario.
- **Lasciar passare claim vaghi.** "Capacità AI superiori" non è un finding. Pretendi un esempio concreto o taglia.
- **Dati stantii.** Feature e pricing cambiano di continuo. Qualsiasi cosa più vecchia di ~6 mesi vuole un freshness check.
- **Report wall-of-text.** Default a piramide + tabelle + summary di sezione. Se non si skimma in 2 minuti per avere il titolo, è troppo denso.

---

## Nota sul posizionamento del collettivo

La ricerca rigorosa **è** il differenziatore ("non partiamo dalle campagne, partiamo dall'analisi"), non un orpello. Ma non confondere rigore con burocrazia: il piano serve a non sprecare cicli, non a rallentare. Italiano, sempre. Tono da practitioner senior che dà consigli diretti.
