---
description: Avvia un audit di prodotto su un cliente esistente o nuovo, usando la skill product-audit
argument-hint: <client-slug> [url] [--dominio=<dominio>] [--profondita=rapida|standard|estesa]
---

Esegui un audit di prodotto usando la skill `product-audit`.

Argomenti ricevuti: $ARGUMENTS

Procedi in questo ordine:

1. **Risolvi il contesto cliente.** Se esiste `clients/$1/context.md`, leggilo: i parametri che contiene non vanno richiesti all'utente. Se non esiste, crealo partendo da `assets/client-context-template.md` della skill e chiedi all'utente solo i campi necessari a questo audit, non l'intera scheda.

2. **Crea la cartella di run** `clients/$1/audits/<AAAA-MM-GG>/` con dentro `intake.md` generato da `assets/intake-template.md` e la sottocartella `evidence/`.

3. **Completa l'intake.** Precompila quanto ricavabile dal contesto cliente e dagli argomenti del comando. Se manca un parametro bloccante, chiedilo all'utente in un unico blocco e fermati in attesa di risposta.

4. **Esegui l'audit** seguendo le fasi della skill. Salva ogni evidenza in `evidence/` con nome parlante e referenziala nel report.

5. **Produci il report** in `clients/$1/audits/<AAAA-MM-GG>/report.md` secondo `references/report-structure.md`, e converti nel formato di consegna richiesto.

6. **Aggiorna il contesto cliente** aggiungendo l'audit allo storico in `clients/$1/context.md`.
