---
title: "Prototipare con Lovable"
date: 2026-01-03
draft: false
type: "blocco-appunti"
layout: "single"
image: "/assets/img/lova.webp"
---

Ho usato Lovable per costruire un prototipo di web app — uno strumento per la gestione e valutazione dei fornitori. Caricamento documenti, scadenze, valutazioni, dashboard, comunicazioni.

<img src="/assets/img/lova.webp">

Il flusso di lavoro era semplice e ripetitivo: descrivevo ogni parte dell'applicazione man mano che la struttura si definiva, trasformavo le richieste in prompt ottimizzati per Lovable, verificavo l'output e tornavo in chat per affinare. Questo approccio ha permesso di procedere per iterazioni rapide, correggendo solo ciò che emergeva di volta in volta.

## Workflow

Descrivere → generare il prompt → incollare in Lovable → verificare → correggere. Ogni ciclo durava pochi minuti. Senza sprechi, senza riscrivere da zero.

## Cosa è stato affinato

La coerenza dei dati tra liste e dettaglio dei fornitori era il punto più critico. Le logiche di scadenza documenti, le categorie di file, i campi di valutazione (numerici, range, liste) hanno richiesto più passaggi per diventare coerenti. Lo stesso vale per le comunicazioni e i template email.

La visibilità dei menu in base al tipo di utenza — admin vs. fornitore — è stata una delle ultime cose sistemate, ma una delle più importanti. Tutto questo senza mai toccare la logica di base già generata: solo chiarire e rendere coerente ciò che Lovable doveva produrre.

## Risultato

Il prototipo è completo e copre tutte le pagine e le interazioni principali. Può essere trasformato nella versione finale usando il design system esistente, senza ripartire da zero.

{{< nota tipo="processo" >}}
Tool utilizzati: [Lovable](https://lovable.dev) · [Copilot](https://copilot.microsoft.com/)
{{< /nota >}}
