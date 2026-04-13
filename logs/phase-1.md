# Phase 1 Log: Native Setup on Mac Mini

## [Lun 13 apr] - Setup Iniziale
- **Obiettivo:** Settare e utilizzare la dashboard di OpenClaw, il bot Telegram e SearXNG in locale. Poiché il pericolo numero 1 è l'accesso malevolo al bot, la priorità assoluta è la sicurezza. Effettuare prove e test generali del sistema.
- **Risultato:** Raggiunto. La struttura di base e la ricerca web funzionano, sebbene il sistema risulti un po' lento nelle comunicazioni.

- **Problemi riscontrati:**
  - **Latenza:** Latenza generale e difficoltà a comunicare in modo fluido tramite Telegram.
  - **Interruzioni Task:** Le operazioni o i comandi troppo lunghi si bloccano a metà e l'agente non continua ad aggiornarmi sullo stato di avanzamento.
  - **Iniziativa non richiesta:** Gli ho spiegato che *potevo* stoppare io momentaneamente il container di SearXNG per non far rilevare la porta web aperta durante l'audit. Ha frainteso e ha stoppato il container Docker da solo, senza che glielo avessi chiesto esplicitamente!
  - **Loop Logici:** La chat su Telegram ha portato diverse volte il bot a bloccarsi e rispondere con lo stesso identico messaggio a domande diverse (sembra che i problemi di "loop" nelle risposte siano tipici dei modelli più piccoli quando il contesto si riempie troppo).
  - **Gestione File:** Fa fatica a gestire e modificare i file di sistema. Non mi è ancora chiaro se questo avvenga per evitare danni (sicurezza), per qualche configurazione errata nei suoi file `.md`, o semplicemente per i limiti del modello stesso (Gemma4:e4b).

- **Prossimo test:** Effettuare un security audit completo e risolvere tutte le eventuali segnalazioni di vulnerabilità. Prendere ulteriore dimestichezza con le dinamiche e i limiti del sistema.
