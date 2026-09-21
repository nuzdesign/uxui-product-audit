# Integrazione nel UX/UI Product Studio

## Collocazione dei file

```
ux-ui-product-studio/
├── CLAUDE.md
├── .claude/
│   ├── skills/
│   │   └── product-audit/          ← contenuto di product-audit.skill
│   │       ├── SKILL.md
│   │       ├── references/
│   │       │   ├── visual-psychology.md
│   │       │   ├── information-architecture.md
│   │       │   ├── heuristics-nielsen.md
│   │       │   ├── accessibility-wcag22.md
│   │       │   ├── report-structure.md
│   │       │   └── domains/
│   │       │       ├── _generic.md
│   │       │       ├── editorial.md
│   │       │       ├── ecommerce.md
│   │       │       ├── saas.md
│   │       │       ├── pa-institutional.md
│   │       │       └── corporate.md
│   │       └── assets/
│   │           ├── intake-template.md
│   │           └── client-context-template.md
│   └── commands/
│       └── audit.md                ← lo slash command
└── clients/
    └── <slug>/
        ├── context.md
        └── audits/
            └── <AAAA-MM-GG>/
                ├── intake.md
                ├── evidence/
                └── report.md
```

Se la tua alberatura usa nomi diversi per `clients/`, correggi i percorsi in `audit.md`: sono le uniche tre righe da adattare. La skill in sé non contiene percorsi hardcoded.

## Riga da aggiungere al CLAUDE.md

```
- Per qualsiasi audit, review o assessment di un prodotto digitale esistente, usa la skill `product-audit`. Non improvvisare un'analisi: la skill definisce intake obbligatorio, scala di severity e struttura del report.
```

## Prerequisiti per un audit completo

L'unico requisito reale è l'accesso al sito con rendering. Senza browser la skill si degrada a analisi del markup e dichiara il limite nelle assunzioni, che è corretto ma dimezza il valore del documento. Verifica di avere attivo almeno uno tra Playwright MCP, Chrome DevTools MCP o un browser MCP equivalente prima del primo run reale.

## Estensioni previste

- `scripts/capture_responsive.py` — cattura automatica delle schermate ai tre breakpoint e salvataggio in `evidence/`. Da scrivere quando è noto quale tooling browser è attivo nello studio
- `scripts/contrast_check.py` — estrazione delle coppie colore testo/sfondo dal DOM e calcolo del rapporto di contrasto
- Nuovi file in `references/domains/` man mano che arrivano settori non coperti

## Primo run consigliato

Esegui il primo audit su un sito che conosci già bene, così puoi giudicare la qualità dell'output invece che il contenuto. Confronta il risultato con quello che avresti scritto tu: le differenze indicano cosa manca nei reference.
