---
title: "Hugo — basics"
date: 2026-01-20
type: "blocco-appunti"
draft: false
layout: "single"
---

Hugo is a static site generator. That means it spits out pure `.html` files — no database, no weird server.

## Installation

On Mac:

{{< code lang="bash" >}}brew install hugo{{< /code >}}

On Windows: download the exe from `github.com/gohugoio/hugo/releases` and add it to PATH (annoying but you only do it once).

Verify it works:

{{< code lang="bash" >}}hugo version{{< /code >}}

## Creating your first site

{{< code lang="bash" >}}hugo new site mysite
cd mysite{{< /code >}}

The structure it creates:

- `content/` → posts and pages in Markdown
- `layouts/` → HTML templates
- `static/` → CSS, images, JS — works exactly as you'd expect
- `hugo.toml` → general config (site title, language, etc.)

## The theme — building from scratch

Since we already know HTML/CSS, it's better not to use someone else's theme at first — you learn very little that way.

`layouts/_default/baseof.html` → the base layout, the "shell" for every page:

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

`layouts/_default/single.html` → for individual pages/posts:

```html
{{ define "main" }}
<h1>{{ .Title }}</h1>
{{ .Content }}
{{ end }}
```

`layouts/index.html` → for the homepage. CSS goes in `static/css/style.css` — same as always.

## Writing content

{{< code lang="bash" >}}hugo new content posts/first-post.md{{< /code >}}

At the top of the file you'll find the front matter:

```toml
+++
title = 'First post'
date = 2024-01-01
draft = true
+++
```

`draft = true` means it won't be published. Change it to `false` when ready. The post content goes below in Markdown.

## Local server

{{< code lang="bash" >}}hugo server -D{{< /code >}}

`-D` includes drafts too. Visit `localhost:1313` — it live-reloads as you edit.

## Build

{{< code lang="bash" >}}hugo{{< /code >}}

Generates everything in the `public/` folder — that's what you upload to hosting.

## Things that confused me

Files in `layouts/` must follow the exact naming structure, otherwise Hugo just won't find them and says nothing — complete silence, infuriating.

Hugo variables inside HTML use `{{ }}` — it looks weird at first but you get used to it. `{{ .Title }}` pulls the title from the front matter, `{{ .Content }}` inserts the markdown already converted to HTML.

{{< nota tipo="processo" >}}
To revisit: better understand "partials" — like PHP includes, for reusable header/footer.
{{< /nota >}}
