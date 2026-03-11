# MSMBRC — Sito Hugo

## Struttura contenuti

```
content/
├── posts/              ← Post in italiano
├── portfolio/          ← Progetti portfolio in italiano
├── blocco-appunti/     ← Appunti in italiano
├── libri/              ← Libri
├── videogame/          ← Videogame
└── en/                 ← Tutto il contenuto in inglese (stesso percorso)
    ├── posts/
    ├── portfolio/
    └── blocco-appunti/
```

---

## Flusso per pubblicare contenuti in DUE lingue

### Nuovo Post

```bash
# Crea il file italiano
hugo new posts/nome-post.md

# Crea il file inglese (stesso slug)
hugo new --contentDir content/en posts/nome-post.md
```

Poi modifica i due file: `content/posts/nome-post.md` e `content/en/posts/nome-post.md`.

Il toggle IT/EN nell'header cambierà automaticamente tra i due.

---

### Nuovo Progetto Portfolio

```bash
# Italiano
hugo new portfolio/nome-progetto.md

# Inglese
hugo new --contentDir content/en portfolio/nome-progetto.md
```

**Front matter del portfolio:**
```yaml
---
title: "Titolo del Progetto"
date: 2026-01-01
tag: "UX / UI"          # ← tag mostrato sulla card (UX / UI | Dev | Design System | Writing | ecc)
description: "Breve descrizione visibile nella card (max 2 righe)"
---
```

---

### Nuovo Appunto (blocco-appunti)

```bash
# Italiano
hugo new blocco-appunti/nome-appunto.md

# Inglese
hugo new --contentDir content/en blocco-appunti/nome-appunto.md
```

---

## Come funziona il toggle della lingua

Il pulsante `IT/EN` nell'header fa un redirect automatico:
- `msmbrc.github.io/portfolio/` → `msmbrc.github.io/en/portfolio/`
- `msmbrc.github.io/en/posts/` → `msmbrc.github.io/posts/`

Non serve configurazione aggiuntiva: basta che esista il file nella cartella `content/en/` con lo stesso slug.

**Regola pratica:** se il file IT è `content/posts/mio-post.md`, quello EN deve essere `content/en/posts/mio-post.md`.

---

## Note sul Portfolio

Le card dei progetti aprono una **modale** (stile Appunti) con il contenuto completo del file `.md`.

La sezione "Esperienze lavorative" e "Categorie attive" sono statiche nel layout `layouts/portfolio/list.html` — modificale direttamente lì.

---

## Build e deploy

```bash
hugo server          # sviluppo locale
hugo --minify        # build produzione
```

---

## Contenuti già tradotti (presenti nel progetto)

| Sezione | IT | EN |
|---|---|---|
| Posts/eccomi | `content/posts/eccomi.md` | `content/en/posts/eccomi.md` |
| Posts/graziano | `content/posts/grazianovisconti.md` | `content/en/posts/grazianovisconti.md` |
| Posts/corsa | `content/posts/corsa-8-marzo.md` | `content/en/posts/corsa-8-marzo.md` |
| Appunti/hugo | `content/blocco-appunti/hugo-info-base.md` | `content/en/blocco-appunti/hugo-info-base.md` |
| Appunti/lovable | `content/blocco-appunti/prototipare-con-lovable.md` | `content/en/blocco-appunti/prototipare-con-lovable.md` |
| Videogame | `content/videogame/_index.md` | `content/en/videogame/_index.md` |
| Libri | `content/libri/_index.md` | `content/en/libri/_index.md` |
| Portfolio (×4) | `content/portfolio/*.md` | `content/en/portfolio/*.md` |
