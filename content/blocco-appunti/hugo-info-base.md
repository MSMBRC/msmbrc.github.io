---
title: "Hugo — info base"
date: 2026-01-20
type: "blocco-appunti"
draft: false
image: "/assets/img/appunto_hugo.webp"
---

Hugo è un generatore di siti statici. Significa che alla fine ti sputa fuori file `.html` puri, niente database, niente server strano.

<img src="/assets/img/appunto_hugo.webp">

## Installazione

Su Mac:

{{< code lang="bash" >}}brew install hugo{{< /code >}}

Su Windows: scarica l'exe da `github.com/gohugoio/hugo/releases` e mettilo nel PATH (rompiscatole ma si fa una volta sola).

Verifica che funzioni:

{{< code lang="bash" >}}hugo version{{< /code >}}

## Creare il primo sito

{{< code lang="bash" >}}hugo new site nomesito
cd nomesito{{< /code >}}

La struttura che crea:

- `content/` → i post e le pagine in Markdown
- `layouts/` → i template HTML
- `static/` → CSS, immagini, JS — funziona esattamente come siamo abituati
- `hugo.toml` → config generale (titolo sito, lingua ecc.)

## Il tema — farlo da zero

Siccome sappiamo già html/css, meglio non usare un tema altrui all'inizio, si capisce poco.

`layouts/_default/baseof.html` → è il layout base, il "guscio" di ogni pagina:

```html
<!DOCTYPE html>
<html>
<head>
  <title>{{ .Title }}</title>
  <link rel="stylesheet" href="/css/style.css">
</head>
<body>
  {{ block "main" . }}{{ end }}
</body>
</html>
```

`layouts/_default/single.html` → per le singole pagine/post:

```html
{{ define "main" }}
<h1>{{ .Title }}</h1>
{{ .Content }}
{{ end }}
```

`layouts/index.html` → per l'homepage. Il CSS va in `static/css/style.css` — uguale a sempre.

## Scrivere un contenuto

{{< code lang="bash" >}}hugo new content posts/primo-post.md{{< /code >}}

In cima al file trovi il front matter:

```toml
+++
title = 'Primo post'
date = 2024-01-01
draft = true
+++
```

`draft = true` significa che non viene pubblicato. Cambiarlo in `false` quando è pronto. Il testo del post si scrive sotto in Markdown.

## Server locale

{{< code lang="bash" >}}hugo server -D{{< /code >}}

`-D` include anche le bozze. Va su `localhost:1313` — si aggiorna da solo mentre modifichi.

## Build

{{< code lang="bash" >}}hugo{{< /code >}}

Genera tutto nella cartella `public/` — quella si carica sull'hosting.

## Cose che mi hanno confuso

I file in `layouts/` devono rispettare la struttura esatta dei nomi, sennò Hugo non li trova e non dice niente — silenzio totale, bestiale.

Le variabili Hugo dentro l'HTML si scrivono con `{{ }}` — all'inizio sembra strano ma ci si abitua. `{{ .Title }}` prende il titolo dal front matter, `{{ .Content }}` mette il testo markdown già convertito in HTML.

{{< nota tipo="processo" >}}
Da rivedere: capire meglio i "partials" — tipo gli include di PHP, per header/footer riutilizzabili.
{{< /nota >}}
