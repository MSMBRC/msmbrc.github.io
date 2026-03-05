# MSMBRC — Guida completa

Blog personale basato su **Hugo**, pubblicato su **GitHub Pages** con deploy automatico.

---

## Struttura del progetto

```
msmbrc/
├── .github/workflows/deploy.yml   → deploy automatico su ogni push
├── archetypes/posts.md             → template per i nuovi post
├── content/posts/                  → qui vivono tutti i tuoi post (.md)
├── layouts/
│   ├── _default/                   → template HTML delle pagine
│   ├── partials/                   → header e footer riutilizzabili
│   └── shortcodes/post-link.html   → componente link visivo
├── static/
│   ├── assets/global/              → profilo.jpg, headerone.jpg
│   ├── assets/img/                 → immagini dei post
│   └── css/main.css                → tutto il CSS del sito
└── hugo.toml                       → configurazione Hugo
```

---

## SETUP INIZIALE (una volta sola)

### 1. Installa Hugo sul tuo Mac

```bash
brew install hugo
```

Verifica:
```bash
hugo version
```

### 2. Crea il repository su GitHub

1. Vai su [github.com](https://github.com) → **New repository**
2. Nome repository: `TUOUSERNAME.github.io`  
   *(sostituisci TUOUSERNAME con il tuo username GitHub)*
3. Imposta come **Public**
4. Non aggiungere README né .gitignore (li abbiamo già)
5. Clicca **Create repository**

### 3. Modifica il file `hugo.toml`

Apri `hugo.toml` e cambia la prima riga:

```toml
baseURL = "https://TUOUSERNAME.github.io/"
```

Sostituisci `TUOUSERNAME` con il tuo username GitHub reale.

Puoi anche aggiornare i tuoi dati personali nella sezione `[params]`.

### 4. Carica il progetto su GitHub

```bash
cd msmbrc                          # entra nella cartella
git init                           # inizializza git
git add .                          # aggiungi tutti i file
git commit -m "primo commit"       # primo commit
git branch -M main                 # rinomina il branch in main
git remote add origin https://github.com/TUOUSERNAME/TUOUSERNAME.github.io.git
git push -u origin main            # carica su GitHub
```

### 5. Attiva GitHub Pages

1. Sul tuo repository GitHub → **Settings** → **Pages**
2. In **Source** seleziona: **GitHub Actions**
3. Salva

GitHub avvierà automaticamente il primo deploy. Dopo 2-3 minuti il sito sarà live su:  
`https://TUOUSERNAME.github.io`

---

## PUBBLICARE UN NUOVO POST

### Metodo rapido (da terminale)

```bash
cd msmbrc
hugo new posts/titolo-del-post.md
```

Hugo crea automaticamente il file in `content/posts/` con la data di oggi.  
Aprilo con qualsiasi editor di testo (TextEdit, VS Code, etc.).

### Struttura di un post

```markdown
---
title: "Il titolo del tuo post"
date: 2026-03-10
draft: false
---

Primo paragrafo del post. Scrivi normalmente.

Secondo paragrafo. Vai a capo due volte per creare un nuovo paragrafo.

Puoi usare **grassetto**, *corsivo*, e [link classici](https://esempio.com).
```

> **Importante:** finché `draft: true`, il post non viene pubblicato.  
> Cambia in `draft: false` quando è pronto.

---

## TIPI DI CONTENUTO

### Testo semplice

Scrivi normalmente in Markdown. I link scritti così:

```markdown
Leggi [questo articolo](https://esempio.com) per saperne di più.
```

appaiono con il classico stile sottolineato.

---

### Immagine standard

```markdown
![Descrizione](../assets/img/nome-immagine.jpg)
```

Metti l'immagine nella cartella `static/assets/img/` prima di usarla.

---

### Link card visivo (shortcode post-link)

Usa questo componente quando vuoi condividere un link in modo visivo,  
con immagine e titolo, come una preview:

```
{{</* post-link 
  url="https://esempio.com/articolo" 
  title="Titolo dell'articolo che condividi" 
  image="/assets/img/cover-articolo.jpg" 
*/>}}
```

**Parametri:**
- `url` — URL esterno (obbligatorio)
- `title` — Titolo mostrato nella card (obbligatorio)  
- `image` — Immagine di anteprima (opzionale — se omessa appare un'icona 🔗)

Se non vuoi il blocco visivo, usa semplicemente un link Markdown normale.

---

### Struttura mista (testo + immagine + link card)

```markdown
Prima parte del testo.

![Una foto](/assets/img/foto.jpg)

Testo dopo l'immagine che commenta quanto sopra.

{{</* post-link url="https://fonte.com" title="Fonte dell'articolo" */>}}

Conclusione del post.
```

---

## AGGIORNARE IL SITO

Ogni volta che vuoi pubblicare qualcosa:

```bash
cd msmbrc

# (scrivi o modifica i file in content/posts/)

git add .
git commit -m "nuovo post: titolo"
git push
```

GitHub fa tutto il resto automaticamente. Dopo circa 1-2 minuti il sito è aggiornato.

---

## AGGIORNARE LE IMMAGINI DI PROFILO

- **Foto profilo:** sostituisci `static/assets/global/profilo.jpg`
- **Banner header:** sostituisci `static/assets/global/headerone.jpg`

Poi fai `git add . && git commit -m "aggiorno immagini" && git push`.

---

## ANTEPRIMA LOCALE (opzionale)

Prima di pubblicare puoi vedere il sito in locale:

```bash
cd msmbrc
hugo server
```

Apri nel browser: `http://localhost:1313`

Il sito si aggiorna in tempo reale mentre scrivi. Premi `Ctrl+C` per fermarlo.

---

## DOMANDE FREQUENTI

**Come cambio il numero di post per pagina?**  
In `hugo.toml`, modifica: `paginate = 7`

**Come cambio il mio nome/bio/Twitter?**  
In `hugo.toml`, modifica la sezione `[params]`.

**Il deploy fallisce — come capisco perché?**  
Su GitHub → tab **Actions** → clicca sul workflow fallito → leggi i log.

**Posso avere post senza immagine nel post-link?**  
Sì, ometti semplicemente il parametro `image`. Apparirà un'icona 🔗 al posto dell'immagine.
# msmbrc.github.io
