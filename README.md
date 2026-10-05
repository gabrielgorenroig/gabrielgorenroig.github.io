# gabrielgorenroig.github.io

Sitio personal, hecho con Jekyll sobre el tema [al-folio](https://github.com/alshedivat/al-folio) y publicado con GitHub Pages.
Este archivo es la referencia de cómo está organizado el contenido y de cómo editarlo.
No se publica en el sitio (está en `exclude` en `_config.yml`).

## Dónde está cada cosa

| Contenido | Archivo(s) | Se muestra en |
|---|---|---|
| Texto de presentación, foto | `_pages/about.md` | landing (`/`) |
| Noticias | `_news/*.md` (+ posts con `news: true`) | landing (últimas 3) y `/news/` |
| Charlas y posters | `_data/talks.yml` | landing, sección "Talks" |
| Publicaciones | `_bibliography/papers.bib` | `/publications/` |
| Blog | `_posts/*.md` | `/blog/` |

La landing se arma en `_layouts/about.liquid`; la cantidad de noticias que muestra se cambia con `announcements.limit` en `_pages/about.md`.

## Noticias

Hay tres modalidades. Todas aparecen en la misma lista de noticias, ordenadas por fecha (`_includes/news.liquid`).

### 1. Noticia corta (inline)

Archivo en `_news/`, con `inline: true`. El texto completo aparece en la lista; no hay página propia enlazada.

```markdown
---
layout: post
date: 2025-06-21
inline: true
related_posts: false
---

Texto de la noticia, con [links](https://...) y _itálicas_.
```

### 2. Noticia larga con página en `/news/` (`inline: false`)

Archivo en `_news/`, con `inline: false`. En la lista aparece el primer párrafo seguido de "Read more →", que lleva a `/news/<nombre-del-archivo>/` con el texto completo.

```markdown
---
layout: post
title: Título que aparece en la página completa
date: 2025-10-07
inline: false
related_posts: false
---

Primer párrafo: esto es lo que se ve en la lista.

Resto: solo en la página completa.
```

Usarla para algo más largo que una noticia corta, pero que no tiene sentido como entrada del blog.

### 3. Blog post que además es noticia (`news: true`)

Archivo en `_posts/` (nombre `AAAA-MM-DD-titulo.md`) con `news: true`. Es un post normal del blog: aparece en `/blog/`, con su URL `/blog/AAAA/titulo/`, tags, archivo por año, RSS, etc. Además aparece en la lista de noticias con el primer párrafo y "Read more →" hacia el post.

```markdown
---
layout: post
title: Título del post
date: 2025-10-07
news: true
tags: [teaching]
---

Primer párrafo: esto es lo que se ve en la lista de noticias.

Resto del post...
```

### Diferencias entre las modalidades 2 y 3

Las dos usan la misma plantilla (`_layouts/post.liquid`) y en la lista de noticias se ven igual. Cambia dónde vive la página completa:

| | 2. `_news/` + `inline: false` | 3. `_posts/` + `news: true` |
|---|---|---|
| URL | `/news/<archivo>/` | `/blog/AAAA/<titulo>/` |
| Aparece en `/blog/` | no | sí |
| Año, tags y categorías enlazados | no | sí |
| Archivo por año/tag, RSS, related posts | no | sí |

### Detalles comunes

- **Extracto:** por defecto es el primer párrafo (hasta la primera línea en blanco). Para cortar en otro lugar, agregar `excerpt_separator: <!--more-->` al front matter y poner `<!--more-->` en el texto.
- **Título:** en la lista de noticias nunca se muestra; solo en la página completa. Si falta `title:`, Jekyll inventa uno a partir del nombre del archivo, así que en las modalidades 2 y 3 conviene ponerlo siempre.
- **Fecha:** el orden lo da el campo `date:`.

## Charlas y posters

Una entrada por charla en `_data/talks.yml`, de la más reciente a la más vieja (se muestran en el orden del archivo):

```yaml
- date: Jul 2025            # texto libre, se muestra tal cual
  title: Arboreal Coreflections
  event: Topos Institute Seminar
  location: Berkeley, California, USA   # opcional
  poster: true              # opcional: agrega la etiqueta "POSTER"
  links:                    # opcional
    - label: recording
      url: https://www.youtube.com/watch?v=...
```

Los links pueden ser externos o rutas del sitio (por ejemplo `/assets/pdf/poster.pdf`).

## Publicaciones

Entradas BibTeX en `_bibliography/papers.bib`, procesadas por jekyll-scholar con la plantilla `_layouts/bib.liquid`. Campos propios del tema: `arxiv`, `selected`, `pdf`, `slides`, etc. (ver `filtered_bibtex_keywords` en `_config.yml`).

## Preview local

```bash
bundle exec jekyll serve --livereload
```

El sitio queda en http://localhost:4000. Al guardar cambios en el contenido, la página se regenera y se recarga sola. Los cambios en `_config.yml` requieren reiniciar el servidor.

Si Ruby tiene variables de gems de otro entorno, puede hacer falta `unset GEM_HOME GEM_PATH BUNDLE_PATH` antes. `Gemfile.lock` está en `.gitignore`: en un worktree nuevo hay que copiarlo desde el checkout principal.
