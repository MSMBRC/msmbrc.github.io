---
title: "Vivaldi browser, tab centrali"
date: 2026-03-26
draft: false
tags: ["guide"]
---

Codice per posizionare le tabs del browser Vivaldi al centro della barra.

## Passo 1: abilita le modifiche CSS

- Digita nella barra degli indirizzi: vivaldi://experiments
- Spunta l'opzione "Allow CSS modifications"

## Passo 2: creare il file CSS

Crea una cartella (es. VivaldiCSS) in un posto sicuro fuori dalla cartella di installazione di Vivaldi (che viene sovrascritta ad ogni aggiornamento), ad esempio in Documenti.
Dentro la cartella crea un file di testo chiamato custom.css e incolla questo codice:

```css

#tabs-container.top,
#tabs-container.bottom {
  width: 100% !important;
  display: flex !important;
  justify-content: center !important;
}

#tabs-container.top .resize,
#tabs-container.bottom .resize {
}

#tabs-container.top .tab-strip,
#tabs-container.bottom .tab-strip {
  display: flex !important;
  justify-content: center !important;
  position: relative !important;
}

#tabs-container.top .toolbar.toolbar-tabbar-after.toolbar-large.toolbar-droptarget, #tabs-container.bottom .toolbar.toolbar-tabbar-after.toolbar-large.toolbar-droptarget {
  position: absolute!important;
  width:100px;
    right: 0!important;
}

#tabs-container.bottom .window-buttongroup {
  /*position: absolute!important;
  width:100px;*/
      left: 0 !important;
}
#tabs-container.top .window-buttongroup {
  position: absolute!important;
  width:100px;
      left: 0 !important;
}

#tabs-container.top .tab-position,
#tabs-container.bottom .tab-position {
  position: relative !important;
  transform: none !important;
  left: auto !important;
  --PositionX: 0px !important;
}
```

## Passo 3: collega la cartella a Vivaldi

- Vai in Impostazioni → Aspetto
- Scorri fino alla sezione "Modifiche UI personalizzate"
- Clicca su "Seleziona cartella" e scegli la cartella VivaldiCSS che hai creato

## Passo 4: riavvia Vivaldi

Chiudi e riapri il browser: le tab dovrebbero ora apparire centrate.

---

<img src="/assets/img/vivaldi01.webp">

<img src="/assets/img/vivaldi02.webp" style="background:#E3E3E8">